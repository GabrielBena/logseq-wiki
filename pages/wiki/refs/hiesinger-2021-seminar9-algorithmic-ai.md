title:: wiki/refs/hiesinger-2021-seminar9-algorithmic-ai
category:: reference
type:: external-ref
tags:: brain-development, ai, self-organisation, evolutionary-programming, cybernetics
authors:: Hiesinger, Peter Robin
year:: 2021
venue:: Princeton University Press (Seminar 9 of *The Self-Assembling Brain*, pp 267-286)
doi::
arxiv::
citation-count:: n/a
summary:: Seminar 9 of Hiesinger's book. The chapter most directly relevant to AI research. Asks "When does a neural network need to grow?" Argues current ANNs take massive shortcuts by skipping development. Self-organisation, evolutionary programming, Hinton on capsules, the indirect/developmental encoding lineage.
confidence:: 0.82
lifecycle:: draft
lifecycle-changed:: 2026-05-10
created:: 2026-05-10
updated:: 2026-05-10
sources:: assets/hiesinger_2021_the_self-assembling_brain.pdf (Seminar 9, pp 267-286, full read)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Seminar 9: From Algorithmic Growth to Artificial Intelligence** — Hiesinger 2021, *The Self-Assembling Brain*, pp 267-286. Parent ref: [[wiki/refs/hiesinger-2021-self-assembling-brain]]. **The single chapter of the book most directly relevant to your research.**

- ## TL;DR
  - **The central question**: "When does a neural network need to grow?" — i.e., when can ANNs get away with the build-then-train shortcut, and when does artificial general intelligence require *algorithmic growth* of the network itself?
  - Reviews the history of self-organisation in cybernetics (Wiener, Ashby) and recasts it as the framework current ANN research has implicitly inherited but rarely names. Feedback + noise + autonomous agents + time + energy = self-organisation; self-organisation iterated = algorithmic growth.
  - Compares engineered ANNs (random init + supervised training) vs evolved/grown ANNs (developmental encoding, indirect representations). The former works for narrow tasks; the latter is barely explored but may be necessary for general AI.
  - **Hinton's 2014 self-critique**: ANNs are missing levels of structure, capsules, and an explicit notion of entity. Hiesinger reads this as Hinton noticing the absence of *what biology gets from the developmental algorithm*.
  - "Big data + deep learning" is the current gold standard. Hiesinger's question: are we hitting the limits of what can be compressed into trained weights without growing the architecture?

- ## Self-Organisation as the AI Framework We Inherited Without Naming

  - ### Cybernetics origins (Wiener 1948, Ashby 1947, 1952)
    - **Norbert Wiener** defined cybernetics as "the scientific study of control and communication in the animal and the machine" — a deliberate bridge between biology and engineering.
    - **Andrey Kolmogorov**'s framing: cybernetics studies "systems of any nature which are capable of receiving, storing and processing information so as to use it for control".
    - **Ross Ashby** (*Design for a Brain*, 1952): asked how a machine, obeying physics and described mathematically, could produce *adaptive* behaviour. His key insight: **"neurons must self-co-ordinate"**, and the artificial-brain designer faces the same problem. The "gene pattern" controls a small number of factors that *develop coordination among many neurons*. This is essentially the genomic-bottleneck argument from 1952.

  - ### Attractors, energy landscapes, and gradient descent
    - Self-organising systems move towards equilibrium states (*attractors*) in an energy landscape. Local minima (small valleys) are easily reached; global minima may not be.
    - **Gradient descent** (the workhorse of ANN training) is a self-organising mechanism by another name: it iteratively follows local rules to navigate an energy landscape. Backpropagation = gradient descent + credit assignment across layers.
    - **Recurrent networks with feedback** are stronger candidates for self-organisation than feedforward networks. Feedforward training "is more like a domino rally than a self-organizing system" (Roland Fleming, U. Giessen, in conversation with Hiesinger).
    - **Noise as productive ingredient**: noise helps ANNs avoid local minima — same role as stochastic filopodial dynamics in axon guidance. Von Foerster (1960): "self-organizing systems do not only feed upon order, they will also find noise on the menu."

  - ### What's missing — feedback at the architecture level
    - Standard ANNs: a fixed architecture is decided up front, randomly connected, then trained. **The architecture itself is not a product of self-organisation.** Hiesinger's point: this is *the* shortcut.
    - In biological brains, the architecture is the *output* of the developmental self-organising process. The information that goes into determining how many neurons exist, where they are, how they connect, is *part of the algorithmic growth*.

