title:: wiki/refs/dehghani-2023-scaling-vit
category:: reference
type:: external-ref
tags:: vision-transformer, scaling, deep-learning
authors:: Dehghani, Mostafa; et al.
year:: 2023
venue:: International Conference on Machine Learning
arxiv:: 2302.05442
doi:: 10.48550/arXiv.2302.05442
citation-count:: 848
summary:: Demonstrates LLM-like scaling laws for Vision Transformers at 22B parameters; key finding that ViT scales similarly to language models with the right recipe.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Scaling Vision Transformers to 22 Billion Parameters** — Dehghani et al. (2023), ICML.

- ## Abstract (extracted)
  - The scaling of Transformers has driven breakthrough capabilities for language models. At present, the largest large language models (LLMs) contain upwards of 100B parameters. Vision Transformers (ViT) have introduced the same architecture to image and video modelling, but these have not yet been successfully scaled to nearly the same degree; the largest dense ViT contains 4B parameters. We present a recipe for highly efficient and stable training of a 22B-parameter ViT (ViT-22B) and perform a wide variety of experiments on the resulting model. When evaluated on downstream tasks, ViT-22B demonstrates increasing performance with scale. We further observe other interesting benefits of scale, including an improved tradeoff between fairness and performance, state-of-the-art alignment to human visual perception in terms of shape/texture bias, and improved robustness.

- ## Key Ideas
  - ViT scales like LLMs with the right training recipe (efficient attention, parallelism). ^[inferred]
  - Larger models show better fairness/performance tradeoffs and improved robustness. ^[inferred]
  - Cited in SODC likely for architecture/scaling context of Transformer update rules. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — cited as evidence that Transformer-style architectures scale reliably.
  - [[wiki/research/self-organising-digital-circuits]] — cited as background on Transformer scaling.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
