title:: wiki/refs/stockl-2021-structure-induces-computational-function
category:: reference
type:: external-ref
tags:: spiking-neurons, genomic-bottleneck, neuron-types, innate-computation, structure-function
authors:: Stöckl, Christoph; Lang, Dominik; Maass, Wolfgang
year:: 2021
venue:: bioRxiv (v4 posted 2022-07-06)
doi:: 10.1101/2021.05.18.444689
biorxiv:: 2021.05.18.444689
citation-count:: 14
summary:: Probabilistic skeleton — a 5-parameter generative model for cortical microcircuits (K neuron types, prevalences, type-pair connection probabilities, 3 uniform weights, σ distance-decay). Optimised via evolution strategies; produces innate computing in spiking nets at fraction of weight-tuning parameters.
confidence:: 0.7
lifecycle:: draft
lifecycle-changed:: 2026-05-15
created:: 2026-05-14
updated:: 2026-05-15
sources:: assets/2021.05.18.444689v4.full.pdf (full PDF, 34 pages; economical pass — read intro, methods, discussion; skipped detailed results sections per user direction)
wiki-generated:: true
ingest-mode:: full-economical
provenance-extracted:: 0.7
provenance-inferred:: 0.25
provenance-ambiguous:: 0.05

- **Structure induces computational function in networks with diverse types of spiking neurons** — Stöckl, Lang & Maass (Institute of Theoretical Computer Science, Graz University of Technology), bioRxiv preprint v4 (July 2022). DOI:10.1101/2021.05.18.444689. 34 pages, 14 citations.
- ## TL;DR
	- The **probabilistic skeleton** is a 5-component generative model for cortical-microcircuit-style recurrent spiking networks (RSNNs):
		1. **K** — number of neuron types (set to 6 in main illustrations; cortex has ~100+ per Tasic 2018)
		2. **Prevalences** `p_I` — fraction of each type per minicolumn
		3. **Base connection probabilities** `p_{I→J}` — for every directed pair of types, the connection probability when somata are within ~75μm (one minicolumn diameter)
		4. **Three uniform synaptic weights** `w_in, w_E, w_I` — one each for external inputs, excitatory recurrent, inhibitory recurrent. All synapses in a class share the same weight.
		5. **Distance decay parameter** `σ` — exponential drop-off of connection probabilities with horizontal distance
	- Sampling rule (eq. 4): `P[synapse i→j] = p_{I→J} · exp(-Dist(i,j)² / σ²)`. The number of synaptic contacts between any pair is drawn S=8 times from this Bernoulli, giving binomial multiplicity.
	- **No synaptic plasticity required.** Optimising the ~tens-of-parameters skeleton via **Separable Natural Evolution Strategies (NES)** is sufficient to produce networks with non-trivial *innate* computing capabilities — but only when K is "substantial" (more than classical ANN models use).
	- **Three computational capabilities demonstrated** (results skipped per user direction): generic 2D pattern matching (delayed similarity judgment), spike-time discrimination (4-way classification of inter-wave delays), and motor control (continuous limb control via spike output).
	- **Side benefits**: total wire length grows *linearly* with neuron count, and networks are *robust to weight perturbations* — both essential for biological tissue and for memristor-based neuromorphic hardware.
- ## Core formulation
	- ### What a probabilistic skeleton is
		- A *generative model* over RSNN architectures. Sampling a network requires:
			- Picking `n_mcol` minicolumns (each containing M ≥ K neurons distributed per type prevalences)
			- For each ordered pair of neurons (i, j), drawing S=8 Bernoulli trials with probability `p_{I→J} · exp(-Dist(i,j)²/σ²)`. The count of "successes" is the synaptic multiplicity `m_ij`.
			- Effective connection strength = `m_ij × w_class(i)` where `w_class` is `w_in`, `w_E`, or `w_I` depending on source neuron type.
		- *What the skeleton does NOT specify*: individual synaptic weight values (all synapses of a class share a single weight); spatial position beyond type-and-distance (positions are uniform within minicolumn discs); plasticity (none — the rule produces fixed weights).
		- *What the genome encodes*: type taxonomy + type-conditioned connection probabilities + 3 weight scales + distance decay. **Total parameter count is O(K²)**, regardless of N — same compression argument as Barabási's GEM ([[wiki/refs/barabasi-2023-complex-computation-developmental-priors]]).
	- ### Spatial substrate
		- Neurons are placed at the centres of minicolumn discs (~60μm diameter, 80-120 neurons each). The 2D sheet of discs is the cortical analogue. *Each disc is a stereotypical minicolumn* (Mountcastle, DeFelipe).
		- The distance-decay function in eq. 4 is *not* restricted to local discs — connections can span the whole sheet, just with exponentially-decreasing probability. The σ ∈ [60μm, 200μm] range in the figures covers within-column to several-column reach.
	- ### Neuron model
		- Discrete-time GLIF_1 (Generalized Leaky Integrate-and-Fire, model 1) from Teeter et al. 2018. Parameters drawn from Allen Institute V1 type templates. The full neuron-level biophysics is *fixed* per type, not part of the skeleton's optimisable parameters.
	- ### Optimisation
		- **Separable NES** (Wierstra et al. 2008, Schaul/Glasmachers/Schmidhuber 2011). Why evolution strategies and not gradient descent? *The skeleton-to-RSNN map involves Bernoulli sampling — the fitness function is non-differentiable w.r.t. skeleton parameters*. NES estimates gradients via sampled perturbations.
		- The base-probability parameters are passed through a sigmoid (`p_{I→J} = σ(κ_{I→J})`) to stay in [0,1].
		- Hyperparameters (number of types K, distance scale σ) optimised by separate search rather than gradient.
