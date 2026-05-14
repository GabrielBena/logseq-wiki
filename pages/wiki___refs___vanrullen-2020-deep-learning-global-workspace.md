title:: wiki/refs/vanrullen-2020-deep-learning-global-workspace
category:: reference
type:: external-ref
tags:: global-workspace, deep-learning, consciousness, neuroscience-ai
authors:: VanRullen, Rufin; Kanai, Ryota
year:: 2020
venue:: Trends in Neurosciences
doi:: 10.1016/j.tins.2021.04.005
arxiv:: 2012.10390
citation-count:: 89
summary:: Roadmap for explicit deep-learning implementations of Global Workspace Theory — unsupervised neural translation between latent spaces produces an amodal Global Latent Workspace integrating specialised modules.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Deep Learning and the Global Workspace Theory** — VanRullen & Kanai (2020/2021), *Trends in Neurosciences*. arXiv:2012.10390.
	- [[wiki/concepts/global-workspace-theory]] — proposes the most direct ML operationalisation of GWT to date.
- ## Abstract (extracted)
	- Recent advances in deep learning have allowed AI to reach near human-level performance in many sensory, perceptual, linguistic, and cognitive tasks. There is a growing need, however, for novel, brain-inspired cognitive architectures. The Global Workspace Theory (GWT) refers to a large-scale system integrating and distributing information among networks of specialized modules to create higher-level forms of cognition and awareness. We argue that the time is ripe to consider explicit implementations of this theory using deep-learning techniques. We propose a roadmap based on unsupervised neural translation between multiple latent spaces (neural networks trained for distinct tasks, on distinct sensory inputs and/or modalities) to create a unique, amodal Global Latent Workspace (GLW). Potential functional advantages of GLW are reviewed, along with neuroscientific implications.
- ## Key Ideas
	- The workspace is constructed by **unsupervised neural translation** between independently-trained module latent spaces — translate then back, self-supervised. ^[inferred]
	- The Global Latent Workspace (GLW) is **amodal**: it accumulates representations across modalities rather than being tied to any one sensory stream. ^[inferred]
	- Argues this is now tractable specifically *because* of recent ML advances — a roadmap claim, not a complete architecture. ^[inferred]
	- Frames GWT as a path to **brain-inspired cognitive architectures**, positioning the workspace as more than a consciousness theory — also a useful AI design pattern. ^[inferred]
- ## Connections to Wiki
	- [[wiki/concepts/global-workspace-theory]] — primary conceptual anchor; this paper is one of the load-bearing GWT-as-architecture references for that concept page.
	- [[wiki/research/growing-networks]] — cited as inspiration for the Perceiver-as-workspace pattern in the postdoc brainstorm.
	- [[wiki/concepts/modularity]] — GWT's "specialised modules + shared workspace" is one answer to the modular-coordination problem.
	- [[wiki/refs/jaegle-2021-perceiver-io]] — architectural neighbour; Perceiver IO's small latent + cross-attention is *structurally* a workspace implementation. ^[inferred]
- ## Open Questions / To Read
	- The paper is a *roadmap*, not a complete model — would benefit from a full-text read once concrete experimental results appear. Upgrade with `/paper-ingest full arXiv:2012.10390`.
	- How does GLW relate to Goyal/Bengio's later shared-workspace formalism (arXiv:2103.01197)? Not yet ingested.
- ## Cited By (in this wiki)
	- [[wiki/research/growing-networks]]
	- [[wiki/concepts/global-workspace-theory]]
