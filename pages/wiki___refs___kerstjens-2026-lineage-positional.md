title:: wiki/refs/kerstjens-2026-lineage-positional
category:: reference
type:: external-ref
tags:: genomic-bottleneck, developmental-encoding, positional-information, lineage, eigengenes
authors:: Kerstjens, Stan; Engert, Florian; Douglas, Rodney J.; Zador, Anthony M.
year:: 2026
venue:: Neuron 114, 1623–1634
doi:: 10.1016/j.neuron.2025.12.043
pubmed:: 41775258
citation-count:: 2
summary:: Positional information inherited via cell lineage as principal eigengenes — co-expression PCA modes that span scales, persist developmentally, are mouse↔zebrafish-conserved, decodable from sparse gene subsets.
confidence:: 0.85
lifecycle:: draft
lifecycle-changed:: 2026-05-15
created:: 2026-05-15
updated:: 2026-05-15
sources:: assets/A-lineage-based-model-of-scalable-positional-information-in-vertebrate-brain-development.pdf (full PDF, 12 pages + references, ~8000 words)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **A lineage-based model of scalable positional information in vertebrate brain development** — Kerstjens, Engert, Douglas & Zador, *Neuron* 114, 1623–1634 (March 2, 2026). DOI:10.1016/j.neuron.2025.12.043. Lead: Stan Kerstjens (CSHL + INI Zurich; Rodney Douglas's old group at INI, now Melika Payvand's home institute). Senior: Anthony M. Zador. Code: github.com/stankerstjens/lineal-positional-information. Data: Zenodo DOI 10.5281/zenodo.18020538.
- ## TL;DR
	- The canonical mechanism for positional information in development is **diffusible morphogens** (Sonic Hedgehog, BMPs, Wnts, FGFs) — chemical gradients that cells decode to know where they are. This breaks down at scale: diffusion gradients become noisy and weak over orders of magnitude, but cortical wiring is reliable across whole brains and conserved from mice to whales.
	- Kerstjens et al. propose a **complementary lineage-based mechanism**: positional information is **inherited from parent to daughter cell at division**, propagated forward without continuous extracellular signalling. Daughter cells stay near parents (spatial constraint) and inherit similar expression vectors (genetic constraint), so the lineage tree implicitly tiles the tissue into a hierarchy of nested contiguous regions.
	- The encoding is not a single morphogen but a **principal eigengene** — the first PC of co-expression across thousands of genes. Eigengene expression forms a stable, brain-wide, dorso-ventral gradient that is **conserved between mouse and zebrafish despite ~400 My evolutionary distance** and despite the underlying gene-loadings changing over development. Eigengene structure is **recursive** — splitting the brain by eigengene sign yields subregions that themselves carry their own eigengene at the next level, producing a multi-scale hierarchy.
	- A single simple cell-division rule reproduces the observed patterns: `c_i = c_{parent} + δ_i, δ_i ~ N(0, σ)` plus an H-tree fractal placement of daughters near parents. This is **the biological mechanism for the chemo-affinity birth + smooth-`φ` machinery** sketched in [[wiki/concepts/developmental-latent-space]]: eigengenes ARE engrams; lineage inheritance IS `g_daughter = g_parent + ε`.
- ## Core Thesis — lineage vs diffusion
	- **The scaling problem.** Diffusion can establish gradients over 50–100 cells. Bigger brains (whales vs mice, hominid cortical expansion) need positional cues over centimetres. Workarounds — adaptive transport, exosomes, cytonemes, multi-cue combinations — still depend on long-range cell-to-cell signalling and inherit the same fundamental constraint.
	- **The lineage alternative.** Positional information is *passed at division*, not transmitted spatially. A cell's expression vector is its parent's plus a small stochastic deviation. Pattern scales with the tissue automatically because the lineage tree grows with the tissue.
	- **Not mutually exclusive.** The authors are careful: lineage *complements* diffusion. Diffusion is well-suited to short-range patterning and local boundaries; lineage handles brain-wide, scale-spanning, evolutionarily conserved structure where diffusion can't reach.
