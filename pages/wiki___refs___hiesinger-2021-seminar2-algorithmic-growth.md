title:: wiki/refs/hiesinger-2021-seminar2-algorithmic-growth
category:: reference
type:: external-ref
tags:: brain-development, algorithmic-information, kolmogorov-complexity, genomic-bottleneck, neurobiology
authors:: Hiesinger, Peter Robin
year:: 2021
venue:: Princeton University Press (Seminar 2 of *The Self-Assembling Brain*, pp 91-111)
doi::
arxiv::
citation-count:: n/a
summary:: Seminar 2 of Hiesinger's book. Establishes the algorithmic-information vs endpoint-information dichotomy via Rule 110, Game of Life, Lindenmayer systems, and Kolmogorov complexity. The genome contains rules to grow a brain, not a description of one. No shortcut to running the algorithm.
confidence:: 0.82
lifecycle:: draft
lifecycle-changed:: 2026-05-10
created:: 2026-05-10
updated:: 2026-05-10
sources:: assets/hiesinger_2021_the_self-assembling_brain.pdf (Seminar 2, pp 91-111, full read)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Seminar 2: From Algorithmic Growth to Endpoint Information** — Hiesinger 2021, *The Self-Assembling Brain*, pp 91-111. Parent ref: [[wiki/refs/hiesinger-2021-self-assembling-brain]].

- ## TL;DR
  - The seminar's core claim: **the genome encodes algorithmic growth (rules + time + energy), not endpoint information (a blueprint).**
  - Builds the case via Rule 110 (Wolfram), Conway's Game of Life, and Lindenmayer systems — all examples where a *short rule* generates *unbounded structural complexity* via iteration. The endpoint information needed to describe the structure is enormous; the algorithmic information needed to produce it is tiny.
  - Maps this directly onto biology: transcription factor cascades are algorithmic growth — every iteration the rules change because the products of earlier iterations alter which genes get read next. The genome is a tape; the cell is a Turing-equivalent reader; the brain is the eventual output of running the tape with time and energy.
  - **No shortcut**: there is no analytic method to know what the genome produces other than running the developmental algorithm. This has profound consequences for how mutations, knockouts, and brain emulation should be interpreted.

- ## The Cellular-Automata Anchor

  - ### Game of Life, Rule 110, and undecidability
    - **John von Neumann + Stanislaw Ulam (1940s)** invented cellular automata at Los Alamos. Von Neumann saw both the digital computer and self-replicating systems as cellular-automaton phenomena.
    - **Conway's Game of Life (1970)**: 4 simple rules → blinkers, oscillators, gliders, spaceships, and (since 2010) self-replicating "Gemini" structures with their own instruction tape.
    - **Wolfram's Rule 110 (1990s, with Cook)**: the simplest possible 1-D cellular automaton that's *Turing-complete*. From an absurdly small information content, the iterated patterns can encode any computation.
    - **Undecidability**: even though Rule 110 is fully deterministic, there is no analytic formula for the state at iteration N. To know iteration 1,234, you have to run iterations 1-1,233. This is *not* a limit of human ingenuity; it's a mathematical property.

  - ### Kolmogorov complexity vs Bennett's logical depth
    - **Solomonoff (1960s)**, then **Kolmogorov** and **Chaitin** independently: complexity = the length of the shortest program that produces a given output. A million 0s followed by a million 1s has tiny Kolmogorov complexity ("print 0 a million times, then 1 a million times"); a random million-digit string has Kolmogorov complexity ≈ its own length.
    - **Bennett's logical depth**: Kolmogorov complexity ignores *time-to-compute*. Rule 110 has low Kolmogorov complexity but enormous logical depth — the precise pattern at iteration 1,000,000 takes 1,000,000 steps to produce. **Logical depth is the version of complexity that matters for biology**: the genome has low Kolmogorov complexity but enormous logical depth, because growing a brain takes years.
    - **Connection to thermodynamics**: Maxwell's demon thought experiment + Boltzmann's constant tie information to entropy. Adding energy = adding information. This is why brain growth requires both time *and energy*.

  - ### Lindenmayer systems (L-systems) — biology's first algorithmic-growth language
    - **Aristid Lindenmayer (1968)**: a formal grammar of iterated string-rewriting rules that, with small extensions, can model essentially any branched biological structure (apple trees, Purkinje cell dendrites, blood vessel networks).
    - Stochastic L-systems add noise → realistic variation between individuals (every apple tree slightly different, every dendritic tree slightly different).
    - **Selection acts on the algorithm, not the endpoint**: evolution selected for L-system-like rules that produce trees that capture sunlight (or dendrites that capture inputs). The exact branch angles are *irrelevant information* — selection ignored them.

