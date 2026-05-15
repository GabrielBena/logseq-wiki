title:: wiki/refs/meszaros-2025-space-as-time
category:: reference
type:: external-ref
tags:: spatial-embedding, learnable-delays, spiking-neurons, structure-function-gap, modularity, neuromorphic
authors:: Mészáros, Balázs; Knight, James C.; Akarca, Danyal; Nowotny, Thomas
year:: 2025
venue:: arXiv preprint
arxiv:: 2511.01632
doi:: 10.48550/arXiv.2511.01632
citation-count:: 1
summary:: Neuron positions as learnable parameters where synaptic delays = Euclidean distance. Position learning links structure to task, induces clustered modular topology, *and produces functional specialisation aligned with spatial clustering* — the missing temporal piece for the structure-function gap.
confidence:: 0.85
lifecycle:: draft
lifecycle-changed:: 2026-05-15
created:: 2026-05-15
updated:: 2026-05-15
sources:: arXiv:2511.01632 (full PDF, 14 pages, ~6500 words; cached in /tmp during ingest)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Space as Time Through Neuron Position Learning** — Mészáros, Knight, Akarca & Nowotny, arXiv:2511.01632 (Nov 2025). Affiliations: Sussex AI (Mészáros, Knight, Nowotny — mlGeNN group), Imperial College Electrical Engineering (Akarca), MRC Cognition & Brain Sciences Unit Cambridge (Akarca). Code: github.com/mbalazs98/spatialdelays + mbalazs98/ml_genn/position_learning branch. Data: sussex DOI 30455591.
- ## TL;DR
	- Standard ANNs treat physical position as irrelevant to dynamics; biological networks treat distance-induces-delay as a *computational substrate*. This paper unifies spatial embeddings (Achterberg et al. 2023 sernns) and learnable synaptic delays (Bohte 2002, Mészáros et al. 2025, Göltz et al. 2025) through a **single mechanism**: **delays = Euclidean distance between neurons**, with positions as learnable parameters.
	- Mathematical core: `d_{ji} = √((x_i - x_j)² + (y_i - y_j)²)`. Spike arrival time at neuron j of spike emitted by neuron i at time t is `t_j = t + d_{ji}`. Light-cone analogy: each spike has a cone of spatiotemporal influence (Figure 1A); where cones intersect strongly enough, downstream neurons fire.
	- **Position-learning gradient** derived via chain rule: `∂L/∂x_i` flows from `∂L/∂d_{ji}` (the delay-learning gradient from Mészáros 2025) times the geometric `∂d_{ji}/∂x_i = (x_i - x_j)/d_{ji}`. Number of position parameters scales as `n × d` (where `d` = embedding dim) vs `n²` for direct delay learning — substantial compression.
	- **Three settings tested** on Spiking Heidelberg Digits (SHD) classification with a 128-neuron recurrent SNN: **Non-spatial** (free delays), **Spatial** (positions learned, delays = distance), **Spatial+cost** (Spatial + L1 regularisation weighted by distance — Achterberg-style wire cost).
	- **Headline result**: **functional specialisation emerges spatially aligned without being explicitly enforced**. Hidden neurons that respond to similar input frequencies cluster together; preferred target positions form trajectory-like structures; pruning long-range connections *increases* both modularity and clustering. This is the structural prediction Gabriel's Ch2 was missing — *delays are the computational reason for spatial structure to align with function*.
