title:: wiki/refs/pessoa-2022-entangled-brain
category:: reference
type:: external-ref
tags:: modularity, brain-networks, neuroscience, complex-systems, anti-localisationism
authors:: Pessoa, Luiz
year:: 2022
venue:: MIT Press (book, 280 pp; OA monograph)
doi::
arxiv::
citation-count:: n/a
summary:: Book-length argument that the brain is *entangled*, not modular — functions are carried out by large-scale distributed networks; brain areas exhibit many-to-many structure-function mapping. Pessoa's central anti-localisationist thesis. Anchors the modularity side of Gabriel's thesis from the neuroscience direction.
confidence:: 0.82
lifecycle:: in-review
lifecycle-changed:: 2026-05-11
review-pass:: 1
review-pass-changed:: 2026-05-11
review-pass-result:: pass-1-addressed (2 of 2)
created:: 2026-05-10
updated:: 2026-05-11
sources:: assets/pessoa_2022_the_entangled_brain.pdf (full book, 280 pp, ~95k words; deep-ingested via 4 chapter pages + this overview)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **The Entangled Brain: How Perception, Cognition, and Emotion Are Woven Together** — Luiz Pessoa (University of Maryland), MIT Press 2022. ISBN 9780262047463. Open-access monograph.
- ## Role in Gabriel's thesis
	- Pessoa is *the* sustained book-length argument *against* the modular / localist view of the brain, written by a major contemporary cognitive neuroscientist. In Gabriel's thesis it functions as a **critical foil / counterweight** rather than a foundation: Part I is itself exploratory-pro-modularity (you have to entertain the modular hypothesis to test it empirically), and Pessoa supplies the principled push-back that the negative results of Ch1/Ch2 then connect to. ^[addressed]
	- Where Hiesinger argues *the brain is grown by an algorithm, not engineered*, Pessoa argues *the brain functions as an entangled network, not a collection of localised modules*. Both are critiques of engineering metaphors applied naively to neural systems. Both push the same direction: stop expecting clean structure-function mappings.
	  id:: 6a006c2e-5694-46c8-94d6-54246c224aa2
	- Direct relevance to thesis Ch1 ([[wiki/research/dynamics-specialization]]) and Ch2 ([[wiki/research/spatial-neuromorphic-priors]]): Pessoa supplies a deep neuroscientific argument for *why* structural modularity **may not** entail functional specialisation. The thesis tests the modular hypothesis empirically in ANNs; Pessoa argues the same point in biological brains. The convergence is partial, not foundational.
	- Pairs with [[wiki/refs/hiesinger-2021-self-assembling-brain]] (anchors the self-organisation / developmental side) — together they form the two-book *theoretical complement* to the thesis, not its foundation.
- ## Central Thesis (verbatim from Preface)
	- **"Functions are carried out by large-scale distributed circuits, also called large-scale networks. ... The circuits are distributed, not local, involving disparate parts in the cortex and the subcortex. ... You can't point to the brain and say, 'This is where X happens.'"**
	- **"A central thesis of the book is that biology does not work like physics, and even less so like engineering. Biological systems are not easily reducible to separate units that, when put together, give us the whole back."**
	- **"In trying to delineate mental processes, ... most of the explanatory work needs to be done at the level of interactions."**
	- **"It's all about complex, entangled networks."** (book ending)
