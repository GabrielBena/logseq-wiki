title:: wiki/refs/barabasi-2023-complex-computation-developmental-priors
category:: reference
type:: external-ref
tags:: developmental-priors, neurodevelopment, genomic-bottleneck, neural-evolution, innateness
authors:: Barabási, Dániel L.; Beynon, Taliesin; Katona, Ádám; Perez-Nieves, Nicolas
year:: 2023
venue:: Nature Communications 14:2226
doi:: 10.1038/s41467-023-37980-1
pubmed-central:: PMC10115783
citation-count:: 20
summary:: Genetic neuroEvolution Model (GEM): network weights `W = H(X O X^T)` emerge from cell-identity matrix X (gene expression per neuron) and gene-interaction matrix O. Matches direct-weight ML at fraction of parameters; meta-learns better. Spatial variant primes topographic / convolutional structure.
confidence:: 0.85
lifecycle:: draft
lifecycle-changed:: 2026-05-15
created:: 2026-05-14
updated:: 2026-05-15
sources:: assets/barabasi-2023-developmental-priors.pdf (full PDF, 8 pages, ~5000 words; cached in /tmp during ingest)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Complex computation from developmental priors** — Barabási, Beynon, Katona & Perez-Nieves (2023), *Nature Communications* 14:2226. DOI:10.1038/s41467-023-37980-1. CC-BY (Gold OA). Code: GitHub via Zenodo DOI 10.5281/zenodo.7689897. Affiliations: Harvard (Biophysics), Wolfram Physics Project, Imperial College London, University of York.
- ## TL;DR
	- **Genetic neuroEvolution Model (GEM)**: network weights are *not* free parameters; they are computed by `W = H(X O X^T)` from a *cell-identity matrix* `X ∈ R^{N×G}` (gene expression per neuron, N neurons × G genes) and a *gene-interaction matrix* `O ∈ R^{G×G}` (symmetric compatibility rules). `H` is Heaviside (relaxed to continuous for differentiability).
	- **Optimisation acts on (X, O), not W.** Backprop through the developmental computation updates gene expressions and gene-interaction rules. Weights emerge from the algorithm. This is the engineering operationalisation of [[wiki/refs/zador-2019-critique-pure-learning]]'s genomic-bottleneck argument — the rule is the optimisation target, not the wire diagram.
	- **Matches direct-weight ML at fraction of parameters.** GEM with 9 genes (~50% of SLP parameters) reproduces 93% MNIST. Spatial GEM (S-GEM) reaches 80% at <2% of SLP parameters, 93% at ~10%. ML-S-GEM hits 90% MNIST at 0.1% of MLP parameters. LeNet-5 variant *exceeds* unencoded LeNet on CIFAR-10 at matched parameter count.
	- **Spatial variant induces topographic structure.** S-GEM places neurons on a grid; each gene's expression is a 2D Gaussian `(μ_x, μ_y, σ)`. Spatially close neurons share genes → similar receptors → convolutional-like local connectivity emerges. **This is the engineering analogue of `p_i = φ(g_i)` in [[wiki/concepts/developmental-latent-space]]**: the Gaussian-on-grid is a specific smooth `φ` parameterisation.
	- **Meta-learning regulariser.** On 5-way 1-shot Omniglot with MAML, GEM at 10× and 25× compression matches or beats standard MLP and crucially *doesn't overfit* while MLP does. The developmental encoding selects "simple circuits" that generalise.
