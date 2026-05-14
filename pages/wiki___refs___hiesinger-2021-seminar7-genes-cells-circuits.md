title:: wiki/refs/hiesinger-2021-seminar7-genes-cells-circuits
category:: reference
type:: external-ref
tags:: levels-problem, polygenic-traits, redundancy, hiesinger, multi-level-encoding
authors:: Hiesinger, Peter Robin
year:: 2021
venue:: Princeton University Press — Seminar 7 of *The Self-Assembling Brain* (book pp 217–236)
parent:: [[wiki/refs/hiesinger-2021-self-assembling-brain]]
citation-count:: n/a
summary:: The levels problem: properties at level N+1 cannot be described in terms of level-N components. Polygenic traits, redundancy, sensitized backgrounds, GWAS limits. The right description level depends on phenomenon.
confidence:: 0.85
lifecycle:: draft
lifecycle-changed:: 2026-05-15
created:: 2026-05-15
updated:: 2026-05-15
sources:: assets/hiesinger_2021_the_self-assembling_brain.pdf (Seminar 7, book pp 217–236)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Seminar 7 — From Genes to Cells to Circuits** — book pp 217–236. Parent: [[wiki/refs/hiesinger-2021-self-assembling-brain]].
- ## TL;DR
	- The **levels problem**: properties at one level (cellular self-avoidance, circuit dynamics, behaviour) often *cannot* be described in terms of level-below components (molecular mechanisms, genes). The hierarchy `gene → protein → interaction network → neuronal properties → circuit properties → brain → behaviour` is conceptually clean but operationally misleading — each `→` involves an algorithmic-growth step whose outcome is not derivable from the level below.
	- **No "gene for X"**: behaviours like aggression, alcoholism, sexuality are polygenic + nonadditive + low-penetrance. GWAS finds many SNPs each contributing 0–25%; combined predictability < 1%. The genetic contribution is real but distributed across thousands of SNPs with high context-dependence.
	- **Redundancy vs sensitized background** (Figure 7.3): two factors A and B can compensate for each other (redundancy) or one can lower the threshold so the other becomes critical (sensitization). The same observation (loss of B causes phenotype only in A-mutant background) supports both interpretations; only mechanistic detail distinguishes them.
	- **The right level depends on the phenomenon.** Self-avoidance is a cellular-level rule; alcoholism is an organismic-level trait; gene expression is a molecular-level event. Asking the question at the wrong level (e.g., "what's the alcoholism gene") guarantees underwhelming answers.
	- **A rule is a set of instructions sufficient to predict an autonomous agent's behaviour.** Rules can be written down independently of executing molecules. McCulloch & Pitts described neurons computationally without knowing about ion channels; the right abstraction skips the level below.