- ## What an eigengene is — and why individual genes don't work
	- **First test (negative result).** Search Allen Brain Atlas (mouse, 1,256 genes, 8 stages E11.5–P56) and Mapzebrain (zebrafish, 290 genes, 6 dpf) for *single* genes whose expression matches an idealised brain-wide stable gradient. **No gene fits both stability and global-pattern criteria.** Known morphogens (Shh, BMPs, Wnts) are restricted to small regions and specific stages, not brain-wide nor temporally persistent.
	- **Eigengene definition.** PCA on the voxel-by-gene expression matrix `X_a` at stage `a`. The principal eigengene `V_a = argmax Var[X_a v]` is the first PC; its expression `U_a = X_a V_a` assigns one value per voxel. The eigengene is a *trend-line direction* across thousands of co-varying genes — a population-coded direction in gene space, not a single-gene signal. ^[extracted]
	- **What the eigengene looks like.** A brain-wide dorso-ventral gradient that partitions the brain into two contiguous regions (positive vs negative). This pattern is **reproduced across all 8 mouse developmental stages** and **across mouse↔zebrafish** despite vast methodological and evolutionary distance.
	- **The cross-stage projection trick.** They cannot point-by-point register voxels across developmental stages (the embryo grows). Instead they compute `U_A^B = X_A V_B` — project stage-A expression onto stage-B's eigengene loadings — and find R² > 0.9 between `U_A^B` and `U_A` across all 8×8 stage pairs. *The expression pattern is conserved even though the gene-level loadings change between stages.* The eigengene reads out the same spatial structure from a moving target. ^[extracted]
	- **Eigengenes vs morphogens, encoding-level.** Morphogen-based codes pin position to a single chemical's concentration (or a small handful in combination). Eigengene-based codes pin position to a *distributed combinatorial code over thousands of genes*. This is **population coding** as it appears in systems neuroscience (the authors' explicit analogy): no single neuron / gene is necessary; the code is robust to noise and perturbations.
- ## Decoding — cells could read position from sparse gene subsets
	- The paper anticipates a sceptical question: even if eigengenes pattern the brain, no real cell can perform brain-wide PCA. Could a cell reconstruct eigengene expression from a small subset of sensed genes?
	- **Random gene subsets work.** Estimate `_k V_A = argmax Var[_k X_A v]` from `k` randomly selected genes, project to a later stage, compare to ground-truth eigengene. Result: **k = 50 randomly chosen genes give R² > 0.5; k = 200 approaches 1.0**. Critically, this holds across *disjoint* random subsets — different cells can decode the same eigengene from different genes. ^[extracted]
	- **Degeneracy is structural.** Eigengene information is broadly distributed; cells could sense any of many partial readouts and recover the same position. This is **engineering degeneracy** in [[wiki/refs/edelman-2001-degeneracy-complexity]]'s sense, mapped onto the developmental code. ^[claude-synth]
	- **Gene ontology of high-loading genes.** Extracellular space, growth cone, and extracellular matrix genes are over-represented among high-eigengene-loading genes — *consistent with* the readout being implemented via cell-surface / receptor machinery, though the authors don't claim a specific mechanism. ^[inferred]
- ## The lineage model — minimal generative rule
	- **Two constraints** suffice to reproduce the observed eigengene structure:
		1. **Genetic similarity to parent.** `c_i = c_{i/2} + δ_i, δ_i ~ N(0, σ)`. Daughter inherits parent's gene-expression vector plus a small random Gaussian perturbation. Most genes do not change significantly per division.
		2. **Spatial proximity to siblings.** Progenitors alternate vertical and horizontal divisions, placing daughters at short distance from parent. The result is an **H-tree fractal** placement: cells closely related in lineage sit close together in physical space.
	- **Simulation result.** Run forward 14 generations from a single cell with 1,000 expressed genes. The simulated tissue's principal eigengene partitions space into two contiguous halves — exactly the qualitative pattern in mouse and zebrafish. Eigengene patterns projected across simulated stages remain stable (matching the experimental cross-stage R² > 0.9 finding).
	- **The neighborhood (morphogen) baseline.** As a control, simulate the alternative: a random expression grid blurred by a fixed-radius kernel (the diffusion analogue). With a kernel covering >½ the tissue, the principal eigengene of the blurred grid does partition the tissue — *at one snapshot*. But **the interaction radius must scale with tissue size** to preserve the global pattern over development. The lineage model is **scale-free by construction** (the tree grows with the tissue); the morphogen model needs unphysical reach to match it. This is the central mechanistic argument for lineage. ^[extracted]
