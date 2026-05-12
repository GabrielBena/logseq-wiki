title:: wiki/refs/hiesinger-2021-seminar8-development-function
category:: reference
type:: external-ref
tags:: brain-development, neural-darwinism, memory, exaptation, neurobiology
authors:: Hiesinger, Peter Robin
year:: 2021
venue:: Princeton University Press (Seminar 8 of *The Self-Assembling Brain*, pp 245-261)
doi::
arxiv::
citation-count:: n/a
summary:: Seminar 8 of Hiesinger's book. Argues function is a *continuation* of development — not a separate phase. Spandrels and exaptation in brain wiring (the inverted retina, cortical columns). Memory as algorithmic rules. Edelman's neural Darwinism extended to function.
confidence:: 0.82
lifecycle:: draft
lifecycle-changed:: 2026-05-10
created:: 2026-05-10
updated:: 2026-05-10
sources:: assets/hiesinger_2021_the_self-assembling_brain.pdf (Seminar 8, pp 245-261, full read)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Seminar 8: From Development to Function** — Hiesinger 2021, *The Self-Assembling Brain*, pp 245-261. Parent ref: [[wiki/refs/hiesinger-2021-self-assembling-brain]].

- ## TL;DR
  - **Function is a continuation of development.** There is no clean break between the brain "growing" and the brain "running"; they are the same algorithmic process under continuous time-and-energy supply.
  - Brain anatomy is partly *adaptation* (selected for function) and partly *spandrel* (developmental side-effect). The famous inverted retina is a textbook spandrel: light has to pass through axon bundles before reaching the photoreceptors, not because that's optimal but because of an embryonic tissue-folding event locked in by evolution.
  - **Memory is not stored as data at an address**; it's encoded as the algorithmic rules sufficient to recreate a representation given input + time + energy. "Storing is changing is retrieving."
  - Edelman's Neural Darwinism — *neural group selection* — is recast here as a unified mechanism: the same selection process operates in development (which neurons survive), in early plasticity (which connections strengthen), and in adult function (which subnetworks get recruited for which memory).

- ## Spandrels and Exaptation in Brain Wiring

  - ### The inverted retina (the textbook spandrel)
    - Vertebrate retinas have photoreceptors *behind* the output axon bundles. Light passes through cables, interneuron layers, and synaptic plexi before reaching the light-sensitive elements. This is *suboptimal* — it creates the blind spot (where axons exit the retina) and reduces light efficiency.
    - **Why does it look like this?** An embryonic tissue-folding event in a vertebrate ancestor flipped the retinal orientation. Once locked in, evolution could not gradually reverse it — there was no fitness-monotone path back. Cephalopod eyes (squid, octopus) evolved independently and have the retina the right way round; both are good vision systems, but cephalopods didn't inherit the developmental constraint.
    - **Implication**: "What is it good for?" is the wrong question. The primary explanation is *historical contingency*, not adaptation. Secondary rationalisations exist (the brain fills in the blind spot from the other eye) but they're post-hoc.

  - ### Spandrels (Gould & Lewontin 1979)
    - Architectural metaphor: when an arch is built inside a rectangular frame, the triangular leftover spaces (spandrels) appear inevitably. Artists later *use* these spaces for art — but the spaces weren't designed for art.
    - In biology: many features arise as side-effects of other selected processes. They aren't *for* anything but exist reliably enough that evolution can later *exapt* them for new functions.
    - **Crystallin proteins**: the lens of the human eye is transparent because of crystallins, which are *repurposed metabolic enzymes* — exapted from a non-vision function.

  - ### Cortical columns — adaptation, spandrel, or exaptation?
    - Hubel & Wiesel's Nobel work: ocular dominance columns in visual cortex shrink/expand with monocular deprivation. Plasticity is real and structural.
    - But: columnar architecture forms even *without any visual input*. And: squirrel monkeys may or may not have anatomically recognisable columns, with no obvious correlation to vision quality.
    - **Hiesinger's reading**: columns are likely a developmental side-effect (driven by axon-guidance kinetics) that's then *exapted* for plasticity. The structure isn't *for* plasticity; plasticity *uses* the structure that growth created.
    - In zebrafish: a *robo2* mutation disrupts the layered organisation of a brain region but leaves direction-selectivity wiring intact — *because the layers are an efficiency side-effect, not a functional requirement*. Wiring still happens, just slower without the layered scaffold.

  - ### Implication for connectomics
    - Looking at a wiring diagram, you cannot tell which features are adaptations and which are spandrels. Topology + function are co-determined by both selection pressure *and* developmental history.
    - **For AI**: copying brain topology naively risks copying spandrels — features that exist because of the developmental algorithm, not because they're functionally required. To benefit from the algorithm, you have to run the algorithm, not just import its output.

