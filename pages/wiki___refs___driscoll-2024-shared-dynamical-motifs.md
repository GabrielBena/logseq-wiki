title:: wiki/refs/driscoll-2024-shared-dynamical-motifs
category:: reference
type:: external-ref
tags:: modularity, functional-specialization, dynamical-systems, compositional-learning, rnn, neuroscience
authors:: Driscoll, Laura N.; Shenoy, Krishna V.; Sussillo, David
year:: 2024
venue:: Nature Neuroscience
doi:: 10.1038/s41593-024-01668-6
citation-count:: 58
summary:: Multitask RNNs reuse "dynamical motifs" (attractors, rotations, decision boundaries) across tasks; these unit-cluster patterns are the compositional building block between neuron and network.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-06-21
created:: 2026-06-21
updated:: 2026-06-21
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Flexible multitask computation in recurrent networks utilizes shared dynamical motifs** — Driscoll, Shenoy & Sussillo (2024), Nature Neuroscience.
	- The dynamical-systems account of *functional* modularity in multitask networks — a direct companion to [[wiki/research/dynamics-specialization]]'s structural-vs-functional split.

- ## Abstract (extracted)
	- Flexible computation is a hallmark of intelligent behavior. However, little is known about how neural networks contextually reconfigure for different computations. In the present work, we identified an algorithmic neural substrate for modular computation through the study of multitasking artificial recurrent neural networks. Dynamical systems analyses revealed learned computational strategies mirroring the modular subtask structure of the training task set. Dynamical motifs, which are recurring patterns of neural activity that implement specific computations through dynamics, such as attractors, decision boundaries and rotations, were reused across tasks. For example, tasks requiring memory of a continuous circular variable repurposed the same ring attractor. We showed that dynamical motifs were implemented by clusters of units when the unit activation function was restricted to be positive. Cluster lesions caused modular performance deficits. Motifs were reconfigured for fast transfer learning after an initial phase of learning. This work establishes dynamical motifs as a fundamental unit of compositional computation, intermediate between neuron and network.

- ## Key Ideas
	- **Dynamical motifs** — recurring activity patterns (attractors, decision boundaries, rotations) that implement specific computations through dynamics — are **reused across tasks** ^[inferred].
	- Motifs are implemented by **clusters of units** *only when the activation function is non-negative*; **cluster lesions cause modular performance deficits** (causal link motif↔cluster) ^[inferred].
	- The motif is proposed as **the unit of compositional computation, intermediate between neuron and network** ^[inferred].
	- Motifs are **reconfigured for fast transfer learning** after an initial learning phase ^[inferred].

- ## Connections to Wiki
	- [[wiki/research/spatial-neuromorphic-priors]] — the Ch2 functional-analysis work that uses this: its Selectivity-Clustering-Lesion pipeline is Yang/Driscoll-style, and the non-negative-activation caveat directly motivates the retanh/softplus question in its methodology reform.
	- [[wiki/research/dynamics-specialization]] — the Ch1 precedent in the same modularity arc ("structure ≠ function"); Driscoll supplies the *positive* account of what functional modularity looks like dynamically (motifs as the unit).
	- [[wiki/concepts/modularity]] — dynamical motifs are a concrete, mechanistic notion of a functional module.
	- [[wiki/concepts/compositional-learning]] — motif reuse = compositional recombination of learned computations.

- ## Open Questions / To Read
	- The cluster↔motif correspondence is gated on non-negative activations — how much of a tanh network's structure is just rotated-basis motifs? (abstract-only; upgrade with `/paper-ingest full`)
	- Fixed-point / Jacobian methodology (Sussillo's FixedPointFinder) is the analysis backbone — relevant to any motif-sharing graph over input conditions.

- ## Cited By (in this wiki)
	- [[wiki/research/spatial-neuromorphic-priors]] — uses this in its functional-analysis methodology (the Selectivity-Clustering-Lesion pipeline + the retanh/softplus reframe).
	- [[wiki/research/dynamics-specialization]] — Ch1 arc precedent; the dynamical-systems account of functional modularity (the "what computes" companion).
