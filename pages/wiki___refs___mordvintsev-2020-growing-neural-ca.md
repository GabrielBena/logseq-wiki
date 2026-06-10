title:: wiki/refs/mordvintsev-2020-growing-neural-ca
category:: reference
type:: external-ref
tags:: nca, morphogenesis, self-organisation, distill
authors:: Mordvintsev, Alexander; Randazzo, Ettore; Niklasson, Eyvind; Levin, Michael
year:: 2020
venue:: Distill
doi:: 10.23915/DISTILL.00023
citation-count:: 272
summary:: Foundational NCA paper: a 16-channel CA whose shared ~8K-param neural update rule is trained by backprop-through-time to grow, persist and regenerate a target pattern from one seed. Origin of the paradigm.
confidence:: 0.80
lifecycle:: draft
lifecycle-changed:: 2026-06-10
created:: 2026-05-08
updated:: 2026-06-10
sources:: blog:distill.pub/2020/growing-ca (full HTML, CC-BY 4.0)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.10
provenance-ambiguous:: 0.05

- **Growing Neural Cellular Automata** — Mordvintsev, Randazzo, Niklasson & Levin (2020), *Distill*. Subtitle: *Differentiable Model of Morphogenesis*. The paper that introduced the [[wiki/concepts/neural-cellular-automata]] paradigm. Part of Distill's *Differentiable Self-organizing Systems* thread; Michael Levin (Allen Discovery Center, Tufts) supplies the regeneration/bioelectric framing.

- ## TL;DR
	- A cellular automaton whose **shared local update rule is a small neural net (~8.3K params)** trained end-to-end by gradient descent to **grow a target image from a single seed cell** — a differentiable toy model of morphogenesis. ^[extracted]
	- Three escalating regimes: **Growing** (reach the target), **Persistent** (make the target a stable attractor, not just a fly-by), **Regenerating** (recover after damage). Each is the same rule trained under a wider set of pressures. ^[extracted]
	- The headline surprise: **regeneration emerges without being trained for it.** Persistent models often regenerate; damage-trained models regenerate robustly even to *damage types never seen in training*. The authors frame this as **enlarging the target's basin of attraction**. ^[extracted]
	- The explicit biological framing — *"all our cells share the same genome (update rule) and are only differentiated by the information encoded in the chemical signalling they receive, emit, and store internally (their state vectors)"* — is the literal seed of the DNA-reframe in [[wiki/concepts/substrate-rule-co-location]]. ^[extracted]

