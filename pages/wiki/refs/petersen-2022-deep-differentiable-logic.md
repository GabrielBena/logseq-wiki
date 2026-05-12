title:: wiki/refs/petersen-2022-deep-differentiable-logic
category:: reference
type:: external-ref
tags:: differentiable-logic-gates, boolean-circuits, deep-learning, efficient-inference
authors:: Petersen, Felix; Borgelt, Christian; Kuehne, Hilde; Deussen, Oliver
year:: 2022
venue:: Neural Information Processing Systems
arxiv:: 2210.08277
doi:: 10.48550/arXiv.2210.08277
citation-count:: 83
summary:: Learns networks of AND/OR/XOR gates via a continuous relaxation; achieves fast CPU inference (1M+ MNIST images/sec). Primary reference for differentiable logic gate networks.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Deep Differentiable Logic Gate Networks** — Petersen, Borgelt, Kuehne & Deussen (2022), NeurIPS.

- ## Abstract (extracted)
  - Recently, research has increasingly focused on developing efficient neural network architectures. In this work, we explore logic gate networks for machine learning tasks by learning combinations of logic gates. These networks comprise logic gates such as "AND" and "XOR", which allow for very fast execution. The difficulty in learning logic gate networks is that they are conventionally non-differentiable and therefore do not allow training with gradient descent. Thus, to allow for effective training, we propose differentiable logic gate networks, an architecture that combines real-valued logics and a continuously parameterized relaxation of the network. The resulting discretized logic gate networks achieve fast inference speeds, e.g., beyond a million images of MNIST per second on a single CPU core.

- ## Key Ideas
  - Continuous relaxation of discrete gate connections: each connection is a weighted mixture of logic gate types. ^[inferred]
  - At inference, discretise to the highest-weight gate per connection — fully binary execution. ^[inferred]
  - Speed advantage: pure logic operations → bitwise CPU parallelism with no floating point. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/differentiable-logic-gates]] — this paper is the primary source for the differentiable LUT relaxation used in SODC.
  - [[wiki/research/self-organising-digital-circuits]] — SODC adopts and extends the differentiable logic gate formulation.
  - [[wiki/code/gabrielbena-boolean-nca-cc]] — implemented in `boolean_nca_cc/circuits/model.py`.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
  - [[wiki/concepts/differentiable-logic-gates]]
