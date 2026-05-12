title:: wiki/refs/hornischer-2025-universal-analog-computation
category:: reference
type:: external-ref
tags:: universal-computation, analog-computing, dynamical-systems, theoretical-cs, cellular-automata
authors:: Hornischer, Levin
year:: 2025
venue::
doi::
arxiv:: 2510.10184
citation-count:: 0
summary:: Formalises universality for analog computation as a property of dynamical systems. Identifies four senses of universality; constructs a universal system as a Fraïssé limit for nondeterministic dynamics. Includes cellular automata and neural networks in scope.
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-05-11
created:: 2026-05-11
updated:: 2026-05-11
sources:: api:semanticscholar arXiv:2510.10184
wiki-generated:: true
ingest-mode:: abstract

- **Universal Analog Computation: Fraïssé Limits of Dynamical Systems** — Levin Hornischer, arXiv:2510.10184 (2025). Single-author, 0 citations as of 2026-05-11.

- ## Abstract
	- Analog computation is an alternative to digital computation, that has recently re-gained prominence, since it includes neural networks and neuromorphic computing. Further important examples are cellular automata and differential analyzers. While analog computers offer many advantages, they lack a notion of universality akin to universal digital computers. Since analog computers are best formalized as dynamical systems, we review scattered results on universal dynamical systems. We identify four senses of universality and connect to the two main general theories of computation: coalgebra and domain theory. For nondeterministic systems, we construct a universal system as a Fraïssé limit. It not only is universal in many of the identified senses, it also is unique in additionally being homogeneous. For deterministic systems, a universal system cannot exist, but we provide a simple method for constructing subclasses of deterministic systems with a universal and homogeneous system. This way, we introduce sofic proshifts: those systems that are limits of sofic shifts. In fact, their universal and homogeneous system even is a limit of shifts of finite type and has the shadowing property.

- ## Why this matters here
	- Directly addresses the open question flagged on [[wiki/concepts/neural-cellular-automata]] § Open Questions and on [[wiki/concepts/universal-computation]]: *what does it mean for an NCA (a continuous dynamical system) to be universal?* Hornischer offers a category-theoretic answer via Fraïssé limits and four formal senses of universality. ^[inferred]
	- The negative result (no universal deterministic system exists in the full class) clarifies why claims that "continuous NCA are likely Turing-complete" need to specify *which* sense of universality is in scope. The "likely affirmative" framing previously on the NCA page was indeed pushing it. ^[inferred]
	- Connects analog computation explicitly to neural networks, neuromorphic computing, and cellular automata — the exact substrate-family that UNCA and SODC live in.

- ## Open Questions / Next Steps
	- Read the full PDF (not yet done) to map the four senses of universality onto UNCA / SODC and decide which sense is the right target for "continuous NCA universality" claims. Triggers a `/paper-ingest full` upgrade. ^[wiki-gap]
	- Cross-reference with the other unread candidate [[What is a universal computing machine?]] (Computational Universality and Continuous Systems) — both flagged in NCA L86 by author 2026-05-11.

- ## Connections
	- [[wiki/concepts/universal-computation]] — primary conceptual page this paper extends.
	- [[wiki/concepts/neural-cellular-automata]] — Open Questions § (Turing completeness of continuous NCA) directly addressed by this paper.
	- [[wiki/research/universal-nca]] — UNCA's "universal" claim needs to be qualified by which sense from this paper.

- ## Cited By (in this wiki)
	- [[wiki/concepts/neural-cellular-automata]]
	- [[wiki/concepts/universal-computation]]
