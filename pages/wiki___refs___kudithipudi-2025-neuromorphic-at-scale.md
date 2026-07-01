title:: wiki/refs/kudithipudi-2025-neuromorphic-at-scale
category:: reference
type:: external-ref
tags:: neuromorphic, in-memory-computing, roadmap, on-chip-learning, scalability, hardware, spinnaker, self-organisation
authors:: Kudithipudi, Dhireesha; Schuman, Catherine; Vineyard, Craig M.; Pandit, Tej; Merkel, Cory; Kubendran, Rajkumar; Aimone, James B.; Orchard, Garrick; Mayr, Christian; Benosman, Ryad; Hays, Joe; Young, Cliff; Bartolozzi, Chiara; Majumdar, Amitava; Cardwell, Suma George; Payvand, Melika; Buckley, Sonia; Kulkarni, Shruti; Gonzalez, Hector A.; Cauwenberghs, Gert; Thakur, Chetan Singh; Subramoney, Anand; Furber, Steve
year:: 2025
venue:: Nature
doi:: 10.1038/s41586-024-08253-8
pmid:: 39843589
citation-count:: 294
summary:: 23-author Nature roadmap for scaling neuromorphic computing. Names the open challenges (co-design, a compilation scheme, on-chip learning, reliability, device non-idealities) AND the biological principles to use (self-organization, dynamic rewiring, growth, variability-as-feature) — the field's own case for our approach.
confidence:: 0.80
lifecycle:: draft
lifecycle-changed:: 2026-07-01
created:: 2026-07-01
updated:: 2026-07-01
sources:: api:semanticscholar, api:pubmed, pdf:wiki/_pdfs/kudithipudi-2025-neuromorphic-at-scale.pdf
wiki-generated:: true
ingest-mode:: full

- **Neuromorphic computing at scale** — Kudithipudi et al. (2025), *Nature* 637:801–812 (Review). A **23-author community roadmap** incl. **M. Payvand** (INI Zürich — the ETH / EIS host), **S. Furber** (SpiNNaker), **H. Gonzalez** (SpiNNcloud), **C. Mayr** (SpiNNaker2). The **#1 rationale anchor** for [[wiki/deliverables/eth-fellowship-2026]]: the field's own statement of where neuromorphic computing is, what's missing to scale it, and which biological principles to draw on. **Full-ingested 2026-07-01 from the PDF** (`wiki/_pdfs/`). ^[author]
- ## What it is
	- Defines **"scaling neuromorphic"** = the capacity of a system (algorithms + hardware + architecture + infrastructure) to operate at the size, speed and energy needed for complex real-world tasks — via large virtual data-centre systems, large edge-device networks, or both. The field is at "a critical juncture" nearing its **"AlexNet moment"** (Box 1). ^[extracted]
	- **5 distinct neuromorphic advantages:** (1) memory + compute **tightly coupled** (no data-transfer cost); (2) **sparse** distributed spike/event encoding with temporal info; (3) **dynamic and local learning** (avoids the power of backprop across layers); (4) stable perception via predictions about sensory signals; (5) **multi-timescale dynamics** for real-time learning. ^[extracted]
- ## The 7 key features for scale (Fig 3, early→late maturation)
	- **Distributed & hierarchical** · **Sparsity** (structural or ephemeral; "can make the slope of model scaling steeper" via unconventional spatial layouts) · **Neuronal scalability** · **Asynchronous communication** (event / AER) · **Dynamic reconfigurability** (*"the brain is an inherently dynamic system… reconfiguring networks"*) · **Redundancy & correlation** (neural redundancy → stable computation, noise filtering) · **Sensor/compute interfaces**. ^[extracted]
	- **+ Resource awareness** — *"the system should be capable of dynamically assigning resources on the basis of changing goals and functionalities"*, tracking energy/compute/memory over its lifetime; drawn from **self-aware architectures + continual-learning accelerators**. ^[extracted]