- ## When Does an ANN Need to Grow? Three Layers of Argument

  - ### Layer 1 — Empirical: it depends on the task
    - For image classification, speech recognition: random init + big data works surprisingly well. Networks like Hinton's 2017 deep CNN (650k neurons) outperform fruit flies (~100k neurons) at narrow tasks.
    - But: a fly does *much more* than image classification — flight control, polarised-light vision, gravity sensing, courtship behaviour, navigation, learning, sleep, metabolism. **The image classifier vs the fly comparison highlights what's lost when development is shortcut.**
    - **The implicit empirical bet**: the more tasks you want one system to handle, the more important the developmental algorithm becomes.

  - ### Layer 2 — Information-theoretic: where does the information come from?
    - Information enters an ANN almost entirely through training data. The architecture contributes *some* information (inductive biases like convolution, attention) but is fixed.
    - In a biological brain, information enters via *both* developmental algorithm (encoded in the genome, unfolded over years) *and* learning (sensory experience, language, social interaction). The developmental contribution is enormous and largely irreducible.
    - **Quantitative claim**: Hawkins (interview cited): "Training times are the limiting factor. Our brains are learning continuously for years." Time and energy are not arbitrary — they're the resources required to unfold logical depth into endpoint information.

  - ### Layer 3 — Generative: evolutionary programming
    - The brain isn't just developed; it's *developed-from-evolved-rules*. Evolutionary programming = selection over genomes that encode developmental algorithms. **A mutation does not change a synaptic weight; it changes the algorithm that produces the brain.**
    - **Pioneers cited**: Arend Hintze, Chris Adami — evolve ANNs by evolving genomes that encode them, often using "direct encoding" (one gene per weight) but increasingly *indirect encoding* + developmental encoding.
    - Hiesinger's predictive flag (p. 285): "first experiments with indirect and developmental encoding already revealed remarkable effects on robustness and adaptability". *This is the literature NDP, LNDP, EngramNCA built on.*
    - **Why it's still fringe**: "evolver of artificial intelligence" is not a job title most parents understand. The compute cost is enormous; the payoff is in capabilities current ANNs can't reach.

- ## Hinton's 2014 Self-Critique (and Why It Matters)

  - In a 2014 MIT lecture, **Geoffrey Hinton** (the inventor of backpropagation) said: "There's a lot of things wrong with the neural nets we are using ... a lot of things very unlike the brain that I believe are making them work not as well as they could."
  - Specifically: "any complex set engineered system should have various levels of structure — neural nets have very few levels of structure ... One thing that's missing in these neural nets is there is no explicit notion of an entity."
  - **Hinton's capsules** (2017+): try to introduce levels of structure inspired by cortical columns and place cells.
  - **Hiesinger's reading**: Hinton is naming a symptom of what's missing — *what biology gets from the developmental algorithm*. Cortical columns, place cells, capsule-like compositional units are emergent products of the brain's growth. Trying to retrofit them into a build-then-train ANN runs into a deeper issue: the *features arise because of the algorithm*, and grafting them on without the algorithm may not capture the function.
  - Hinton has also publicly questioned backpropagation itself (2017+: "we need to throw it all away and start over"). Hiesinger reads this as Hinton arriving at the same conclusion from a different direction: ANN learning rules are too narrow compared to what biological algorithmic growth produces.

