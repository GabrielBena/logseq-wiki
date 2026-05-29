title:: wiki/refs/raghunathan-2026-noracl-neurogenesis
alias:: NORACL
category:: reference
type:: research-paper
tags:: continual-learning, neurogenesis, growth, plasticity, postdoc-adjacent
authors:: Raghunathan, Karthik; Metzner, Christian; Kriener, Laura; Payvand, Melika
year:: 2026
venue:: arXiv (preprint)
arxiv:: 2604.27031
citation-count:: 0
summary:: NORACL — neurogenesis-inspired continual learning that grows capacity on demand. From a compact net, it adds neurons only when two signals jointly fire: representational saturation (Effective Dimension via SVD) and plasticity saturation (Fisher diagonal); matches/beats oracle-sized baselines with 10–20% fewer params.
confidence:: 0.80
lifecycle:: draft
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-29
sources:: arxiv:2604.27031 (full PDF read 2026-05-29)
wiki-generated:: true
ingest-mode:: full

- **NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning** — Raghunathan, Metzner, Kriener, Payvand (2026), arXiv 2604.27031 (7-page preprint, full read). Institute of Neuroinformatics, UZH & ETH Zurich; Kriener & Payvand shared senior authorship — Gabriel's home lab.

- ## Core argument
  - The **stability–plasticity dilemma has an architectural root**: a finite network has limited representational and plastic resources, but the capacity actually required depends on two *unknown-in-advance* properties of the task stream — **task count** and **task geometry** (how much tasks overlap in feature space).
  - Regularization-based CL (e.g. EWC) preserves past knowledge inside a **fixed** architecture, so it implicitly relies on an **"oracle architecture"** sized for that unknown future. Weakly-related tasks → fixed nets run out of plastic resources; few/overlapping tasks → over-provisioned.
  - NORACL resolves this with **on-demand neuronal growth** from a compact start — biological adult-neurogenesis as the inspiration.

- ## Growth mechanism — when / where / how
  - The mechanism must answer three questions: **when** to grow (is current capacity insufficient?), **where** (which layer is the bottleneck?), **how** (how to initialize new neurons?). NORACL monitors state each epoch and grows only when **two complementary signals jointly cross threshold**:
  - **(1) Representational saturation — *when/where*.** Per layer, the normalized **Effective Dimension (ED)** of activations `H_l` is computed from the cardinality of its singular values (SVD; Maile et al. 2022). High ED ⇒ neurons produce near-orthogonal features ⇒ layer at full representational capacity. Growth triggers when `φ_l > γ·φ̄_l` (current ED exceeds a γ-discounted reference ED measured at the end of the previous task). The γ-discount lets growth start *slightly before* full saturation, leaving margin to act proactively rather than reactively.
  - **(2) Plasticity saturation — *confirmation*.** ED alone can fire spuriously on transient batch effects, so a second signal based on the **Fisher-information diagonal** confirms that existing parameters are *too important for previous tasks to be safely overwritten* (i.e. plasticity is genuinely exhausted, not just noisy).
  - **Combined trigger:** growth at layer `l` only when **both** conditions hold — representational saturation says capacity is needed, plasticity saturation confirms the existing params can't absorb more.
  - **(3) How to grow — function-preserving.** New neurons' fan-in weights are drawn from a **random orthogonal basis** and added so prior behaviour is preserved; they keep full effective learning rate (`η_eff = η`), so fresh capacity is fully plastic for new tasks.

- ## Results
  - Across varying task counts and geometries, NORACL matches or beats **oracle-sized static baselines** while using **10–20% fewer parameters**.
  - **Interpretable growth**: dissimilar tasks predominantly expand *early* feature-extraction layers; tasks sharing features shift growth toward *later* feature-combination layers — the growth pattern is itself a readout of task structure.
  - Analysis explains *why* fixed-capacity nets lose plasticity as tasks accumulate (even with regularization), whereas growth creates fresh capacity. Conclusion: adaptive neurogenesis pushes the stability–plasticity **Pareto frontier**.

- ## Connections to Wiki
  - [[wiki/projects/growing-networks]] — direct cite; provides a concrete, evaluated trigger-based growth mechanism the broader proposal can incorporate.
  - [[wiki/projects/growing-computation]] — closest mechanical neighbour to Stage 3 (continual learning as progressive logical recruitment): grow-on-demand under a saturation signal, only-as-needed, from the same lab. growing-computation is roughly "NORACL on a many-core boolean substrate".
  - [[wiki/refs/najarro-2023-neural-developmental-programs]] — both grow networks, but NDP grows from a developmental rule whereas NORACL grows *reactively* from task-driven saturation signals.
  - [[wiki/concepts/genomic-bottleneck]] — grow-only-as-needed is *post-hoc* capacity compression, complementary to the genomic bottleneck's *a-priori* compression of developmental rules. ^[inferred]

- ## Open Questions / To Read
  - **Are the growth signals learnt or hand-designed?** Resolved by full read: **hand-designed** (ED via SVD + Fisher diagonal), not learnt — so the trigger is generic but not itself meta-optimized.
  - **Pruning / death?** Growth is **additive and function-preserving**; the paper does not introduce neuron death — capacity only grows. A death/pruning mechanism is an open extension (cf. growing-computation's "alive/dead cell colonisation").
  - **Can an NCA / meta-optimizer estimate these signals *locally*?** Gabriel's 2026-05-29 question: ED needs an SVD over a mini-batch and Fisher needs gradient statistics — both are *global* per-layer quantities, not locally available to a cell. Whether a competent NCA could learn to approximate ED/Fisher locally after enough message-passing (and re-derive them at test time) is the open research thread linking NORACL to [[wiki/concepts/neural-cellular-automata]] as Gardener. ^[inferred]
  - Connection to [[wiki/research/spatial-neuromorphic-priors]] — NORACL's grown architectures could be analysed for emergent spatial/modular structure.

- ## Cited By (in this wiki)
  - [[wiki/projects/growing-networks]]
  - [[wiki/projects/growing-computation]]