- ## Core formulation
	- ### The connectivity formula `W = H(X O X^T)`
		- `X ∈ R^{N×G}` — each row `X_i` is one neuron's gene-expression vector. `X_{ia} = 1` (binary) or ≥0 (continuous) if neuron *i* expresses gene *a*.
		- `O ∈ R^{G×G}` — symmetric matrix of gene-interaction strengths. `O_{ab}` = "how strongly does gene a interact with gene b at synapse formation".
		- `W = H(X O X^T)` — connectivity from pairwise compatibility. Expanded: for neurons *i* and *j*, the connection score is `Σ_{a,b} X_{ia} O_{ab} X_{jb}` — a *bilinear* compatibility of their gene profiles under the interaction matrix. Heaviside thresholds to binary in the original Genetic Connectome Model (GCM, Barabási & Barabási 2020 Neuron); the GEM relaxes to continuous for backprop.
	- ### Parameter scaling
		- Direct ML: `N_i × N_o` weights for an SLP, `Σ N_l × N_{l+1}` for an MLP. Scales with neuron count.
		- GEM: `P = G(N_i + N_o + G)`. Scales with *gene count*; small G → strong compression.
		- S-GEM (spatial): `P = G² + 3G = G(G + 3)`. Parameter count *independent of neuron count* — cell identities are emergent from the spatial-Gaussian gene expressions. This is the strongest compression.
		- ML-S-GEM (multilayer spatial): `P = G² + L × 3G = G(G + 3L)`. Shared O matrix across layers; only spatial gene-expression centroids change per layer.
	- ### What the optimisation does
		- Forward: `X` and `O` initialised randomly. Compute `W = X O X^T` (for SLP; for multilayer, separate `X_l` per layer, shared `O`). Run forward pass. Compute loss.
		- Backward: gradients flow through the `W = X O X^T` computation. Update `X` and `O` (not `W`). Each batch yields a *new* `W`, derived from the updated developmental rules. **The network is "re-grown" at every batch from its developmental rules** — analogous to evolution selecting on phenotypes by varying genotypes.
	- ### S-GEM mechanism (the spatial variant)
		- Neurons placed on a 28×28 grid (matching MNIST input). Each gene has a 2D-Gaussian expression profile `(μ_x, μ_y, σ)` over the grid. A neuron's gene expression `X_i = [g_1(x_i, y_i), …, g_G(x_i, y_i)]` is determined by its grid position.
		- Optimisation updates `(μ_x, μ_y, σ)` per gene + the `O` matrix. The neuron *positions* are fixed; the *gene expression gradients* shift, redrawing which neurons express which genes.
		- Result: gene expression centroids organise to "tile the space" with informative regions. Recovered structure is *similar to* convolutional layers but learnt rather than imposed.
	- ### LeNet variant
		- Convolutional layer = neurons connecting to local patches. GEM-LeNet learns separate kernels per output neuron (no weight sharing). Parameter count balloons (61,706 → 423,038) without compression. S-GEM-LeNet learns spatial gene Gaussians as before; weights for each receptive field derived from spatial-overlap of gene fields.
		- GEM-LeNet at 2× compression: 98.95% MNIST. S-GEM-LeNet on CIFAR-10: **52.5% vs unencoded 50.6% at equivalent parameter count** — the developmental prior is *better*, not just smaller. Hints at the prior being useful for harder tasks.
- ## Key Findings
	- **Representational sufficiency.** Developmental encoding can produce ANNs with state-of-the-art-comparable performance. Not a hack to compress; a genuinely different parameterisation.
	- **Parameter efficiency.** Order-of-magnitude smaller parameter counts at the same accuracy. ML-S-GEM at 0.1% of MLP parameters for 90% MNIST.
	- **Topographic priming.** S-GEM produces gene-expression gradients that "tile" the visual input space — emergent receptive-field-like structure. Similar to but distinct from imposed convolutional weight-sharing.
	- **Meta-learning advantage.** Where MLPs overfit on Omniglot, compressed GEM/S-GEM don't. The bottleneck *regularises* generalisation.
	- **Modularity dynamics are different.** During training, standard ANN modularity rises mid-training and falls during fine-tuning. S-GEM modularity stays roughly stable — the encoding constrains weight variability across training.
