title:: wiki/refs/shanahan-2021-encoders-ensembles-continual
category:: reference
type:: external-ref
tags:: continual-learning, task-free, ensembles, representation-learning, self-supervised
authors:: Shanahan, Murray; Kaplanis, Christos; Mitrović, Jovana
year:: 2021
venue:: arXiv
arxiv:: 2105.13327
citation-count:: 26
summary:: Task-free continual learning via a frozen pre-trained encoder plus an ensemble of simple classifiers; specialisation and competitive selection across the ensemble beat any single member, with no catastrophic forgetting.
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-06-04
created:: 2026-06-04
updated:: 2026-06-04
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Encoders and Ensembles for Task-Free Continual Learning** — Shanahan, Kaplanis & Mitrović (2021), arXiv:2105.13327.
	- Online, task-free continual learning: no (or unknown) task boundaries, each example seen once, classes learned incrementally.

- ## Abstract (extracted)
	- We present an architecture that is effective for continual learning in an especially demanding setting, where task boundaries do not exist or are unknown, and where classes have to be learned online (with each example presented only once). To obtain good performance under these constraints, while mitigating catastrophic forgetting, we exploit recent advances in contrastive, self-supervised learning, allowing us to use a pre-trained, general purpose image encoder whose weights can be frozen, which precludes forgetting. The pre-trained encoder also greatly simplifies the downstream task of classification, which we solve with an ensemble of very simple classifiers. Collectively, the ensemble exhibits much better performance than any individual classifier, an effect which is amplified through specialisation and competitive selection. We assess the performance of the encoders-and-ensembles architecture on standard continual learning benchmarks, where it outperforms prior state-of-the-art by a large margin on the hardest problems, as well as in less familiar settings where the data distribution changes gradually or the classes are presented one at a time.

- ## Key Ideas
	- A frozen, pre-trained (contrastive self-supervised) general-purpose encoder precludes forgetting by never updating the representation. ^[inferred]
	- Downstream classification is solved by an **ensemble of very simple classifiers** rather than one model. ^[inferred]
	- The ensemble outperforms any individual member — an effect **amplified through specialisation and competitive selection** among members. ^[inferred]
	- Large gains on the hardest continual-learning benchmarks, plus the gradual-distribution-shift and one-class-at-a-time regimes. ^[inferred]

- ## Connections to Wiki
	- [[wiki/projects/growing-networks]] — Gabriel's growth/pruning route to continual learning; "specialisation + competitive selection" rhymes with recruiting saturated capacity into new units. ^[inferred]
	- [[wiki/projects/growing-computation]] — cited in the 2026-06-04 design note as the "move through a latent space" analogue, recast as movement through *physical* space (grow/prune tiles); the ensemble keys "remind of engrams". ^[inferred]
	- [[wiki/concepts/modularity]] — specialisation + competitive selection across an ensemble is a functional-specialisation mechanism. ^[inferred]

- ## Open Questions / To Read
	- The frozen-encoder assumption is the crux — how would it transfer to a self-organising substrate that has *no* pre-trained encoder to freeze? Abstract-only; run `/paper-ingest full 2105.13327` to upgrade.

- ## Cited By (in this wiki)
	- [[wiki/projects/growing-computation]]
