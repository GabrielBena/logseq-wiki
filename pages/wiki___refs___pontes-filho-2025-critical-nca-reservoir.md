title:: wiki/refs/pontes-filho-2025-critical-nca-reservoir
category:: reference
type:: external-ref
tags:: nca, self-organisation, reservoir-computing, criticality, evolution
authors:: Pontes-Filho, Sidney; Nichele, Stefano; Lepperød, Mikkel
year:: 2025
venue:: IEEE Symposium on Artificial Life (ALIFE 2025)
arxiv:: 2508.02218
citation-count:: 2
summary:: An ANN-governed NCA is evolved toward criticality (power-law avalanches) as a reservoir substrate — perfect 5-bit memory, MNIST matching the best elementary CA; a self-organized critical system.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-06-21
created:: 2026-06-21
updated:: 2026-06-21
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Reservoir Computing with Evolved Critical Neural Cellular Automata** — Pontes-Filho, Nichele & Lepperød (2025), ALIFE 2025 (Simula / OsloMet / Østfold).
	- A second reviewer-suggested reservoir-computing-on-CA comparison for [[wiki/research/self-organising-digital-circuits]]; from the Nichele lab, linking to the [[EngramNCA]] line.

- ## Abstract (extracted)
	- Criticality is a behavioral state in dynamical systems that is known to present the highest computation capabilities, i.e., information transmission, storage, and modification. Therefore, such systems are ideal candidates as a substrate for reservoir computing, a subfield in artificial intelligence. Our choice of a substrate is a cellular automaton (CA) governed by an artificial neural network, also known as neural cellular automaton (NCA). We apply evolution strategy to optimize the NCA to achieve criticality, demonstrated by power law distributions in structures called avalanches. With an evolved critical NCA, the substrate is tested for reservoir computing. Our evaluation of the substrate is performed with two benchmarks, 5-bit memory task and image classification of handwritten digits. The result of the 5-bit memory task achieved a perfect score and the system managed to remember all 5 bits. The result for the image classification task matched and sometimes surpassed the performance of the best elementary CA for this task. Moreover, the proposed critical NCA may operate as a self-organized critical system, due to its robustness to extreme initial conditions.

- ## Key Ideas
	- An **NCA whose update rule is an ANN** is optimized **by evolution strategy toward criticality** (power-law avalanche distributions) ^[inferred].
	- Used as a **reservoir-computing substrate**: **perfect 5-bit memory** score; **MNIST matching/surpassing the best elementary CA** ^[inferred].
	- Argues the evolved critical NCA is a **self-organized-criticality substrate, robust to extreme initial conditions** ^[inferred].

- ## Connections to Wiki
	- [[wiki/research/self-organising-digital-circuits]] — reviewer R1e comparison; reservoir-on-CA where the substrate is evolved for *generic* capacity and read out separately, vs SODC's policy directly configuring a *specified* function ^[inferred].
	- [[wiki/concepts/neural-cellular-automata]] — an evolved-rule NCA used as a computational substrate.
	- [[wiki/concepts/self-organisation]] — self-organized criticality as the operating regime.
	- [[wiki/refs/guichard-2025-engramnca]] — same Nichele-lab NCA lineage ^[from source note].

- ## Open Questions / To Read
	- Does tuning to criticality transfer across task families, or is it benchmark-specific? (abstract-only). Upgrade with `/paper-ingest full`.
	- SODC bibkey: `pontes_filho_reservoir_2025`. Reference code: github.com/bioAI-Oslo/critical-nca-reservoir ^[from source note, unverified]. (S2 lists only an arXiv DOI 10.48550/arXiv.2508.02218; the ISAL DOI in the source note was unreliable.)

- ## Cited By (in this wiki)
	- (forward-linked from this ref; SODC backlink added during the ALIFE-revision intake)
