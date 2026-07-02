title:: wiki/refs/ielmini-2018-resistive-switching
category:: reference
type:: external-ref
tags:: in-memory-computing, rram, memristor, resistive-switching, hardware, review
authors:: Ielmini, Daniele; Wong, H.-S. Philip
year:: 2018
venue:: Nature Electronics
doi:: 10.1038/s41928-018-0092-2
citation-count:: 1911
summary:: Review of in-memory computing with resistive-switching (RRAM) devices — the memory wall, digital/analogue/stochastic schemes, the microscopic switching physics, and the scaling challenges toward next-gen computing.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-07-02
created:: 2026-07-02
updated:: 2026-07-02
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **In-memory computing with resistive switching devices** — Ielmini & Wong (2018), *Nature Electronics* 1:333–343 (Review). The RRAM-specific device-physics pillar for [[wiki/deliverables/eth-fellowship-2026]] — the companion to [[wiki/refs/sebastian-2020-in-memory-computing]]. ^[author]
- ## Abstract (extracted)
	- Modern computers are based on the von Neumann architecture in which computation and storage are physically separated: data are fetched from the memory unit, shuttled to the processing unit (where computation takes place) and then shuttled back to the memory unit to be stored. The rate at which data can be transferred between the processing unit and the memory unit represents a fundamental limitation of modern computers, known as the memory wall. In-memory computing is an approach that attempts to address this issue by designing systems that compute within the memory, thus eliminating the energy-intensive and time-consuming data movement that plagues current designs. Here we review the development of in-memory computing using resistive switching devices, where the two-terminal structure of the devices, their resistive switching properties, and direct data processing in the memory can enable area- and energy-efficient computation. We examine the different digital, analogue, and stochastic computing schemes that have been proposed, and explore the microscopic physical mechanisms involved. Finally, we discuss the challenges in-memory computing faces, including the required scaling characteristics, in delivering next-generation computing. ^[extracted]
- ## Key ideas ^[inferred]
	- The **memory wall** — the processing↔memory data-transfer rate — is a fundamental limit of von-Neumann computers; in-memory computing sidesteps it by computing *within* the memory. ^[inferred]
	- **Resistive-switching (RRAM) devices**: their two-terminal structure + resistive-switching physics enable area- and energy-efficient in-memory computation. ^[inferred]
	- Surveys **digital, analogue, and stochastic** in-memory computing schemes and the microscopic physical mechanisms behind them. ^[inferred]
	- Names the **required scaling characteristics** (endurance / retention / variability trade-offs) as the central challenge for delivering next-generation in-memory computing — the device-non-ideality barrier the ETH bid leans on. ^[inferred]
- ## Connections to Wiki
	- [[wiki/deliverables/eth-fellowship-2026]] — device-physics anchor (RRAM specifically).
	- [[wiki/refs/sebastian-2020-in-memory-computing]] — companion in-memory-computing review.
	- [[wiki/concepts/memristor-crossbar]] — the substrate whose physics this reviews.
	- [[wiki/projects/self-organising-mosaic-compiler]] — targets exactly this RRAM / memristive substrate class.
	- [[wiki/refs/dalgaty-2024-mosaic]] — a fabricated memristive in-memory system instance.
- ## Open Questions / To Read
	- Abstract-mode; the switching-physics detail + the endurance/retention trade-off numbers are in the body. ^[inferred]
- ## Cited By (in this wiki)
	- [[wiki/deliverables/eth-fellowship-2026]]
