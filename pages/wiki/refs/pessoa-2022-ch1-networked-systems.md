title:: wiki/refs/pessoa-2022-ch1-networked-systems
category:: reference
type:: external-ref
tags:: modularity, brain-networks, anti-localisationism, neuroscience, network-science
authors:: Pessoa, Luiz
year:: 2022
venue:: MIT Press (Chapter 1 of *The Entangled Brain*, pp 1-14)
doi::
arxiv::
citation-count:: n/a
summary:: Chapter 1 of Pessoa's book. Sets up the anti-localist / pro-network thesis. Reviews Brodmann mapping, modularity as concept, network science (Watts-Strogatz small-world), and the problem of "filler verbs" in mechanistic explanation.
confidence:: 0.82
lifecycle:: draft
lifecycle-changed:: 2026-05-10
created:: 2026-05-10
updated:: 2026-05-10
sources:: assets/pessoa_2022_the_entangled_brain.pdf (Chapter 1, pp 1-14, full read)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Chapter 1: From One Area at a Time to Networked Systems** — Pessoa 2022, *The Entangled Brain*, pp 1-14. Parent ref: [[wiki/refs/pessoa-2022-entangled-brain]].

- ## TL;DR
  - The chapter that *makes the case* for the entire book. Opens with the 2016 Glasser et al. *Nature* paper that subdivided the human cortex into 360 areas — and uses it to ask whether the very notion of *brain area* is the right unit of analysis.
  - Reviews the localisation-vs-connectionism debate from Brodmann (1908) through Lashley (cortical equipotentiality, 1930s) up to network-science approaches (Watts & Strogatz 1998, Barabási & Albert 1999).
  - Introduces the **modularity-as-decomposability** framing: a continuum from fully decomposable (each subsystem has intrinsic principles) to non-decomposable (interactions defy decomposition). The brain sits much closer to non-decomposable than the field admits.
  - **Centerpiece**: the analysis of *filler verbs* in neuroscience papers. Phrases like "the amygdala *contributes to* / *is involved in* / *modulates* fear processing" stand in for mechanism without specifying it. Pessoa cites the Adolphs & Anderson speedometer analogy: imaging activity in a region tells you *something is correlated with the function*, not how the function is implemented.