- ## The McCarthy / Minsky Tradition vs the Developmental View

  - **John McCarthy** (gave AI its name): "AI does not have to confine itself to methods that are biologically observable." (2006: "we've gotten to know a lot about how the brain works. I don't think it's got very much that connects with artificial intelligence yet.")
  - McCarthy died in 2011, *just* before the deep-learning revolution. The 5 years following 2011 effectively refuted the "AI doesn't need biology" stance: ANNs (a biologically inspired architecture) became the dominant paradigm.
  - **Minsky's definition of AI**: "the science of making machines do things that would require intelligence if done by men". Hiesinger: by this bar, a car GPS is intelligent. But Minsky was clearly aware that this isn't AGI.
  - **The disconnect**: AI research focuses on *function*; brain research has long focused on *function* as well, but Hiesinger's claim is that for AGI the *generative process* matters and current AI has barely engaged with it.

- ## The Continuum of Function-as-Development

  - **The build-then-train model** treats development and function as distinct: the architecture is engineered, then frozen, then training is run on top. This is the **car-then-driver model**: build the car, then drive it.
  - **The biological model** has no such cut: the brain keeps developing while it functions. Synaptic plasticity is just continued algorithmic growth at slower kinetics. Aging is continued algorithmic growth too.
  - **For AI**: replacing build-then-train with grow-and-function-continuously is what NDP/LNDP attempt. EngramNCA's pool training is another instance — the network keeps reconfiguring during evaluation.
  - **The hard claim**: if function and development are continuous, then *the only way to specify a function is via the developmental rules that produce a network capable of it*. There is no way to short-cut from "I want capability X" to "trained network with capability X" without going through "developmental rule that grows a network with capability X".

- ## What Cannot Be Cut Short

  - Each shortcut taken in current AI corresponds to a piece of biological information that's discarded:
    - **Random initialisation** discards: structural priors, modular organisation, levels of structure, entity-level representations.
    - **Fixed architecture** discards: structural plasticity, cell-type heterogeneity, brain-region differentiation.
    - **Standard training rules (SGD/Adam)** discards: gene-regulatory feedback, transcription-factor cascades, cell-intrinsic state changes.
    - **Single-parameter synaptic weights** discards: the rich molecular state of a synapse — receptor types, vesicle dynamics, neuromodulation, metabolic state, all of which are parameters evolution can act on.
  - Hiesinger's claim is *not* that all of this needs to be simulated. It's that **the choice of shortcut determines the type of AI you can build**. AGI may require keeping more of these layers than narrow AI does.

