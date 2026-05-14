title:: wiki/refs/goyal-2021-shared-global-workspace
category:: reference
type:: external-ref
tags:: global-workspace, modularity, transformers, attention, deep-learning
authors:: Goyal, Anirudh; Didolkar, Aniket; Lamb, Alex; Badola, Kartikeya; Ke, Nan Rosemary; Rahaman, Nasim; Binas, Jonathan; Blundell, Charles; Mozer, Michael; Bengio, Yoshua
year:: 2021
venue:: ICLR
arxiv:: 2103.01197
citation-count:: 114
summary:: Architecture proposal — specialist modules communicate through a shared bandwidth-limited workspace, must compete for access. Capacity limits encourage specialisation/compositionality and synchronise otherwise independent specialists. Direct ML operationalisation of GWT, complementary to VanRullen & Kanai.
confidence:: 0.44
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Coordination Among Neural Modules Through a Shared Global Workspace** — Goyal, Didolkar, Lamb, Badola, Ke, Rahaman, Binas, Blundell, Mozer & Bengio (2021), *ICLR*. arXiv:2103.01197. 114 citations.
	- [[wiki/concepts/global-workspace-theory]] — alongside [[wiki/refs/vanrullen-2020-deep-learning-global-workspace]], one of the two anchor papers for GWT-as-ML-architecture.
- ## Abstract (extracted)
	- Deep learning has seen a movement away from representing examples with a monolithic hidden state towards a richly structured state. For example, Transformers segment by position, and object-centric architectures decompose images into entities. In all these architectures, interactions between different elements are modeled via pairwise interactions: Transformers make use of self-attention to incorporate information from other positions; object-centric architectures make use of graph neural networks to model interactions among entities. However, pairwise interactions may not achieve global coordination or a coherent, integrated representation that can be used for downstream tasks. In cognitive science, a global workspace architecture has been proposed in which functionally specialized components share information through a common, bandwidth-limited communication channel. We explore the use of such a communication channel in the context of deep learning for modeling the structure of complex environments. The proposed method includes a shared workspace through which communication among different specialist modules takes place but due to limits on the communication bandwidth, specialist modules must compete for access. We show that capacity limitations have a rational basis in that (1) they encourage specialization and compositionality and (2) they facilitate the synchronization of otherwise independent specialists.
- ## Key Ideas
	- **Pairwise attention is insufficient for global coordination.** Self-attention in Transformers and object-centric GNNs model interactions, but never reach a *coherent integrated* state — there's no contention bottleneck forcing synthesis. ^[inferred]
	- **Workspace as bandwidth-limited shared channel.** Specialist modules write into a small, shared latent; capacity is the load-bearing constraint. ^[inferred]
	- **Capacity limits are functional, not just regularisation.** Two reported benefits: (1) competition drives **specialisation and compositionality** in modules, (2) the workspace **synchronises** otherwise independent specialists. ^[inferred]
	- **Architecture is concrete and trainable** — distinct from VanRullen & Kanai's *roadmap*, this paper proposes a specific runnable module. The two are complementary GWT-as-ML references. ^[inferred]
- ## Connections to Wiki
	- [[wiki/concepts/global-workspace-theory]] — paired with [[wiki/refs/vanrullen-2020-deep-learning-global-workspace]] for the GWT-as-architecture cluster. Goyal et al. is the *constructive* counterpart to VanRullen & Kanai's *roadmap*.
	- [[wiki/projects/growing-networks]] — the Perceiver-as-workspace pattern envisioned in growing-networks is mechanically close to this paper's shared-workspace architecture.
	- [[wiki/refs/jaegle-2021-perceiver-io]] — Perceiver IO and the shared workspace share the same primitive: small latent + cross-attention as a competitive bottleneck. ^[inferred]
	- [[wiki/concepts/modularity]] — load-bearing claim that capacity limits drive specialisation provides a *functional* argument for emergent modularity (consistent with the thesis-side modularity-by-pressure framing).
	- [[wiki/concepts/compositional-learning]] — the paper explicitly claims compositionality as a benefit of workspace bandwidth limits.
- ## Open Questions / To Read
	- How large is the workspace they actually use, and does the qualitative behaviour change with workspace size? Needs full read.
	- Comparison with later mixture-of-experts / shared-expert designs that have similar competition-for-routing dynamics.
- ## Cited By (in this wiki)
	- [[wiki/concepts/global-workspace-theory]]
	- [[wiki/projects/growing-networks]]
