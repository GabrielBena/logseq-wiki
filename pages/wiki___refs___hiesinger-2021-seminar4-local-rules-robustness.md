title:: wiki/refs/hiesinger-2021-seminar4-local-rules-robustness
category:: reference
type:: external-ref
tags:: self-organisation, autonomous-agents, synaptotropic-growth, stigmergy, hiesinger
authors:: Hiesinger, Peter Robin
year:: 2021
venue:: Princeton University Press — Seminar 4 of *The Self-Assembling Brain* (book pp 146–160)
parent:: [[wiki/refs/hiesinger-2021-self-assembling-brain]]
citation-count:: n/a
summary:: Autonomous agents (filopodia, growth cones, neurons) following local rules without a master regulator. Synaptotropic growth, stigmergy, dynamic normality — biology's version of self-organising NCAs.
confidence:: 0.85
lifecycle:: draft
lifecycle-changed:: 2026-05-15
created:: 2026-05-15
updated:: 2026-05-15
sources:: assets/hiesinger_2021_the_self-assembling_brain.pdf (Seminar 4, book pp 146–160)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Seminar 4 — From Local Rules to Robustness** — book pp 146–160. Parent: [[wiki/refs/hiesinger-2021-self-assembling-brain]].
- ## TL;DR
	- The brain's robust higher-order behaviour emerges from **autonomous agents at lower levels** (filopodia, growth cones, neurons) each following **local rules with no knowledge of the higher level**. This is biology's version of Wolfram's Rule 110: deterministic local rules produce globally unpredictable, scale-spanning structure.
	- **Local rules in biology are *composite* and *changing***. Rule 110 has one global rule applied locally; biology has many overlapping rules executed by different molecular complements at different developmental stages. A "rule" in this sense is a *cell-level instruction set*, not a single molecular event.
	- **Synaptotropic growth** (Vaughn 1980s) is the canonical example: filopodia explore stochastically → stabilise on partner contact → new filopodia branch from contact site → repeat. The dendritic tree finds its targets by *iterated stochastic exploration plus contact-stabilisation*, not by following an instructive gradient.
	- **Dynamic normality** is the key concept: each cell's developmental algorithm is run in an environment of other cells running *their* algorithms, and the result is that **each cell finds itself in the perfect environment for what it can do at that moment**. The choreography is self-coordinating; no conductor.
	- The biological analogue of NCA is direct: cell-autonomous local rules + neighbour-cell interactions + spatial-temporal context = self-organising development. This is the substrate [[wiki/refs/najarro-2023-neural-developmental-programs]] / [[wiki/refs/plantec-2024-lifelong-ndp]] / [[wiki/refs/guichard-2025-engramnca]] all try to operationalise.
- ## Key Arguments
	- ### The Rule-110 analogue and its biological complications
		- Rule 110 (Wolfram, [[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]]): a single local rule, applied uniformly, generates Turing-complete unpredictable structure. The rule *is* the algorithm; understanding the rule does not let you predict the output without running it.
		- Biology departs from Rule 110 in three ways: **(a)** new proteins enter the cell over time and *change* the local rule, **(b)** rules apply to *autonomous agents* (filopodia, growth cones) whose properties themselves change, and **(c)** noise is *productive*, providing pools of variation for selection. The brain's algorithm is "Rule 110 with changing rules and stochastic agents".
		- The deeper point: **algorithmic determinism does not imply predictability**. Even strictly deterministic rules can produce systems that look stochastic from inside, because we cannot read out the algorithmic information without running it. This is at the heart of Hiesinger's "no shortcut" thesis.
	- ### Self-avoidance and Dscam — composite rules from molecular machinery
		- Dscam-Dscam molecular interaction is *adhesion* (binding). But at the cellular level, in the context of growing filopodia on dendritic branches, the result is **self-avoidance** (homophilic repulsion).
		- The same Dscam molecule executes different rules in different contexts: in another developmental compartment, Dscam-Dscam interaction *sustains* exploratory branching rather than repelling it.
		- "Self-avoidance is a property of the filopodium, not the molecule." Multiple molecular mechanisms can implement the same rule; the rule is at the cellular level. This anticipates Seminar 7's levels problem and provides the molecular evidence for it.
	- ### Synaptotropic growth (Vaughn, 1980s)
		- A three-rule program: (1) **Stochastic exploration**: filopodia branch, extend, retract randomly. (2) **Stabilisation on contact**: filopodia that contact a target stabilise; others retract. (3) **Iteration**: new exploration starts at the stabilised contact. Repeated, this produces dendritic trees that grow toward "sources of attraction" without anyone instructing them where.
		- The branching pattern makes every Purkinje cell as distinct as a snowflake. **Algorithmic stochasticity + structural attraction = robust, individualised structure.**
		- This is "an iterative, local application of a simple set of rules by autonomous agents" — the closest biological analogue to NCA growth.
	- ### Autonomous agents — Minsky's Society of Mind
		- Minsky (1986): intelligence as a collection of agents, each unaware of the higher-level whole. The "GRASPING agents want to keep hold of the cup; BALANCING agents want to keep the tea from spilling." None has a model of the whole.
		- Biology has agents at multiple levels: filopodia don't know about growth cones; growth cones don't know about neuronal connectivity; neurons don't know about behaviour. **Each level's autonomy is what makes the system robust and decentralised.**
		- The agents' interactions create the higher-order property — without a master plan, by virtue of each agent operating in an environment shaped by all others.
	- ### Dynamic normality and stigmergy
		- **Dynamic normality**: each cell's developmental program runs in an environment of other cells' programs. The growth cone finds itself surrounded by precisely the chemical and mechanical context it expects, because the surrounding cells' programs jointly produce that context. No agent designs the niche; the niche emerges.
		- **Stigmergy** (Grassé 1959): autonomous agents coordinate through *traces left in the environment*, not through direct interaction. Termite mounds, ant colonies. The agents don't communicate; they read and modify shared environmental state.
		- These two concepts (dynamic normality + stigmergy) together describe how decentralised self-organisation produces robust global structure. Biology's version of "no central organiser" works because the *medium itself* carries the coordination signal.
