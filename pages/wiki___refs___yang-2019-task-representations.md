title:: wiki/refs/yang-2019-task-representations
category:: reference
type:: external-ref
tags:: modularity, functional-specialization, compositional-learning, rnn, neuroscience
authors:: Yang, Guangyu Robert; Joglekar, Madhura R.; Song, H. Francis; Newsome, William T.; Wang, Xiao-Jing
year:: 2019
venue:: Nature Neuroscience
doi:: 10.1038/s41593-018-0310-2
citation-count:: 593
summary:: A single RNN trained on 20 cognitive tasks develops functionally specialized unit clusters and compositional task representations (recombinable instructions); the classic functional-clusters result.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-06-21
created:: 2026-06-21
updated:: 2026-06-21
sources:: api:semanticscholar, api:pubmed
wiki-generated:: true
ingest-mode:: abstract

- **Task representations in neural networks trained to perform many cognitive tasks** — Yang, Joglekar, Song, Newsome & Wang (2019), Nature Neuroscience.
	- The foundational "functional clusters emerge in multitask RNNs" paper and the origin of the **Yang-style task-variance selectivity measure** that the functional-analysis pipeline builds on.

- ## Abstract (extracted)
	- The brain has the ability to flexibly perform many tasks, but the underlying mechanism cannot be elucidated in traditional experimental and modeling studies designed for one task at a time. Here, we trained single network models to perform 20 cognitive tasks that depend on working memory, decision making, categorization, and inhibitory control. We found that after training, recurrent units can develop into clusters that are functionally specialized for different cognitive processes, and we introduce a simple yet effective measure to quantify relationships between single-unit neural representations of tasks. Learning often gives rise to compositionality of task representations, a critical feature for cognitive flexibility, whereby one task can be performed by recombining instructions for other tasks. Finally, networks developed mixed task selectivity similar to recorded prefrontal neurons after learning multiple tasks sequentially with a continual-learning technique. This work provides a computational platform to investigate neural representations of many cognitive tasks. *(abstract via PubMed PMID 30643294; not exposed by Semantic Scholar or CrossRef.)*

- ## Key Ideas
	- A **single network trained on 20 cognitive tasks** develops **functionally specialized clusters** of recurrent units ^[inferred].
	- Introduces a **simple measure for single-unit task-relationship structure** (the "task-variance" selectivity that downstream functional-analysis pipelines adopt) ^[inferred].
	- Learning gives rise to **compositionality**: a task can be performed by **recombining instructions** for other tasks ^[inferred].
	- Sequential continual learning produces **PFC-like mixed selectivity** ^[inferred].

- ## Connections to Wiki
	- [[wiki/research/spatial-neuromorphic-priors]] — the Ch2 work whose Selectivity-Clustering-Lesion pipeline uses Yang's task-variance selectivity measure; the "phantom selectivity at init" critique in its methodology reform is precisely a critique of applying Yang-style selectivity without an init baseline.
	- [[wiki/research/dynamics-specialization]] — the Ch1 precedent (same arc): Yang's functional-cluster framing is the methodological ancestor for testing whether clusters track structural modules.
	- [[wiki/concepts/modularity]] — functional specialization as emergent unit clusters.
	- [[wiki/concepts/compositional-learning]] — compositionality of task representations is the headline claim.

- ## Open Questions / To Read
	- The Yang selectivity measure is per-task-period and assumes sequence-stable contexts — how does it behave when contexts change every timestep? (the dilation question in the functional-analysis reframe). Upgrade with `/paper-ingest full`.

- ## Cited By (in this wiki)
	- [[wiki/research/spatial-neuromorphic-priors]] — its Selectivity-Clustering-Lesion pipeline uses Yang-style task-variance selectivity.
	- [[wiki/research/dynamics-specialization]] — Ch1 arc precedent; the functional-clusters methodological ancestor.
