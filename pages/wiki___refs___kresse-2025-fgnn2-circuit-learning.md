title:: wiki/refs/kresse-2025-fgnn2-circuit-learning
category:: reference
type:: external-ref
tags:: circuit-learning, graph-neural-networks, logic-synthesis, eda
authors:: Wang, Ziyi; Bai, Yang; He, Zuohui; Zhang, Xinyu; Xu, Qiang; Ho, Tsung-Yi; Huang, Yu; Yu, Bei
year:: 2025
venue:: IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems
doi:: 10.1109/TCAD.2024.3434464
citation-count:: 24
summary:: FGNN2: contrastive pretraining framework for gate-level circuit representation that captures logic functionality, not just graph topology; outperforms prior circuit learning approaches.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **FGNN2: A Powerful Pretraining Framework for Learning the Logic Functionality of Circuits** — Wang et al. (2025), IEEE TCAD.

- ## Abstract (extracted)
  - Learning feasible representation from raw gate-level circuits is essential for incorporating machine learning techniques in logic synthesis, physical design, or verification. Existing structure-based learning methods tend to concentrate mainly on the graph topology, often neglecting logic functionality. This oversight frequently results in a failure to capture the underlying semantics, thereby limiting their overall applicability. To address the concern, we propose a novel circuit representation learning framework, FGNN2, that utilizes a contrastive scheme to effectively extract generic functionality knowledge. We construct a comprehensive pretraining dataset through a customized circuit augmentation scheme. We have also developed a novel contrastive loss function to capture the relative functional distance between different circuits, and to generate representations that are invariant to the input order.

- ## Key Ideas
  - Contrastive pretraining on circuits captures functional (not just topological) distance. ^[inferred]
  - Input-order invariance via the contrastive loss is key for circuit semantics. ^[inferred]
  - Related to SODC in that both must learn representations that respect circuit logic, not just graph structure. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/differentiable-logic-gates]] — complementary approach: FGNN2 learns circuit representations; SODC learns circuit configurations.
  - [[wiki/research/self-organising-digital-circuits]] — cited as related EDA work on circuit ML.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