- ## The open challenges (the field's own list — verbatim-ish)
	- **Hardware/software co-design** (Box 2) — top-down (cortex→models→HW) vs bottom-up (device→architecture); both inefficient alone; *"innovations in in-memory computing, emerging device technologies and low-precision arithmetic are necessary."* ^[extracted]
	- **A compilation scheme / hardware abstraction** — *"algorithms are hardware dependent"*; the field needs *"a compilation scheme for porting arbitrary spiking neural network models to any hardware architecture."* ^[extracted]
	- **On-chip / local learning + lifelong learning** — Box 5 (medium-term): *"how can event-driven local learning and plasticity support machines that are capable of lifelong learning? What unified architecture can be used?"* ^[extracted]
	- **Reliability** — scaling introduces challenges in *"manufacturing, testing and reliability, particularly … performance under uncontrolled conditions."* ^[extracted]
	- **Emerging-memory device non-idealities** (Box 3) — RRAM/PCM/etc.: *"device non-idealities, challenges in integration with CMOS, and leakage"* limit large-scale use; viable emerging memory needs ≈fJ/bit, <1 V, >10¹⁷ cycles, <10 nm, CMOS integration. ^[extracted]
	- Also named: **benchmarks / metrics / standards**, **field-crossing interface losses**, **proofs-of-concept**, **cross-platform software**. Explicit short/medium/long-term question lists in Boxes 4 / 5 / 6. ^[extracted]
- ## Direct alignment with our bid (the gold)
	- **The roadmap names our *approach*, not just our problem.** *"This field is close to neuroscience and biology, which have found ways to solve these problems through **self-organization, dynamic rewiring, 3D growth, modularity, efficient signal encoding, sparsity, event-based computation** and so on. The promise is that these biological principles can inspire the design of large-scale systems."* → the flagship roadmap explicitly points to self-organization + dynamic rewiring + growth = [[wiki/projects/self-organising-mosaic-compiler]] / [[wiki/projects/growing-computation]]. ^[extracted]
	- **Variability-as-feature + self-organized networks** (Box 3): *"non-idealities … have also been exploited as 'features', for example, the cycle-to-cycle and device-to-device variability can … provide a parameter space for learning in **self-organized dynamical networks** [ref 145]. However, the scalability of these approaches to large models and practical use cases is an active area of research."* → **exactly** our thesis + Payvand's MEMSORN line, with the roadmap naming its **scalability as the open problem** we target. ^[extracted]
	- **Resource awareness** = our **energy-as-developmental-drive** + self-compilation under resource pressure (Melika's Stage-2 power/thermal remap). ^[inferred]
	- **The unification, requested:** Box 5 asks for a *"unified architecture"* for event-driven local learning + lifelong learning — our compile + remap + continual-as-one-process. ^[inferred]
	- **The honesty hook matches ours:** *"these features do not offer a magical solution. We can also achieve these optimizations through a fully top-down engineering approach, but we believe that a quicker route is possible by looking at the solutions that evolution has produced."* → mirrors §1.1's "software magic trick" + "biology = the hinge" (the shortcut, not the motivation). ^[extracted]
	- **The "two threads" (Summary):** (1) *robust, distributed + asynchronous models/algorithms*; (2) *scaling learning models to larger networks* — our self-organising rule is both. ^[extracted]
- ## Anti-mis-claim check → §1.1 ① is accurate, and can be sharpened
	- Our §1.1 ① ("the roadmap names **on-chip learning** + **scalable/adaptive mapping**") is **confirmed** — both are named (dynamic + local learning = advantage #3, lifelong learning = Box 5; a "compilation scheme for porting … to any hardware" = the mapping need). But it *undersells*: the roadmap also names **co-design, reliability, resource-awareness, device non-idealities** — and, crucially, it **names our approach** (self-organization / dynamic rewiring / growth / variability-as-feature). **Recommend sharpening §1.1** to cite the *compilation-scheme* need + the *self-organization / variability-as-feature* framing (quotable, un-mis-claimable). ^[author]
- ## Connections to Wiki
	- [[wiki/deliverables/eth-fellowship-2026]] — the #1 rationale anchor (§1.1 ①).
	- [[wiki/projects/self-organising-mosaic-compiler]] — the roadmap names the compilation/mapping gap + the self-organization/rewiring approach this project *is*.
	- [[wiki/projects/growing-computation]] · [[wiki/projects/blastema]] — self-organization + growth as named biological principles.
	- [[wiki/concepts/online-meta-learning]] — on-chip/local learning + the "unified architecture for lifelong learning" question.
	- [[wiki/concepts/substrate-rule-co-location]] — hardware/software co-design; in-memory computing; resource-awareness.
	- [[wiki/refs/raghunathan-2026-noracl-neurogenesis]] — [[NORACL]] (Payvand lab); the "continual-learning accelerators" that resource-awareness draws on.
	- [[wiki/refs/dalgaty-2024-mosaic]] — Payvand's Mosaic memristive substrate.
	- *Authors in Gabriel's orbit:* **Payvand** (the host); **Furber + Gonzalez + Mayr** (SpiNNaker / SpiNNaker2 / SpiNNcloud — where Gabriel worked).
- ## Cited By (in this wiki)
	- [[wiki/deliverables/eth-fellowship-2026]]