- ## Book Structure (12 chapters, 3 conceptual movements)
	- **Movement 1 — Setup and methodology** (Chapters 1-4, pp 1-64): the conceptual framing of what's wrong with the modular view + anatomy primer + the central methodological problem of functional ascription.
		- **Ch 1: From One Area at a Time to Networked Systems** — *deep-ingested:* [[wiki/refs/pessoa-2022-ch1-networked-systems]]
		- Ch 2: Learning a Bit of Anatomy — primer (cortex, subcortex, neocortex layers, projection systems)
		- Ch 3: The Minimal Brain: Building Simple Defenses and Seeking Rewards — sensorimotor circuits, the uncoupling of sensation and motor production
		- **Ch 4: What Do Brain Areas Do?** — *deep-ingested:* [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]]
	- **Movement 2 — The traditional one-region-one-function story (and its limits)** (Chapters 5-7, pp 65-128): Pessoa walks through the orthodox subcortical/cortical localisation story so the reader can see *what's missing* by the end. Each chapter closes with the inadequacy of the localisation framing.
		- Ch 5: Emotion and Motivation: The Subcortical Players — hypothalamus, amygdala, striatum, dopamine. The amygdala-as-fear-centre story is set up specifically so it can be undermined later.
		- Ch 6: Emotion and Motivation: The Cortex Comes to the Party — orbitofrontal cortex, anterior cingulate, insula. The cortical-subcortical interaction story.
		- Ch 7: Cognition and the Prefrontal Cortex — executive function, cognitive control, working memory. The PFC-as-CEO story and its problems.
	- **Movement 3 — Networks, evolution, and the entangled view** (Chapters 8-12, pp 129-230): the synthesis chapters where Pessoa argues for replacing localisation with complex-systems-and-networks.
		- **Ch 8: Complex Systems: The Science of Interacting Parts** — *deep-ingested:* [[wiki/refs/pessoa-2022-ch8-complex-systems]]
		- Ch 9: 500 Million Years of Evolution — the comparative-vertebrate perspective; why "the human cortex is unique" is mostly wrong; reorganisation of conserved circuits across taxa.
		- Ch 10: The Big Network: Putting Things Together — the synthesis of network science with neuroanatomy. Hub-and-spoke organisation, rich-club nodes, communication paths.
		- Ch 11: Unlearning Fear — extended case study showing fear extinction as a distributed-circuit phenomenon (case study chosen specifically to illustrate the synthesis).
		- **Ch 12: It's All about Complex, Entangled Networks** — *deep-ingested:* [[wiki/refs/pessoa-2022-ch12-entangled-networks]]
- ## Five Cross-Cutting Concepts
	- ### 1. The structure-function mapping is many-to-many
		- Modular thinking assumes one-to-one (region X computes function Y). Empirically, brain regions show *one-to-many* (a region participates in many functions — the amygdala does emotion, attention, reward, decision-making, social processing) and functions show *many-to-one* (multiple regions can carry out a function — attention emerges across frontal-parietal cortex, not from a single "attention area").
		- The combination is **many-to-many**: M areas × N functions, with the empirical pattern being far from sparse.
		- **Consequence**: the very vocabulary of "the function of region X" is misleading. Better: "the *functional repertoire* of region X" — how engaged is X across many tasks?
		- Pessoa's lab generated 20-dimensional functional profiles for cortical regions from massive functional MRI databases, finding that brain regions are functionally diverse, not specialised.
	- ### 2. Modularity has at least 5 distinct meanings (Ch4)
		- **M1**: parts A and B are modules iff separately modifiable.
		- **M2**: a module computes a particular input-output mapping.
		- **M3**: there's a decomposition where within-subsystem interactions ≫ between-subsystem interactions.
		- **M4**: subsystems form complex networks, each carrying a *subfunction* of an overall function.
		- **M5** (specific to brain): the subsystem must be spatially localised.
		- **Why this matters**: most neuroscientific claims of "modularity" smuggle M5 in implicitly. M1-M4 alone could be satisfied by a *spatially distributed* functional module — but the field tends to require M5, which is what creates the localisation pressure. Drop M5 and "modularity" becomes a claim about *functional decomposability*, which Pessoa argues fails in the brain.
	- ### 3. Filler verbs and the poverty of mechanistic explanation (Ch1)
		- Pessoa surveys neuroscience papers and finds a list of "filler verbs": *contributes to, involves, is involved in, mediates, modulates, supports, underlies, plays a role in, encodes, regulates, generates, induces, ensures, reflects, reveals, shapes...*
		- These verbs *stand in for the processes we presume did the "real" work* but rarely specify a mechanism. Pessoa cites: "Despite centuries of study of brain–behavior relationships, a clear formalization of the function of many brain regions ... is lacking." (Genon et al. 2018)
		- **Why this matters**: claims like "the amygdala is involved in fear" are *not mechanistic explanations*; they're correlations dressed in mechanism's clothing. Adolphs & Anderson's speedometer analogy: imaging the amygdala during a fear task is like imaging a speedometer — it tells you something is correlated with the function, not how the function is implemented.
	- ### 4. Reductionism vs decomposability (Chs 1, 4, 8)
		- Pessoa carefully distinguishes between *reductionism as scientific analysis* (decomposing a system to study its parts — Mayr: "no complex system can be understood except through careful analysis") and *reductionism as ontological claim* (the whole is fully explained by lower levels).
		- Pessoa rejects ontological reductionism for biology while keeping methodological analysis: "rejecting the philosophy of reductionism is not an attack on scientific analysis ... however, the interactions of the components must be considered as much as the properties of the isolated components."
		- **Why this matters**: the brain may be analysable into parts, but its *function* lives in the *interactions* — and interactions are not derivable from properties of the isolated parts. This is exactly the structural-modularity-without-functional-specialisation finding of [[wiki/research/dynamics-specialization]] and [[wiki/research/spatial-neuromorphic-priors]].
	- ### 5. Process ontology — "the world is made of processes, not things" (Ch12)
		- Pessoa endorses the *organicist / process-philosophy* view (Heraclitus, Whitehead, Waddington): biology doesn't study things, it studies processes.
		- For the brain: **trajectories in high-dimensional state space** are the right units of analysis, not regions. A behaviour is the temporal evolution of a vector x(t) = (activity of region 1, activity of region 2, ...) — not a snapshot of a "responsible" region.
		- **Why this matters**: this reframes "what does the brain do" from a localisation question into a *dynamical systems* question. The same regions can support different functions via different trajectories; the same trajectory can be implemented by different regional substrates (multiple realizability — connects to [[wiki/concepts/functionalism]]).
