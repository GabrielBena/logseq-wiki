title:: wiki/refs/cook-2025-heterogeneous-experts-pathways
category:: reference
type:: external-ref
tags:: mixture-of-experts, modularity, routing, brain-networks, pathways
authors:: Cook, Jack; Akarca, Danyal; Costa, Rui Ponte; Achterberg, Jascha
year:: 2025
venue:: NeurIPS 2025
arxiv:: 2506.02813
citation-count:: 4
summary:: Heterogeneous experts don't form pathways alone; three inductive biases (routing cost, low-performance cost-scaler, expert dropout) make brain-like task pathways emerge — a "Mixture-of-Pathways".
confidence:: 0.74
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-08
updated:: 2026-06-08
sources:: arxiv:2506.02813 (full PDF read 2026-06-08)
wiki-generated:: true
ingest-mode:: full

- **Brain-Like Processing Pathways Form in Models With Heterogeneous Experts** — Cook, Akarca, Costa & Achterberg (2025), NeurIPS 2025. arXiv:2506.02813. Oxford (Neural Circuits & Behaviour) + Imperial. Full PDF read 2026-06-08.
	- Flagged (Gabriel) as relevant to a **hierarchical / diverse-size tile** implementation — and a cool paper in its own right. Note: it **cites Gabriel's own** [[wiki/research/dynamics-specialization]] in its resource-constraint lineage.

- ## Abstract (extracted)
	- The brain is made up of a vast set of heterogeneous regions that dynamically organize into pathways as a function of task demands… Despite the large role these pathways play in cognition, the mechanisms through which brain regions organize into pathways remain unclear. In this work, we use an extension of the Heterogeneous Mixture-of-Experts architecture to show that heterogeneous regions do not form processing pathways by themselves, implying that the brain likely implements specific constraints which result in the reliable formation of pathways. We identify three biologically relevant inductive biases that encourage pathway formation: a routing cost imposed on the use of more complex regions, a scaling factor that reduces this cost when task performance is low, and randomized expert dropout. When comparing our resulting *Mixture-of-Pathways* model with the brain, we observe that the artificial pathways match how the brain uses cortical and subcortical systems to learn and solve tasks of varying difficulty.

- ## Architecture — Heterogeneous Mixture-of-Experts (HMoE)
	- 3 layers; **each layer has 3 heterogeneous experts**: two GRUs (16 and 32 neurons) + a **skip connection (identity)** — the skip lets a layer do *no computation* for a timestep. A **router** (a 64-neuron GRU) emits softmax weights `w_j`; outputs combine as `h_l = Σ_j w_j h_{l,j}`. Experts vary in *size and activation* (hence *heterogeneous*).
	- Trained on **Mod-Cog**: 82 time-series cognitive tasks (a NeuroGym expansion), tasks 0.8–3 s long, 115-dim input (fixation + two 16-dim stimuli + 82-dim task one-hot → a 16-dim task embedding). Output zero during fixation, correct choice during response.

