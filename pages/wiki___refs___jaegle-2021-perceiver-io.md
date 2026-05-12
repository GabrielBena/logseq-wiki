title:: wiki/refs/jaegle-2021-perceiver-io
category:: reference
type:: external-ref
tags:: transformers, cross-attention, general-architecture, deep-learning
authors:: Jaegle, Andrew; Borgeaud, Sebastian; Alayrac, Jean-Baptiste; Doersch, Carl; et al.
year:: 2021
venue:: International Conference on Learning Representations
arxiv:: 2107.14795
citation-count:: 797
summary:: Perceiver IO: a general-purpose architecture using cross-attention to arbitrary input and output query arrays, scaling linearly and achieving strong results across diverse modalities.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Perceiver IO: A General Architecture for Structured Inputs & Outputs** — Jaegle et al. (2021), ICLR.

- ## Abstract (extracted)
  - A central goal of machine learning is the development of systems that can solve many problems in as many data domains as possible. Current architectures, however, cannot be applied beyond a small set of stereotyped settings, as they bake in domain & task assumptions or scale poorly to large inputs or outputs. In this work, we propose Perceiver IO, a general-purpose architecture that handles data from arbitrary settings while scaling linearly with the size of inputs and outputs. Our model augments the Perceiver with a flexible querying mechanism that enables outputs of various sizes and semantics, doing away with the need for task-specific architecture engineering. The same architecture achieves strong results on tasks spanning natural language and visual understanding, multi-task and multi-modal reasoning, and StarCraft II.

- ## Key Ideas
  - Cross-attention to a learnable latent array: separates input size from computational cost. ^[inferred]
  - A query array for each output type enables flexible output shapes without task-specific heads. ^[inferred]
  - Directly inspires the Perceiver model in SODC, which uses cross-attention to input/output residuals as an alternative update mechanism. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — Perceiver is the alternative model to TMT in SODC.
  - [[wiki/research/self-organising-digital-circuits]] — one of three model architectures evaluated.
  - [[wiki/code/gabrielbena-boolean-nca-cc]] — `model=perceiver_attention` is implemented in `models/attention/`.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
