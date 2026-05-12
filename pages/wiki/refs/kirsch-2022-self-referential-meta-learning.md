title:: wiki/refs/kirsch-2022-self-referential-meta-learning
category:: reference
type:: external-ref
tags:: meta-learning, self-reference, neural-networks
authors:: Kirsch, Louis; Schmidhuber, Jürgen
year:: 2022
venue:: arXiv preprint
arxiv:: 2212.14392
doi:: 10.48550/arXiv.2212.14392
citation-count:: 10
summary:: Self-referential meta-learning without explicit meta-optimisation: a network self-modifies via fitness-monotonic execution, learns to learn on bandit and control tasks.
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Eliminating Meta Optimization Through Self-Referential Meta Learning** — Kirsch & Schmidhuber (2022), arXiv.

- ## Abstract (extracted)
  - Meta Learning automates the search for learning algorithms. At the same time, it creates a dependency on human engineering on the meta-level, where meta learning algorithms need to be designed. In this paper, we investigate self-referential meta learning systems that modify themselves without the need for explicit meta optimization. We discuss the relationship of such systems to in-context and memory-based meta learning and show that self-referential neural networks require functionality to be reused in the form of parameter sharing. Finally, we propose fitness monotonic execution (FME), a simple approach to avoid explicit meta optimization. A neural network self-modifies to solve bandit and classic control tasks, improves its self-modifications, and learns how to learn, purely by assigning more computational resources to better performing solutions.

- ## Key Ideas
  - Self-referential learning: the network modifies its own weights without an outer meta-optimiser. ^[inferred]
  - Fitness-monotonic execution: resources assigned to better-performing modifications — a form of selection pressure. ^[inferred]
  - Strong resonance with SODC: both are self-modifying systems that learn without a privileged external optimiser. ^[inferred]

- ## Connections to Wiki
  - [[wiki/research/self-organising-digital-circuits]] — thematic connection: SODC circuits self-repair without external re-training.
  - [[wiki/concepts/topology-masked-transformer]] — shared-weight NCA update rule is a self-referential modifier of circuit states.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