- ## Key Arguments

  - ### The Brodmann inheritance and its unspoken assumption
    - Brodmann's 1908 cytoarchitectonic map (~50 areas per hemisphere) became the de facto standard for a century. The 2016 Glasser et al. update (180 areas per hemisphere) is more refined but inherits the same assumption: *brain tissue is meaningfully partitioned into spatially delimited areas, each anatomically and functionally meaningful*.
    - Pessoa's challenge: the assumption is so deeply baked in that the question "*should* we partition the brain this way?" is rarely asked. The success of the partition strategy is partly self-fulfilling — once you commit to areas, you find areas.

  - ### What is a "brain area" anyway?
    - The amygdala is "*one* region" or "12 regions" depending on the criteria. Subcortical regions have multiple subdivisions; cortical boundaries are fuzzy. The question "what counts as an area?" is *far from straightforward*.
    - For the cortex: layering, cell density, cytoarchitectonics, myelination patterns, connectivity, functional response profiles all give different answers. There is no canonical partition.

  - ### How modular is the brain? "Not much at all"
    - **Modularity = degree of interdependence.** Decomposable system → high modularity (each subsystem operates by its own intrinsic principles). Non-decomposable → low modularity (parts are so interrelated they can't be cleanly separated).
    - **Lashley's cortical equipotentiality** (1930s): cortex functions jointly; lesion deficit ∝ amount of cortex compromised. Empirically too extreme but historically important as the *non-modular* counterargument.
    - **Pessoa's empirical claim**: across decades of evidence, the brain is much closer to non-decomposable than the localist-modular tradition allows.

  - ### Lessons from network science
    - **Watts & Strogatz 1998** "Collective Dynamics of 'Small-World' Networks": many real networks combine local clustering with a few long-range connections, giving short path lengths between any two nodes. Tested on a 200,000-actor co-acting network → average path length of ~4 connections.
    - **Barabási & Albert 1999** scale-free networks. The 1998-1999 papers ignited "network science" — the study of interconnected systems where collective properties dominate.
    - **Application to brains**: human neuroimaging (functional MRI) provides whole-brain measurements that can be analysed with network-science tools. The framework *encourages* shifting from "what does region X do?" to "what are the network-level properties?"
    - Pessoa: the framework's core lesson is conceptual, not just methodological — once you adopt it, individual parts matter less than collective/system-wide properties.

  - ### Neuroscientific explanations: lesion, activity, manipulation
    - Three study types: lesion (naturally occurring or surgical), activity (electrophysiology, fMRI), manipulation (optogenetics, TMS, pharmacology).
    - The summary form for nearly all studies: **"Area or circuit X is involved in behavior Y."** Pessoa argues this is the *symptom of the localist disease*. The form invites — even *demands* — a one-area-one-function reading even when the underlying data don't support it.

  - ### Filler verbs (the bombshell of the chapter)
    - **A list of filler verbs from neuroscience explanations**:
      *Reflects, Involves, Mediates, Modulates, Contributes to, Encodes, Enables, Supports, Determines, Underlies, Reveals, Regulates, Generates, Shapes, Produces, Induces, Ensures, Promotes, Plays a role in, Is associated with*.
    - Each of these "stands in for the processes we presume did the 'real' work." The verb is mechanism-flavoured but specifies no mechanism.
    - **The honest summary** (cited from Genon et al. 2018): "Despite centuries of study of brain–behavior relationships, a clear formalization of the function of many brain regions, accounting for the engagement of the region in different behavioral functions, is lacking."
    - **The speedometer analogy** (Adolphs & Anderson 2018): imaging the amygdala during a fear task is like imaging the speedometer of a moving car — it tells you something is correlated with motion, not how the engine works. *In the absence of further knowledge, fMRI activation provides a marker, not a mechanism.*

  - ### Mechanisms and complexity in biology — the Rube Goldberg standard
    - Standard scientific explanation = *causal narrative*: cause-and-effect chain, A → B → C → outcome. Rube Goldberg machines as the gold standard.
    - **But biological systems frequently have tangled webs of explanatory factors with bidirectional couplings.** Pessoa cites Endler's guppy network (figure 1.4): light → predation → coloration involves multiple interacting feedback loops. *And this is "simple" by biological standards* — Endler's network has only one bidirectional pair.
    - **The reductionist tradition** (Newton via Descartes via Crick): all biology should reduce to physics+chemistry. Pessoa: this is the dominant philosophy of practising scientists, even if biologists nominally object. The book argues it's inadequate for the brain.

- ## Connections to Gabriel's Research

  - ### The structure-function gap, biology side
    - **[[wiki/concepts/modularity]]** — Pessoa Ch1 supplies the *neuroscience-side* argument that structural modularity does not yield clean functional specialisation. The *brain itself* doesn't have separable functional modules; expecting *artificial structurally modular networks* (Ch1 of thesis) to develop them was already against the biological grain.
    - **[[wiki/research/dynamics-specialization]]** — the empirical finding that resource constraints can drive functional specialisation in *artificial* networks is consistent with what Pessoa argues for biological brains: functional specialisation is something selection has to *push for*, not a structural default.

  - ### Filler verbs as a tool for SODC self-critique
    - **[[wiki/research/self-organising-digital-circuits]]** — when describing what the [[wiki/concepts/topology-masked-transformer]] *does*, Pessoa's filler-verb list is a good check. "The TMT *configures* function" is borderline filler. Better: "the TMT applies attention-weighted aggregation over circuit edges to produce an updated LUT logit." The mechanism specifies inputs, computation, outputs.
    - **For the wiki generally**: when a wiki page describes a mechanism using a filler verb, that's often a signal it could be tightened.

  - ### Network science as theoretical foundation for graph-NCAs
    - **[[wiki/concepts/neural-cellular-automata]]** — Pessoa Ch1's brief network-science overview explicitly mentions Watts-Strogatz small-world organisation, which is *also* the framing in [[wiki/refs/pio-lopez-2026-brainca]] (BraiNCA's scale-free hubs). Same theoretical cluster, applied at different levels: BraiNCA imposes the wiring as inductive bias, Pessoa argues the brain *has* this wiring as an empirical fact.

  - ### Phd thesis preface — "modularity got me one last time"
    - **[[wiki/research/phd-thesis]]** — the worry that the modularity narrative is seductive even when the evidence undermines it is *exactly Pessoa's thesis position*. Reading Ch1 in full reinforces why modularity is so hard to escape: every methodological tool, every default vocabulary ("function of region X"), every neuroscience training programme reinforces it.

  - ### Solution degeneracy — connection to non-decomposability
    - **[[wiki/concepts/solution-degeneracy]]** — Pessoa's "non-decomposable system" framing is solution degeneracy seen from the *system level*. If the system is non-decomposable, multiple structural configurations realise the same global function — that's degeneracy. The "interactions matter as much as parts" claim is the structural prerequisite for narrow MR.

  - ### Two-book pairing with Hiesinger
    - **[[wiki/refs/hiesinger-2021-self-assembling-brain]]** — Hiesinger Seminar 2 (algorithmic growth) and Pessoa Ch1 are doing the same conceptual work from different sides. Hiesinger says: the brain isn't engineered, it's grown by an algorithm. Pessoa says: the resulting brain isn't a collection of modules, it's an entangled network. Both arrive at the same place: stop expecting clean functional decomposition.

- ## Memorable Lines

  - "How modular is the brain? Not much at all."
  - "We see that to make a 'network' out of the information they had available, they considered two actors to be 'connected' if they had appeared in a film together."
  - "Imaging activity in the amygdala (or anywhere else in the brain), in the absence of further knowledge, tells us nothing about the causal mechanism and only provides a 'marker' that may be correlated with an emotion." (Adolphs & Anderson, quoted)
  - "We currently lack an understanding of most brain science phenomena."
  - "The book is as much about what we know about the brain as it is a text to stimulate how we can think about the brain as a highly complex network — indeed entangled — system."

- ## Cited By (in this wiki)
  - [[wiki/refs/pessoa-2022-entangled-brain]] — parent
