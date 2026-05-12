title:: wiki/refs/velickovic-2018-graph-attention-networks
category:: reference
type:: external-ref
tags:: graph-neural-networks, attention, deep-learning
authors:: Veličković, Petar; Cucurull, Guillem; Casanova, Arantxa; Romero, Adriana; Liò, Pietro; Bengio, Yoshua
year:: 2017
venue:: International Conference on Learning Representations
arxiv:: 1710.10903
doi:: 10.17863/CAM.48429
citation-count:: 25903
summary:: Graph Attention Networks (GAT): masked self-attention over neighbours allows implicit per-node attention weights without matrix inversion or knowing the graph structure upfront.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Graph Attention Networks** — Veličković et al. (2017/2018), ICLR.

- ## Abstract (extracted)
  - We present graph attention networks (GATs), novel neural network architectures that operate on graph-structured data, leveraging masked self-attentional layers to address the shortcomings of prior methods based on graph convolutions or their approximations. By stacking layers in which nodes are able to attend over their neighborhoods' features, we enable (implicitly) specifying different weights to different nodes in a neighborhood, without requiring any kind of costly matrix operation (such as inversion) or depending on knowing the graph structure upfront. In this way, we address several key challenges of spectral-based graph neural networks simultaneously, and make our model readily applicable to inductive as well as transductive problems.

- ## Key Ideas
  - Attention over neighbours: replace uniform aggregation with learned per-edge weights. ^[inferred]
  - No dependency on graph structure at training time — inductive; generalises to unseen graphs. ^[inferred]
  - The GNN baseline in SODC uses attention-based aggregation in the spirit of GAT. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — TMT's topology mask is a hard version of GAT's soft attention mask.
  - [[wiki/research/self-organising-digital-circuits]] — GNN baseline draws on GAT-style attention aggregation.
  - [[wiki/code/gabrielbena-boolean-nca-cc]] — GNN model in `models/gnn/`.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
