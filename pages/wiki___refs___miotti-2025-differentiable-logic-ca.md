title:: wiki/refs/miotti-2025-differentiable-logic-ca
alias:: DiffLogic CA, DiffLogic-CA, Differentiable Logic Cellular Automata
category:: reference
type:: external-ref
tags:: nca, differentiable-logic-gates, boolean-circuits, programmable-matter
authors:: Miotti, Pietro; Niklasson, Eyvind; Randazzo, Ettore; Mordvintsev, Alexander
year:: 2025
venue:: Google Paradigms of Intelligence (Distill-style web article) + arXiv 2506.04912
arxiv:: 2506.04912
doi:: 10.48550/arXiv.2506.04912
citation-count:: 5
summary:: DiffLogic CA — NCA whose update rule is a discrete logic-gate circuit, trained end-to-end via soft relaxation, deployed as native binary hardware. First successful application of differentiable logic to a recurrent setting; explicitly frames itself toward Computronium / CAM-8 programmable matter.
confidence:: 0.80
lifecycle:: draft
lifecycle-changed:: 2026-05-20
created:: 2026-05-08
updated:: 2026-06-11
sources:: blog:google-research.github.io/self-organising-systems/difflogic-ca, arxiv:2506.04912
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.10
provenance-ambiguous:: 0.00

- **Differentiable Logic Cellular Automata: From Game of Life to Pattern Generation** — Miotti, Niklasson, Randazzo & Mordvintsev (2025), Google Paradigms of Intelligence Team. Published as a Distill-style interactive web article; the blog *is* the paper. arXiv mirror at 2506.04912.
- ## What it does
	- Combines Neural Cellular Automata (NCA) with Deep Differentiable Logic Gate Networks (DLGNs). Cells carry an n-dim **binary** state vector; the update rule is a *discrete logic circuit* applied identically at every cell. The circuit is trained end-to-end via gradient descent on continuous relaxations, then binarised for inference.
	- **First demonstration of DLGNs in a recurrent setting.** Prior DLGN work (Petersen et al.) had only addressed feedforward classification. Recurrent-in-time + recurrent-in-space + discrete gates is the new combination.
	- The architecture has two stages per cell per step, mirroring vanilla NCA:
		- **Perception kernels** — small logic circuits that read the central cell + its Moore-neighbourhood and produce a per-channel summary. Replace Sobel filters.
		- **Update network** — a deeper logic circuit that takes the perception output + the cell's current state, outputs the *new* binary state directly (no incremental ODE-style update — full replacement).
	- Gates parameterised by a 16-dim probability vector over the 16 possible 2-input boolean operations; softmax during training, argmax at inference. Continuous relaxations listed for each op (e.g. soft-AND = `a*b`, soft-XOR = `a + b − 2ab`).
