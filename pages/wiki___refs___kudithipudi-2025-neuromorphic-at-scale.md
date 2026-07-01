title:: wiki/refs/kudithipudi-2025-neuromorphic-at-scale
category:: reference
type:: external-ref
tags:: neuromorphic, in-memory-computing, roadmap, on-chip-learning, scalability, hardware, spinnaker
authors:: Kudithipudi, Dhireesha; Schuman, Catherine; Vineyard, Craig M.; Pandit, Tej; Merkel, Cory; Kubendran, Rajkumar; Aimone, James B.; Orchard, Garrick; Mayr, Christian; Benosman, Ryad; Hays, Joe; Young, Cameron; Bartolozzi, Chiara; Majumdar, Amitava; Cardwell, Suma G.; Payvand, Melika; Buckley, Sonia; Kulkarni, Shruti; Gonzalez, Hector A.; Cauwenberghs, Gert; Thakur, Chetan Singh; Subramoney, Anand; Furber, Steve
year:: 2025
venue:: Nature
doi:: 10.1038/s41586-024-08253-8
pmid:: 39843589
citation-count:: 294
summary:: 23-author community roadmap (incl. Payvand & Furber) charting scalable neuromorphic computing — architectures, key features, applications, the main open challenges, and the ecosystem needed to scale. The field's own "what's next".
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-07-01
created:: 2026-07-01
updated:: 2026-07-01
sources:: api:semanticscholar, api:pubmed
wiki-generated:: true
ingest-mode:: abstract

- **Neuromorphic computing at scale** — Kudithipudi et al. (2025), *Nature* 637:801–812. A **23-author community roadmap** including **M. Payvand** (INI Zürich — the ETH / [[wiki/deliverables/eth-fellowship-2026]] host) and **S. Furber** (SpiNNaker) + H. Gonzalez (SpiNNcloud). The **#1 rationale anchor** for the bid: the field's own statement of where neuromorphic computing is and what is missing to scale it. ^[author]
- ## Abstract (PubMed, verbatim)
	- Neuromorphic computing is a brain-inspired approach to hardware and algorithm design that efficiently realizes artificial neural networks. Neuromorphic designers apply the principles of biointelligence discovered by neuroscientists to design efficient computational systems, often for applications with size, weight and power constraints. With this research field at a critical juncture, it is crucial to chart the course for the development of future large-scale neuromorphic systems. We describe approaches for creating scalable neuromorphic architectures and identify key features. We discuss potential applications that can benefit from scaling and the main challenges that need to be addressed. Furthermore, we examine a comprehensive ecosystem necessary to sustain growth and the new opportunities that lie ahead when scaling neuromorphic systems. Our work distils ideas from several computing sub-fields, providing guidance to researchers and practitioners of neuromorphic computing who aim to push the frontier forward.
- ## Key Ideas (from abstract only — ^[inferred])
	- The field is at "a critical juncture"; the paper charts the course toward **large-scale** neuromorphic systems. ^[inferred]
	- Contributes four things: (1) approaches + **key features** for scalable neuromorphic architectures; (2) applications that benefit from scaling; (3) **the main challenges to address**; (4) the **ecosystem** needed to sustain growth. ^[inferred]
	- Explicitly a **cross-sub-field distillation** — guidance for researchers/practitioners pushing the frontier. ^[inferred]
- ## ⚠ Full-text status — paywalled (ABSTRACT-mode only)
	- No open-access PDF (S2 `openAccessPdf` empty), not free in PMC, no preprint. The abstract only says "**the main challenges that need to be addressed**" — it does **not** enumerate them. Those specifics live in the paywalled body.
	- **Anti-mis-claim note for the bid:** §1.1 ① of [[wiki/deliverables/eth-fellowship-2026]] asserts the roadmap "names **on-chip learning** + **scalable/adaptive mapping**" as the missing pieces. That specificity currently rests on the literature-verification pass, **not** on this abstract. To quote it verbatim (and bulletproof the anchor), drop the Nature PDF into `wiki/_pdfs/` → `/paper-ingest full` for a true deep read.
- ## Connections to Wiki
	- [[wiki/deliverables/eth-fellowship-2026]] — the #1 rationale anchor (§1.1 ①): "the field's own roadmap names the missing pieces."
	- [[wiki/projects/self-organising-mosaic-compiler]] — the bid's subject; the roadmap frames the on-chip-learning + mapping gap this project targets.
	- [[wiki/concepts/online-meta-learning]] — on-chip learning as a named open challenge.
	- [[wiki/concepts/substrate-rule-co-location]] — scalable / adaptive mapping of computation onto substrates.
	- [[wiki/projects/growing-computation]] — the broader arc the bid serves.
	- *Co-authors in Gabriel's orbit:* **M. Payvand** (the host); **S. Furber** + **H. Gonzalez** (SpiNNaker / SpiNNcloud — where Gabriel worked on Spinnaker2); **C. Mayr** (TU Dresden, SpiNNaker2).
- ## Open Questions / To Read
	- **Upgrade to full mode** once the PDF is available — capture the *enumerated* open challenges + the "key features" of scalable architectures verbatim (this is what bulletproofs the §1.1 anchor and mines "what's hot").
- ## Cited By (in this wiki)
	- [[wiki/deliverables/eth-fellowship-2026]]