- ## The result — pathways need three inductive biases
	- Three criteria define "a pathway has formed": **consistent** (same routing across training seeds), **self-sufficient** (removing non-pathway experts barely hurts), **distinct** (different task groups → different pathways).
	- **Baseline HMoE forms no stable pathways** (mean pairwise routing correlation across seeds = 0.0324). Three biases fix this:
		- **(1) Routing cost — Learned Pathway Complexity (LPC).** `LPC_i = (1/T_i) Σ_t Σ_j w_{i,j,t} · s_j²` — routing weight × **squared expert size** (squared because storing a weight matrix is `O(s²)`); skip connections are free. Added to the loss → penalises activating complex experts. Alone, lifts routing consistency to 0.15.
		- **(2) Task-performance scaling.** Divide `LPC_i` by the task's response loss `L_response,i`, so the complexity penalty *relaxes when the task isn't yet solved* (don't starve hard tasks). Lifts consistency to **0.71**.
		- **(3) Expert dropout.** Randomly deactivate low-weight experts in training (`p_j = β − (β/γ)w_j` for `w_j < γ`). Buys **self-sufficiency**: baseline drops 98.2%→16.4% when low-weight experts are removed; with dropout (`β=0.8`) only 85.8%→74.4%. All three together = the **Mixture-of-Pathways (MoP)**.

- ## Brain comparison (the payoff)
	- **Multiple-demand (MD) system:** harder tasks recruit more-complex experts — MoP shows a positive task-difficulty ↔ LPC correlation (`r≈0.51–0.54`); baseline none (`r≈−0.01`). Lesioning the complex expert: MoP still solves *simple* tasks but fails hard ones (like MD-lesion patients); baseline collapses on everything.
	- **Cortical→subcortical hand-off over learning:** complex tasks first *increase* pathway complexity early in training, then reduce it (`r≈0.31`); the baseline does the opposite (`r≈−0.48`), prematurely pushing hard tasks to cheap pathways and failing to learn them. The routing cost is tied to thalamic/neuromodulatory control of metabolic budget (norepinephrine, orexin).

- ## Why it's relevant to [[wiki/projects/growing-computation]] (nuanced)
	- **Cost-shaped recruitment.** The *routing-cost-on-complexity* + *don't-starve-hard-tasks* objective is a clean template for **which tile to recruit**: cheap to use small / skip tiles, pay more for complex ones, but relax the penalty while a task is unsolved. The **skip / do-nothing expert** is a neat analogue of a NOP / dormant tile, and the **squared-size cost** echoes the project's real `O(s²)`-ish data-movement/energy concern (deck Step 1). A framing to borrow for the recruitment *loss*, not a 1:1 map. ^[claude-synth]
	- **The key contrast for the oracle thread.** Unlike PathNet (global GA) or [[NORACL]] (hand-designed trigger), Cook's selection is a **learned, differentiable router trained end-to-end** — the pole the project leans toward. *But it is still global*: the router reads the whole layer state and LPC is a per-task global quantity. So Cook informs the *objective* (what cost produces good pathways) more than the *mechanism* a local rule needs. The open question stays: realise a cost-shaped router under nearest-neighbour locality (cf. [[wiki/concepts/grow-and-learn]]). ^[inferred]
	- **Heterogeneous = diverse-size tiles.** Directly supports the deck Step-2 "tiles could compose hierarchically / diverse sizes" idea.

- ## Connections to Wiki
	- [[wiki/projects/growing-computation]] — diverse-size tiles + cost-shaped recruitment objective; the skip-expert ≈ NOP/dormant tile.
	- [[wiki/concepts/grow-and-learn]] — Cook as the *learned-but-global* router pole on the oracle spectrum (closer than PathNet/NORACL, still not local).
	- [[wiki/research/dynamics-specialization]] — Gabriel's own resource-constraint→specialisation work, cited by Cook; same "cost pressure shapes functional structure" lineage.
	- [[wiki/refs/fernando-2017-pathnet]] — also "pathways through a module net"; PathNet *evolves* the path (global GA), Cook *routes* it (learned router) — two ends of the selection-mechanism axis.
	- [[wiki/refs/achterberg-2023-sernns]] — same Akarca/Achterberg spatially-embedded-networks lineage (cost/structure → function).
	- [[wiki/concepts/modularity]] — pathways as emergent functional modularity under routing pressure.

- ## Open Questions / To Read
	- Can the cost-shaped routing objective be implemented by a *local* rule (no global router), so recruitment cost ∝ tile size/distance works under 2D-mesh comms? ^[claude-synth]
	- Forward-only (no loops back to earlier layers) is a stated limitation — the project's mesh is also forward-feedforward in dataflow; worth comparing. ^[inferred]

- ## Cited By (in this wiki)
	- [[wiki/projects/growing-computation]] — diverse-size-tile / routing-cost-recruitment angle.
	- [[wiki/concepts/grow-and-learn]] — oracle-spectrum (learned-but-global router).
