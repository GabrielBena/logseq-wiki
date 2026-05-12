title:: Wiki Index
alias:: wiki, Wiki, wiki index
category:: hub
type:: hub
wiki-generated:: true
lifecycle:: published
lifecycle-changed:: 2026-05-12
updated:: 2026-05-11
exclude-from-graph-view:: true

- Top-level hub for the wiki. New here? Read [[wiki/meta/handbook]] for philosophy, conventions, and workflow.
- Browse curated hubs: [[Wiki Concepts Hub]] · [[Wiki Research Hub]] · [[Wiki Refs Hub]] · [[Wiki Code Hub]] · [[Wiki Projects Hub]] · [[Wiki Meta Hub]]
- Recent activity: [[wiki/hot]]
- ## Concepts
	- [[wiki/concepts/neural-cellular-automata]] — CA with neural update rule; NCA as computer (Ch3) and as optimizer (Ch4); grand vision of self-organising brain ( #nca #self-organisation)
	- [[wiki/concepts/self-organisation]] — Emergence of global behaviour from local rules; NCA paradigm; grand vision from Discussion ( #self-organisation #emergence #nca)
	- [[wiki/concepts/modularity]] — 2×2 PP/UP/PS/US framework; structural≠functional; modularity trap and Discussion synthesis ( #modularity #neuroscience)
	- [[wiki/concepts/compositional-learning]] — Systematic recombination of finite learned primitives; 4-axis complexity framework (symbolic/sequential/combinatorial/atomic) ( #compositional-learning #generalisation)
	- [[wiki/concepts/topology-masked-transformer]] — Shared-weight Transformer masked to circuit topology; SODC's decentralised meta-optimiser ( #architecture #meta-learning)
	- [[wiki/concepts/differentiable-logic-gates]] — Continuous relaxation of Boolean LUTs for gradient-based circuit training ( #boolean-circuits)
	- [[wiki/concepts/solution-degeneracy]] — Multiple structurally distinct but functionally equivalent configurations; mechanism of robust self-repair ( #complex-systems #biology)
	- [[wiki/concepts/functionalism]] — Function decoupled from implementation; Turing's MR; broad MR (cross-substrate) vs narrow MR (within-substrate, configurational) ( #philosophy-of-mind #multiple-realizability)
	- [[wiki/concepts/universal-computation]] — Substrate-independent computability; the universal property NCA / UNCA reach toward ( #universal-computation #theoretical-cs)
- ## Research
	- [[wiki/research/phd-thesis]] — Overarching PhD thesis (Imperial, ~Feb 2026); 2×2 framework, Discussion grand vision, ingest status map ( #thesis #modularity #self-organisation)
	- [[wiki/research/dynamics-specialization]] — Ch1: structural modularity ≠ functional specialization; resource constraints drive emergence. Nature Comms 2024 ( #modularity #neuroscience)
	- [[wiki/research/spatial-neuromorphic-priors]] — Ch2: spatial/neuromorphic priors for compositional learning; 2D-PVR + Spatial DEEP-R. Unpublished ( #modularity #compositional-learning #neuromorphic)
	- [[wiki/research/universal-nca]] — Ch3: NCA as continuous universal computation substrate. GECCO 2025 ( #research #nca)
	- [[wiki/research/self-organising-digital-circuits]] — Ch4: NCA as meta-optimizer for self-assembling/repairing Boolean circuits. arXiv 2026 ( #research #postdoc #nca)
- ## Code
	- [[wiki/code/gabrielbena-boolean-nca-cc]] — JAX/Flax SODC implementation; TMT, Perceiver, GNN models; pool meta-learning ( #jax #nca #boolean-circuits)
	- [[wiki/code/maxencefaldor-universal-nca]] — JAX UNCA implementation; Gabriel's `gabriel` branch adds Brain NCA experiments ( #jax #nca)
	- [[wiki/code/gabrielbena-logseq-public]] — Earlier Logseq-public-pages attempt (inactive Oct 2024); precedent for wiki publishing ( #logseq #publishing)
- ## Projects
	- [[wiki/projects/position-paper]] — *Genesis (2026-05-11).* Brain-modularity position paper from the thesis; walks the line between clean-cut modularity and one-giant-network views ( #position-paper #modularity)
	- *Living-document projects (papers in genesis, grant proposals, talks). See [[Wiki Projects Hub]] for the workflow.*
- ## References — most recent 5 ingests (full list at [[Wiki Refs Hub]])
	- [[wiki/refs/salatiello-2026-modularity-bedrock]] — Single-author review arguing modularity is a unifying computational principle across engineering, evolutionary biology, neuroscience, and AI. Proposes implicit/emergent/architectural taxonomy and a formal modular-model definition. ( #modularity #brain-inspired-ai)
	- [[wiki/refs/hornischer-2025-universal-analog-computation]] — Formalises universality for analog computation as a property of dynamical systems. Identifies four senses of universality; constructs a universal system as a Fraïssé limit for nondeterministic dynamics. Includes cellular automata and neural networks in scope. ( #universal-computation #analog-computing)
	- [[wiki/refs/pessoa-2022-entangled-brain]] — Book-length argument that the brain is *entangled*, not modular — functions are carried out by large-scale distributed networks; brain areas exhibit many-to-many structure-function mapping. Pessoa's central anti-localisationist thesis. Anchors the modularity side of Gabriel's thesis from the neuroscience direction. ( #modularity #brain-networks)
	- [[wiki/refs/pessoa-2022-ch8-complex-systems]] — Chapter 8 of Pessoa's book — the explicit complex-systems chapter. Cellular automata, predator-prey dynamics, emergence, von Bertalanffy's general systems theory, nonlinear dynamical systems, heterarchy. The conceptual bridge to NCA and self-organisation literatures. ( #complex-systems #brain-networks)
	- [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]] — Chapter 4 of Pessoa's book — the methodological core. Five formal definitions of modularity (M1-M5), the double-dissociation logic and its limits, the many-to-many structure-function mapping, and Pessoa's lab's 20-dimensional functional-profile approach. ( #modularity #brain-networks)
	- *See [[Wiki Refs Hub]] for the full thematic listing (50 refs).*
- ## Meta
	- [[wiki/meta/handbook]] — How to use this wiki: philosophy, workflow, conventions, lifecycle, three-tier file model
	- [[wiki/meta/github-pages-site]] — Gabriel's academic website; publishes distill-format paper blog posts ( #website #publishing)
	- [[wiki/meta/wiki-publishing]] — Public wiki pipeline: push-sync GH Action → `GabrielBena/logseq-wiki` → publish-spa; gated by `lifecycle:: published` ( #publishing #wiki-lifecycle)
	- [[wiki/meta/wiki-home]] — Landing page stub for the public SPA; promote to `published` once written ( #publishing)