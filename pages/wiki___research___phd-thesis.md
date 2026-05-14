title:: wiki/research/phd-thesis
category:: research
type:: research
index-order:: 0
tags:: thesis, modularity, self-organisation, nca, review, postdoc
summary:: Gabriel Béna's PhD thesis — "Emergence, Modularity and Self-Organisation in Neural Systems" (Imperial College London, submitted ~Feb 2026). Unifying document spanning four papers across two themes: modularity (Ch1+Ch2) and self-organisation (Ch3+Ch4). Contains the definitive literature review, the 2×2 PP/UP/PS/US framework, and the grand vision of a self-organising neuromorphic brain.
confidence:: 0.90
lifecycle:: published
lifecycle-changed:: 2026-05-08
lifecycle-reason:: User's own thesis
ingest-mode:: full
created:: 2026-05-08
updated:: 2026-05-08
sources:: phd_thesis.pdf — preambles (Ch1/Ch3/Ch4), full text (Ch2 pp63-91, Intro pp19-42, Discussion pp133-138)
wiki-generated:: true

- ## Bibliographic
	- **Author:** Gabriel Béna
	- **Institution:** Imperial College London, Department of Bioengineering
	- **Supervisors:** Dan Goodman (primary), Antoine Cully
	- **Submitted:** ~February 2026 (Discussion signed Montpellier, 13 Feb 2026)
	- **Full text:** https://gabrielbena.github.io/assets/pdf/phd_thesis.pdf
	- ![PhD_Gabriel(1).pdf](../../../assets/PhD_Gabriel(1)_1778488453013_0.pdf)
- ## Structure
	- **General Introduction** (pp 19–41) — 2×2 framework, literature review of modularity in neuroscience and AI, thesis roadmap
	- **Part I: Modularity**
		- Chapter 1 (pp 43–62): [[wiki/research/dynamics-specialization]] — structural modularity ≠ functional specialization (Nature Comms 2024)
		- Chapter 2 (pp 63–91): [[wiki/research/spatial-neuromorphic-priors]] — spatial/neuromorphic priors for compositional learning (unpublished)
	- **Part II: Self-Organising Principles of Intelligence**
		- Chapter 3 (pp 93–131): [[wiki/research/universal-nca]] — NCA as continuous universal computation (GECCO 2025)
		- Chapter 4 (pp 111–132): [[wiki/research/self-organising-digital-circuits]] — self-organising digital circuits (arXiv 2026)
	- **General Discussion** (pp 133–138) — synthesis, grand vision, honest reflection
	- **Bibliography** (pp 150–171)
- ## The 2×2 Framework (Introduction)
	- Proposes four quadrants to disambiguate modularity research, separating *locus of causation* (physical/proximate vs functional/ultimate) from *causal role* (pressure/input vs signature/output):
	- **PP — Proximate Pressures:** Connection cost, noise, energy budget, genomic bottleneck (physical drivers)
	- **UP — Ultimate Pressures:** Compositional tasks, varying environments, continual learning (functional drivers)
	- **PS — Proximate Signatures:** Q-metric, small-worldness, structural clustering (measured structural outputs)
	- **US — Ultimate Signatures:** Functional specialization, compositional generalization, transfer (measured functional outputs)
	- Core insight: "connection cost" is a PP (driver); "energy efficiency" is a PS (result). These are routinely conflated in the literature.
	- The thesis traces causal paths across quadrants: Ch1 (PP/UP→US), Ch2 (PP→PS, PS→US), Discussion (PS loops back as PP).
- ## Thesis Arc (Narrative)
	- **Part I** chases modularity as a *target*: impose it structurally (Ch1) and spatially (Ch2), measure whether functional specialisation follows. Answer: no, consistently. The structure-function gap holds across both paradigms.
	- **Pivot:** "Stop trying to find modularity and start building the kind of system where it could happen down the line." The thesis pivots in Part II to self-organisation as the generative principle.
	- **Part II** relinquishes control: NCA as a computational substrate (Ch3) and as a local meta-optimizer (Ch4). Structure and function are no longer engineered but discovered.
	- **Discussion** closes the loop: the grand vision proposes a single local rule governing growth, learning, and repair — and predicts that modularity may emerge as a by-product rather than a target.