- ## Hawkins' Memory-Prediction System (and Hiesinger's Reformulation)

  - ### Jeff Hawkins' core idea (*On Intelligence*)
    - The neocortex is not a computer that *computes solutions*. It's a *memory-prediction system*: incoming input is continuously matched against memory; the system constantly predicts the next thing likely to happen; surprise (failed prediction) drives learning.
    - Three features of cortical memory: **(a) sequential** (you can't sing a song backwards without re-learning it as a new sequence); **(b) auto-associative** (a fragment retrieves the whole); **(c) invariant representations** (different inputs map to the same stored pattern).

  - ### Hiesinger's twist — memory as algorithmic rules
    - Hiesinger reformulates Hawkins: **the brain doesn't store memories; it stores the algorithmic rules sufficient to recreate them**, given input as a starting condition and time-energy as the substrate.
    - "Storing is changing is retrieving." Every retrieval modifies the network; the same memory is never recalled identically. The invariant representation is *the rule that produces something close to the previous output*, not a static stored copy.
    - **Connection to Rule 110**: just as the only way to know the state of Rule 110 at iteration 1,234 is to run iterations 1-1,233, the only way to retrieve a memory is to *run the network forward from a triggering input*.
    - **Decentralised storage**: a "grandmother neuron" doesn't *contain* the grandmother memory; it gets *recruited* by the wave of activation propagating through the network. Killing it would slightly modify retrieval, not erase the memory.

  - ### The PIN code and the guitar etude
    - The 4-digit PIN: the digits stay stable, but the *associations* (what ATM I last used, what felt the keys) drift constantly. The "memory" is the *current rules of the network*, which keep getting re-shaped by recall.
    - The Bach etude: I can play five specific notes only as part of playing the entire piece up to that point. There is *no random access* — the only retrieval mechanism is to run the algorithm from the beginning. **This is exactly Hiesinger's no-shortcut claim applied to memory.**

- ## Edelman's Neural Darwinism — Unified Across Development and Function

  - ### Neural group selection (Edelman 1978, 1987)
    - **Developmental selection**: during embryogenesis, more neurons are produced than survive. Connections form exuberantly; activity patterns determine which survive (neural Darwinism applied to wiring).
    - **Experiential selection**: during function, different patterns of synaptic strength compete; some get reinforced, others wither (neural Darwinism applied to circuits).
    - **Reentry**: massively parallel reciprocal fibres allow synchronisation between functionally segregated areas. Reentrant networks have *many alternative circuits* that can produce the same output — an integration mechanism that *requires* degeneracy ([[wiki/refs/edelman-2001-degeneracy-complexity]]).

  - ### Hiesinger's extension: the same Darwinian process operates throughout
    - **Development → function continuum.** Selection during embryogenesis (which neurons survive) is the same process as selection during function (which neurons get recruited for which memory). Hawkins' "specific-face neuron" is *selected* by the wave of activation when the monkey first sees the face — like an antibody clone selected by an antigen.
    - **Memory as evolutionary process inside the brain.** Each new input is like a new selective pressure; the network's response is the population of variants that get selected. Edelman: "the fundamental requirement for successful adaptation is preexisting diversity" — the network's diversity (decentralised, redundant, slightly different at every neuron) is exactly what enables this.
    - **Implication**: the brain's modus operandi is *self-selection, not programming*. You don't write a memory into the brain; you create conditions under which the network selects which subnet will represent the new information.

- ## Why This Matters — Implications

  - ### (1) The "build-then-train" architecture is a category error
    - Standard ANNs: design a fixed architecture, randomly initialise, train via supervised/reinforcement learning. The development phase is *engineering*, not algorithmic growth; the function phase is *learning*, not continued growth.
    - Hiesinger: in biology, these are the *same process at different timescales*. There is no "off the production line" moment for a brain.
    - **Implication for AI**: an AGI that grows during training would be more biologically faithful, but more importantly, it would have *more information density* — the algorithmic growth process is itself an information-bearing process that random init + train cannot replicate.

  - ### (2) Aging is continued algorithmic growth
    - Most theories treat aging as deterioration. Hiesinger argues it's *continued progress* — the algorithm keeps running, transcription factor cascades keep updating, the cell keeps changing state. Aging *is* algorithmic growth that doesn't stop.
    - This reframes "neurodegenerative disease" as algorithmic-growth-gone-wrong rather than passive decay.

  - ### (3) Programming the brain = using the brain
    - You can't write a memory directly; you can only feed inputs and let the network select its own representation. This is consistent with how *training* works in deep learning — you give examples, the network's loss landscape selects which weights change. **Hiesinger's claim is that this isn't a quirk of gradient descent; it's the only way information enters any algorithmic-growth system.**

- ## Connections to Gabriel's Research

  - ### Function as continuation of development → SODC's pool meta-learning
    - **[[wiki/research/self-organising-digital-circuits]]** — SODC's pool training is *exactly* Hiesinger's "function = continued development" thesis. Circuits never finish being shaped; the [[wiki/concepts/topology-masked-transformer]] keeps reconfiguring LUTs in response to ongoing perturbation. The build-then-train boundary doesn't exist in SODC — there's no point at which "the meta-optimisation is done and now the circuits just run". ^[inferred]
    - The basin-hopping recovery story ([[wiki/concepts/solution-degeneracy]]) is *neural Darwinism in an engineered substrate*: the TMT selects from a pool of structurally distinct functionally equivalent configurations, exactly as Edelman's neural-group-selection theory predicts for biological brains.

  - ### LNDP and continued algorithmic growth
    - **[[wiki/refs/plantec-2024-lifelong-ndp]]** — LNDP's whole point is that the developmental rule keeps running throughout the agent's lifetime. *This Seminar is the theoretical justification for that design choice.* LNDP's spontaneous-activity pre-experience phase is also Hiesinger-aligned: pre-environmental development based on retinal-wave-style spontaneous activity is mentioned explicitly in this Seminar.

  - ### Spandrels and the modularity trap
    - **[[wiki/concepts/modularity]]** — Hiesinger's spandrel/exaptation framing is the deep biological grounding for why structural modularity ≠ functional specialisation. The thesis Ch1 / Ch2 finding (modularity is elusive without resource constraints) maps onto: structural modularity may be a *spandrel of the developmental algorithm*; functional specialisation requires *exaptation under selection pressure*. ^[inferred]
    - The retina-the-wrong-way example is the canonical case: an apparent inefficiency that's locked in developmentally and works because the rest of the system *adapted around it* (the brain fills in the blind spot). The thesis Discussion's "modularity narrative got me one last time" worry is exactly this: structural patterns that look meaningful may be developmental side-effects that we then over-interpret functionally.

  - ### Memory as algorithmic rules → connection to NCA-as-engram
    - **[[wiki/refs/guichard-2025-engramnca]]** — EngramNCA's public/private channel split, with private gene channels propagable via GenePropCA, is a *direct architectural instantiation* of "memory is rules sufficient to recreate a representation". The genes are the rule-substrate; the GeneCA is the rule-runner; the morphology is the recreated representation.
    - **[[wiki/concepts/solution-degeneracy]]** — Hiesinger's "single neuron in face-recognition area gets selected, doesn't encode the face" is degeneracy applied to memory: the memory is in the *network's response capability*, not in any specific cell. SODC's basin-hopping recovery has the same structure — function is in the basin, not in any specific configuration.

  - ### Edelman's Neural Darwinism — already in the wiki
    - **[[wiki/refs/edelman-2001-degeneracy-complexity]]** — already deep-ingested. This Seminar is the biological-developmental complement to Edelman's degeneracy paper: Edelman explains *why* the brain is selectionally organised; Hiesinger explains *how* it gets that way through algorithmic growth.

  - ### Connection to Aguera y Arcas's functionalism
    - **[[wiki/refs/aguera-y-arcas-2025-functional-perspective]]** — Aguera argues that intelligence/consciousness is *functional* (multiply realisable). Hiesinger here suggests the *path to a particular instantiation* may be irreducible (no shortcut). **They're consistent at different levels**: function-as-property is multiply realisable; function-as-developmental-history-of-this-particular-system is not. Self-consciousness as functional theory-of-mind (Aguera) is exactly what Hiesinger calls "the brain's modus operandi" — neural-Darwinist self-selection during function.

- ## Memorable Lines

  - "Brain wiring is no less a product of evolution and development than the eye's lens and retina." (p. 252)
  - "Storing is changing is retrieving." (paraphrase of pp. 257-258 — Hiesinger's reformulation of Hawkins)
  - "There are no single neurons that can be killed to remove the 'child' or 'grandmother' information content. The memory is not stored in a data bank separate from the processing unit (the von Neumann architecture). Rather, the information becomes part of how the processing unit processes information itself." (p. 258)
  - "Both the developmental growth of a neural network and its function are based on algorithmic rules." (p. 261)

- ## Cited By (in this wiki)
  - [[wiki/refs/hiesinger-2021-self-assembling-brain]] — parent
