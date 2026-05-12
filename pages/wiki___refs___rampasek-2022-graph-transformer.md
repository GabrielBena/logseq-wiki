title:: wiki/refs/rampasek-2022-graph-transformer
category:: reference
type:: external-ref
tags:: graph-transformers, graph-neural-networks, positional-encoding, deep-learning
authors:: Rampášek, Ladislav; Galkin, Mikhail; Dwivedi, Vijay Prakash; Luu, Anh Tuan; Wolf, Guy; Beaini, Dominique
year:: 2022
venue:: Neural Information Processing Systems
arxiv:: 2205.12454
doi:: 10.48550/arXiv.2205.12454
citation-count:: 960
summary:: GPS: a recipe for general, powerful, scalable graph Transformers combining positional encodings, local MPNN, and global attention with O(N+E) complexity.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Recipe for a General, Powerful, Scalable Graph Transformer** — Rampášek et al. (2022), NeurIPS.

- ## Abstract (extracted)
  - We propose a recipe on how to build a general, powerful, scalable (GPS) graph Transformer with linear complexity and state-of-the-art results on a diverse set of benchmarks. Graph Transformers (GTs) have gained popularity in the field of graph representation learning with a variety of recent publications but they lack a common foundation about what constitutes a good positional or structural encoding, and what differentiates them. In this paper, we summarize the different types of encodings with a clearer definition and categorize them as being local, global or relative. The prior GTs are constrained to small graphs with a few hundred nodes, here we propose the first architecture with a complexity linear in the number of nodes and edges O(N+E) by decoupling the local real-edge aggregation from the fully-connected Transformer.

- ## Key Ideas
  - GPS recipe: (1) positional/structural encoding, (2) local message-passing, (3) global attention — modular composition. ^[inferred]
  - Linear complexity by decoupling local aggregation from global Transformer. ^[inferred]
  - Provides the graph Transformer framework context for TMT's topology-masked attention design. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — TMT is a topology-constrained variant of the graph Transformer framework described here.
  - [[wiki/research/self-organising-digital-circuits]] — cited for graph Transformer background.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
