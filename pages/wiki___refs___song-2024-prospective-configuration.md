title:: wiki/refs/song-2024-prospective-configuration
category:: reference
type:: research-paper
tags:: predictive-coding, credit-assignment, local-learning, computational-neuroscience
alias:: Prospective Configuration
summary:: Prospective configuration — a backprop-alternative credit-assignment principle: the network first infers the target neural activity, then adjusts weights to consolidate it; more efficient and more brain-consistent than backprop.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-05-29
created:: 2026-05-29
updated:: 2026-05-29
sources:: DOI:10.1038/s41593-023-01514-1
authors:: Song, Yuhang; Millidge, Beren; Salvatori, Tommaso; Lukasiewicz, Thomas; Xu, Zhenghua; Bogacz, Rafal
year:: 2024
venue:: Nature Neuroscience
doi:: 10.1038/s41593-023-01514-1
ingest-mode:: abstract
wiki-generated:: true

- Song, Millidge, Salvatori, Lukasiewicz, Xu & Bogacz (Nature Neuroscience 2024) introduce **prospective configuration**, a principle for credit assignment that differs from backpropagation and is argued to be both more efficient and more consistent with neural/behavioural data.

- ## Key Ideas
  - The essence of learning is **credit assignment** — pinpointing which components of the processing pipeline are responsible for an output error. Backprop has long been assumed to be the best solution; this paper sets out a different one.
  - In **prospective configuration**, the network *first infers the pattern of neural activity that should result from learning*, then modifies synaptic weights to consolidate that change in activity — activity-inference precedes weight change (the reverse emphasis from backprop).
  - It is shown to (1) underlie learning in a well-established family of cortical-circuit models (energy-based / predictive-coding networks), (2) enable learning that is more efficient and effective in many biologically realistic contexts, and (3) reproduce surprising patterns of neural activity and behaviour seen in human and rat experiments.
  - Positions itself as a biologically plausible **alternative to backprop** for "learning beyond backpropagation". ^[inferred] This places it alongside other local/predictive learning rules rather than gradient transport.

- ## Connections
  - [[wiki/refs/boeshertz-2025-predictive-learning-compositional]] — same predictive-learning family; both treat learning as inference over activity rather than error backprop.
  - [[wiki/projects/growing-computation]] — directly relevant to the "NCA-as-Gardener / meta-optimizer" thread: a meta-learned local rule that re-derives useful update signals at test time without explicit local errors is closer to prospective configuration than to backprop. ^[inferred]
  - [[wiki/concepts/neural-cellular-automata]] — candidate local-rule substrate for activity-inference-then-consolidation dynamics. ^[inferred]

- ## Open Questions
  - Can an NCA / meta-optimizer be *pushed* toward prospective-configuration-style local updates without being handed explicit local errors at inference time — i.e. learn to re-derive them? (Gabriel, journal 2026-05-29.) ^[inferred]
  - Full-text upgrade pending — abstract-mode only; the energy-based formalism and the specific cortical-circuit model deserve a deep read.

- ## Sources
  - DOI:10.1038/s41593-023-01514-1 — *Inferring neural activity before plasticity as a foundation for learning beyond backpropagation*, Nature Neuroscience 2024 (abstract mode).