- ## Key Arguments
	- ### The levels hierarchy as conceptually clean, operationally treacherous
		- The textbook chain `Gene → protein → protein interaction network → neuronal properties → circuit properties → brain → behaviour` reads as a clean cascade. Each arrow is an algorithmic-growth step where information *unfolds* — it is not a 1-to-1 mapping.
		- A property like neuronal excitability is shaped by ion channels, but also by axon physical properties, ion distributions, membrane composition. *All* of which result from earlier protein-network actions, all of which result from earlier gene expressions. The "gene → behaviour" link goes through layers that each add or transform information.
		- **Key claim**: "Genetic information had to unfold through all these processes to produce neuronal excitability." Genes do not contain the higher-level information directly; they contain the *seed for the algorithmic process* that will produce it.
	- ### Polygenic and nonadditive effects — why GWAS finds nothing definitive
		- 2019 GWAS on ~500k people for sexual orientation: aggregate genetic contribution ~8–25%, but *predictability from genotype < 1%*. No "gay gene".
		- Behavioural traits are typically **polygenic** (many genes contribute) and **nonadditive** (effects depend on combinations — gene A's effect only manifests if B is also mutated, or only in the absence of B, etc.).
		- The thought experiment: "5 SNPs that together cause homosexuality, but rarely co-occur" → many heterosexuals carry 1-4 of them, many homosexuals lack them all. Low individual penetrance, real genetic contribution.
		- More radical: "There may be as many different genomes that determine a specific trait as there are individuals." The trait is *encoded by the genome to a high degree* but **not derivable from the individual genome without running the developmental algorithm**. This is Hiesinger's no-shortcut thesis applied to behaviour.
	- ### Redundancy and sensitized backgrounds (Figure 7.3)
		- Two mutants A and B, neither causing a phenotype alone, but together causing one. Two interpretations:
			- **Genetic redundancy**: A and B have similar functions; either compensates for the loss of the other. Loss of both removes the function entirely.
			- **Sensitized background**: A lowers the threshold for B's contribution to become critical (or vice versa). A and B have *different* functions, but the system tolerates loss of one until the other is also lost.
		- Same observation, different mechanism. Only deeper mechanistic work distinguishes them. The geneticist's "redundancy" label is often premature.
		- The implication for any developmental model: **single-gene perturbations are uninformative**; many decisions are made by composite genetic backgrounds where every component is below-threshold individually but above-threshold collectively.
	- ### Rules at the right level
		- A *rule* is "a set of instructions sufficient to predict the behaviour of a player (autonomous agent)". Self-avoidance of dendrites can be written as: (1) extend filopodia stochastically, (2) retract on contact with own dendrites, (3) stabilise on contact with non-self. This rule is fully described at the cellular level — the molecules executing it (Dscam, protocadherins) can swap without changing the rule.
		- "The molecular stuff is somebody else's problem" — for rule descriptions, the level above the executing mechanism is the right one. The molecules are the *executive power*; the rule is the *abstraction*.
		- McCulloch & Pitts could describe neuronal computation without ion-channel biophysics. This is the operational definition of the "right level": when an abstraction is sufficient for prediction, lower-level detail is *not* needed for that question.
	- ### "How deep do we need to go in simulation?"
		- The OpenWorm question (running through the book): can we simulate *C. elegans* without simulating every molecule? Hiesinger's answer is nuanced — for *function*, no, you probably don't; for *development*, you may need much more detail because the developmental algorithm relies on molecular and cellular specifics.
		- The trap: simulation projects that aim for the right *output* but skip the developmental *process* may miss the structural properties that emerge from the process. Build-then-train ANNs are the AI analogue.
- ## Direct relevance to the developmental-latent-space concept
	- ### The "engram does 5 jobs" question, formalised
		- The [[wiki/concepts/developmental-latent-space]] concept flags as a tension: the per-cell engram does connection prior, budget, niche, lifecycle stability, replication. Seminar 7's levels problem reframes this: **the engram is the per-cell algorithm input; its 5 "jobs" are level-N+1 emergent properties of how the engram interacts with the substrate, not 5 dedicated subspaces of the vector itself**. ^[claude-synth]
		- Concretely: don't decompose the engram into `g = [g_conn, g_budget, g_niche, g_stability, g_replication]`. Instead, let each "job" be a *learned readout function* on the full engram vector — the 5 jobs are different lenses on one composite vector, each lens is a small head over the same code. This is the cellular-level-rule framing applied to engineering: the rule sits in the readout, not the substrate. ^[claude-synth]
	- ### Polygenic engrams + sparse decoding (cross-reference)
		- The eigengene story in [[wiki/refs/kerstjens-2026-lineage-positional]] is *exactly* a polygenic-and-nonadditive code: thousands of genes contribute, none is decisive alone, the eigengene is the trend across many. Seminar 7's "no gay gene" argument is the same shape: no single component is sufficient; the composite is what's informative. **The engram in the developmental-latent-space framing should behave the same way** — distributed across the vector with no privileged channels. ^[claude-synth]
	- ### "No shortcut" applies to the engineering model
		- If the engram-manifold is genuinely a developmental code, the manifold's geometry should *emerge from* the developmental training process, not be designed in. Designing in clusters / a particular `φ` shape is the equivalent of specifying the wiring diagram directly — it short-circuits the algorithmic growth. Engram-manifold geometry should be a *learnt outcome* of running the developmental algorithm under appropriate pressures. ^[claude-synth]
	- ### Implications for ablations
		- Single-channel ablations of the engram are likely uninformative (polygenic/nonadditive). Multi-channel ablations or *background sensitization* (reduce one channel while perturbing another) are the right experimental design. This is a non-obvious methodological commitment for testing the developmental-latent-space hypothesis. ^[claude-synth]
- ## Connections
	- [[wiki/refs/hiesinger-2021-self-assembling-brain]] — parent.
	- [[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]] — algorithmic-information framing; the levels problem is the cross-level cost of algorithmic unfolding.
	- [[wiki/refs/hiesinger-2021-seminar4-local-rules-robustness]] — autonomous-agents at every level is the structural origin of the levels problem.
	- [[wiki/refs/hiesinger-2021-seminar6-chemoaffinity-permissiveness]] — composite instructions at the molecular level give cellular-level specificity; same shape of argument at the molecular↔cellular boundary.
	- [[wiki/refs/hiesinger-2021-seminar8-development-function]] — Seminar 8 takes this into development↔function.
	- [[wiki/refs/kerstjens-2026-lineage-positional]] — eigengenes are polygenic positional codes; concrete biological case of the levels problem (eigengene level vs individual-gene level).
	- [[wiki/concepts/modularity]] — Pessoa's anti-localisation thesis is closely related; many-to-many mappings across levels are the structural reason why modularity-as-blueprint fails.
	- [[wiki/concepts/developmental-latent-space]] — engram = vector at the cellular level; its 5 jobs are level-N+1 readouts.
	- [[wiki/projects/growing-networks]] — the levels-problem-aware engineering response is to keep the engram dense and learn the readouts, not decompose the vector channel-by-channel.
- ## Cited By (in this wiki)
	- [[wiki/concepts/developmental-latent-space]] (pending update — adds polygenic-readout grounding)
	- [[wiki/projects/growing-networks]] (pending update — Decisions log on engram channel discipline)
