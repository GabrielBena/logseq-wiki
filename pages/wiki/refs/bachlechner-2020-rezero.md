title:: wiki/refs/bachlechner-2020-rezero
category:: reference
type:: external-ref
tags:: transformers, initialisation, deep-learning, training-stability
authors:: Bachlechner, Thomas; Majumder, Bodhisattwa Prasad; Mao, Huanru Henry; Cottrell, Garrison W.; McAuley, Julian
year:: 2020
venue:: Conference on Uncertainty in Artificial Intelligence
arxiv:: 2003.04887
citation-count:: 373
summary:: A single zero-initialised gate per residual connection (ReZero) satisfies dynamical isometry at init and outperforms more complex schemes, enabling training of 120-layer Transformers.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **ReZero is All You Need: Fast Convergence at Large Depth** — Bachlechner et al. (2020), UAI.

- ## Abstract (extracted)
  - Deep networks often suffer from vanishing or exploding gradients due to inefficient signal propagation, leading to long training times or convergence difficulties. Various architecture designs, sophisticated residual-style networks, and initialization schemes have been shown to improve deep signal propagation. Recently, Pennington et al. used free probability theory to show that dynamical isometry plays an integral role in efficient deep learning. We show that the simplest architecture change of gating each residual connection using a single zero-initialized parameter satisfies initial dynamical isometry and outperforms more complex approaches. Although much simpler than its predecessors, this gate enables training thousands of fully connected layers with fast convergence and better test performance for ResNets trained on CIFAR-10. We apply this technique to language modeling and find that we can easily train 120-layer Transformers. When applied to 12 layer Transformers, it converges 56% faster on enwiki8.

- ## Key Ideas
  - Zero-init residual gate: output = x + α·F(x) where α=0 at init; network starts as identity, gradually learns residuals. ^[inferred]
  - Achieves dynamical isometry (near-unit singular values of Jacobian) at initialisation. ^[inferred]
  - Used in SODC's TMT for stable training of the shared-weight update network across large circuit populations. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — ReZero init is used in the TMT block.
  - [[wiki/research/self-organising-digital-circuits]] — cited as architectural detail for training stability.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
