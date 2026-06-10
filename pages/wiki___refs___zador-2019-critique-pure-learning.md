title:: wiki/refs/zador-2019-critique-pure-learning
category:: reference
type:: external-ref
tags:: genomic-bottleneck, evo-devo, neuroscience-ai, encoding, innateness
authors:: Zador, Anthony M.
year:: 2019
venue:: Nature Communications
doi:: 10.1038/s41467-019-11786-6
citation-count:: 538
summary:: Argues competence-at-birth is mostly innate: the genome is ~6 orders of magnitude too small to specify wiring, so it encodes compressive developmental rules — the "genomic bottleneck", a productive regularizer.
confidence:: 0.80
lifecycle:: draft
lifecycle-changed:: 2026-06-10
created:: 2026-05-14
updated:: 2026-06-10
sources:: europepmc:PMC6704116 (full text, CC-BY)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.10
provenance-ambiguous:: 0.05

- **A critique of pure learning and what artificial neural networks can learn from animal brains** — Anthony M. Zador (2019), *Nature Communications* 10:3770. Single-author essay; the title plays on Kant's *Critique of Pure Reason*. Coined the [[wiki/concepts/genomic-bottleneck]] framing the postdoc's developmental thread is built on.

- ## TL;DR
	- Animals function astonishingly well *at or soon after birth* (a colt walks within hours, a spider hunts from birth) — **not** because of a clever supervised/unsupervised learning algorithm, but because **most behaviour is innate**, encoded in the genome as **rules for wiring up the brain**. ^[extracted]
	- The genome **cannot** store the wiring diagram explicitly: a ~1 GB genome is **≥6 orders of magnitude too small** to specify ~10¹⁴ connections — so it must compress wiring into a **developmental program**. This is the **genomic bottleneck**. ^[extracted]
	- The bottleneck is a **feature, not a bug**: limited genome capacity acts as a **regularizer**, shifting variance→bias and selecting for *generic, generalizable* wiring/plasticity rules. (Genome size is *not* a hard constraint — lungfish genomes are 40× human — so the smallness is selected, not imposed.) ^[extracted]
	- Reframes deep learning's "supervised learning" as **"supervised evolution"**: animals run **two nested optimisations** — an outer *evolution* loop (generational, reward = #progeny) that writes the genome, and an inner *learning* loop (within-lifetime). ANN training conflates both. ^[extracted]

- ## The argument
	- ### Innate ≠ learned, but synergistic — "scaffolding innate, content learned"
		- The innate/learned line is not sharp; they interact. Canonical examples: **place cells** (the propensity to form a spatial map is innate; the specific map is learned), the **fusiform face area** (innate face-salience scaffolding; specific faces learned), **language areas** (Broca/Wernicke scaffolding innate; specific syntax/vocabulary learned). The genome lays the **scaffold**; experience populates it. ^[extracted]
		- Evolutionary logic: a species at 98% of mature performance *at birth* outcompetes one at 50%-needing-a-month — unless the environment changes within a lifetime, which is what creates pressure for a learned component. A **bias-variance tradeoff between innate and learned**. ^[extracted]
	- ### The bottleneck, quantified
		- Human genome ≈ 3×10⁹ nucleotides ≈ **1 GB**. Brain ≈ 10¹¹ neurons × ~10³ synapses ≈ 10¹⁴ connections; at ~37 bits/synapse to name a target → **~3.7×10¹⁵ bits** to specify explicitly. Even spending the whole genome, capacity is **≥6 orders short**. ^[extracted]
		- Therefore the genome encodes **wiring rules + connection motifs**, not the diagram. *C. elegans* (302 neurons, ~7000 synapses) can afford a near-lookup-table; mammals cannot — they must grow the brain from rules during development. ^[extracted]
	- ### Supervised evolution — two nested loops
		- Evolution = a reinforcement process on the generational timescale (reward = number of progeny); learning = the within-lifetime inner loop. ANN "supervised learning" recapitulates **both** the statistical-regularity extraction that evolution did *and* lifetime learning — hence "supervised evolution" would be the more honest name. Evolution acts on wiring **only indirectly, through the genome**; learning acts directly on weights. ^[extracted]
	- ### Implications for ANNs
		- **Architecture/wiring topology is the target of optimisation**, not just weights — CNNs (translation-invariance as an innate constraint inspired by visual receptive fields) are the one big success; "ANNs exploit only a tiny fraction of possible architectures." ^[extracted]
		- Brains "transfer" *less* than transfer-learning (information must pass the bottleneck) — which is *why* the transferred rules generalise better. A path toward rapid-learning ANNs is to build in compact, evolved structural priors. ^[extracted]
		- AGI "is not general at all" — it is tightly constrained to match human capacities, so only a brain-structured machine achieves it (airplane-vs-bird). ^[extracted]

- ## Why it matters for Gabriel's program
	- **The genomic-bottleneck anchor.** This is the coined source for [[wiki/concepts/genomic-bottleneck]] and the *"the rule must be small"* constraint on [[wiki/projects/growing-computation]]'s Region-II regulatory rule and [[wiki/projects/growing-networks]]'s developmental program. The compression-→-generalisation claim is the load-bearing one. ^[claude-synth]
	- **The two-nested-loops framing speaks directly to the Level-3 open question.** [[wiki/concepts/substrate-rule-co-location]] §Level 3 asks *"where does evolution fit?"* — Zador's outer-evolution / inner-learning decomposition is the cleanest statement that an evolved, compressed prior (the genome) and online learning are *distinct* optimisations on different timescales. It supports the position that an outer loop setting Layer-1 may be unavoidable rather than absorbed into on-substrate learning. ^[claude-synth]
	- **Innate-scaffold / learned-content = engram/active split.** The "scaffolding innate, content learned" pattern is the biological licence for [[wiki/projects/growing-networks]]'s slow **engram layer** (structure) vs fast **active layer** (task), and for [[wiki/concepts/developmental-latent-space]]. ^[claude-synth]
	- *Hedge:* the bottleneck is grounded **independently** in the wiki via [[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]] (algorithmic vs endpoint information) — Zador supplies the crisp information-theoretic numbers and the ML framing; Hiesinger supplies the developmental-biology mechanism. They corroborate, not duplicate. ^[claude-synth]

- ## Limitations / caveats
	- A **position essay**, not a method — Zador proposes no specific algorithm; the operationalisations live downstream ([[NDP]], [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]], the engram cluster). ^[extracted]
	- The bit-counting argument is an upper-bound sketch (it assumes near-explicit specification); it bounds *what the genome can't do*, not *what the developmental rule does do*. ^[inferred]

- ## Connections to wiki
	- [[wiki/concepts/genomic-bottleneck]] — this paper coined the framing.
	- [[wiki/projects/growing-networks]] — the foundational reference for the developmental/bottleneck thread.
	- [[wiki/projects/growing-computation]] — "the rule must be small" constraint on the Region-II regulatory rule.
	- [[wiki/concepts/substrate-rule-co-location]] — the outer-evolution / inner-learning loops bear on the §Level-3 "where does evolution fit?" question.
	- [[wiki/concepts/neural-cellular-automata]] — NCAs are a computational realisation of "a compact rule grows the structure".
	- [[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]] — independent grounding of the same bottleneck via algorithmic-information theory.
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — [[NDP]] operationalises the bottleneck (per-cell rule grows topology).
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]] — GEM operationalises innateness as developmental priors on weights.

- ## Cited By (in this wiki)
	- [[wiki/concepts/genomic-bottleneck]]
	- [[wiki/projects/growing-networks]]
	- [[wiki/projects/growing-computation]]
