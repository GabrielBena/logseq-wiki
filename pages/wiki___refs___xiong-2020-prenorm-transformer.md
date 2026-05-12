title:: wiki/refs/xiong-2020-prenorm-transformer
category:: reference
type:: external-ref
tags:: transformers, normalisation, training-stability, deep-learning
authors:: Xiong, Ruibin; Yang, Yunchang; He, Di; Zheng, Kai; Zheng, Shuxin; Xing, Chen; Zhang, Huishuai; Lan, Yanyan; Wang, Liwei; Liu, Tieyan
year:: 2020
venue:: International Conference on Machine Learning
arxiv:: 2002.04745
citation-count:: 1389
summary:: Proves theoretically why Post-LN Transformers need warm-up (large output-layer gradients at init) and shows Pre-LN avoids this; enables removing the warm-up stage entirely.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **On Layer Normalization in the Transformer Architecture** — Xiong et al. (2020), ICML.

- ## Abstract (extracted)
  - The Transformer is widely used in natural language processing tasks. To train a Transformer however, one usually needs a carefully designed learning rate warm-up stage, which is shown to be crucial to the final performance but will slow down the optimization and bring more hyperparameter tunings. In this paper, we first study theoretically why the learning rate warm-up stage is essential and show that the location of layer normalization matters. Specifically, we prove with mean field theory that at initialization, for the original-designed Post-LN Transformer, which places the layer normalization between the residual blocks, the expected gradients of the parameters near the output layer are large. Therefore, using a large learning rate on those gradients makes the training unstable. The warm-up stage is practically helpful for avoiding this problem. On the other hand, our theory also shows that if the layer normalization is put inside the residual blocks (recently proposed as Pre-LN Transformer), the gradients are well-behaved at initialization.

- ## Key Ideas
  - Post-LN: LayerNorm after residual → large output-layer gradients at init → needs warm-up. ^[inferred]
  - Pre-LN: LayerNorm inside residual → well-behaved init gradients → no warm-up needed. ^[inferred]
  - Practical consequence: Pre-LN enables simpler training recipes with fewer hyperparameters. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/topology-masked-transformer]] — SODC likely uses Pre-LN for stable training; this paper motivates the choice.
  - [[wiki/research/self-organising-digital-circuits]] — cited as architectural justification.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
