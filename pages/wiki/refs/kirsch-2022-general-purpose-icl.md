title:: wiki/refs/kirsch-2022-general-purpose-icl
category:: reference
type:: external-ref
tags:: meta-learning, transformers, in-context-learning
authors:: Kirsch, Louis; Harrison, James; Sohl-Dickstein, Jascha; Metz, Luke
year:: 2022
venue:: arXiv preprint
arxiv:: 2212.04458
doi:: 10.48550/arXiv.2212.04458
citation-count:: 111
summary:: Shows Transformers can be meta-trained from scratch to act as general-purpose in-context learners; characterises transitions between generalisation, memorisation, and meta-training failure.
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **General-Purpose In-Context Learning by Meta-Learning Transformers** — Kirsch et al. (2022), arXiv.

- ## Abstract (extracted)
  - Modern machine learning requires system designers to specify aspects of the learning pipeline, such as losses, architectures, and optimizers. Meta-learning, or learning-to-learn, instead aims to learn those aspects, and promises to unlock greater capabilities with less manual effort. One particularly ambitious goal of meta-learning is to train general-purpose in-context learning algorithms from scratch, using only black-box models with minimal inductive bias. Such a model takes in training data, and produces test-set predictions across a wide range of problems, without any explicit definition of an inference model, training loss, or optimization algorithm. In this paper we show that Transformers and other black-box models can be meta-trained to act as general-purpose in-context learners. We characterize transitions between algorithms that generalize, algorithms that memorize, and algorithms that fail to meta-train at all, induced by changes in model size, number of tasks, and meta-optimization.

- ## Key Ideas
  - Transformer as in-context algorithm: takes training data as input tokens, outputs predictions without gradient steps. ^[inferred]
  - Meta-training transitions (generalise → memorise → fail) depend on model size, task diversity, and meta-optimiser. ^[inferred]
  - Capability bottlenecked by accessible state (context window), not parameter count. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — the TMT acts as a meta-learner operating on circuit states; related conceptual framing.
  - [[wiki/research/self-organising-digital-circuits]] — cited as background on meta-learning Transformers.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