- ## Connections to Gabriel's Research

  - ### NDP / LNDP / EngramNCA — operationalising Hiesinger's prescription
    - **[[wiki/refs/najarro-2023-neural-developmental-programs]]** — NDP is essentially "Hiesinger's algorithmic-growth argument operationalised in graph-NCA form". Per-cell shared NN, growth from a seed, no separate engineering phase. Cites Hiesinger 2018 + 2021 explicitly.
    - **[[wiki/refs/plantec-2024-lifelong-ndp]]** — LNDP is the more ambitious operationalisation: spontaneous-activity pre-experience development + lifelong structural plasticity + activity/reward-dependent dynamics. **This is what Seminar 9 was prescribing four years before the paper appeared.**
    - **[[wiki/refs/guichard-2025-engramnca]]** — EngramNCA's public/private channel split is closer to Hiesinger's "private memory is part of the rule, not the visible state" framing than any other architecture. The Lenia-glider stability over long horizons (where vanilla NCA fails) is direct evidence that *cell-internal information* can serve the role Hiesinger ascribes to genome-as-rule-substrate.
    - **[[wiki/refs/guichard-2025-arc-nca]]** — ARC-NCA is the *empirical evidence* that grown-from-scratch developmental networks can be competitive with frontier LLMs at reasoning tasks. 17.6% solve rate vs ChatGPT 4.5's 10.3% at ~1000× lower cost is *exactly* the "narrow shortcut vs full algorithmic growth" tradeoff Hiesinger predicts.

  - ### NCA as the candidate substrate for developmental AI
    - **[[wiki/concepts/neural-cellular-automata]]** — NCAs are explicitly the architecture that comes closest to Hiesinger's prescription. Local rules, autonomous agents, time + energy, no master regulator. The NCA Seven Angles can be re-read as "seven stages of approaching Hiesinger's full vision":
      - Mordvintsev (image NCA): pattern-former with local rules
      - UNCA Ch3: substrate for computation
      - SODC Ch4: rule-as-meta-optimiser (function emerges from algorithmic process)
      - BraiNCA: brain-economy spatial priors
      - NDP: substrate growth via per-cell NN
      - LNDP: structural plasticity + lifelong development
      - EngramNCA: cell-private propagable memory
    - The gap from current NCAs to Hiesinger's full vision: *evolutionary programming over the developmental rule*. None of the current NCA architectures use evolution to *select* the rule; they all train it via gradient descent on a fixed loss. Hiesinger suggests this may be the next frontier. ^[inferred]

  - ### SODC and the "function is continued development" claim
    - **[[wiki/research/self-organising-digital-circuits]]** — SODC's pool meta-learning is the cleanest existing instance of "function as continued development". The TMT keeps reconfiguring LUTs in response to perturbation; there's no point at which training is done and inference begins. The basin-hopping recovery story is *neural-Darwinist* in Edelman's sense and *algorithmic-growth* in Hiesinger's sense.
    - The fact that SODC works at all on hard tasks (Boolean function recovery under permanent damage, scale-free generalisation) is *evidence* that algorithmic-growth-style training is competitive with build-then-train when tasks demand robustness and adaptation. ^[inferred]

  - ### The thesis grand vision — Hiesinger as the strongest external "why"
    - **[[wiki/research/phd-thesis]]** Discussion's grand vision is *the same vision Hiesinger argues for in this Seminar*. A single local rule governing growth + learning + repair = the developmental algorithm not artificially separated into phases. Reading this Seminar is reading the strongest external defence of why the grand vision is worth pursuing.
    - The thesis flags structural plasticity (NCA-rewires-topology) as the central open challenge. Hiesinger Seminar 9 doesn't solve it but supplies the strongest argument for *why solving it matters*: it's the missing piece between current NCA and a true developmental architecture.

  - ### Functionalism complement
    - **[[wiki/concepts/functionalism]]** — Hiesinger's "you have to grow it, you can't just engineer it" claim seems to challenge broad multiple realizability. **It does not.** Function-as-property remains substrate-independent; what Hiesinger argues is that *the path to a particular substrate-instance* is irreducible. You can in principle build a silicon brain that's intelligent in the human-functional sense, but you have to *grow* it on silicon (or simulate that growth), not just engineer-and-flip-the-switch. The two views compose: broad MR says intelligence-the-function is platform-independent; Hiesinger says the *generative algorithm for any particular instantiation* must be run.

- ## Memorable Lines

  - "Self-organization is the bottom-up antithesis to top-down engineering." (p. 267)
  - "Just because ANNs are not typically designed as self-organizing systems does not mean that they can avoid it." (p. 270)
  - "When we design artificial neural networks with random initial states, we simply shortcut the preceding growth process and flip the on switch for an algorithmic learning process." (p. 274)
  - "AI's biggest successes to date came from leaving the learning to a scruffy self-organizing process rather than neat programming. Maybe this is enough. Or, maybe, this approach will reveal fundamental limitations as long as the learning system has not yet learned to learn by self-assembling itself. Especially if the principles of self-assembly during development and learning turn out to be the same." (p. 282)
  - "When it comes to algorithmically growing the whole, changes in the underlying code will be as little predictable to its intelligence as genetic changes currently are for human or fly intelligence." (p. 286)

- ## Cited By (in this wiki)
  - [[wiki/refs/hiesinger-2021-self-assembling-brain]] — parent