- ## Discussion: Key Reflections
	- ### The Modularity Trap
		- Modularity is elusive. Ch1 and Ch2 both failed to produce clean structure-function causation despite precise experimental control.
		- "The more rigorously we controlled our experiments — fair baselines, proper null hypotheses, clean variable isolation — the more the expected modularity seemed to dissolve."
		- The Emergence Paradox: by gaining control, you relinquish reality. Precise isolation of variables → drift from the messy systems you set out to understand.
		- The "umbrella" problem: discussing these concepts under a general "modularity" umbrella says remarkably little about any actual system.
	- ### Toward Self-Organising Neuromorphic Substrates
		- **Core postulate:** a single, shared local rule on a sparse graph of heterogeneous units, under spatial and resource constraints, could simultaneously grow and teach a neural substrate.
		- **Structural phase:** NCA lays down topology via wiring-cost pressure → modular small-world without explicit modularity priors.
		- **Functional phase:** hidden state channels mediate dynamic functional couplings (short-term plasticity analogue, not fixed weights). Recurrent Transformer = morphogenetic program + local learning rule.
		- **Dual timescales, not phases:** structural and functional phases overlap; functional feedback shapes structural refinement, structural reorganisation opens new functional possibilities.
		- **Sparse attention as feature:** biological sparsity of connectivity is not an obstacle but a computational advantage — structural modifications update only local attention mask patches.
		- **Space as active resource:** propagation delays enable temporal coding; wiring-cost pressure sculpts compositional architecture.
		- **The Baldwin Effect:** learned signatures retro-act on developmental scaffold — not metaphor, literal mechanism when one model governs both development and learning.
		- Target: "a minimal in silico model of a self-organising brain."
	- ### Self-Aware Irony
		- "After four chapters of demonstrating that modularity is elusive, that emergence resists our expectations, and that grand frameworks have a way of flattering our narrative instincts, I am ending this thesis by arguing that with the right framework, this time, it will all come together. The pull of the modular narrative is strong — perhaps it got me one last time."
		- "But even if it did, I believe the principles themselves have earned their keep."
- ## Key Concepts Introduced
	- [[wiki/concepts/modularity]] — 2×2 PP/UP/PS/US framework; structure-function gap
	- [[wiki/concepts/self-organisation]] — NCA as self-organising intelligence; grand vision
	- [[wiki/concepts/neural-cellular-automata]] — two paradigm shifts: NCA as computer (Ch3) and optimizer (Ch4)
	- [[wiki/concepts/compositional-learning]] — 4-axis complexity framework (Ch2)
	- [[wiki/concepts/functionalism]] — the grand vision is a maximally functionalist position: one local rule, multiple substrates (developing tissue, learning brain, damaged circuit). Both broad MR (cross-substrate) and narrow MR (configurational; cf. solution-degeneracy) are load-bearing for the SODC interpretation. ^[inferred]
- ## Most Relevant External Operationalisation
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — Najarro, Sudhakaran & Risi 2023. **NDP grows the topology, SODC configures the function — together they are both halves of this thesis's grand vision.** NDP is a concrete proof-of-concept for the structural-plasticity rule that SODC explicitly leaves as an open question.
	- [[wiki/refs/plantec-2024-lifelong-ndp]] — Plantec, Pedersen, Montero, Nisioti & Risi 2024 (LNDP). The direct sequel adding **lifelong structural plasticity, reward-dependent dynamics, and spontaneous-activity pre-experience development**. The Risi-lab cluster (NDP → LNDP) is now the closest external implementation of the grand vision — only the integration with SODC-style function configuration remains.
	- [[wiki/refs/guichard-2025-engramnca]] — Guichard, Reimers, Kvalsund, Lepperød & Nichele 2025 (EngramNCA). Public/private cell-state split with propagable intracellular memory ("engram"). A third operationalisation of "function-as-cell-internal-state" complementing UNCA and SODC.
	- [[wiki/refs/guichard-2025-arc-nca]] — Same Nichele group 2025. Applies EngramNCA to ARC-AGI via test-time training; competitive with ChatGPT 4.5 at ~1000× lower cost. **First evidence that NCA-based developmental computation is competitive on hard reasoning benchmarks** — a structural validation of the grand-vision direction.
