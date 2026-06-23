title:: wiki/refs/barandiaran-2025-dgca-reservoirs
category:: reference
type:: external-ref
tags:: nca, self-organisation, morphogenesis, reservoir-computing, developmental, graph-ca
authors:: Barandiaran, Matias; Stovold, James
year:: 2025
venue:: IEEE Symposium on Artificial Life (ALIFE 2025)
arxiv:: 2508.08091
doi:: 10.1162/ISAL.a.854
citation-count:: 3
summary:: Developmental Graph Cellular Automata grow directed graphs from single-node seeds; trained to grow reservoirs, they produce specialized, life-like structures that outperform typical reservoirs.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-06-21
created:: 2026-06-21
updated:: 2026-06-21
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Growing Reservoirs with Developmental Graph Cellular Automata** — Barandiaran & Stovold (2025), ALIFE 2025 (Lancaster University Leipzig).
	- A self-organising-CA substrate that itself computes — a reviewer-suggested reservoir-computing-on-CA point of comparison for [[wiki/research/self-organising-digital-circuits]], and a structural/developmental sibling to the [[NDP]] line.

- ## Abstract (extracted)
	- Developmental Graph Cellular Automata (DGCA) are a novel model for morphogenesis, capable of growing directed graphs from single-node seeds. In this paper, we show that DGCAs can be trained to grow reservoirs. Reservoirs are grown with two types of targets: task-driven (using the NARMA family of tasks) and task-independent (using reservoir metrics). Results show that DGCAs are able to grow into a variety of specialized, life-like structures capable of effectively solving benchmark tasks, statistically outperforming 'typical' reservoirs on the same task. Overall, these lay the foundation for the development of DGCA systems that produce plastic reservoirs and for modeling functional, adaptive morphogenesis.

- ## Key Ideas
	- **DGCA** (extends NCA to directed graphs) **grows directed graphs from single-node seeds** — morphogenesis of topology ^[inferred].
	- Trained to **grow reservoirs** under two target types: **task-driven** (NARMA family) and **task-independent** (reservoir metrics) ^[inferred].
	- Grown structures are **specialized and life-like** and **statistically outperform "typical" reservoirs** on the same task ^[inferred].
	- Aimed at **plastic reservoirs** that adapt to change / recover after damage — functional, adaptive morphogenesis ^[inferred].

- ## Connections to Wiki
	- [[wiki/research/self-organising-digital-circuits]] — reviewer R1e's reservoir-computing-on-CA comparison: a substrate that *itself computes*. SODC's distinction is that its policy *directly configures and repairs* the substrate's functional parameters toward a *specified* function, whereas a grown reservoir is selected for generic capacity and read out separately ^[inferred].
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — [[NDP]] grows a network from a seed by local rules; DGCA is the directed-graph-growth cousin (both develop *structure*).
	- [[wiki/concepts/neural-cellular-automata]] — DGCA extends the NCA paradigm to graph substrates.
	- [[wiki/concepts/self-organisation]] — growth from a single seed via local update rules.

- ## Open Questions / To Read
	- How is the discrete graph-growth operation trained (the credit-assignment-through-growth question)? (abstract-only). Upgrade with `/paper-ingest full`.
	- SODC bibkey: `barandiaran_growing_2025`. Reference code: github.com/mbaranr/alife2025 ^[from source note, unverified].

- ## Cited By (in this wiki)
	- (forward-linked from this ref; SODC backlink added during the ALIFE-revision intake)