- ## From CA to Biology — Three Differences

  - **(1) Rules change with iteration.** In Rule 110, the same rule applies forever. In biology, transcription factor cascades mean each TF's expression alters which genes are read next — the *rules themselves change* with every iteration.
  - **(2) Stochasticity is built in.** Biological algorithms include noise as a *productive* ingredient (immune system, Dscam self-avoidance), not just as something to be minimised. CA can be made stochastic but it's an extension; in biology, noise is fundamental.
  - **(3) The substrate matters.** Rule 110 runs on any computer. The genome runs on a specific molecular machinery (DNA, ribosomes, proteins) whose *physical properties* enter the algorithm. Time and energy are not abstract resources but real metabolic constraints.

- ## Transcription Factor Cascades — Biology's Algorithmic Engine

  - 2,000-3,000 transcription factor genes in the human genome. Each TF binds DNA + regulates gene expression. Combinations of ~12 TFs can create vastly more functional TF complexes, each reading different parts of the genome.
  - The cascade: TF1 → expresses gene X → produces TF2 → expresses gene Y → produces TF3 → ... — each step changes the *cell's transcriptional state*, which changes *what's possible at the next step*.
  - **Logical depth in action**: a neuron may pass through thousands of distinct transcriptional states during development. Each state is the output of running the algorithm to that point; each state is the input to the next iteration.
  - **Implication for knockouts**: knocking out a gene that's used at iteration 1,234 of the algorithm produces a phenotype only if the algorithm reaches iteration 1,234 — which it may not, because earlier iterations were already affected. *Mutations have nonlinear, position-dependent consequences.*

- ## The Genome Is Not a Code (in the engineering sense)

  - Hiesinger argues the "genetic code" metaphor is *misleading* when applied to development. A code typically maps directly to its referent (Morse code → letters); the genome maps to *the iterative growth process*, not to the brain.
  - **"The code is a metaphor that works well for the genetic code or the rules of a cellular automaton. The code is a bad metaphor for the continuously changing states of neurons as they run through their algorithmic programs."** (p. 110)
  - The "extremely small amount of information to be specified genetically" (Willshaw & von der Malsburg 1979 — cited explicitly here) is sufficient to run the developmental algorithm but cannot be unpacked without running it.

- ## Why This Matters — Three Implications

  - ### (1) Endpoint information is the wrong target for connectomics
    - Reverse-engineering a wiring diagram doesn't yield the rules that produced it. The rules are *not visible* in the static structure — they're a property of the *generative process*.
    - **Implication for brain emulation**: copying the connectome doesn't copy the brain. The connectome is the snapshot at iteration N; running the brain forward requires the rules, which are *in the molecular machinery*, not in the wiring diagram.

  - ### (2) Mutations don't tell you what the gene "does"
    - Genes don't "do" anything in isolation — they participate in the algorithm at specific iterations. A mutation's phenotype is the *cumulative effect* of altered iterations, not a "function".
    - **Implication for genetics-of-behaviour**: there are very few "genes for traits"; there are mostly genes that contribute to many algorithmic steps that together produce the trait.

  - ### (3) AI shortcuts what biology cannot
    - Standard ANNs replace the entire developmental algorithm with random initialisation. **This works for narrow tasks** (image classification, language modelling) — but Hiesinger's argument is that the *information density* of the trained network is bounded by the algorithmic information that went in, which for ANNs is "random init + N iterations of learning rule".
    - **Implication for AI**: if we want artificial general intelligence, we may need to put more information *into the algorithm*, which means *growing the network* rather than just training a fixed one. NDP/LNDP/EngramNCA are early steps in this direction.

