title:: wiki/refs/guichard-2025-engramnca
category:: reference
type:: external-ref
tags:: nca, memory-engram, private-channels, morphogenesis, planaria
authors:: Guichard, Etienne; Reimers, Felix; Kvalsund, Mia; Lepperød, Mikkel; Nichele, Stefano
year:: 2025
venue:: IEEE Symposium on Artificial Life (ALIFE 2025)
doi::
arxiv:: 2504.11855
citation-count:: 5
summary:: NCA with public visible channels + private intracellular memory ("engram"). Two NCAs (GeneCA, GenePropCA) cooperate to grow distinct morphologies from shared substrate via primitive embeddings stored in private channels. Inspired by RNA-mediated memory transfer in planaria/aplysia.
confidence:: 0.78
lifecycle:: in-review
lifecycle-changed:: 2026-05-11
review-pass:: 1
review-pass-changed:: 2026-05-11
review-pass-result:: pass-1-addressed (1 of 1)
created:: 2026-05-09
updated:: 2026-05-11
sources:: arXiv:2504.11855 (full PDF, 7869 words)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **EngramNCA: a Neural Cellular Automaton Model of Memory Transfer** — Guichard, Reimers, Kvalsund, Lepperød & Nichele (Østfold University College, Oslo Met, Simula, U. Oslo), ALIFE 2025, arXiv:2504.11855. Code: https://github.com/etimush. Web version with videos: https://etimush.github.io.
- ## TL;DR
	- Standard NCA cells expose all hidden channels to neighbours via convolution. **EngramNCA partitions cell state into public (visible) channels and private (intracellular memory / "gene") channels** that are *not* visible to neighbours.
	- Two networks cooperate:
		- **GeneCA** — updates only public channels (visible+hidden), conditioned on the cell's own private genes. Trained to grow primitive morphologies (shapes, body parts) from a single seed, where the seed cell's gene channels carry a binary encoding of which primitive to grow.
		- **GenePropCA** — updates only private gene channels (visible channels untouched). Trained on top of frozen GeneCA. Propagates and modifies gene encodings across the grid, enabling complex morphologies to be built by *combining primitives that exist in the GeneCA's repertoire*.
	- Key biological inspiration: planaria retain memory after head regeneration; RNA injected from trained aplysia transfers memory to untrained ones; "synapses are merely a visible reverberation of private memories" (Gold & Glanzman 2021).
	- **Applications**: coexisting morphologies on the same lattice without interference; out-of-distribution mixtures (square-circle hybrids); fractal-like compositions from line primitives; even **continuous Lenia-glider dynamics** more stable than a vanilla NCA.
- ## Architecture Detail
	- ### Cell state partition
		- Each cell at (i,j): c_{i,j} = [v_{i,j}, h_{i,j}, g_{i,j}]
			- **v** ∈ R^4 — RGB-α visible channels
			- **h** ∈ R^{n_h} — public hidden channels (visible to neighbours via convolution)
			- **g** ∈ R^{n_g} — *private* gene channels (visible only to the cell itself)
		- Total channel count is fixed; gene channels are *carved out of* the hidden channel pool, not added — so any improvement is not from added capacity. (Appendix verifies via DummyVCA / MaskedCA / ReducedCA control experiments.)
	- ### Perception
		- P(c_{i,j}^t) = [Identity, Sobel_x, Sobel_y, Laplacian] applied to public channels only.
		- **Private gene channels are accessed by the cell's own update network but not by perception kernels** — they cannot be sensed by neighbouring cells. This is the architectural enforcement of privacy.
	- ### GeneCA update rule
		- [v^{t+1}, h^{t+1}] = [v^t, h^t] + φ_{GeneCA}(P(c^t), g^t)
		- g^{t+1} = g^t  (genes are *frozen* by GeneCA; they enter as conditioning input but are not modified)
		- Trained per-primitive in a multi-pool setup: one pool per primitive-encoding pair, batch contains n repetitions of each target image.
	- ### GenePropCA update rule
		- [v^{t+1}, h^{t+1}] = [v^t, h^t]  (visible+hidden channels frozen)
		- g^{t+1} = g^t + ψ_{GenePropCA}(P(c^t), g^t)
		- Trained on top of frozen GeneCA — gradients flow through GeneCA but only update GenePropCA parameters.
	- ### Ensemble step
		- At each time step: (a) GeneCA computes ∆v, ∆h based on current state; (b) state is updated; (c) GenePropCA computes ∆g based on the updated state; (d) gene channels updated.
		- The two NCAs operate at different rates in principle; experiments show the system is robust to the rate ratio.
