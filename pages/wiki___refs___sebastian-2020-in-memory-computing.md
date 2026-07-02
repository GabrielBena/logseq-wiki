title:: wiki/refs/sebastian-2020-in-memory-computing
category:: reference
type:: external-ref
tags:: in-memory-computing, memristor, rram, hardware, neuromorphic, review
authors:: Sebastian, Abu; Le Gallo, Manuel; Khaddam-Aljameh, Riduan; Eleftheriou, Evangelos
year:: 2020
venue:: Nature Nanotechnology
doi:: 10.1038/s41565-020-0655-z
pmid:: 32231270
citation-count:: 1970
summary:: IBM-Zürich review of in-memory computing — the computational primitives charge/resistance-based memory devices enable, their applications, and the device non-idealities (noise/drift/variability) that limit scaling.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-07-02
created:: 2026-07-02
updated:: 2026-07-02
sources:: api:semanticscholar, api:pubmed
wiki-generated:: true
ingest-mode:: abstract

- **Memory devices and applications for in-memory computing** — Sebastian, Le Gallo, Khaddam-Aljameh, Eleftheriou (2020), *Nature Nanotechnology* 15:529–544 (Review). **IBM Research – Zürich.** A device-physics pillar for [[wiki/deliverables/eth-fellowship-2026]] §1–2 (the "in-memory computing is the route past the memory wall, but device non-idealities are the barrier" grounding). ^[author]
- ## Abstract (extracted)
	- Traditional von Neumann computing systems involve separate processing and memory units. However, data movement is costly in terms of time and energy and this problem is aggravated by the recent explosive growth in highly data-centric applications related to artificial intelligence. This calls for a radical departure from the traditional systems and one such non-von Neumann computational approach is in-memory computing. Hereby certain computational tasks are performed in place in the memory itself by exploiting the physical attributes of the memory devices. Both charge-based and resistance-based memory devices are being explored for in-memory computing. In this Review, we provide a broad overview of the key computational primitives enabled by these memory devices as well as their applications spanning scientific computing, signal processing, optimization, machine learning, deep learning and stochastic computing. ^[extracted]
- ## Key ideas ^[inferred]
	- **In-memory computing = compute where the data lives**: exploit the physical attributes of memory devices to do computation in place, eliminating the von-Neumann data-movement bottleneck (the "memory wall"). ^[inferred]
	- Spans **charge-based** (SRAM/DRAM/Flash) and **resistance-based** (PCM/RRAM/memristive) devices, across **digital, analogue, and stochastic** computing schemes. ^[inferred]
	- Computational primitives cover a broad application span: scientific computing, signal processing, optimization, ML/DL, stochastic computing. ^[inferred]
	- The Review's Challenges section names **device non-idealities + scaling characteristics** as the barrier to next-generation in-memory computing — the specific point the ETH bid cites. *(Fleet-verified beyond the abstract, `wiki/_pdfs/eth-litreview-2026-06-26/`: "noise, drift, write variability fundamentally limit in-memory computing; on-chip training accuracy explicitly open.")* ^[inferred]
- ## Connections to Wiki
	- [[wiki/deliverables/eth-fellowship-2026]] — device-physics anchor (①/②: the substrate varies / drifts / ages).
	- [[wiki/projects/self-organising-mosaic-compiler]] — the in-memory substrate class this project targets.
	- [[wiki/concepts/substrate-rule-co-location]] — in-memory computing is the hardware setting for the co-location problem.
	- [[wiki/refs/ielmini-2018-resistive-switching]] — companion review, RRAM-specific.
	- [[wiki/refs/kudithipudi-2025-neuromorphic-at-scale]] — the roadmap that names this device-physics barrier.
- ## Open Questions / To Read
	- Abstract-mode: the non-ideality taxonomy + on-chip-training-accuracy limits live in the paper body (verified summary in the lit-review pool). Upgrade to full with `/paper-ingest full` if exact figures are needed. ^[inferred]
- ## Cited By (in this wiki)
	- [[wiki/deliverables/eth-fellowship-2026]]