- ## The light-cone analogy and the position-learning algorithm
	- ### Why space-as-time matters
		- Biological neural networks live in physical space where axonal conduction is bandwidth-limited (Swadlow 1985). Distance between somata determines transmission delay. Evolution has exploited this — the barn-owl interaural-time-difference system (Carr & Konishi 1988) uses precisely tuned spatial delays to localise sound.
		- Most ANNs discard this entirely: layers are abstract; "distance" between units has no temporal meaning. Recent work introduced spatial embeddings for *cost* (Achterberg 2023; Erb 2026; Sheeran 2024) but not for *computational benefit*. Mészáros et al.'s contribution is to give space a *computational role* via delays.
	- ### The learning algorithm
		- Parameters: `(x_i, y_i)` per neuron + standard SNN weights + LIF dynamics. Delays implied by distances (eq. 1). Spike arrival times shifted accordingly (eq. 2).
		- Gradient w.r.t. position (eq. 6): combines the *delay gradient* `∂L/∂d_{ji} = -w_{ji} Σ_{spikes from i} (λ_I - λ_V)_j|_{t_k + d_{ji}}` (from Mészáros 2025's event-based delay learning) with the geometric `∂d_{ji}/∂x_i = (x_i - x_j)/d_{ji}`. Both pre- and post-synaptic gradients contribute; magnitudes normalised by distance from the other neuron.
		- Built on the GeNN simulator + mlGeNN framework (Knight & Nowotny 2023) using EventProp-style exact event-based backprop (Wunderlich & Pehle 2021; Nowotny, Turner, Knight 2025).
		- Delay distribution inherits from Euclidean distance: zero-diagonal (self-connections instantaneous), symmetric (`d_{ji} = d_{ij}`), satisfies triangle inequality. These are biologically natural constraints "for free".
	- ### The Spatial+cost variant
		- L1 regularisation on hidden weights, with each penalty weighted *proportionally* to distance between connected neurons. Distances renormalised by mean so regularisation strength is comparable across geometries. This is Achterberg sernns wire-cost generalised to dynamic geometries.
- ## Key findings
	- ### Position learning links structure to task (Section 2.1)
		- Train on SHD; visualise neuron positions over training. **Networks grow during training** — some neurons diverge outward, others stay near center (Figure 1E). Final spatial structure is *task-shaped*: not arbitrary, not collapsed.
		- The non-trivial part: positions don't simply find some convenient embedding. They organise around the *temporal demands* of the task.
	- ### Nearby neurons become functionally connected (Section 2.2)
		- Ridge regression of hidden-neuron positions from input-hidden weights: **R² high across all conditions** (≈0.7-0.9), particularly for Spatial+cost. Position is *predictable from input connectivity*.
		- "Preferred target positions" of input neurons (weighted by either input-hidden weight or input-hidden activity correlation) **localise by audio frequency** — neurons tuned to similar input frequencies project to nearby hidden regions.
		- **Trajectory-like structures emerge** in preferred positions: weak regularisation → loose clustering; strong regularisation → smooth trajectories tracing frequency space (Figure 2C, 2D). This is **emergent topographic mapping** — frequency-to-space without explicit topographic loss.
		- Even more striking: **centre-of-mass of input influence migrates spatially over time within a trial**. Early time steps → positions near network centre (short delays, fast feature extraction). Late time steps → positions toward periphery (long delays, integration of accumulated info). **Temporal hierarchy emerges spatially** — consistent with Moro et al. 2024's "temporal hierarchy in spiking networks".
	- ### Short vs long delays under constraints (Section 2.3)
		- Increasing L1 regularisation: network shrinks, sparsity rises. At *extreme* regularisation, non-spatial networks **collapse to no recurrent connections**, while spatial networks retain *structured* connectivity by moving neurons close together.
		- Delay distributions across architectures: **concentrated in the short range, with a heavy tail of essential long delays**. Spatial networks have *fewer but more important* long connections — the few that survive are computationally necessary, not redundant. This is exactly the "rich-club hubs" structure from connectomics.
	- ### Learnt topology is constraint-dependent (Section 2.4)
		- **Modularity** (weighted, Rubinov & Sporns 2010): Spatial+cost shows *monotonic increase* with regularisation strength — reaching ~0.75 at strong reg. Non-spatial and Spatial-without-cost peak at *medium* regularisation then plateau. **Distance-weighted regularisation is the load-bearing ingredient for modularity** — not spatial embedding alone, not L1 alone.
		- **Clustering coefficient**: similar pattern. Spatial+cost wins at high regularisation.
		- **Wiring efficiency** (against random shuffled null): Spatial+cost reaches ~1.0 (optimal) while non-spatial stays ~0.4. The framework finds *efficient* networks.
	- ### Position learning converges on more local solutions (Section 2.5)
		- Without explicit cost, pure position-learning networks **still gravitate toward short connections** (Figure 6B). Magnitude-pruning and random-pruning behave similarly across architectures; **delay-length-based pruning preserves spatial networks but destroys non-spatial ones**.
		- Pruning longest connections in spatial networks: **modularity and clustering both increase** — pruning *reveals* the underlying structure rather than degrading it. This is strong evidence that spatial position-learning embeds an *inductive bias toward locality* that pure delay-learning does not.
	- ### Why don't all neurons collapse to one point?
		- This is the central question the Discussion explicitly raises and answers. If positions were free and short connections were cheaper (less delay, less L1), why don't all neurons converge to the same coordinate?
		- **Because the temporal computation requires diverse delays.** Some neurons MUST sit far from others to provide the long delays that the SHD task needs for integration. Distance is no longer purely a cost — it's a *resource* the network spends to perform the temporal task. **Resource constraints work because distance has a computational benefit, not just a cost.**
		- This resolves a long-standing tension in spatial-embedding ML: Achterberg et al. used fixed positions because allowing them to be free would have collapsed the network. Mészáros et al. show that *temporal coupling unlocks free positions*.
- ## Direct relevance to Gabriel's research — load-bearing
	- ### **The missing ingredient for the structure-function gap**
		- Gabriel's [[wiki/research/dynamics-specialization]] (Ch1, Béna & Goodman 2025, *explicitly cited by this paper as an extension target*) and [[wiki/research/spatial-neuromorphic-priors]] (Ch2) both found a *structure-function gap*: spatial / wire-cost constraints produce **structural modularity** but **not functional specialisation**. The thesis Discussion flagged this as the central open question.
		- Mészáros et al. closes that gap when *delays are added*: **functional specialisation emerges aligned with spatial clustering, without being explicitly enforced**. The Spatial+cost condition (which most closely matches Ch2's Spatial DEEP-R + distance penalty) reaches monotonic modularity AND preferred-target-position trajectories aligned with input frequencies. The Ch2 result *would predict* spatial structure without functional specialisation; this paper's Spatial+cost result *contradicts* that prediction when delays are part of the dynamics.
		- The strong testable conjecture: **add learnable delays to Ch2's Spatial DEEP-R and the structure-function gap closes**. The L1+distance regulariser was the right idea; the missing ingredient was that the network must have a *temporal computational reason* for the spatial structure to matter, which delays supply. ^[claude-synth]
		- This is also Mészáros et al.'s explicit Discussion direction: "extending this analysis to modular tasks (Béna & Goodman, 2025) with an added temporal structure ... provide a promising avenue for extending this mechanistic analysis." Direct invitation to collaborate or build on. ^[extracted]
	- ### Direct connection to [[wiki/concepts/developmental-latent-space]]
		- The developmental-latent-space concept proposes `p_i = φ(g_i)` — position derived from engram. Mészáros et al. provide the *computational reason for position to matter*: positions determine delays, delays support temporal computation, gradient flows back to positions, positions back to engrams.
		- Combined view: **engrams determine positions; positions determine delays; delays support temporal computation; temporal computation drives the loss; loss flows back to engrams**. This is the full closed loop the concept page was missing. The connection prior `P(i↔j) = σ(f_θ(g_i, g_j, d_ij))` now has a *second* role for `d_ij`: not just connection probability, but *transmission delay* once connected. ^[claude-synth]
		- Worth a new Decisions log entry on the project page: should `d_ij` in the engram-manifold framing serve double duty (connection prior + delay), or should we separate them? Biology argues for double duty (Mészáros et al.'s point — distance has both meanings simultaneously). ^[claude-synth]
	- ### Connection to the [[wiki/projects/growing-networks]] structural-side mechanism
		- The 2026-05-15 brainstorm proposed "continuous attention with sparsemax over `(engram-compat − λ·distance)`" as the differentiable structural mechanism. Mészáros et al. adds: **distance also contributes a computational benefit** (delay-supports-temporal-tasks), not just a cost.
		- For SNN-flavoured operationalisations of growing-networks: this paper is the *closest existing engineering implementation*. Their architecture (rsnn + learnable positions + L1+distance) is essentially the SNN version of the structural-side mechanism the project sketches. **Should be a direct baseline once the engineering work begins.** ^[claude-synth]
	- ### Connection to the INI/Payvand/Imperial cluster
		- The reference list reads like Gabriel's intellectual neighbourhood:
			- **Béna & Goodman 2025** (your Ch1 paper, Nature Comms) — cited in Discussion as a target extension.
			- **Achterberg et al. 2023** (sernns) — the spatial-embedding baseline this paper extends.
			- **Dalgaty et al. 2024 (Mosaic)** — cited as "explicitly relies on clustered connectivity" — directly aligned with this paper's spatial+cost result. Confirms [[wiki/refs/dalgaty-2024-mosaic]] as the right hardware target.
			- **Bellec et al. 2018 (DEEP-R)** — cited; the Discussion explicitly mentions extending DEEP-R with position-learning as a next step: *"introducing distance awareness with position learning to DEEP R could yield interesting network geometries, as neuron positions would no longer need to be constrained to a hypersphere, but merely comply with system constraints."* — this is **exactly what Spatial DEEP-R from Ch2 + position-learning would look like.** ^[claude-synth]
			- **Weber, Ballet, Payvand 2025** — Jimmy Weber + Melika Payvand (Gabriel's PI). Hardware-routing-aware DEEP-R extension. Cited as motivation.
			- **Göltz, Weber, Kriener, Billaudelle, Lake, Schemmel, Payvand, Petrovici 2025** — *Delgrad*: exact event-based gradients for delays+weights on neuromorphic hardware. Same INI cluster.
			- **Sun, Achterberg, Su, Goodman, Akarca 2025** — Dan Goodman (your supervisor) + Akarca (this paper's coauthor). Exploiting heterogeneous delays for efficient computation.
		- The picture: **a Sussex+Imperial+Cambridge+INI cluster is converging on spatial+delay+resource-constraint SNNs**, and they explicitly want to incorporate Ch1's modular-task framework. Strong collaboration vector / co-publication target. ^[claude-synth]
	- ### Connection to [[wiki/refs/stockl-2021-structure-induces-computational-function]] (probabilistic skeletons)
		- Stöckl/Maass uses `exp(-d²/σ²)` as the connection-probability decay — distance is a *probabilistic cost*. Mészáros et al. uses `d_{ji}` as the *transmission delay*. **Both papers operate on the same `d_{ji}` quantity but extract different computational structure from it**: Stöckl uses it for connectivity, Mészáros uses it for timing. Combining: a network where `d_{ji}` determines both *whether* `i` and `j` connect (via probability) and *when* signals arrive between them (via delay). This is the most complete spatial-SNN picture in the literature. ^[claude-synth]
	- ### Connection to [[wiki/refs/kerstjens-2026-lineage-positional]]
		- Kerstjens: positions are inherited via lineage. Mészáros: positions are learnable parameters of the computational dynamics. **The two are about different timescales** — Kerstjens's positions emerge from development; Mészáros's positions emerge from task gradient. In the engram-manifold framing, slow lineage positions (Kerstjens) shape the initial geometry; fast task gradient (Mészáros) refines it under the temporal demands of the active layer. Strongly compatible. ^[claude-synth]
- ## Limitations / Open Questions
	- **Small networks (128 hidden neurons)**. The authors note they "deliberately focus on small networks ... [but] this choice does not reflect an inherent limitation of SNNs". Scaling open.
	- **Only input-hidden specialisation was analysed**, not internal hidden specialisation. The paper notes the limited internal temporal structure of SHD as a likely reason; modular tasks (à la Béna & Goodman 2025) would force internal specialisation.
	- **No volume exclusion / repulsive force between neurons.** Neurons can be arbitrarily close (provided not coincident). Real biology has volume exclusion; introducing it is flagged as future work.
	- **2D embeddings only in the main results.** Higher-dimensional and dynamic-dimension embeddings (Tohouri's MSc thesis is cited as exploring 3D) are open.
	- **Spatial+cost dominates**, but the *separation* of effects (geometric induction from distance learning, vs explicit cost-driven sparsification) needs more careful ablation. The paper does the work for SHD; the conclusion may be task-dependent.
- ## Connections to Wiki
	- [[wiki/research/dynamics-specialization]] — **cited by this paper as an extension target**. Gabriel's Ch1 modular-task framework is what Mészáros et al. propose to extend with temporal structure.
	- [[wiki/research/spatial-neuromorphic-priors]] — **the missing piece**: Ch2's structure-function gap finding gets a candidate resolution (add delays).
	- [[wiki/refs/bellec-2018-deep-r]] — DEEP-R is cited as a base algorithm to extend with position-learning. Spatial DEEP-R + position-learning is a direct next-step research direction.
	- [[wiki/refs/dalgaty-2024-mosaic]] — Mosaic hardware "explicitly relies on clustered connectivity"; this paper's clustered-modular result is the algorithmic counterpart.
	- [[wiki/refs/stockl-2021-structure-induces-computational-function]] — distance enters both papers, used for connectivity probability (Stöckl) vs transmission delay (Mészáros). Composable.
	- [[wiki/refs/kerstjens-2026-lineage-positional]] — slow biological positions (lineage) vs fast learnable positions (Mészáros) at different timescales.
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]] — S-GEM's gene-Gaussian-on-grid is one parameterisation of `φ`; Mészáros's free position-learning is another. The two are different operating points on the design space.
	- [[wiki/refs/achterberg-2023-sernns]] — direct predecessor (fixed-position spatial RNN); this paper is the *learnable-position + delay* extension.
	- [[wiki/concepts/developmental-latent-space]] — closes the loop: positions matter because delays support temporal computation; gradient flows back through positions to engrams.
	- [[wiki/concepts/modularity]] — the structure-function gap (Pessoa side too); this paper produces functional specialisation aligned with structure, when temporal computation is the substrate.
	- [[wiki/projects/growing-networks]] — most direct engineering reference for the structural-side mechanism in the SNN context.
	- [[wiki/concepts/genomic-bottleneck]] — `n × d` position parameters vs `n²` delays is a bottleneck-style compression; positions are the compact code, the delay matrix is emergent.
	- [[wiki/concepts/neural-cellular-automata]] — the light-cone framing (Figure 1A) is essentially an NCA visualisation: each spike has a cone of influence in spacetime; computation happens where cones intersect.
- ## Cited By (in this wiki)
	- [[wiki/concepts/developmental-latent-space]] (pending update — delays close the position-learning loop)
	- [[wiki/research/spatial-neuromorphic-priors]] (pending update — candidate resolution to the Ch2 structure-function gap)
	- [[wiki/projects/growing-networks]] (pending update — Decisions log on dual role of `d_ij`)
