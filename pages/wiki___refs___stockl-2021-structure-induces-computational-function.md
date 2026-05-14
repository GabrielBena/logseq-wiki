title:: wiki/refs/stockl-2021-structure-induces-computational-function
category:: reference
type:: external-ref
tags:: spiking-neurons, genomic-bottleneck, neuron-types, innate-computation, structure-function
authors:: Stöckl, Christoph; Lang, Dominik; Maass, Wolfgang
year:: 2021
venue:: bioRxiv
doi:: 10.1101/2021.05.18.444689
biorxiv:: 2021.05.18.444689
citation-count:: 14
summary:: Spiking-neuron networks gain substantial *innate* computing capabilities when the genome specifies only type-dependent, distance-dependent connection probabilities — provided the network has many neuron types. Direct operationalisation of the genomic-bottleneck argument with experimentally-grounded substrate.
confidence:: 0.41
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Structure induces computational function in networks with diverse types of spiking neurons** — Stöckl, Lang & Maass (2021), bioRxiv preprint. DOI:10.1101/2021.05.18.444689. 14 citations.
	- [[wiki/concepts/genomic-bottleneck]] — load-bearing operationalisation: genome encodes connection probabilities by neuron type, not individual synapses; *low-dimensional code* is sufficient for innate function.
- ## Abstract (extracted)
	- Nature endows networks of spiking neurons in the brain with innate computing capabilities. But it has remained an open problem how the genome achieves that. Experimental data imply that the genome encodes synaptic connection probabilities between neurons depending on their genetic types and spatial distance. We show that this low-dimensional parameterization suffices for programming fundamental computing capabilities into networks of spiking neurons. However, this method is only effective if the network employs a substantial number of different neuron types. This provides an intriguing answer to the open question why the brain employs so many neuron types, many more than were used so far in neural network models. Neural networks whose computational function is induced through their connectivity structure, rather than through synaptic plasticity, are distinguished by short wire length and robustness to weight perturbations. These neural networks features are not only essential for the brain, but also for energy-efficient neuromorphic hardware.
- ## Key Ideas
	- **Genome-encoded code is low-dimensional but sufficient.** Connection probabilities indexed by neuron type and spatial distance are enough for innate computing capabilities — no per-synapse specification needed. ^[inferred]
	- **Neuron-type diversity is load-bearing.** The method only works when a *substantial* number of neuron types are present. This is offered as an explanation for why brains have so many cell types — well beyond what classical neural-network models use. ^[inferred]
	- **Structure-induced computation has dual benefits.** Networks whose function comes from connectivity (rather than plasticity) exhibit **short wire length** and **robustness to weight perturbations** — useful for neuromorphic hardware. ^[inferred]
	- **No plasticity required.** Demonstrates that *structure alone*, set by a compact genomic code, produces functional networks — the strongest possible version of [[wiki/refs/zador-2019-critique-pure-learning]] argument. ^[inferred]
- ## Connections to Wiki
	- [[wiki/concepts/genomic-bottleneck]] — perhaps the most direct *operationalisation* of the bottleneck argument: a low-dim type-by-distance code that *demonstrably* produces innate function.
	- [[wiki/refs/zador-2019-critique-pure-learning]] — Stöckl/Maass is what Zador's argument looks like when fully reduced to an implementation: structure-induced function via a compact genomic code.
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]] — adjacent: Barabási operates on wiring *rules*, Stöckl/Maass operates on type-conditioned *probabilities*. Both reject direct weight specification; different parameterisation of the developmental encoding.
	- [[wiki/research/spatial-neuromorphic-priors]] — directly relevant: spatial-distance-based connection rules are the spatial-prior story extended to spiking nets with type diversity.
	- [[wiki/projects/growing-networks]] — supports the developmental-rule + budget story; the *wire length* and *weight robustness* benefits are exactly the budget-aware properties the project argues for.
	- [[wiki/refs/dalgaty-2024-mosaic]] — possible neuromorphic-hardware tie-in: Stöckl/Maass's "energy-efficient neuromorphic hardware" framing.
	- [[wiki/refs/achterberg-2023-sernns]] — adjacent line on spatially-embedded networks producing modular structure under wire-cost regularisation.
- ## Open Questions / To Read
	- What "fundamental computing capabilities" are demonstrated? Needs full read to map exactly which tasks the type-conditioned probabilities solve.
	- How many neuron types are needed in practice? The abstract claims "substantial" — quantification matters for the genomic-bottleneck argument.
	- Is the work plasticity-free *forever*, or just at initialisation? If structure-induced function is plastic-compatible, this is much stronger.
- ## Cited By (in this wiki)
	- [[wiki/concepts/genomic-bottleneck]]
	- [[wiki/projects/growing-networks]]
