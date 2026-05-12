title:: wiki/refs/pessoa-2022-ch4-what-do-areas-do
category:: reference
type:: external-ref
tags:: modularity, brain-networks, functional-ascription, neuroscience, structure-function
authors:: Pessoa, Luiz
year:: 2022
venue:: MIT Press (Chapter 4 of *The Entangled Brain*, pp 47-63)
doi::
arxiv::
citation-count:: n/a
summary:: Chapter 4 of Pessoa's book — the methodological core. Five formal definitions of modularity (M1-M5), the double-dissociation logic and its limits, the many-to-many structure-function mapping, and Pessoa's lab's 20-dimensional functional-profile approach.
confidence:: 0.82
lifecycle:: draft
lifecycle-changed:: 2026-05-10
created:: 2026-05-10
updated:: 2026-05-10
sources:: assets/pessoa_2022_the_entangled_brain.pdf (Chapter 4, pp 47-63, full read)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Chapter 4: What Do Brain Areas Do?** — Pessoa 2022, *The Entangled Brain*, pp 47-63. Parent ref: [[wiki/refs/pessoa-2022-entangled-brain]]. The methodological core of the book.

- ## TL;DR
  - The chapter that *unpacks the question* on which all of neuroscience hinges. Five formal definitions of modularity are laid out so the reader can see how much work is being done by which assumption.
  - History: Tan (Broca's patient, 1861) and Hitzig & Fritsch's dog stimulation (1870) cemented the *function localisation* programme. The double-dissociation logic became the canonical tool for inferring functional architecture.
  - But: brain regions show **one-to-many** mapping (one region → many functions) and functions show **many-to-one** mapping (one function → many regions). The combined empirical reality is **many-to-many** — which is *much harder* to study than the one-to-one ideal that the localisation tradition assumes.
  - **Pessoa's lab's contribution**: 20-dimensional functional profiles for cortical regions, computed across thousands of fMRI studies. Brain regions are *functionally diverse*, not specialised — they have preferences but participate broadly. This is the "functional repertoire" view that replaces "the function of region X".

- ## The Five Modularity Definitions (M1-M5)

  Pessoa lays these out as a way to make explicit what's being claimed when someone says "the brain is modular":

  - **M1**: Two parts A and B of a system are modules iff they are *separately modifiable*.
  - **M2**: The process carried out in such a (modifiable) subsystem computes a particular type of *input-output mapping*.
  - **M3**: There exists a decomposition of the system such that *within-subsystem interactions are much more complex than between-subsystem interactions*.
  - **M4**: Subsystems form *complex networks* with other subsystems, each carrying out a particular *subfunction* of a much more complex overall function.
  - **M5**: The subsystem must be *relatively spatially localised in the brain*.

  ### Why this decomposition matters

  - M1 to M4 are general — they could apply to *any* system, natural or human-made.
  - **M5 is what's specific to the brain — and is what most "modularity" claims smuggle in implicitly.**
  - It is logically possible to have M1-M4 satisfied by a *spatially distributed* system: a functional module exists, can be modified separately, has clean I/O, but its physical implementation spans the cortex non-locally. This is *functionally modular but not spatially modular*.
  - Pessoa: the brain may well satisfy weakened versions of M1-M4 — but M5 is empirically problematic. Drop M5 and the dispute is over decomposability + I/O specifications, not over geographic location.
  - **Implication for AI**: the tendency in computational modelling to bake in M5 (each "module" is a separate weight matrix in a separate physical location) is *not* what biological brains do, even when they exhibit functional specialisation.

- ## The History of Functional Localisation

  - ### Tan, Tan (Paul Broca, 1861)
    - Tan was admitted aged 21, lost the use of speech, could only pronounce "tan, tan." Examined by Broca shortly before death. Brain preserved; Broca concluded the left frontal lobe lesion caused the speech deficit.
    - Broca's 1.5-page case report in *Bulletin de la Société Anthropologique*: "the lesion of the frontal lobe was the cause of the loss of speech."
    - **The most important paper in the history of brain function localisation** (Pessoa). Set the template for *area X is responsible for function Y*.

  - ### Hitzig & Fritsch dog stimulation (1870)
    - Performed not in a university lab but on a dressing table in Hitzig's bedroom in Berlin. Electrically stimulated the canine cortex; uncovered locations whose stimulation elicited muscular responses of forepaw, hindpaw, face, neck on the contralateral side.
    - Then *removed* the area (with a scalpel) — observed paw-specific impairment. Established the *cortex contains processing centres* claim.
    - "Some psychological functions, and perhaps all of them, in order to enter matter or originate from it, need circumscribed centers of the cortex." (Hitzig & Fritsch, quoted)

- ## The Double-Dissociation Logic

  - ### Single dissociation (weak)
    - Two tasks A and B; manipulation m affects A but not B. Inference: there's a mental function required by A but not B.
    - **Inferentially weak**: maybe the lesion just impairs *difficult* tasks and A happens to be harder than B.

  - ### Double dissociation (the gold standard)
    - Region 1 affects task A but not B; region 2 affects task B but not A.
    - Inference: regions 1 and 2 carry out *isolable* functions.
    - **Example**: patient PW (left-hemisphere stroke) read 67% of concrete words but only 13% of abstract words. Patient CAV (left-hemisphere tumour) read 36% of concrete words but 55% of abstract words. Together → double dissociation of concrete vs abstract word reading.

  - ### Pessoa's critique
    - Double dissociations are *consistent with* modularity but don't *establish* it. They establish that *something* differs between the two cases — but the difference could be at the *interaction* level rather than the modular-component level.
    - Quote: "There can be no argument with the fact of modularity, only about its nature and extent" (Andrew Ellis, neuropsychologist) — Pessoa cites this to show the field treats modularity as foundational rather than as an empirical hypothesis.

- ## The Structure-Function Mapping

  Pessoa systematically considers all four possible mappings:

  - ### One-to-one (figure 4.2a) — the localist ideal
    - Region A_i implements function F_i. The amygdala is for fear; the fusiform gyrus is for faces; V1 is for visual edges.
    - **Pessoa**: this almost never holds at any meaningful level of specificity.

  - ### One-to-many (figure 4.2b) — empirical reality (per region)
    - **Region A_1 → {F_1, F_2, ..., F_k}**: as research on a region progresses, the list of functions it participates in *grows*. The prefrontal cortex was thought to do "working memory" in the 1930s; now it spans cognitive control, decision-making, emotion regulation, language, social cognition.
    - The amygdala — the textbook fear centre — also processes appetitive (rewarding) information, salience, social cues.
    - This holds even for *small* regions. "Too large to be specific" is not the explanation.

  - ### Many-to-one (figure 4.2c) — empirical reality (per function)
    - **{A_1 or A_2 or ... A_j} → F**: a single mental function (attention, working memory, cognitive control) is supported by *multiple* regions across the frontal-parietal network. No single attentional area.
    - This is biological *narrow MR* in Edelman's degeneracy sense — multiple structural substrates implement the same function.

  - ### Many-to-many (figure 4.2d) — what we actually have
    - The combined empirical reality. M brain regions, N functions, with rich connectivity in the bipartite graph between them.
    - **Implication**: the study of such systems is much harder than systems with one-to-one organisation. Standard methods (lesion → infer function) fail to converge.

- ## Pessoa's Lab — 20-Dimensional Functional Profiles

  - In the BrainMap database (a repository combining thousands of fMRI studies), each study reports brain locations active in particular task domains.
  - Pessoa's lab chose 20 task domains spanning perception, action, emotion, cognition (vision, audition, executive function, fear, sadness, anger, language, memory, reasoning, motor learning, etc.).
  - For each brain location, they computed a **20-dimensional engagement profile**: how often each task domain activated this location across all published studies.
  - **Result**: brain regions are *functionally diverse*, not specialised. They have *preferences* (some regions are more engaged by emotion, some by perception) but participate across many domains. The radial-plot visualisation (figure 4.4a) shows this directly.
  - **Functional-diversity index**: a scalar summary of how broadly a region is engaged. *Varies across the brain*: some regions are highly diverse, others moderately. No region is a "pure" specialist.

- ## The "Functional Repertoire" View — Pessoa's Replacement for "The Function of X"

  - Instead of asking "what does region X do?" → ask "what is region X's *functional repertoire*?"
  - The repertoire = a multidimensional profile of engagement across many tasks.
  - **Analogy**: coffee flavour profiles. A Brazilian coffee is not "the coffee that does flavour" but is described by *chocolaty, nutty, light acidity* — a multidimensional repertoire. So is a brain region.
  - **Open problem**: what's the right basis set of "functions"? Pessoa's 20 dimensions is a working choice; it could be 42 (like English phonemes) or 420. The basis-set question is genuinely unsettled — like the basis-functions question in signal processing.

- ## Connections to Gabriel's Research

  - ### M5 and the structural-modularity-without-functional-specialisation finding
    - **[[wiki/concepts/modularity]]** — Pessoa's M1-M5 decomposition is the *clean vocabulary* for the thesis Ch1/Ch2 result. The thesis demonstrates that *artificial M5-modular* networks (spatially separated weight matrices) do not develop M1-M4 functional modularity unless additional pressure is applied. **Pessoa's empirical claim about biological brains is the same finding from the other direction**: the biological brain doesn't have M5 cleanly *and* doesn't have M1-M4 cleanly either.
    - **[[wiki/research/dynamics-specialization]]** — the resource-constraint result is exactly what Pessoa would predict needs to happen for *any* form of modularity to emerge: pressure on a structurally modular substrate is needed to drive functional separation. Without it, function distributes across the whole.

  - ### Many-to-many and the topology-masked transformer
    - **[[wiki/research/self-organising-digital-circuits]]** — SODC is a *many-to-many architecture by design*: shared TMT weights operate on every node, every node implements multiple functions across tasks (LUT configurations are task-conditional), every function involves multiple nodes. This is closer to Pessoa's empirical-brain framing than to the M5-modular ANN tradition.
    - The basin-hopping recovery story is *many-to-one mapping made explicit*: the same Boolean function is realised by many distinct LUT configurations. Pessoa Ch4's many-to-one is at the regional scale; SODC's many-to-one is at the LUT-configuration scale.

  - ### Functional-repertoire framing for SODC
    - The SODC blog post could productively reframe its "what TMT does" section as a *functional repertoire across task families* rather than as a single mechanism. Pessoa's 20-dim profile is the inspiration: *what is the TMT's functional repertoire across Boolean function families, perturbation regimes, and depth scales?*

  - ### The double-dissociation logic and ablation experiments in NCA
    - **[[wiki/refs/najarro-2023-neural-developmental-programs]]** + **[[wiki/refs/plantec-2024-lifelong-ndp]]** — both rely on ablation studies (turn off SP, turn off SA) that are essentially single dissociations. Pessoa's critique applies: results are *consistent with* the proposed mechanism but don't *establish* its modularity. Future work should aim for double dissociations between mechanisms.
    - **For the thesis itself**: when claiming that resource constraints drive specialisation, the cleanest case is a double dissociation — resource constraints alone vs. modular topology alone vs. both. ^[inferred]

  - ### The 2×2 PP/UP/PS/US framework gains M-vocabulary
    - **[[wiki/research/phd-thesis]]** — the thesis's PS/US distinction maps onto Pessoa's M5/M2 distinction. PS = signature of localised *spatial* organisation (M5-flavoured). US = signature of clean *input-output* mapping (M2-flavoured). The 2×2 framework is essentially asking: *under which Pressures does which subset of M1-M5 emerge?*

- ## Memorable Lines

  - "There can be no argument with the fact of modularity, only about its nature and extent." (Andrew Ellis, quoted by Pessoa as the field's default)
  - "The one-to-one framework, even if implicitly accepted or adopted by neuroscientists, is an oversimplification that hampers progress in understanding the mind and the brain."
  - "A single-function description is like a straitjacket that needs to be shed."
  - "Brain regions participate in specific computations, functions, processes, or behaviors only when embedded within larger circuits comprised of multiple brain areas."
  - "The reasoning is analogous to what one would adopt to reverse-engineer a human-made device — say, remove the pistons in a car to try to 'discover' that they are a key element in the combustion process." (on dissociation logic — and its hidden engineering assumption)

- ## Cited By (in this wiki)
  - [[wiki/refs/pessoa-2022-entangled-brain]] — parent