- ## Connections to Gabriel's Research

  - ### NDP and the operationalisation of "genome encodes growth, not endpoint"
    - **[[wiki/refs/najarro-2023-neural-developmental-programs]]** — NDP's per-cell shared NN is *exactly* the Rule-110-like setup Hiesinger argues underlies biology: a small fixed rule, applied iteratively per node, that produces a richly structured policy network. The "genomic bottleneck" framing in the NDP paper (14-parameter NDP grows a CartPole-solving network) is the engineering version of "tiny algorithmic information, large logical depth".
    - **[[wiki/refs/plantec-2024-lifelong-ndp]]** — LNDP extends this with rules-that-change-with-iteration (activity-dependent dynamics) — closer to biology's "rules change at every iteration" property.

  - ### Boolean NCA and SODC — narrow MR via post-developmental degeneracy
    - **[[wiki/research/self-organising-digital-circuits]]** — SODC's basin-hopping recovery is what *post-developmental* algorithmic growth looks like in an engineered system. The TMT keeps reconfiguring the LUTs in response to perturbation — this is "function as continuation of development" in Hiesinger Seminar 8's sense, but already foreshadowed here in Seminar 2's continuum framing.
    - The fact that 50,000 SODC-recovered circuits cluster into discrete structural archetypes (UMAP visualisation) maps onto Hiesinger's claim that structurally distinct configurations can serve the same function — narrow MR ([[wiki/concepts/functionalism]]) at the post-development scale, with the development itself being the path-dependent process Seminar 2 is about. ^[inferred]

  - ### Solution degeneracy and Kolmogorov complexity
    - **[[wiki/concepts/solution-degeneracy]]** — the genome's small algorithmic information ↔ the brain's enormous endpoint information has a direct analogue in SODC: the trained TMT (small parameter count) ↔ the configured Boolean circuits (a large basin of valid LUT configurations). The genome IS a degenerate generator; the SODC TMT is too. ^[inferred]
    - Hiesinger's no-shortcut claim is the key reason narrow MR matters: even though many configurations realise the same function, you can't just *pick one* without running the algorithm — the path matters because the algorithm's intermediate states determine which basin you reach.

  - ### NCA as the canonical model
    - **[[wiki/concepts/neural-cellular-automata]]** — NCA is *exactly* the substrate Hiesinger uses to motivate his thesis. Mordvintsev's image NCA is a learnable Rule 110 + biology-style noise + slightly more complex rules. Every paper in the NCA Seven Angles inherits Hiesinger's algorithmic-information framing whether or not it cites him.

  - ### The genomic bottleneck (Zador 2019, cited in NDP)
    - Hiesinger doesn't cite Zador 2019 directly (the book is contemporary), but the genomic-bottleneck argument is the same shape as Hiesinger's central claim. The 100-trillion-synapse human brain encoded by ~30k active genes is an extreme case of "small algorithmic information, large logical depth".

- ## Memorable Lines

  - "We can simulate it all right, but the result would not have been predictable in any way other than actually running the whole simulation." (p. 95)
  - "There is no shortcut to unfolding it step by step." (p. 96)
  - "The molecule or the gene that encodes the molecule does not contain the information. The molecule in space and time is an output of the running algorithm at one step, and it becomes part of the input for the next step of development." (p. 105)
  - "An infinitely deep code would be a code ad absurdum, a bottomless abyss in information theoretical terms." (p. 109)

- ## Cited By (in this wiki)
  - [[wiki/refs/hiesinger-2021-self-assembling-brain]] — parent