- ## Multi-scale hierarchy — the structural prediction
	- **Recursive eigengene decomposition.** Split the brain by the principal eigengene's sign (red vs blue voxels) → re-run PCA on each subset → get a sub-eigengene → split again → repeat until every leaf is a single voxel. This yields a *binary tree of nested contiguous regions*, each level patterned by its own eigengene.
	- **Contiguity metric.** Define contiguity = (size of largest connected component) / (total voxels in region). 1 = fully contiguous; 0 = scattered. The lineage model predicts high contiguity at every level; the neighborhood/morphogen model predicts contiguity collapsing fast as you recurse.
	- **Empirical finding.** Mouse and zebrafish data both show *high contiguity at every level of the recursive decomposition* — eigengenes form **nested contiguous regions all the way down**. The simulated lineage model reproduces this; the simulated morphogen baseline does not.
	- **Implication.** The lineage tree's hierarchical structure is *mirrored* in the eigengene hierarchy. The tissue's spatial organisation is the lineage tree, made explicit through gene expression. ^[extracted]
- ## Discussion (Kerstjens et al.'s own framing)
	- **Eigengenes as positional cues** are stable, scalable, conserved — the three properties diffusion-based mechanisms struggle with simultaneously. They complement (don't replace) morphogen gradients; the two mechanisms operate at different ranges.
	- **The lineage tree as implicit organiser.** Development doesn't need a central command structure ("the army metaphor"). Locally-coupled cells fracture into subunits as they multiply; each subunit inherits a state from its progenitor; recursive splitting builds a scalable hierarchy. *Global positional information emerges naturally from self-replicating cells whose descendants remain spatially and epigenetically related to their ancestors.*
	- **Predictions for evolution and pathology.** Migrating cells / axons that decode eigengenes follow their inherited patterns; expanding regions (hominid cortex) stay consistently patterned and innervated as they scale. Tumours, organoids, embryos should all carry eigengenes as a shared geometric scaffold.
	- **Testing.** Genetic screens — which knock out single genes — are *predicted to mostly fail* at revealing the system, because eigengenes are distributed across thousands of genes with high redundancy. Targeted perturbations of *lineage structure* (e.g., inducing larger or smaller progeny) should automatically generate patterned tissue, even without changes in gene regulation. The right experiments are on the **tree**, not on the **gene list**.
- ## Connections to Gabriel's Research — load-bearing
	- ### Direct biological grounding for [[wiki/concepts/developmental-latent-space]]
		- The new concept page (genesis 2026-05-15) proposed an *engineering* sketch: per-cell engram `g_i` as a position on a learnable manifold; daughter inherits `g_d = g_parent + ε`; smooth `p_i = φ(g_i)` gives chemo-affinity for free.
		- Kerstjens et al. is the **biological version of the same architecture**:
			- *Engrams ≡ eigengenes.* Per-cell continuous codes, high-dimensional, decodable from sparse subsets. Stable patterns across time with changing loadings.
			- *Manifold inheritance ≡ lineage.* `g_d = g_parent + ε` is *literally* `c_i = c_{i/2} + δ_i, δ_i ~ N(0, σ)` (Equation 5 of the paper).
			- *Smooth `φ` ≡ H-tree fractal placement.* Spatial proximity to siblings + inheritance from parent is exactly the smooth-`φ` mechanism that makes nearby cells (in code space) sit nearby (in physical space).
			- *Multi-scale hierarchy* is a **structural prediction** the engineering concept can now test in NCA models: the engram manifold should admit a recursive nested-region partition reproducible from random gene subsets.
		- **This re-grades the developmental-latent-space concept from 0.42 to something like 0.55+** once the connection is wired into the page. Five of the concept's claims (engram = type code; smooth `φ`; lineage-style inheritance; degeneracy of sparse subsets; multi-scale clustering) are now backed by an empirical paper at Neuron/2026. ^[claude-synth]
	- ### Closes the loop on [[wiki/concepts/genomic-bottleneck]] / [[wiki/refs/zador-2019-critique-pure-learning]]
		- Zador is senior author on both this paper and the 2019 *Critique of pure learning*. The 2019 paper *argued* the genome can't store the wire diagram directly and must compress through a "genomic bottleneck". The 2026 paper *shows what the compression looks like in vivo*: not direct rule specification, but **inherited eigengene states propagated by division** — a compact "deviation from parent" code rather than a "rule applied at each cell" code.
		- This is operationally different from [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]]'s compatibility-rule formulation (which optimises rules statically) and from [[wiki/refs/najarro-2023-neural-developmental-programs]]'s NDP (which runs a per-cell rule at every step). Lineage inheritance is a **third axis of operationalising the bottleneck** — *state inheritance* rather than *rule application*. ^[claude-synth]
		- The wiki's genomic-bottleneck concept page should be updated to note this third operationalisation (alongside type-conditioned probabilities, compatibility rules, and per-cell developmental rule). Worth a follow-up pass.
	- ### Parallels with [[wiki/refs/stockl-2021-structure-induces-computational-function]]
		- Stöckl/Maass parameterise connections by `type × distance`. Kerstjens et al. parameterise *position itself* by an eigengene that splits the brain into nested regions. Combine them: in the engram-manifold framing, the "type" *is* the eigengene state, the "distance" *is* physical position on the H-tree, and the connection prior `P(i↔j) = σ(f_θ(g_i, g_j, d_ij))` becomes an **eigengene compatibility × spatial proximity** function. Stöckl provides the connection rule; Kerstjens provides the substrate for the type code. ^[claude-synth]
	- ### Lineage as the "slow timescale" in the engram/active split
		- In [[wiki/projects/growing-networks]] the architecture sketch has engrams updating slowly (structural backbone) and active layer updating fast (computation). Kerstjens et al. shows the biological slow timescale is *cell division* — the engram (eigengene) updates only when a cell divides, by adding a small Gaussian deviation. Between divisions, the engram is constant.
		- This suggests a clean computational analogue: in an NCA, the engram-update operation should be **discretely triggered by cell division** (or replication event), not a continuous slow drift. Daughter inherits, parent persists, the manifold geometry is built once and only re-evaluated at births. ^[claude-synth]
	- ### Implications for [[wiki/concepts/modularity]] structure-function gap
		- The multi-scale nested-region hierarchy is the **deepest structural form of modularity** the wiki has seen described: a recursive binary partition where every level carries its own eigengene. Yet the paper makes no claim that these regions are *functionally* specialised — they are structurally distinct without (necessarily) being functionally distinct.
		- This is the [[wiki/research/dynamics-specialization]] / [[wiki/research/spatial-neuromorphic-priors]] structure-function gap in vivo: modular hierarchy emerges from developmental lineage, but whether each region computes something distinct is a separate question. The gap holds biologically just as it does in artificial systems. ^[claude-synth]
