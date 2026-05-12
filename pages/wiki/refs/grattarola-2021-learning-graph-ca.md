title:: wiki/refs/grattarola-2021-learning-graph-ca
category:: reference
type:: external-ref
tags:: nca, graph-neural-networks, cellular-automata, self-organisation
authors:: Grattarola, Daniele; Livi, Lorenzo; Alippi, Cesare
year:: 2021
venue:: Neural Information Processing Systems
arxiv:: 2110.14237
citation-count:: 42
summary:: Uses GNNs to learn transition rules for graph cellular automata on arbitrary topologies; shows GCA can learn Voronoi tiling rules, flocking, and target-state convergence.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Learning Graph Cellular Automata** — Grattarola, Livi & Alippi (2021), NeurIPS.

- ## Abstract (extracted)
  - Cellular automata (CA) are a class of computational models that exhibit rich dynamics emerging from the local interaction of cells arranged in a regular lattice. In this work we focus on a generalised version of typical CA, called graph cellular automata (GCA), in which the lattice structure is replaced by an arbitrary graph. In particular, we extend previous work that used convolutional neural networks to learn the transition rule of conventional CA and we use graph neural networks to learn a variety of transition rules for GCA. First, we present a general-purpose architecture for learning GCA, and we show that it can represent any arbitrary GCA with finite and discrete state space. Then, we test our approach on three different tasks: 1) learning the transition rule of a GCA on a Voronoi tessellation; 2) imitating the behaviour of a group of flocking agents; 3) learning a rule that converges to a desired target state.

- ## Key Ideas
  - GNNs as learned transition rules for GCAs replace hand-designed cellular update rules. ^[inferred]
  - Arbitrary-topology CA — NCA generalised beyond regular grids to graph substrates. ^[inferred]
  - Direct precursor to SODC's use of circuit topology as the CA "lattice". ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/neural-cellular-automata]] — generalises NCA to graph-structured substrates.
  - [[wiki/research/self-organising-digital-circuits]] — SODC treats Boolean circuit graphs as the substrate; direct conceptual extension of graph NCA.
  - [[wiki/code/gabrielbena-boolean-nca-cc]] — GNN model in the codebase is the SODC analogue of this architecture.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