- ## Methods — deep-read of the technical sections (2026-06-11) ^[claude-synth]
	- *Full-text fetch of the Distill blog + arXiv 2506.04912, focused on architecture — the perception + hidden-state questions for [[wiki/projects/blastema]]'s Priority #0.*
	- ### Cell state = the working-memory reservoir (dual register, CAM-8 style)
		- A cell's state is an **n-dim binary vector** that *"acts as the cell's working memory, storing information from previous iterations"* — the **hidden channels ARE the computational reservoir**. State dimension is a per-task knob: **1 bit** for Game of Life (memoryless — GoL is state-independent), **8 bits** (checkerboard), **64 ch** (coloured G), **128 bits** (lizard). Only a few channels are *visible* (1st channel mono; channels 0–2 = binary RGB); the rest are hidden scratch.
		- **Dual register (Toffoli–Margolus CAM-8):** a **gray** register = the persistent state, an **orange** register = the perception output. Perception reads neighbours' gray → writes orange; update reads gray+orange → writes new gray and **clears orange**. Two physical memories per cell — a clean hardware mapping (two FF/BRAM banks per tile).
	- ### Perception = a fixed-wired, learned-gate logic circuit (replaces Sobel)
		- Not a neural conv: each **perception kernel is a distinct logic circuit with FIXED topology but LEARNED gates**, applied **channel-wise**, emulating the Moore-neighbourhood interaction.
		- Structure ≈ a 4-layer funnel, e.g. **[8, 4, 2, 1]** gates/layer. **Layer 1 has 8 gates — one per Moore neighbour — each taking `(central cell, one neighbour)` as its two inputs**, so the first layer computes pairwise *centre×neighbour* interactions (the logic analogue of a gradient filter). 4–16 kernels per model; **output dim = #kernels × #channels**. (Variant: multiple output bits per kernel/channel → better convergence.)
	- ### Update = a deeper DLGN, full-replacement
		- A much deeper logic-gate network (GoL **23 layers ~128 wide**; lizard **10×512**; G **11×512**) takes `concat(previous state [gray] + perception output [orange])` and **outputs the new state directly** — *no* incremental/ODE update.
		- Gates: a 16-dim probability vector over the 16 two-input boolean ops (softmax in training → argmax at inference); init biased toward pass-through for stability.
	- ### Numbers worth carrying
		- The whole perceive+update **rule** is small-to-moderate: **5 active gates** (checkerboard, after pruning!), **336** (GoL), **577** (lizard), **927** (coloured G). The rule really can be tiny — reinforces the compactness argument for [[wiki/concepts/substrate-rule-co-location]] / [[wiki/projects/blastema]].
		- Trained by pixel-wise MSE at the **final** timestep only (random init each step); robustness + self-healing **emerge unforced**; async training improves noise robustness.
	- ### The limitation that bears directly on us — full-replacement vs a real memory
		- Every step **overwrites** the whole state; the Discussion flags this as the weakness and proposes **LSTM-like gating for state-forgetting** to "enable a richer combination of past and newly computed candidate states." This is exactly Gabriel's *"hidden states of LUTs as a computational reservoir"* point — the reservoir is there but crude (overwrite); a **gated/persistent hidden channel** is the upgrade [[wiki/projects/blastema]] should bake in from the start. Also flagged: **hierarchical NCA** as future work (rhymes with the lineage/multi-scale thread). ^[claude-synth]
- ## Key results
	- **Game of Life learned perfectly** from all 512 3×3 ground-truth grids. Final circuit uses **336 active gates** (excluding pass-through). The most frequent gates after training are OR and AND.
	- **Checkerboard pattern generation** in 20 steps on 16×16 grid. After pruning: **just 5 active gates** suffice — the entirety of the procedural checkerboard rule. Generalises to 4× larger grids (64×64) over 4× more time steps with no retraining.
	- **Lizard growth** (homage to original Mordvintsev NCA) — 20×20 target shape grown in 12 steps from a single seed cell, with 577 active gates. Generalises to 40×40 grid.
	- **Coloured "G" generation** — 16×16 RGB-binary target in 15 steps, 927 active gates. The most complex experiment.
- ## Robustness — emerges without being trained for
	- **Damage tolerance.** Permanently disabling a large fraction of cells: pattern integrity is maintained. The system degrades gracefully.
	- **Self-healing.** Disabled cells reactivated after several steps: the system successfully repairs to produce the correct pattern.
	- **Asynchronous updates.** Trained synchronously, run async at inference: works. Trained async: works better, with markedly improved noise robustness.
	- The authors frame this as **a new paradigm for robust computing**: discrete logic CAs trained on the task alone produce fault-tolerant, self-healing dynamics as a side effect of the architecture, not as an explicit training objective. Direct echo of biological resilience.
- ## The Computronium framing
	- Explicit. From the paper's introduction: *"the integration of differentiable logic gates and neural cellular automata is a potential step towards programmable matter — Computronium — a theoretical physical substance capable of performing arbitrary computation."*
	- Lineage cited:
		- **Toffoli & Margolus** — CAM-8 architecture (cellular automata machine, late 1980s). Each cell is a tiny computer with a DRAM-like state register and an SRAM-like update LUT. DiffLogic CA's cell structure (gray "state" register + orange "perception" register + update circuit) is a direct architectural descendant.
		- **Amato et al.** — noted the persistent open problem: "researchers still worry about the difficulty of finding local rules that correspond to real natural systems". DiffLogic CA's answer is *learn them by gradient descent*.
	- This frames the paper as **a deployable pipeline from continuous training to discrete physical hardware**: continuous NCA training → soft logic gates → hard binarisation → bitstream that runs natively on logic-gate hardware (FPGAs, ASICs, CAM-8-style substrates).