- ## Why K (neuron-type count) is load-bearing
	- The paper's central claim: **structure can induce function *only if K is large enough***. With K=1 or K=2 (typical of classical ANNs), the type-conditioned probability table collapses to near-uniform; with K=6 to dozens, the table can encode rich connectivity patterns.
	- Quantitative answer to "how many types needed" is task-dependent; main illustrations use K=6 but the paper argues for "a fair number" (likely several to dozens). ^[partial — full quantitative answer is in the results sections not deeply read]
	- This is the paper's strongest contribution to the neuroscience question of cell-type proliferation: *the brain has many cell types because the type-conditioned wiring rule needs them for innate function*. Classical ANN reductions to 1-2 types lose this capacity.
- ## Discussion — what the authors emphasise
	- ### Three flavours of operationalising the genomic bottleneck
		- The Discussion explicitly compares three contemporaneous approaches:
			- **Koulakov, Shuvaev & Zador 2021** — abstract approach: connection-existence determined by *linear operations on binary codes* for neurons. Most abstract; no cell biology.
			- **Barabási & Beynon 2021** (now [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]]) — *transcription-factor compatibility rules*. Concrete, ML-tested; weights emergent from gene-pair interactions.
			- **Stöckl/Lang/Maass (this paper)** — *type-conditioned probability tables with experimentally-grounded substrate*. Most directly comparable to Allen Institute cell-type / connectivity data (Markram 2015, Billeh 2020, Tasic 2018).
		- Each parameterisation makes the bottleneck encoding concrete in a different way; the three approaches are complementary. The wiki should note all three as parallel operationalisations.
	- ### Probabilistic skeletons subsume cellular automata
		- "Cellular automata are special cases of 2D sheets of neural circuits that can be induced through a probabilistic skeleton." A CA is essentially a uniform 2D sheet of identical cells with neighbour-only connections; probabilistic skeletons relax this to type-varied cells with distance-modulated connections.
		- But probabilistic-skeleton RSNNs are *more powerful than CAs* because connections aren't restricted to immediate neighbours — long-range connections are sampled with lower probability, not forbidden. This is the link Hiesinger ([[wiki/refs/hiesinger-2021-self-assembling-brain]]) draws between Rule 110 and brain self-assembly, made differentiable.
		- The reverse mapping (NCA recovers probabilistic-skeleton behaviour) is worth flagging as a research direction: an NCA whose per-cell rule is conditioned on cell type and where attention scales like `exp(-d²/σ²)` is essentially a probabilistic skeleton run as an NCA. ^[claude-synth]
	- ### Brain-economy and neuromorphic-hardware implications
		- **Linear wire length**: total wires grow as O(N), not O(N²). Essential for any physical implementation (brain or chip).
		- **Robustness to weight perturbations**: with weights determined by `m_ij × w_class`, individual synapse values can vary substantially without functional impact. Memristor-style implementations (with their analog noise) become viable.
		- **Organoid applications**: the authors specifically mention brain-organoid engineering as a target — induce computational function through structured connectivity without invoking plasticity.