- ## Experimental Findings
	- ### Coexisting primitives
		- Three target primitives: blue square, green circle, red triangle (one-hot 3-bit gene encoding).
		- Multiple seed cells with different gene encodings on the same grid grow their respective primitives without interference. Even with overlapping placement, distinct primitives form (possibly with mixing colours at boundaries — a graceful degeneration mode).
		- **Out-of-distribution gene mixing**: a seed cell with a gene encoding that's a *mixture* of trained encodings grows a *spatially mixed primitive* (e.g. a circle-square hybrid) — the binary gene space behaves as a structured latent.
	- ### Hierarchical morphogenesis (lizard from body parts)
		- GeneCA trained on lizard body parts (legs, head, torso, tail) as primitives.
		- GenePropCA trained to grow the *complete lizard* starting from a single torso-encoding seed cell.
		- GenePropCA learns to spread "body-part" gene signals to the right cells in the right order — heads grow at one end, tails at the other.
		- **Generalisation**: GenePropCA can also grow a lizard when GeneCA was only trained on basic polygons (not lizard parts) — gene encodings transfer non-trivially.
		- Seed-cell encoding *matters*: lizard only grows from the encoding GenePropCA was trained with.
	- ### Coexisting full morphologies (lizard + butterfly)
		- One extra "meta-gene" channel (immutable to both GeneCA and GenePropCA) selects between morphologies.
		- Trained the same GeneCA + GenePropCA pair to grow both lizard and butterfly given the meta-gene.
		- Quality drops compared to single-morphology training, but both grow successfully.
	- ### Lenia gliders (continuous dynamics)
		- Trained EngramNCA to replicate ~500 frames of a Lenia glider video.
		- Compared against a parameter-matched vanilla NCA (GeneCA + GenePropCA total params = vanilla NCA params).
		- **Vanilla NCA replicates frames but loses dynamics past frame ~300**; EngramNCA reproduces the glider stably past the training horizon — strong evidence that private memory provides stability for time-extended computation.
- ## Theoretical Framing — Memory Beyond Synapses
	- **The "synaptic dogma" challenge**: classical view (Cajal 1894; Mayford 2012) holds memory lives in synaptic strengths. But:
		- **Planaria** decapitated and regrown retain learned behaviours (Shomrat & Levin 2013).
		- **Aplysia**: RNA from trained animals injected into untrained ones induces memory-like changes (Bédécarrats et al. 2018).
		- **Cell biology**: gene regulatory networks orchestrate morphogenesis (Davidson 2006); intracellular signalling cascades underpin long-term memory (Kandel et al. 2014).
	- **Engram** = the physical substrate of memory (neuropsychology). EngramNCA's private channels are the engram analogue — information stored *inside* cells, transferable cell-to-cell via the GenePropCA mechanism (analogous to RNA transfer via extracellular vesicles or tunneling nanotubes).
	- **"Genome instantiates a generative model"** (Mitchell & Cheney 2024; Hartl & Levin 2024 — same Levin lab as [[wiki/refs/pio-lopez-2026-brainca]]): the gene encoding is a *compact generative latent* that the GeneCA decodes into morphology. EngramNCA operationalises this view in NCA form. ^[addressed]