- ## Methods (essentials only)
	- **Datasets.** MNIST (digit recognition), Fashion-MNIST, CIFAR-10, Omniglot (1623 character classes, 1200 train / 423 test).
	- **Networks tested.** Single-layer perceptron (SLP, 784→10), MLPs (784→784→784→5), LeNet-5 convolutional.
	- **Comparison baselines.** Direct-trained equivalents at equal/varying parameter counts; *Random Basis* (RB, Li et al. 2018) encoding as a developmental-encoding baseline; standard MLP for Omniglot MAML.
	- **Training.** PyTorch + ADAM. MAML for meta-learning. Custom backprop through the developmental computation (handled automatically by autograd via `W = X O X^T`).
- ## Direct relevance to the developmental-latent-space concept
	- ### Barabási's `W = H(X O X^T)` is the engineering analogue of `P(i↔j) = σ(f_θ(g_i, g_j, d_ij))`
		- The developmental-latent-space concept proposes a differentiable connection prior of the form `σ(f_θ(g_i, g_j, d_ij))`. Barabási's GEM is **exactly this** with `f_θ(g_i, g_j) = g_i^T O g_j` — a bilinear form rather than a generic MLP, plus no spatial term (in vanilla GEM) or spatial term via the Gaussian-on-grid construction (in S-GEM).
		- **The bilinear form is the minimal `f_θ` that respects gene-pair compatibility.** Generalising to a deeper MLP `f_θ(g_i, g_j, d_ij)` is a natural extension once distance becomes an input. ^[claude-synth]
	- ### S-GEM's gene-expression Gaussians ARE `p_i = φ(g_i)` inverted
		- The developmental-latent-space concept proposes `p_i = φ(g_i)`: position derived from engram via a smooth map. S-GEM does the *inverse*: gene expression `X_i` derived from position via Gaussian-on-grid. **The two are equivalent under invertibility of `φ`** — and S-GEM gives a concrete parameterisation: gene `a`'s "position" is `(μ_a, σ_a)`, neurons at position `(x, y)` express gene `a` with weight `g_a(x, y)`. ^[claude-synth]
		- For the engineering work in [[wiki/projects/growing-networks]], S-GEM's parameterisation is **immediately usable**: pick `G` genes, learn `(μ_g, σ_g)` per gene, derive cell identities from position. Differentiable end-to-end; tested at scale; matches CNN performance on CIFAR-10 at equivalent params. Worth being a starting point. ^[claude-synth]
	- ### State-inheritance (Kerstjens) vs rule-application (Barabási) are complementary
		- [[wiki/refs/kerstjens-2026-lineage-positional]] operationalises the genomic bottleneck via **state inheritance** (daughter inherits parent's gene-expression + noise). Barabási operationalises it via **rule application** (`X O X^T` produces W from current expressions). The biological case is both: lineage *generates* `X` (eigengene state) over time; gene interactions *consume* `X` to determine connectivity.
		- For the engineering model: Barabási gives us the static-snapshot connectivity function; Kerstjens gives us the dynamic-update rule for engrams. A unified picture would combine: engrams update slowly via lineage-style `c_i = c_{parent} + δ`; connections derived at each step via Barabási-style `W = σ(X O X^T - λ D)` (with distance penalty). ^[claude-synth]
	- ### "Weights as emergent" matches Hiesinger's composite-instructions
		- [[wiki/refs/hiesinger-2021-seminar6-chemoaffinity-permissiveness]]: synaptic specificity is a property of the cellular level, emergent from composite molecular interactions. Barabási's `W_{ij} = Σ_{a,b} X_{ia} O_{ab} X_{jb}` is *exactly* this composite picture: connection between `i` and `j` is the sum of pairwise gene compatibilities. No single gene is instructive; all contribute. ^[claude-synth]
	- ### Levels-problem awareness in Barabási's framing
		- [[wiki/refs/hiesinger-2021-seminar7-genes-cells-circuits]]: the right level depends on the phenomenon. Barabási operates at the *gene/cell-identity* level for ANN training; the `W` matrix at the synaptic level emerges from this lower-level optimisation. This is the levels problem turned into engineering: optimise at the developmental level, get the synaptic level for free. ^[claude-synth]
- ## Connections (substantive — replaces old abstract-only list)
	- [[wiki/concepts/genomic-bottleneck]] — direct operationalisation; `(X, O)` is the compressed code, `W` is the brain. The bilinear-form `f_θ` is one specific implementation of "rule emits weights".
	- [[wiki/refs/zador-2019-critique-pure-learning]] — framing paper. Barabási provides one of the constructive answers (alongside Kerstjens lineage and NDP per-cell-rule).
	- [[wiki/refs/kerstjens-2026-lineage-positional]] — complementary operationalisation (state inheritance vs rule application). Both anchored on the `X` (gene expression) matrix but with different dynamics. Worth a side-by-side comparison in the developmental-latent-space concept page.
	- [[wiki/refs/stockl-2021-structure-induces-computational-function]] — closely related: type×distance probabilities for connection. Barabási's S-GEM with distance penalty would essentially be Stöckl/Maass made differentiable. The conceptual lineage runs Sperry → Stöckl/Maass → GEM with relaxations.
	- [[wiki/refs/najarro-2023-neural-developmental-programs]] — sister operationalisation (per-cell developmental NN runs at each step). Different mechanism (rules apply iteratively vs once); both compress to the developmental level.
	- [[wiki/refs/plantec-2024-lifelong-ndp]] — LNDP adds activity-dependent plasticity throughout lifetime; Barabási's GEM is activity-independent at deployment (no plasticity beyond the rule update).
	- [[wiki/refs/hiesinger-2021-seminar6-chemoaffinity-permissiveness]] — composite molecular instructions ≅ `W_{ij} = Σ X O X` summation.
	- [[wiki/refs/hiesinger-2021-seminar7-genes-cells-circuits]] — gene-level optimisation produces synaptic-level connectivity via algorithmic growth; the levels problem turned constructive.
	- [[wiki/concepts/developmental-latent-space]] — Barabási's bilinear `f_θ` + S-GEM's Gaussian-on-grid `φ` are immediately-usable engineering instantiations of the concept.
	- [[wiki/concepts/neural-cellular-automata]] — Barabási doesn't use NCA explicitly, but the developmental computation `W = X O X^T` could be unrolled iteratively to produce an NCA-style growth process; flagged as a research direction in the Discussion.
	- [[wiki/projects/growing-networks]] — most direct engineering reference for the structural-side mechanism. Worth a Decisions log entry on whether to start from S-GEM as a baseline.
- ## Limitations / Open Questions
	- **No activity-dependent dynamics.** GEM is rolled out per batch; the `W` is a static snapshot of the developmental rule. No spontaneous-activity-dependent refinement (cf. Tsigankov 2010, Triplett 2011 cited in the paper). [[wiki/refs/plantec-2024-lifelong-ndp]] / [[wiki/refs/guichard-2025-engramnca]] handle this.
	- **G-level scaling.** Performance scales with gene count G; the "compression" claim is meaningful when G << N. For very large networks, even `G²` may be large.
	- **No spatial inhomogeneity.** S-GEM places neurons on a regular grid. Real biological neurons are non-uniformly distributed; the concept page's `p_i = φ(g_i)` allows that, S-GEM doesn't currently.
	- **Bilinear `f_θ` is one parameterisation.** Could be generalised to deeper MLPs that allow non-symmetric and non-additive gene interactions — but the bilinear form is interpretable and seems sufficient for the tested tasks.
- ## Cited By (in this wiki)
	- [[wiki/concepts/genomic-bottleneck]]
	- [[wiki/concepts/developmental-latent-space]]
	- [[wiki/projects/growing-networks]]
	- [[wiki/refs/zador-2019-critique-pure-learning]]
	- [[wiki/refs/kerstjens-2026-lineage-positional]]