- ## Methods (essentials only — full STAR Methods online)
	- **Data sources.** Allen Brain Institute mouse atlas (1,256 genes × 8 developmental stages E11.5, E13.5, E15.5, E18.5, P4, P14, P28, P56). Mapzebrain zebrafish atlas (290 genes, 6 dpf). 45 homologous genes shared. Voxel-level expression normalised; each mouse voxel = many cells, each zebrafish voxel ≈ single cell.
	- **Eigengene calculation.** PCA on voxel × gene expression matrix at each stage independently; first principal component = principal eigengene. Eigengene loadings are unconstrained — no spatial regularisation, no alignment to known anatomical axes. Spatial structure emerges *from* PCA, not is *imposed on* it.
	- **Cross-stage projection.** `U_A^B = X_A V_B`: apply stage-B's eigengene loadings to stage-A's expression matrix. Squared correlation `Corr[U_A^B, U_A]²` measures whether the pattern is preserved.
	- **Computational controls.** Shuffle expression matrix (random rows/columns) → eigengene shows no spatial structure (R² ≈ 0.05). "Random eigengenes" with random loadings → uncorrelated patterns. Confirms eigengene signal is a feature of underlying data, not a PCA artifact.
	- **Lineage simulation.** Start single cell with 1,000 genes; simulate 14 generations of division with `c_i = c_{parent} + δ_i, δ_i ~ N(0, σ)`; place daughters via H-tree fractal (alternating vertical/horizontal); run eigengene analysis on terminal population.
	- **Hierarchical decomposition.** Recursive: compute eigengene → split by sign → recurse on each half. Contiguity metric on each region quantifies multi-scale structure.
- ## Limitations the authors flag
	- **Datasets cover <10%** of mouse and zebrafish genomes. Could be more eigengenes / additional spatial modes hiding in the unsampled genes.
	- **No ground-truth lineage tree.** Cannot directly verify that observed eigengene hierarchy mirrors the actual cell-division tree — only show consistency.
	- **No spatial registration across developmental stages** (the embryo grows). The cross-stage R² is a projection-based proxy, not point-by-point alignment.
	- **Lineage-decoding mechanism is hypothesised, not demonstrated.** The "cells sense 50 random genes and reconstruct position" path is a *possibility argument*, not a measured biological process.