- ## Direct relevance to the developmental-latent-space concept
	- ### Type-conditioned table = `O` in Barabási's `X O X^T` = `f_θ(g_i, g_j)` in our concept
		- Stöckl/Maass's `K × K` base-probability table is the *discrete* version of Barabási's `G × G` gene-interaction matrix `O`. When you let "type" become a continuous engram vector (Kerstjens-style eigengene), the discrete table relaxes to a continuous bilinear (or MLP) form. The conceptual lineage is **discrete cell types (Stöckl) → continuous gene profiles (Barabási) → continuous engrams on a manifold ([[wiki/concepts/developmental-latent-space]])**. ^[claude-synth]
	- ### Distance decay `exp(-d²/σ²)` is the canonical form of `λ·distance` in our sparsemax formula
		- The developmental-latent-space concept proposes a connection score `(engram-compat − λ·distance)` with sparsemax for differentiable hard budget. Stöckl/Maass uses `exp(-d²/σ²)` multiplicatively. **These are equivalent up to choice of monotone transform**: `log(P) = log(p_{I→J}) − d²/σ²`, so working in log-probability space, Stöckl's formulation matches `(engram-compat + spatial-term)` with a Gaussian spatial kernel. The σ in Stöckl is the engineering counterpart of our `λ`. ^[claude-synth]
	- ### Type diversity argues for *high-dimensional* engrams
		- Stöckl/Maass: K=1 or 2 doesn't work; need K ≈ 6+ for innate function. **For continuous engrams this likely means dimensionality of the engram vector matters more than channel count** — but a working operating range of "rich enough to support a 6+-cluster basin structure on the manifold" is a useful design constraint. The eigengene story in [[wiki/refs/kerstjens-2026-lineage-positional]] suggests effective dimensionality ≈ tens (each eigengene-level partition), consistent with Stöckl's K. ^[claude-synth]
	- ### Evolution strategies because the sampling is non-differentiable — and the alternative
		- Stöckl/Maass uses NES because the Bernoulli sample step blocks gradient flow. The developmental-latent-space concept's *sparsemax over (engram-compat − λ·distance)* is the differentiable analogue: instead of sampling and getting a non-differentiable W, sparsemax returns a soft-but-sparse weight matrix end-to-end. **This is one of the main engineering advantages of the engram-manifold framing over a literal Stöckl/Maass replication**: we don't need evolution strategies; backprop works directly. ^[claude-synth]
	- ### "No plasticity required" is the strongest form of the structure-induces-function argument
		- Stöckl/Maass demonstrates that structure ALONE — no synaptic plasticity, no learning — can produce non-trivial spiking-network function. In our engram-manifold framing, the equivalent is: *the slow engram timescale can produce a useful active-layer scaffold without any fast-layer plasticity*. Whether this holds for ML benchmarks is a strong testable prediction. ^[claude-synth]
- ## Limitations / What this economical pass missed
	- **The actual computing capabilities demonstrated** — 2D pattern matching, spike-time classification, motor control — were skipped per user direction. The headline-level claim (structure suffices for these tasks) is captured; quantitative comparisons against baseline RSNNs are in the results section. ^[wiki-gap]
	- **Exact value of K used in each task** — varies by experiment, not fully resolved without reading the results sections. Main illustrations use K=6; the open question "how many neuron types are needed in practice" remains partially answered. ^[wiki-gap]
	- **Whether plasticity is compatible** — the paper demonstrates plasticity is *unnecessary*. Whether the probabilistic skeleton is *compatible with* online plasticity (i.e., if you add learning rules, do they break the innate function?) is not addressed. ^[wiki-gap]
	- **Hardware/organoid extensions** — mentioned but not implemented in this paper; flagged as future work.
- ## Connections (substantive — replaces old abstract-only list)
	- [[wiki/concepts/genomic-bottleneck]] — Stöckl/Maass is the most experimentally-grounded operationalisation in the wiki: the K-types × distance table maps directly onto Allen Institute connectivity data.
	- [[wiki/refs/zador-2019-critique-pure-learning]] — Zador's bottleneck argument concretised at the cortical-microcircuit level.
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]] — same operationalisation strategy (rule-emits-weights), different parameterisation (continuous gene profiles + bilinear vs discrete types + table). The two papers are sister approaches to the same problem.
	- [[wiki/refs/kerstjens-2026-lineage-positional]] — supplies what Stöckl/Maass leaves out: *where the cell types come from*. Eigengene-via-lineage produces the type distinctions that Stöckl uses as primitives.
	- [[wiki/refs/hiesinger-2021-seminar6-chemoaffinity-permissiveness]] — Sperry chemoaffinity is the biological background; Stöckl's type-conditioned probabilities are the engineering implementation of "composite molecular instructions" at the cell-type level.
	- [[wiki/refs/hiesinger-2021-seminar4-local-rules-robustness]] — probabilistic skeletons as a more general CA framework; the Hiesinger framing of cells-as-autonomous-agents is the substrate this paper formalises.
	- [[wiki/refs/dalgaty-2024-mosaic]] — neuromorphic-hardware target; Stöckl's "linear wire length + weight robustness" claim is exactly the property Mosaic-style chips need.
	- [[wiki/refs/achterberg-2023-sernns]] — spatially-embedded RNNs under wire-cost regularisation; complementary to Stöckl in operating on weight optimisation rather than probability tables.
	- [[wiki/research/spatial-neuromorphic-priors]] — the spatial-prior story for trained-RNNs; Stöckl/Maass shows the same story for *untrained* RSNNs with structure-encoded function.
	- [[wiki/concepts/developmental-latent-space]] — Stöckl's discrete-types-on-distance becomes engram-vectors-on-manifold-with-distance under the natural continuous relaxation.
	- [[wiki/concepts/neural-cellular-automata]] — probabilistic skeletons subsume CAs as a special case; an NCA with type-conditioned attention is essentially a probabilistic skeleton running as a CA.
	- [[wiki/projects/growing-networks]] — directly motivates the structural-side mechanism in the project's brainstorm log.
- ## Cited By (in this wiki)
	- [[wiki/concepts/genomic-bottleneck]]
	- [[wiki/concepts/developmental-latent-space]]
	- [[wiki/projects/growing-networks]]
	- [[wiki/refs/zador-2019-critique-pure-learning]]
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]]
	- [[wiki/refs/kerstjens-2026-lineage-positional]]
