title:: wiki/refs/zador-2019-critique-pure-learning
category:: reference
type:: external-ref
tags:: genomic-bottleneck, evo-devo, neuroscience-ai, encoding, innateness
authors:: Zador, Anthony
year:: 2019
venue:: Nature Communications
doi:: 10.1038/s41467-019-11786-6
citation-count:: 533
summary:: Foundational argument that most animal behaviour is encoded in the genome via a "genomic bottleneck" — the wiring diagram is too complex for explicit specification, so the genome must compress it into developmental rules. Direct seed for the genomic-bottleneck concept in growing-networks.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **A critique of pure learning and what artificial neural networks can learn from animal brains** — A. Zador (2019), *Nature Communications*. Single-author opinion piece. 533 citations.
	- [[wiki/concepts/genomic-bottleneck]] — coined the framing this concept page is built on.
- ## Abstract (extracted)
	- Artificial neural networks (ANNs) have undergone a revolution, catalyzed by better supervised learning algorithms. However, in stark contrast to young animals (including humans), training such networks requires enormous numbers of labeled examples, leading to the belief that animals must rely instead mainly on unsupervised learning. Here we argue that most animal behavior is not the result of clever learning algorithms—supervised or unsupervised—but is encoded in the genome. Specifically, animals are born with highly structured brain connectivity, which enables them to learn very rapidly. Because the wiring diagram is far too complex to be specified explicitly in the genome, it must be compressed through a "genomic bottleneck". The genomic bottleneck suggests a path toward ANNs capable of rapid learning. Recent gains in artificial neural networks rely heavily on large amounts of training data. Here, the author suggests that for AI to learn from animal brains, it is important to consider that animal behaviour results from brain connectivity specified in the genome through evolution, and not due to unique learning algorithms.
- ## Key Ideas
	- **Most animal behaviour is encoded, not learnt.** Young animals exhibit complex behaviour with no training data — the structure is innate. The dichotomy between supervised and unsupervised learning is the wrong axis. ^[inferred]
	- **The genome cannot specify the wiring directly.** A few-Gb genome cannot encode the ~10¹⁵ synapses of a human brain explicitly — there must be a *compressive* developmental program. This compression is the *genomic bottleneck*. ^[inferred]
	- **Implication for ANNs.** Rapid learning in animals comes from highly structured *initial* connectivity. ANN architectures that pre-specify rich structural priors should learn more efficiently than blank-slate nets. ^[inferred]
	- The bottleneck is *productive*: it forces compositional, repeatable, locally-applicable encoding schemes. (Inferred — Zador frames the bottleneck as a feature, not a constraint.) ^[inferred]
- ## Connections to Wiki
	- [[wiki/concepts/genomic-bottleneck]] — this paper coined the framing; the concept page summary explicitly references it.
	- [[wiki/research/growing-networks]] — Zador is the foundational reference for the genomic-bottleneck thread of the postdoc proposal.
	- [[wiki/concepts/neural-cellular-automata]] — NCAs are arguably a computational realisation of the bottleneck idea: a small parameter set encodes the rule that grows the target structure. ^[inferred]
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — NDP is an explicit operationalisation of Zador's bottleneck idea, with a per-cell NN that grows the topology from a developmental rule.
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]] — complementary recent work that operationalises the "innateness" idea via developmental priors on weight matrices.
- ## Open Questions / To Read
	- Zador doesn't propose a specific algorithm — the paper is a position piece. The follow-up question is *how to operationalise* the bottleneck in trainable systems. The wiki's NCA / NDP / engram cluster collectively answers this.
	- How does Zador's bottleneck relate to the broader meta-learning literature (learn-to-learn)? Different framing but related compression argument. ^[inferred]
- ## Cited By (in this wiki)
	- [[wiki/concepts/genomic-bottleneck]]
	- [[wiki/research/growing-networks]]