- ## Connections to Gabriel's Research
	- ### Public/private channel split parallels mutable/immutable state in UNCA — but extended
		- **[[wiki/research/universal-nca]]** introduced the *mutable/immutable* state separation: immutable = "hardware" (spatially heterogeneous, fixed per task instance); mutable = "computation" (updated by the NCA rule). EngramNCA's public/private split is a closely related dichotomy: public channels are inter-cellular communication ("computation observable to neighbours"); private channels are intracellular memory ("immutable from neighbour perspective, mutable from the cell's own perspective").
		- **Crucial difference**: EngramNCA's private channels are *propagable* — GenePropCA can transfer them across cells (the RNA-transfer analogue). UNCA's immutable hardware does not transfer. EngramNCA thus extends UNCA's separation into a *flexible, context-modulatable* memory layer that can be moved around. ^[inferred]
		- Conceptually, EngramNCA's gene channels behave like *task descriptors* in UNCA's hardware-state — and *also* like SODC's LUT logits ([[wiki/research/self-organising-digital-circuits]]) in that they parameterise function while not being directly observable. Triangulates a third instantiation of "function-as-cell-internal-state" across this lab cluster. ^[inferred]
	- ### Stability via private memory — connection to SODC's pool training
		- Vanilla NCA Lenia replication failed at ~frame 300; EngramNCA was stable past 500. The paper credits the private memory channels for providing *stable function representation* over long horizons.
		- **[[wiki/research/self-organising-digital-circuits]]** uses *pool-based meta-learning* to enforce long-horizon stability — circuits persist across task resets, reinforcing functional homeostasis. EngramNCA arrives at long-horizon stability via a different mechanism (architectural privacy of memory channels). Both target the same pathology: NCA dynamics drifting away from learned function over time.
		- Possible cross-pollination: SODC's pool training + EngramNCA's private channels could give a more sample-efficient long-horizon training regime. The EngramNCA paper itself flags this: "One avenue for future work is to use EngramNCA cell memory mechanisms when pool-training is not applicable." ^[inferred]
	- ### NCA Five Angles — and now a 6th
		- **[[wiki/concepts/neural-cellular-automata]]** — the existing Five Angles (pattern-former → computer → optimizer → brain-economy substrate → developer) gain a sixth: **NCA-as-engram-bearer**. The substrate is now augmented with cell-private memory that propagates separately from visible state.
		- **Mapping onto the trilogy / quintet**:
			- Mordvintsev: pure visible state (no private memory)
			- UNCA Ch3: mutable/immutable separation (private "hardware" but immobile)
			- SODC Ch4: function-as-state (LUTs configurable per cell)
			- BraiNCA: attention over graph + long-range
			- NDP/LNDP: substrate growth via per-cell rules
			- **EngramNCA**: cell-private propagable memory (RNA-transfer analogue)
		- The natural composition: a unified rule with growth (NDP/LNDP), function-config (SODC), and engram propagation (EngramNCA) all operating on the same cell-state architecture. Closer to the [[wiki/research/phd-thesis]] grand vision than any single paper. ^[inferred]
	- ### Functionalism — narrow MR via *task-conditional substrate*
		- **[[wiki/concepts/functionalism]]** — EngramNCA exhibits a particularly clean form of narrow MR: *the same network parameters realise different morphological functions* depending on the gene encoding in the seed cell. The gene channels are a *substrate for function specification*; they do not *change the implementation* (the NN weights are frozen) but *change which function is computed*.
		- This is a much sharper version of multiple realizability than gradient-trained networks: same cell-rule realises {square, circle, triangle, lizard, fractal} purely by changing the private gene encoding. The genotype-phenotype map is *one-to-many in a controllable way*.
		- **[[wiki/concepts/solution-degeneracy]]** — the OOD gene-mixing experiment is degeneracy made deliberate: untrained encodings still produce coherent (mixed) phenotypes, suggesting the gene-space is a *smooth* degenerate basin rather than discrete island-of-the-trained.
	- ### Memory-engram + functional plasticity → bio-inspired AGI thread
		- The connection to **planaria regeneration** ties this thread directly to Levin's work, which sits behind both BraiNCA ([[wiki/refs/pio-lopez-2026-brainca]]) and the Mitchell-Cheney 2024 / Hartl-Levin 2024 "genomic generative model" framing.
		- Combined with [[wiki/refs/aguera-y-arcas-2025-functional-perspective]]'s functionalist chain (Turing → Von Neumann → DNA-as-tape), EngramNCA is a particularly clean engineering instantiation of *life-as-embodied-computation*: cells carry their own private "DNA" and propagate it intercellularly.
- ## Limitations / Where the Paper Stops
	- Privatising channels carries a performance penalty (Appendix 1 — DummyVCA/MaskedCA/ReducedCA all degrade as more channels become private). There's a delicate balance in the n_g / n_h split.
	- Limited to morphogenesis and Lenia replication tasks — not yet demonstrated on functional control / RL.
	- Two-stage training (freeze GeneCA, then train GenePropCA) is rigid; jointly training the two is left to future work.
	- The paper itself proposes ARC-AGI as the next application — addressed in [[wiki/refs/guichard-2025-arc-nca]] from the same group.
- ## Adjacent Work to Track
	- **[[wiki/refs/guichard-2025-arc-nca]]** — direct successor by the same group; applies EngramNCA to ARC-AGI.
	- **Pande & Grattarola 2023 — Hierarchical NCA** — same Grattarola lineage as [[wiki/refs/grattarola-2021-learning-graph-ca]]; cited as an inspiration for the multi-scale / multi-level extension of NCA.
	- **Sudhakaran, Najarro & Risi 2022 — Goal-guided NCA** — Risi lab; cited as a similar architectural idea (a goal-encoder vs GenePropCA's gene-prop).
	- **Mitchell & Cheney 2024** "The genomic code: The genome instantiates a generative model of the organism" (arXiv:2407.15908) — the theoretical backbone for the engram framing. Worth a stub.
	- **Hartl & Levin 2024** "What does evolution make? learning in living lineages and machines" — same Levin lab as BraiNCA.
- ## Theoretical Anchor
	- **[[wiki/refs/hiesinger-2021-self-assembling-brain]]** — Hiesinger Seminar 8 ([[wiki/refs/hiesinger-2021-seminar8-development-function]]) reformulates memory as *the algorithmic rules sufficient to recreate a representation given input + time + energy*. EngramNCA's private gene channels + GenePropCA implement exactly this: the genes ARE the rule-substrate; the GeneCA is the rule-runner; the morphology is the recreated representation. The "memory beyond synapses" framing in EngramNCA's Discussion is also the framing Hiesinger's continuum-of-development-and-function argument leads to.
- ## Cited By (in this wiki)
	- [[wiki/concepts/neural-cellular-automata]]
	- [[wiki/research/self-organising-digital-circuits]]
	- [[wiki/research/universal-nca]]