- ## Direct relevance to the developmental-latent-space concept
	- ### NCA-as-developmental-program is biologically grounded
		- The [[wiki/concepts/neural-cellular-automata]] paradigm operationalises Seminar 4's argument: each cell runs a local rule, neighbours interact through shared state, global structure emerges. NDPs ([[wiki/refs/najarro-2023-neural-developmental-programs]]) make the local rule a small NN; EngramNCA ([[wiki/refs/guichard-2025-engramnca]]) adds per-cell private memory. All three are engineering instantiations of Hiesinger's autonomous-agents picture. ^[claude-synth]
	- ### Slow engram + fast active layer is dynamic normality
		- The [[wiki/projects/growing-networks]] architecture has slow-timescale engrams (structural backbone) and fast-timescale active layer (computation). This maps onto dynamic normality: the engram layer is the *environment of slow-changing cell context* that each active-state operation runs in. Each fast operation finds itself in the perfect engram-shaped niche. The slow/fast separation is the engineering counterpart of "the growth cone finds its perfect environment because all other cells contribute to it". ^[claude-synth]
	- ### Synaptotropic growth as the NCA growth rule
		- Vaughn's three-step rule (explore stochastically → stabilise on contact → re-iterate from contact) is essentially what NDP's replication MLP + edge weight does, plus a stochastic exploration step. The engram-NCA framing should incorporate this: edge creation should be **iteratively stochastic + content-stabilised**, not deterministic from a single forward pass. The continuous attention with sparsemax does some of this (soft contact, hard budget) but missing the *iterative exploration* aspect. Worth a Decisions log entry. ^[claude-synth]
	- ### Filopodial composite rules and the engram-doing-5-jobs question
		- Seminar 4 makes the case that *a single molecule executes different cellular rules in different contexts*. Translated: a single engram dimension probably encodes different cellular consequences depending on context (other engram dimensions, position, developmental stage). This supports keeping the engram as a *vector with context-dependent readout* rather than a vector with channel-by-channel commitments. The "five jobs" risk in [[wiki/concepts/developmental-latent-space]] is mitigated if each "job" is a context-dependent readout of the full vector, not a dedicated subspace. ^[claude-synth]
- ## Connections
	- [[wiki/refs/hiesinger-2021-self-assembling-brain]] — parent.
	- [[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]] — Rule 110, Kolmogorov complexity; this seminar extends to biological agents.
	- [[wiki/refs/hiesinger-2021-seminar6-chemoaffinity-permissiveness]] — Seminar 6 develops the composite-instructions picture this seminar sets up.
	- [[wiki/refs/hiesinger-2021-seminar7-genes-cells-circuits]] — Seminar 7 generalises the levels-problem implicit in this seminar (cellular-level rules ≠ molecular-level mechanisms).
	- [[wiki/concepts/neural-cellular-automata]] — direct engineering analogue.
	- [[wiki/concepts/self-organisation]] — autonomous-agents, dynamic normality, stigmergy are core mechanisms.
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — NDP is the synaptotropic-growth-style operationalisation.
	- [[wiki/refs/guichard-2025-engramnca]] — engram channels are biology's "molecules + cell state" abstracted into NCA.
	- [[wiki/concepts/developmental-latent-space]] — the autonomous-agents framing supports vector-level (not channel-level) engram-compat.
	- [[wiki/projects/growing-networks]] — slow/fast timescale separation = dynamic normality at the architectural level.
- ## Cited By (in this wiki)
	- [[wiki/concepts/developmental-latent-space]] (pending update)
	- [[wiki/projects/growing-networks]] (pending update — synaptotropic-growth-style iterative edge creation)