- ## The model
	- ### Cell state — 16 channels
		- Each cell is a **16-dim real vector**. Channels 1–3 = visible **RGB**; channel 4 = **alpha (α)**, which demarcates *living* cells: α > 0.1 ⇒ "mature", neighbours of a mature cell ⇒ "growing", everything else ⇒ "dead" and **hard-zeroed each step**. Channels 5–16 = **hidden** state with no predefined meaning — interpretable as chemical concentrations / electric potentials the rule learns to use for signalling. ^[extracted]
	- ### The update rule — four phases, applied per cell, identically everywhere
		- **1 · Perception.** A *fixed* 3×3 **Sobel filter** pair estimates x- and y-gradients of every channel; concatenated with the cell's own state → a **48-dim percept** (16 + 16 + 16). Kernels are hand-fixed (not learned) because real cells navigate by chemical gradients. ^[extracted]
		- **2 · Update.** A per-cell MLP: `dense(128) → ReLU → dense(16)`. The **final layer is zero-initialised** so the rule starts as a no-op ("do-nothing" init); output is a **residual increment** to the state (no final ReLU — updates must add *and* subtract). ~8.3K params total. ^[extracted]
		- **3 · Stochastic update.** Each cell updates independently with **probability 0.5 per step** (a per-cell dropout mask on the increment) — relaxing the global-clock assumption, i.e. **asynchrony** as a self-organisation requirement. ^[extracted]
		- **4 · Alive masking.** Cells with no mature (α>0.1) neighbour in their 3×3 are forced to all-zero — empty cells carry no hidden state and don't compute. ^[extracted]
	- Trained by **backpropagation-through-time** (it's a recurrent residual conv net), pixel-wise L2 against the target after a random number of steps. The authors note it can be read as a *"Recurrent Residual Convolutional Network with per-pixel dropout."* ^[extracted]

- ## The three regimes — and the sample pool
	- **Experiment 1 — Learning to Grow.** Naive train-to-target-after-N-steps. Works, but unstable beyond the training horizon: different seeds give *drastically different* long-term behaviour — some explode, some decay, a few happen to be stable. ^[extracted]
	- **Experiment 2 — "What persists, exists".** Reframes via dynamical systems: make the target an **attractor**. The mechanism is a **sample pool** — keep a pool of states, sample a batch, **reset the highest-loss sample to the seed**, train, write the outputs back into the pool. This lets loss be applied over long horizons *without* the memory blow-up of long BPTT, molding the dynamics to return to the target from wherever the system wandered. **This is exactly the pool-based meta-training [[SODC]] inherits.** ^[extracted]
	- **Experiment 3 — Learning to regenerate.** Damage pool-sampled states (erase random discs) before training steps → robust regeneration that **generalises to unseen damage geometries** (e.g. rectangular cuts). Framed explicitly as *increasing the basin of attraction* — the origin of the basin language [[wiki/concepts/solution-degeneracy]] later makes precise. ^[extracted]
	- **Experiment 4 — Rotating the perceptive field.** Rotating the Sobel kernels by θ rotates the grown pattern **without retraining** — evidence of robustness to out-of-distribution conditions. ^[extracted]

- ## Discussion — the two forward-looking passages most relevant to Gabriel
	- **Bioelectric setpoint (Levin).** Target morphology is *not* hard-coded by DNA but maintained by a physiological circuit storing a **setpoint for anatomical homeostasis**; rewriting it yields e.g. 2-headed flatworms that breed true in plain water. A biological precedent for "function as a maintained attractor, not a stored blueprint." ^[extracted]
	- **"A more physical implementation" — the growing-computation seed, written in 2020.** *"We can imagine it as a grid of tiny independent computers, simulating individual cells. Each … would require approximately 10Kb of ROM to store the 'cell genome' (neural network weights and control code), and about 256 bytes of RAM … The system … is uniform and decentralised … our method provides a way to program it to reach the predefined global state, and recover this state in case of multi-element failures and restarts."* This is [[wiki/projects/growing-computation]]'s thesis (a tiled substrate running one shared rule, self-healing by re-reaching a global state) stated as a conjecture five years early. ^[extracted]

- ## Why this is foundational for Gabriel's program
	- **It is the origin of the [[wiki/concepts/neural-cellular-automata]] paradigm** — locality, homogeneity (one shared rule), differentiability, and learned self-organisation all begin here. [[UNCA]] (NCA-as-computer), [[SODC]] (NCA-as-optimiser), and the whole [[NDP]]/[[LNDP]]/[[EngramNCA]] lineage descend from this rule. ^[claude-synth]
	- **The four facets of the unified vision are all latent in it:** (i) *co-location / DNA* — "same genome, differentiated by state" is the soft-conditioning ancestor of [[wiki/concepts/substrate-rule-co-location]]'s P/C/E stack; (ii) *degeneracy* — "increase the basin of attraction" is [[wiki/concepts/solution-degeneracy]] before it had a name; (iii) *growth = repair* — the same rule grows *and* regenerates, the kernel of "growth and repair are one operation under different pressure"; (iv) *functionalism* — the rule is substrate-agnostic, which the "grid of tiny computers" passage makes explicit. ^[claude-synth]
	- **Mechanistic inheritances:** the **sample pool** → [[SODC]]'s pool meta-learning; **asynchronous/stochastic update** → the async-robustness story in [[wiki/refs/miotti-2025-differentiable-logic-ca]]; **fixed Sobel perception + learned update** → the perception-vs-update split [[wiki/refs/miotti-2025-differentiable-logic-ca]] keeps and [[wiki/projects/growing-computation]] eyes for its router-vs-compute tiles. ^[claude-synth]

- ## Related work (as cited)
	- Reaction-diffusion / Turing patterns, Gray–Scott; von Neumann self-reproducing automata ([[wiki/refs/von-neumann-1966-self-reproducing-automata]]); Conway's Game of Life; Rule 110 / Wolfram; SmoothLife & Lenia (continuous GoL); evolutionary-CA morphogenesis (Miller's self-repairing French flag; Nichele et al. CA-NEAT); CNN↔CA equivalence; the Neural GPU; GNNs; swarm robotics (Boids, Kilobots, mergeable nervous systems). ^[extracted]

- ## Limitations / caveats
	- A **toy** model: single 2D target patterns, small grids, RGBA images — not computation or function in [[UNCA]]/[[SODC]]'s sense. ^[extracted]
	- Regeneration is **emergent and inconsistent** without damage-training; some models over-stabilise or self-destruct. The "basin of attraction" framing is qualitative here. ^[extracted]
	- 8-bit quantisation for the web demo was an after-thought, occasionally requiring best-of-N checkpoint selection — an early hint of the deploy-time crispness issues [[wiki/projects/self-organising-boolean-circuits]] hits with the live demo. ^[inferred]

- ## Connections to wiki
	- [[wiki/concepts/neural-cellular-automata]] — this paper *is* the paradigm's origin.
	- [[wiki/concepts/self-organisation]] — the canonical differentiable self-organisation demonstration.
	- [[wiki/concepts/solution-degeneracy]] — "increase the basin of attraction" is the proto-degeneracy framing.
	- [[wiki/concepts/substrate-rule-co-location]] — "same genome, differentiated by state" = the soft-conditioning ancestor of the DNA-reframe.
	- [[wiki/research/universal-nca]] — [[UNCA]] extends this toward universal computation via mutable/immutable state separation.
	- [[wiki/research/self-organising-digital-circuits]] — [[SODC]] applies the paradigm to Boolean circuits and inherits the sample pool.
	- [[wiki/refs/miotti-2025-differentiable-logic-ca]] — [[DiffLogic CA]] discretises this exact rule into logic gates for hardware.
	- [[wiki/projects/growing-computation]] — the Discussion's "grid of tiny computers" is this project's thesis, stated early.

- ## Cited By (in this wiki)
	- [[wiki/concepts/neural-cellular-automata]]
	- [[wiki/research/universal-nca]]
	- [[wiki/research/self-organising-digital-circuits]]
	- [[wiki/refs/miotti-2025-differentiable-logic-ca]]
