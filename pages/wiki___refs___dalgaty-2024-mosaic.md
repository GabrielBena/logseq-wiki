title:: wiki/refs/dalgaty-2024-mosaic
category:: reference
type:: external-ref
tags:: neuromorphic, memristor, rram, in-memory-computing, small-world, routing, mosaic, hardware
authors:: Dalgaty, Thomas; Moro, Filippo; Demirağ, Yiğit; De Pra, Alessio; Indiveri, Giacomo; Vianello, Elisa; Payvand, Melika
year:: 2024
venue:: Nature Communications
doi:: 10.1038/s41467-023-44365-x
pmid:: 38167293
citation-count:: 61
summary:: The Mosaic neuromorphic chip — memristive Neuron Tiles (in-memory compute) + Routing Tiles (in-memory routing) implementing small-world SNN topologies in 130nm CMOS; ≥1 order-of-magnitude routing-energy savings.
confidence:: 0.60
lifecycle:: draft
lifecycle-changed:: 2026-07-02
created:: 2026-05-08
updated:: 2026-07-02
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Mosaic: in-memory computing and routing for small-world spike-based neuromorphic systems** — Dalgaty, Moro, Demirağ, De Pra, Indiveri, Vianello, **Payvand** (2024), *Nature Communications* 15 (DOI 10.1038/s41467-023-44365-x). The memristive substrate targeted by [[wiki/projects/self-organising-mosaic-compiler]] (Mosaic-v2). *Upgraded from stub → draft with the verified citation, 2026-07-02.* ^[author]
- ## Abstract (extracted)
	- The brain's connectivity is locally dense and globally sparse, forming a small-world graph — a principle prevalent in the evolution of various species, suggesting a universal solution for efficient information routing. However, current artificial neural network circuit architectures do not fully embrace small-world neural network models. Here, we present the neuromorphic Mosaic: a non-von Neumann systolic architecture employing distributed memristors for in-memory computing and in-memory routing, efficiently implementing small-world graph topologies for Spiking Neural Networks (SNNs). We've designed, fabricated, and experimentally demonstrated the Mosaic's building blocks, using integrated memristors with 130 nm CMOS technology. We show that thanks to enforcing locality in the connectivity, routing efficiency of Mosaic is at least one order of magnitude higher than other SNN hardware platforms. This is while Mosaic achieves a competitive accuracy in a variety of edge benchmarks. Mosaic offers a scalable approach for edge systems based on distributed spike-based computing and in-memory routing. ^[extracted]
- ## Key ideas ^[inferred]
	- **Non-von-Neumann systolic architecture**: distributed memristors do **in-memory computing** (dense **Neuron Tiles**) *and* **in-memory routing** (sparse **Routing Tiles**), realising **small-world** graph topologies for SNNs. ^[inferred]
	- **Designed, fabricated, and experimentally demonstrated** with integrated memristors in **130 nm CMOS** — a real chip, not a simulation. ^[inferred]
	- Enforcing locality → **routing efficiency ≥1 order of magnitude** higher than other SNN hardware platforms, at competitive edge-benchmark accuracy. ^[inferred]
	- **Reliability nuance:** Mosaic treats RRAM variability / drift / read-noise as a **non-ideality to *mitigate*** (noise-injection + quantization-aware training, ~2–3% loss) — **not** a resource to exploit. So Mosaic is the *substrate / routing* story; "variability-as-a-feature" belongs instead to [[wiki/refs/payvand-2022-memsorn]]. ^[inferred]
- ## Connections to Wiki
	- [[wiki/projects/self-organising-mosaic-compiler]] — the Mosaic-v2 substrate this project targets.
	- [[wiki/projects/growing-computation]] — inherited the Mosaic *geometry* (many-core, small-world, Router/Neuron-Tile split) but **rejected the memristor primitive** for [[wiki/concepts/fpga]]-style boolean fabric (frequent differentiation/recovery fights memristor write-cost / wear / drift — see [[wiki/concepts/memristor-crossbar]]). Mosaic is the conceptual ancestor.
	- [[wiki/research/spatial-neuromorphic-priors]] — uses Mosaic as a spatial prior: hop-distance connectivity → **Spatial DEEP-R** (`d_eff ∝ 1/P(h)`, P(h) = target connection probability at hop distance h); small-world routing as a structural inductive bias.
	- [[wiki/refs/payvand-2022-memsorn]] · [[wiki/refs/raghunathan-2026-noracl-neurogenesis]] — the host's self-organisation line on the same substrate family.
- ## Cited By (in this wiki)
	- [[wiki/research/spatial-neuromorphic-priors]] · [[wiki/projects/self-organising-mosaic-compiler]]