- ## Connections to Gabriel's Research
	- ### The structure-function gap, with deeper neuroscience grounding
		- **[[wiki/concepts/modularity]]** — Pessoa's *many-to-many mapping* framework is the canonical neuroscience-side statement of the structure-function gap. The Ch1 (dynamics-specialization) finding that *structural modularity does not entail functional specialisation* is *predicted* by Pessoa's framework: structural modules don't carve mental processes at the joints because mental processes don't have such joints.
		- The thesis Ch1/Ch2 work is the *artificial-network-side empirical demonstration* of what Pessoa argues from neuroanatomy/imaging. They converge.
		- The thesis Ch1 functional-modularity definitions are *directly derived* from Pessoa Ch4's M1-M5 decomposition ([[wiki/refs/pessoa-2022-ch4-what-do-areas-do]]) — Pessoa supplies not just the empirical convergence but the operational vocabulary used in the thesis itself. ^[addressed]
	- ### The 2×2 PP/UP/PS/US framework gains a critical reading
		- **[[wiki/research/phd-thesis]]** — Pessoa Ch4's M1-M5 modularity decomposition gives a sharper vocabulary for the 2×2 framework's *Signature* axis. PS (Pressures-Structural) is roughly M5+M3 (localised + within-cluster connectivity dominant); US (Pressures-Ultimate) is M2+M1 (input-output mapping + separate modifiability). The framework's critique of "modular narrative" maps onto Pessoa's critique that M5 is doing illegitimate work in most modularity claims.
		- The "modularity got me one last time" worry from the thesis Discussion is *Pessoa's worry*. He spends 280 pages arguing why the worry is justified.
	- ### Complex systems framing (Ch8) → NCA / SODC theoretical framing
		- **[[wiki/concepts/neural-cellular-automata]]** — Pessoa Ch8 explicitly cites von Neumann's cellular automata + Game of Life as exemplars of emergence from local rules. The NCA paradigm is the engineering instantiation of the framework Pessoa argues neuroscience needs to adopt. ^[inferred]
		- **[[wiki/research/self-organising-digital-circuits]]** — SODC's basin-hopping recovery is what *non-decomposable, interaction-dominant* function looks like in an engineered substrate. The fact that recovery doesn't restore the pre-damage configuration but routes to a degenerate equivalent is exactly the "process not thing" view operationalised.
		- **[[wiki/refs/pessoa-2022-ch8-complex-systems]]** — explicit complex-systems chapter; the natural target for cross-citing whenever the wiki discusses emergence, feedback, nonlinearity in neural systems.
	- ### Functionalism — Pessoa converges with the broad-MR position
		- **[[wiki/concepts/functionalism]]** — Pessoa's many-to-many mapping (multiple regions can implement the same function; same region implements many functions) is a strong empirical case for *narrow MR* in biological brains. The "process not thing" view also flirts with the broader MR claim — if functions are trajectories, the substrate is incidental.
		- Where Pessoa is *cautious*: he doesn't endorse strong functionalism in the AGI sense. His skepticism of clean substrate-decoupling at the implementation level coexists with the *empirical* claim that mental functions don't live at single sites.
	- ### Solution degeneracy — the biological evidence
		- **[[wiki/concepts/solution-degeneracy]]** — Pessoa Ch4's many-to-one mapping (multiple regions can implement a function) is biological narrow MR with selection pressure attached. Ch12's process-ontology framing reinforces it: degeneracy of trajectories is fundamental, not a deviation from a "true" implementation.
	- ### Self-organisation — bridging Pessoa and Hiesinger
		- **[[wiki/concepts/self-organisation]]** — Pessoa Ch8's complex-systems framing aligns with Hiesinger's algorithmic-growth framing: both say the brain's properties emerge from local interactions over time, not from designed mechanisms.
		- **[[wiki/refs/hiesinger-2021-self-assembling-brain]]** — the natural pairing. Hiesinger explains *how the brain gets entangled* (algorithmic growth from genome); Pessoa explains *what entanglement means functionally* (many-to-many distributed networks). Read together they give a complete picture: development → entangled adult function.
