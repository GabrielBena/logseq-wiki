title:: wiki/refs/raghunathan-2026-noracl-neurogenesis
category:: reference
type:: external-ref
tags:: continual-learning, neurogenesis, growth, plasticity, postdoc-adjacent
authors:: Raghunathan, Karthik; Metzner, Christian; Kriener, Laura; Payvand, Melika
year:: 2026
venue:: arXiv (preprint)
arxiv:: 2604.27031
citation-count:: 0
summary:: NORACL — neurogenesis-inspired continual learning that grows network capacity on demand. Starts from a compact net and adds capacity only when monitored representational/plasticity signals saturate; matches or beats oracle-sized static baselines with fewer parameters.
confidence:: 0.41
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning** — Raghunathan, Metzner, Kriener, Payvand (2026), arXiv preprint 2604.27031. From Melika Payvand's lab.
	- [[wiki/research/growing-networks]] — directly motivates the postdoc growing-networks thread; "Karthik's paper" cited in the brainstorm.
- ## Abstract (extracted)
	- In a continual learning setting, we require a model to be plastic enough to learn a new task and stable enough to not disturb previously learned capabilities. We argue that this dilemma has an architectural root. A finite network has limited representational and plastic resources, yet the required capacity depends on properties of the future task stream that are unknown: how many tasks will be encountered, and how much they overlap in feature space. Regularization-based methods preserve past knowledge within fixed-capacity architectures and therefore implicitly rely on an oracle architecture sized for this unknown future. When tasks are only weakly related, fixed architectures progressively run out of plastic resources; when tasks are few or strongly overlapping, models are often over-provisioned. Inspired by neurogenesis in biology, we propose NORACL to address the stability-plasticity dilemma by tackling the oracle architecture problem through neuronal growth. Starting from a compact network, NORACL grows only when needed by monitoring two complementary signals for representational and plasticity saturation. We evaluate NORACL against oracle-sized static baselines across varying task counts and geometries. Across all settings, NORACL achieves final average accuracies that are better than or on par with oracle-provisioned static baselines while using fewer parameters. Additionally, NORACL yields architectures with interpretable growth, i.e. dissimilar tasks predominantly expand feature-extraction layers, whereas tasks which rely on common features shift growth toward later feature-combination layers. Our analysis further explains why fixed-capacity networks lose plasticity as tasks accumulate, whereas NORACL creates fresh capacity for new tasks through growth.
- ## Key Ideas
	- Reframes the **stability-plasticity dilemma as an architectural problem**: fixed-capacity nets implicitly assume an "oracle architecture" sized for the unknown future task stream. ^[inferred]
	- **Trigger-based growth**: two complementary monitoring signals (representational saturation + plasticity saturation) gate when new capacity is added — the network grows only when needed. ^[inferred]
	- **Interpretable growth**: dissimilar tasks expand feature-extraction layers; similar tasks expand feature-combination (later) layers. Growth pattern itself becomes a readout of task structure. ^[inferred]
	- Outperforms or matches oracle-sized static baselines with fewer total parameters → growth is more parameter-efficient than over-provisioning. ^[inferred]
- ## Connections to Wiki
	- [[wiki/research/growing-networks]] — direct cite. Provides a concrete, evaluated trigger-based growth mechanism that the broader growing-networks proposal can incorporate.
	- [[wiki/concepts/genomic-bottleneck]] — adjacent: NORACL grows only-as-needed, which is a form of *post-hoc compression* analogous to the genomic bottleneck's *prior* compression of developmental rules. ^[inferred]
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — both grow networks, but NDP grows from a developmental rule while NORACL grows reactively from task signals. Different mechanisms, same goal.
- ## Open Questions / To Read
	- How does NORACL handle pruning / death — or is growth only ever additive? Upgrade with full-text read.
	- Is the trigger mechanism *learnt* or hand-designed? Affects how generic the approach is.
	- Connection to spatial / neuromorphic priors ([[wiki/research/spatial-neuromorphic-priors]]) — NORACL's grown architectures could be analysed for spatial structure.
- ## Cited By (in this wiki)
	- [[wiki/research/growing-networks]]