- ## Adjacent work to track
	- **Davidson 2006** *The Regulatory Genome* — invoked as the gene-regulatory-network framing the paper inherits.
	- **Wolpert 1969 / 2016** — original positional-information conjecture (cells decode their `x,y,z` from molecular cues); this paper is a direct successor offering a complementary mechanism.
	- **Turing 1952** / **Gierer & Meinhardt 1972** — reaction-diffusion morphogen tradition the paper situates itself against.
	- **Crick 1970** "Can molecular gradients wire the brain?" — Goodhill 2016's review of why pure-diffusion models struggle at brain scale; this paper is one of the affirmative answers.
	- **Hubert & Wellik 2023** Hox genes in development — the canonical example of lineage-encoded positional information at a coarser scale.
	- **Mitchell & Cheney 2024** "The genome instantiates a generative model of the organism" — adjacent theoretical frame flagged in [[wiki/refs/guichard-2025-engramnca]]. Eigengene-as-inherited-generative-state is one operationalisation of "the genome instantiates a generative model". ^[claude-synth]
- ## Connections to Wiki
	- [[wiki/concepts/developmental-latent-space]] — direct biological grounding; eigengenes = engrams, lineage inheritance = `g_d = g_parent + ε`, H-tree = smooth `φ`. Highest-relevance connection.
	- [[wiki/concepts/genomic-bottleneck]] — third operationalisation of the bottleneck (state inheritance via division), alongside type-conditioned probabilities and compatibility rules.
	- [[wiki/refs/zador-2019-critique-pure-learning]] — Zador is co-author here too; this is the biological *implementation* of his 2019 framing.
	- [[wiki/refs/barabasi-2023-complex-computation-developmental-priors]] — sister operationalisation of the bottleneck via wiring rules. Different axis (rule application) from lineage (state inheritance).
	- [[wiki/refs/stockl-2021-structure-induces-computational-function]] — Stöckl/Maass type×distance becomes engrim-compat × distance when type=eigengene.
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — NDP runs a per-cell rule; this paper *inherits* a per-cell state. Different developmental encoding strategy.
	- [[wiki/refs/guichard-2025-engramnca]] — engram private channels propagated by GenePropCA. Kerstjens et al. is the in-vivo case where propagation IS cell division; GenePropCA is the NCA-engineering analogue.
	- [[wiki/refs/hiesinger-2021-self-assembling-brain]] — algorithmic-growth-from-genome; lineage-inherited eigengenes are an instance of Hiesinger's "no shortcut" thesis (the developmental algorithm runs at every division).
	- [[wiki/refs/edelman-2001-degeneracy-complexity]] — eigengene decodable from any random subset = degeneracy realised in the developmental code.
	- [[wiki/refs/aguera-y-arcas-2025-functional-perspective]] — "genome instantiates generative model" theme; eigengene-as-inherited-state is one mechanism by which the genome's generative process runs.
	- [[wiki/concepts/modularity]] — multi-scale nested-region hierarchy is a biological version of the structure-function gap (modular hierarchy without necessary functional specialisation).
	- [[wiki/projects/growing-networks]] — biological motivation for the engram/active layer split + slow/fast timescale separation; lineage events are the discrete trigger for slow engram updates.
- ## Open Questions / To Follow Up
	- **What's the temporal grain of the engram update in our NCA model?** Continuous slow drift (current sketch) or discrete-at-cell-division (this paper's biology)? The latter is more parsimonious and matches the data — worth a Decisions log entry in [[wiki/projects/growing-networks]].
	- **Hierarchical vs flat engram manifold.** Kerstjens et al. predicts the manifold should admit a recursive binary partition (multi-scale eigengene hierarchy). Should `φ` be regularised to produce such structure, or should it emerge from the training pressure?
	- **Distributed code over thousands of "genes" in engram-NCAs.** The Guichard et al. EngramNCA uses small gene-channel dimensions (3-bit one-hot for primitives). Kerstjens et al. uses 1,256 genes with the *first PC* doing the heavy lifting. The right engram dimensionality for our model is probably **larger than EngramNCA's 3-bit codes, smaller than 1,256, and the load-bearing thing is the first few PCs not individual channels**. Worth flagging in the developmental-latent-space tensions section.
	- **Read STAR Methods.** Some implementation details (eigengene similarity metric variants, contiguity threshold sensitivity, sigma in the lineage simulation) are in the online STAR Methods and worth a follow-up if the engineering analogue is being built.
- ## Cited By (in this wiki)
	- [[wiki/concepts/developmental-latent-space]]
	- [[wiki/concepts/genomic-bottleneck]] (pending update — third operationalisation)
	- [[wiki/projects/growing-networks]] (pending update — links to Decisions log on engram update timescale)
