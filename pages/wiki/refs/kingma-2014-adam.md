title:: wiki/refs/kingma-2014-adam
category:: reference
type:: external-ref
tags:: optimisation, deep-learning, stochastic-gradient
authors:: Kingma, Diederik P.; Ba, Jimmy
year:: 2014
venue:: International Conference on Learning Representations
arxiv:: 1412.6980
citation-count:: 165703
summary:: Adam: adaptive moment estimation for stochastic optimisation. Computationally efficient, little memory overhead, robust to noisy/sparse gradients. The dominant deep-learning optimiser.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Adam: A Method for Stochastic Optimization** — Kingma & Ba (2014/2017), ICLR.

- ## Abstract (extracted)
  - We introduce Adam, an algorithm for first-order gradient-based optimization of stochastic objective functions, based on adaptive estimates of lower-order moments. The method is straightforward to implement, is computationally efficient, has little memory requirements, is invariant to diagonal rescaling of the gradients, and is well suited for problems that are large in terms of data and/or parameters. The method is also appropriate for non-stationary objectives and problems with very noisy and/or sparse gradients. The hyper-parameters have intuitive interpretations and typically require little tuning.

- ## Key Ideas
  - Maintains per-parameter adaptive learning rates using first and second moment estimates. ^[inferred]
  - Bias-correction in early training prevents underestimation of moment estimates. ^[inferred]
  - Standard optimiser used in SODC and virtually all modern deep-learning training. ^[inferred]

- ## Connections to Wiki
  - [[wiki/research/self-organising-digital-circuits]] — used to train the TMT update rule.
  - [[wiki/research/universal-nca]] — used to train the UNCA model.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
