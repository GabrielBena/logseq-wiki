title:: wiki/refs/dwivedi-2021-benchmarking-gnns
category:: reference
type:: external-ref
tags:: graph-neural-networks, benchmarking, deep-learning
authors:: Dwivedi, Vijay Prakash; Joshi, Chaitanya K.; Laurent, Thomas; Bengio, Yoshua; Bresson, Xavier
year:: 2023
venue:: Journal of Machine Learning Research
arxiv:: 2003.00982
citation-count:: 1163
summary:: Introduces a standardised GNN benchmarking framework; systematic comparison of WL-GNNs vs message-passing GCNs across graph regression, classification, and link prediction tasks.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Benchmarking Graph Neural Networks** — Dwivedi et al. (2021/2023), JMLR.

- ## Abstract (extracted)
  - Graph neural networks (GNNs) have become the standard toolkit for analyzing and learning from data on graphs. As the field grows, it becomes critical to identify key architectures and validate new ideas that generalize to larger, more complex datasets. Unfortunately, it has been increasingly difficult to gauge the effectiveness of new models in the absence of a standardized benchmark with consistent experimental settings. In this paper, we introduce a reproducible GNN benchmarking framework, with the facility for researchers to add new models conveniently for arbitrary datasets. We demonstrate the usefulness of our framework by presenting a principled investigation into the recent Weisfeiler-Lehman GNNs (WL-GNNs) compared to message passing-based graph convolutional networks (GCNs) for a variety of graph tasks.

- ## Key Ideas
  - Reproducible GNN benchmark with standardised splits, metrics, and experimental settings. ^[inferred]
  - WL-GNNs vs GCNs systematically evaluated on tasks requiring graph-level and node-level predictions. ^[inferred]
  - Standard reference for evaluating graph learning architectures (GNN baseline in SODC builds on this context). ^[inferred]

- ## Connections to Wiki
  - [[wiki/research/self-organising-digital-circuits]] — GNN baseline architecture is evaluated against this benchmarking context.
  - [[wiki/code/gabrielbena-boolean-nca-cc]] — GNN model implemented in the codebase.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
