title:: wiki/refs/barabasi-2023-complex-computation-developmental-priors
category:: reference
type:: external-ref
tags:: developmental-priors, neurodevelopment, genomic-bottleneck, neural-evolution, innateness
authors:: Barabási, Dániel L.; Beynon, Taliesin; Katona, Adam
year:: 2023
venue:: Nature Communications
doi:: 10.1038/s41467-023-37980-1
citation-count:: 20
summary:: Neurodevelopmental encoding of ANNs — weight matrices treated as emergent from neuronal-compatibility rules. Optimisation acts on wiring rules rather than weights, mirroring evolutionary selection on brain development. Compressed parameter count + regularising effect on meta-learning.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Complex computation from developmental priors** — Barabási, Beynon & Katona (2023), *Nature Communications*. (S2 lists 2022 — the bioRxiv preprint version; the NatComms DOI is 2023.) 20 citations as of ingest.
	- [[wiki/concepts/genomic-bottleneck]] — operationalises Zador's idea: weights are *not* the optimisation target, the developmental rule is.
- ## Abstract (extracted)
	- Machine learning (ML) models have long overlooked innateness: how strong pressures for survival lead to the encoding of complex behaviors in the nascent wiring of a brain. Here, we derive a neurodevelopmental encoding of artificial neural networks that considers the weight matrix of a neural network to be emergent from well-studied rules of neuronal compatibility. Rather than updating the network's weights directly, we improve task fitness by updating the neurons' wiring rules, thereby mirroring evolutionary selection on brain development. We find that our model (1) provides sufficient representational power for high accuracy on ML benchmarks while also compressing parameter count, and (2) can act as a regularizer, selecting simple circuits that provide stable and adaptive performance on metalearning tasks. In summary, by introducing neurodevelopmental considerations into ML frameworks, we not only model the emergence of innate behaviors, but also define a discovery process for structures that promote complex computations. Neuroscience has long inspired AI, however the neuroevolutionary search that produces sophisticated behaviors has not been systematized. This paper defines neurodevelopmental ML as a discovery process for structures that promote complex computations.
- ## Key Ideas
	- **Weights as emergent.** The network's weight matrix is *derived* from a small set of neuronal compatibility rules, not directly optimised. The rules are the genome; the matrix is the brain. ^[inferred]
	- **Optimisation lives at the rule level.** Task fitness updates wiring rules rather than weights — algorithmically a form of neuro-evolution but with a structured developmental prior. ^[inferred]
	- **Two reported benefits.** (1) Competitive accuracy on benchmarks with compressed parameter count — the encoding is *more efficient* than direct weight parameterisation. (2) Regularising effect on meta-learning — selects simple, stable, adaptive circuits. ^[inferred]
	- **Discovery process framing.** The paper positions neurodevelopmental ML as a *discovery* process for computation-promoting structures, not just a competitive ML method. ^[inferred]
- ## Connections to Wiki
	- [[wiki/concepts/genomic-bottleneck]] — direct operationalisation of Zador's bottleneck via developmental priors.
	- [[wiki/refs/zador-2019-critique-pure-learning]] — the framing paper; Barabási et al. provide the constructive answer.
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — sister work from the Risi-lab cluster; both grow networks from developmental rules but via different mechanisms.
	- [[wiki/refs/plantec-2024-lifelong-ndp]] — adjacent: LNDP adds lifelong plasticity to the NDP framework.
	- [[wiki/research/growing-networks]] — postdoc proposal explicitly draws on the developmental-priors line.
	- [[wiki/concepts/neural-cellular-automata]] — NCA-as-genomic-bottleneck framing in the wiki maps cleanly onto Barabási's "rules emit weights" pattern. ^[inferred]
- ## Open Questions / To Read
	- What *exactly* are the "neuronal compatibility rules" — chemo-affinity-style or more abstract? Needs full read.
	- How does the meta-learning regularisation compare quantitatively to standard meta-learning baselines?
	- Relation to LNDP's activity-dependent dynamics — Barabási's rules look weight-static at deployment.
- ## Cited By (in this wiki)
	- [[wiki/concepts/genomic-bottleneck]]
	- [[wiki/research/growing-networks]]
	- [[wiki/refs/zador-2019-critique-pure-learning]]