- ## Strongest External Philosophical Anchors (the two-book pairing)
  The two foundational books for the thesis, each anchoring one of the two thesis sides:
	- **Self-organisation side** (Part II / Chs 3-4 / NCA / SODC / Discussion grand vision):
		- [[wiki/refs/hiesinger-2021-self-assembling-brain]] — Hiesinger 2021, *The Self-Assembling Brain*, Princeton UP. The book-length argument that brains develop via *algorithmic information* (rules + time + energy), not *endpoint information* (a blueprint). The Discussion's grand vision is exactly Hiesinger's continuum-of-development-and-function operationalised as a single local NCA rule. Three deep-ingested seminars:
			- [[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]] — algorithmic vs endpoint information; Rule 110, Kolmogorov complexity; "no shortcut" claim.
			- [[wiki/refs/hiesinger-2021-seminar8-development-function]] — *function is a continuation of development*; spandrel/exaptation framing — also relevant to the modularity side.
			- [[wiki/refs/hiesinger-2021-seminar9-algorithmic-ai]] — *the* chapter on algorithmic growth and AI; "when does a neural network need to grow?".
	- **Modularity side** (Part I / Chs 1-2 / structure-function gap):
		- [[wiki/refs/pessoa-2022-entangled-brain]] — Pessoa 2022, *The Entangled Brain*, MIT Press. The book-length argument that the brain is *entangled* (large-scale distributed networks with many-to-many structure-function mapping), *not modular*. Provides the cleanest neuroscience-side argument for *why* the Ch1/Ch2 structure-function gap is what biology looks like too. Four deep-ingested chapters:
			- [[wiki/refs/pessoa-2022-ch1-networked-systems]] — anti-localisation thesis; "filler verbs"; network science applied to brains.
			- [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]] — M1-M5 modularity decomposition; double-dissociation logic; many-to-many mapping; functional repertoire.
			- [[wiki/refs/pessoa-2022-ch8-complex-systems]] — explicit complex-systems chapter (cellular automata + emergence + heterarchy); the *Pessoa-side bridge to NCA literature*.
			- [[wiki/refs/pessoa-2022-ch12-entangled-networks]] — final synthesis; process ontology + trajectory framing + causation in complex systems.
	- **The two books read together** are the most coherent theoretical frame for the entire thesis. Hiesinger answers "*how* did the brain get this way?" (algorithmic growth from genome). Pessoa answers "*what kind of system* did the brain become?" (entangled distributed networks). The grand vision is *both at once*: a single local rule for development and function, producing a system that's structurally entangled and functionally distributed.
- ## Status in Wiki
	- Introduction (pp 19–41): key sections ingested (2×2 framework, thesis narrative). Full ingest pending.
	- Ch1 (pp 43–62): preamble ingested; full content in [[wiki/research/dynamics-specialization]] (via Nature Comms paper ingest).
	- Ch2 (pp 63–91): fully ingested → [[wiki/research/spatial-neuromorphic-priors]]
	- Ch3 preamble: ingested here. Full content mostly in [[wiki/research/universal-nca]] (via blog post ingest).
	- Ch4 preamble: ingested here. Full content mostly in [[wiki/research/self-organising-digital-circuits]] (via blog post ingest).
	- Discussion (pp 133–138): fully ingested here.
	- Bibliography (pp 150–171): not yet scanned.