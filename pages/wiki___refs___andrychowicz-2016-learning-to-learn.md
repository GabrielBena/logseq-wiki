title:: wiki/refs/andrychowicz-2016-learning-to-learn
category:: reference
type:: external-ref
tags:: meta-learning, optimisation, lstm
authors:: Andrychowicz, Marcin; Denil, Misha; Colmenarejo, Sergio G.; Hoffman, Matthew; Pfau, David; Schaul, Tom; de Freitas, Nando
year:: 2016
venue:: Neural Information Processing Systems
arxiv:: 1606.04474
citation-count:: 2184
summary:: Casts optimiser design as a learning problem; an LSTM learns to exploit structure in a class of problems, outperforming hand-designed optimisers.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Learning to learn by gradient descent by gradient descent** — Andrychowicz et al. (2016), NeurIPS.

- ## Abstract (extracted)
  - The move from hand-designed features to learned features in machine learning has been wildly successful. In spite of this, optimization algorithms are still designed by hand. In this paper we show how the design of an optimization algorithm can be cast as a learning problem, allowing the algorithm to learn to exploit structure in the problems of interest in an automatic way. Our learned algorithms, implemented by LSTMs, outperform generic, hand-designed competitors on the tasks for which they are trained, and also generalize well to new tasks with similar structure. We demonstrate this on a number of tasks, including simple convex problems, training neural networks, and styling images with neural art.

- ## Key Ideas
  - Optimiser design as meta-learning: an LSTM acts as the update rule and is trained end-to-end. ^[inferred]
  - Learned optimisers outperform Adam/SGD on the task distribution they were trained on. ^[inferred]
  - Generalisation to new tasks with similar structure shows meta-learned optimisers transfer. ^[inferred]

- ## Connections to Wiki
  - [[wiki/research/self-organising-digital-circuits]] — SODC pool-based training loop is conceptually related to meta-learning over problem distributions.
  - [[wiki/concepts/topology-masked-transformer]] — the TMT acts as a learned update rule across circuit instances; analogous framing.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