- ## Why this matters for the [[wiki/projects/growing-computation]] thread
	- **Provides the bridge from soft training to hard substrate.** [[SODC]], [[wiki/projects/growing-networks]], [[EngramNCA]] all train continuous rules. DiffLogic CA's contribution is the *compilation step* — that continuous rule can be reduced to a discrete circuit of bounded size, deployable on physical logic-gate substrates like [[wiki/concepts/fpga]]. Without this bridge, "self-organising on hardware" remains a software metaphor.
	- **Demonstrates that the universal rule can be very small.** 5 gates for a procedural pattern, ~300 for Conway, ~900 for the hardest experiment so far. This kills the "Option B is too expensive" worry on layer 1 of the [[wiki/concepts/substrate-rule-co-location]] framework: an always-on regulatory circuit running per-tile is plausibly *tens of gates*, well below any reasonable per-tile budget.
	- **Robustness and async are free.** Two properties the [[wiki/projects/growing-computation]] needs (stage 2 thermal/power recovery, stage 3-bis corruption recovery) emerge from discrete-logic architectures *without explicit training for them*.
	- **It does Level 0 of the merger, not Level 1.** Every cell runs the same circuit. There is no regulatory/workload decomposition, no role differentiation, no on-substrate write decisions. The training is still off-substrate (host-side gradient descent). See [[wiki/concepts/substrate-rule-co-location]] for the level-by-level ladder.
- ## The [[SODC]] flip
	- [[SODC]] puts the NCA *outside* the boolean circuit — the NCA is the optimizer, the circuit is the substrate being optimised.
	- DiffLogic CA inverts this — the NCA *is* a boolean circuit. The substrate runs the NCA natively.
	- **Together they bracket the project.** [[wiki/projects/growing-computation]] is the synthesis: the regulatory NCA *runs* on the boolean substrate (DiffLogic-style) AND it orchestrates the substrate's role assignments ([[SODC]]-style, but for hardware regions rather than gate-types). ^[claude-synth]
- ## Open questions / limitations
	- Training is still off-substrate. No on-chip learning mechanism. Their hardest experiment (G with colors) needed extensive hyperparameter tuning.
	- The deployed circuit is fixed at inference time. There's no on-substrate equivalent of further fine-tuning. This is what Level 2/3 of the [[wiki/concepts/substrate-rule-co-location]] ladder would require.
	- Hierarchical / multi-scale circuits are flagged as future work — could compose larger behaviours from smaller learned rule-circuits.
	- LSTM-like gating mechanisms suggested for state-forgetting in the update network. Currently every step replaces full state, which limits temporal-credit-assignment.
- ## Connections to wiki
	- [[wiki/concepts/differentiable-logic-gates]] — the foundational building block.
	- [[wiki/concepts/neural-cellular-automata]] — the framework being made discrete + deployable.
	- [[wiki/concepts/fpga]] — the natural physical substrate for the deployed circuit.
	- [[wiki/concepts/programmable-matter]] — the theoretical lineage explicitly invoked.
	- [[wiki/concepts/substrate-rule-co-location]] — situates this paper at Level 0 of the optimiser-substrate merger ladder.
	- [[wiki/research/self-organising-digital-circuits]] — the inverse setup (NCA optimises circuit vs circuit runs NCA); together they bracket the merger.
	- [[wiki/projects/growing-computation]] — the project that takes this paper as its layer-2-compilation primitive.
	- [[wiki/refs/petersen-2022-deep-differentiable-logic]] — original DLGN paper this builds on.
	- [[wiki/refs/mordvintsev-2020-growing-neural-ca]] — original NCA paper this discretises.
- ## Cited By (in this wiki)
	- [[wiki/research/self-organising-digital-circuits]]
	- [[wiki/projects/growing-computation]]
	- [[wiki/concepts/substrate-rule-co-location]]
	- [[wiki/concepts/fpga]]
	- [[wiki/concepts/programmable-matter]]