- ## Limitations / Caveats
	- **Light on AI**: as a cognitive neuroscientist, Pessoa engages briefly with neural networks (Ch1, Ch8) but the book is not about AI architecture. Where Hiesinger Ch9 has direct prescriptions for AI design, Pessoa's prescriptions are more methodological — *how to think about brains*, less *how to build artificial ones*.
	- **MIT Press OA monograph format**: short (280 pp), idiosyncratic by design ("more idiosyncratic, reflecting my view of the brain"). It's a thesis statement, not a comprehensive review. For exhaustive coverage of brain networks, see Sporns or Bassett's work.
	- **Confidence 0.82, not 0.90+**: full book read, deep-ingested for the 4 most-relevant chapters, structural summaries for the rest. Hand-curation of individual chapter pages by Gabriel could push them to 0.85-0.88.
- ## Where to find what (cross-reference table)
  
  | Topic | Best chapter | Wiki page |
  |---|---|---|
  | Anti-localisationist thesis statement | Ch 1 | [[wiki/refs/pessoa-2022-ch1-networked-systems]] |
  | "How modular is the brain? Not much at all" | Ch 1 | [[wiki/refs/pessoa-2022-ch1-networked-systems]] |
  | Filler verbs + the poverty of mechanism | Ch 1 | [[wiki/refs/pessoa-2022-ch1-networked-systems]] |
  | Network science applied to brain (small-world etc) | Ch 1, Ch 10 | [[wiki/refs/pessoa-2022-ch1-networked-systems]] |
  | One-area-one-function critique / many-to-many | Ch 4 | [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]] |
  | M1-M5 modularity decomposition | Ch 4 | [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]] |
  | Double dissociation logic | Ch 4 | [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]] |
  | Functional repertoire / 20-dim profiles | Ch 4 | [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]] |
  | Cellular automata, Lotka-Volterra, von Bertalanffy | Ch 8 | [[wiki/refs/pessoa-2022-ch8-complex-systems]] |
  | Emergence, nonlinear dynamical systems, chaos | Ch 8 | [[wiki/refs/pessoa-2022-ch8-complex-systems]] |
  | Heterarchy and decentralised processing | Ch 8 | [[wiki/refs/pessoa-2022-ch8-complex-systems]] |
  | Process ontology / "things vs processes" | Ch 12 | [[wiki/refs/pessoa-2022-ch12-entangled-networks]] |
  | Trajectories in high-dim state space | Ch 12 | [[wiki/refs/pessoa-2022-ch12-entangled-networks]] |
  | Causation in complex systems / mutual causality | Ch 12 | [[wiki/refs/pessoa-2022-ch12-entangled-networks]] |
  | Phase transition needed in neuroscience | Ch 12 | [[wiki/refs/pessoa-2022-ch12-entangled-networks]] |
  | Subcortical structures (amygdala, striatum, etc.) | Ch 5, Ch 6 | (parent only) |
  | Prefrontal cortex / executive function | Ch 7 | (parent only) |
  | Comparative vertebrate brains / evolution | Ch 9 | (parent only) |
  | Hub-and-spoke / rich-club brain network analyses | Ch 10 | (parent only) |
  | Fear extinction case study | Ch 11 | (parent only) |
- ## Cited By (in this wiki)
	- [[wiki/refs/pessoa-2022-ch1-networked-systems]]
	- [[wiki/refs/pessoa-2022-ch4-what-do-areas-do]]
	- [[wiki/refs/pessoa-2022-ch8-complex-systems]]
	- [[wiki/refs/pessoa-2022-ch12-entangled-networks]]