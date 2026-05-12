title:: wiki/refs/plantec-2024-lifelong-ndp
category:: reference
type:: external-ref
tags:: nca, developmental-encoding, structural-plasticity, lifelong-learning, neuroevolution
authors:: Plantec, Erwan; Pedersen, Joachim Winther; Montero, Milton L.; Nisioti, Eleni; Risi, Sebastian
year:: 2024
venue:: ALIFE 2024 (The 2024 Conference on Artificial Life)
doi::
arxiv:: 2406.09787
citation-count:: 6
summary:: Lifelong Neural Developmental Program (LNDP) — extends NDP with synaptogenesis, pruning, and spontaneous-activity-driven pre-experience development. Per-cell Graph Transformer + GRU; activity- and reward-dependent structural plasticity throughout the agent's lifetime.
confidence:: 0.78
lifecycle:: draft
lifecycle-changed:: 2026-05-09
created:: 2026-05-09
updated:: 2026-05-09
sources:: arXiv:2406.09787 (full PDF, 6674 words)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Evolving Self-Assembling Neural Networks: From Spontaneous Activity to Experience-Dependent Learning** — Plantec, Pedersen, Montero, Nisioti & Risi (IT University of Copenhagen), ALIFE 2024, arXiv:2406.09787. Code: https://github.com/erwanplantec/LNDP. ERC "GROW-AI" funded.

- ## TL;DR
  - **Lifelong NDP (LNDP)** = Neural Developmental Program ([[wiki/refs/najarro-2023-neural-developmental-programs]]) extended along three axes: (1) **structural plasticity** — synaptogenesis (add edges) + pruning (remove edges) at every step; (2) **activity- and reward-dependent dynamics** — both edges and nodes update based on local activity *and* the global reward signal; (3) **spontaneous-activity (SA) pre-experience phase** — a learnable Ornstein-Uhlenbeck stochastic process drives input neurons before any environmental contact, enabling pre-environmental development.
  - Architecture: Graph Transformer (per-cell shared) updates node embeddings; GRUs update node states and edge states; MLPs handle synaptogenesis/pruning probabilities. The full model is optimised by CMA-ES on RL tasks.
  - Demonstrates that **structural plasticity is decisively useful** in (a) fast-adaptation regimes (CartPole, where models without SP fail completely) and (b) non-stationary environments (foraging task with switching reward).
  - **Spontaneous activity gives innate skills** — agents trained with SA can solve CartPole in the *first* episode without any environmental feedback. Synergies appear between SA-driven development and lifetime learning.
  - **The activity-dependent piece NDP was missing** — exactly the future-work axis flagged in the 2023 NDP paper.

- ## Architecture (LNDP components)

  - ### Graph state representation
    - Network at time t = directed graph G^t with N nodes; tuple ⟨A^t, I, O, h^t, e^t, v^t, w^t⟩ where A^t is the adjacency matrix, I/O are input/output neurons (fixed), h^t are node states, e^t are edge states, v^t are activations, w^t are edge weights.
    - Per-edge state e_ij is masked to zero where A_ij = 0.

  - ### Node model (Graph Transformer + GRU)
    - GT layer takes node activations v^t, node states h^t, structural features (in/out/total degree, one-hot for input/hidden/output role), and edge features (forward/backward/self-loop bits).
    - GT output feeds a per-cell GRU that produces h^{t+1}. **Importantly, GT was chosen over plain GraphConv because it prevents node-state collapse** — a recurrent NDP failure mode where all nodes drift to the same state (Pedersen et al. 2024 SFNN).

  - ### Edge model (synapse GRU)
    - Per-edge state e_ij^{t+1} = GRU(e_ij^t, [h_i, h_j, r]) — concatenates pre/post-synaptic node states and the last reward.
    - Weight is read out as the first element of the edge state: w_ij = e_ij,0.
    - This enables **Hebbian-like activity-dependent rules** to emerge if the GRU learns to use the activity component.

  - ### Structural plasticity (synaptogenesis + pruning)
    - Per-pair synaptogenesis probability: P(A_ij ← 1) = f^+_θ(h_i, h_j) — MLP with sigmoid output.
    - Per-edge pruning probability: P(A_ij ← 0) = f^-_θ(e_ij) — also MLP+sigmoid.
    - These can fire at every step → networks can rewire continuously throughout the agent's lifetime, not just during a separate developmental phase.

  - ### Spontaneous activity (the pre-experience trick)
    - Before the environmental phase, input nodes are driven by a learnable Ornstein-Uhlenbeck process: o_SA^{t+1} = o_SA^t + α(μ - o_SA^t) + W^t with W^t ~ N(0, Σ). Mean μ, covariance Σ, time constants α are *all learnable*.
    - The same node/edge dynamics run during SA as during the environmental phase — no separate "developmental machinery". This is the key elegance: one rule for both pre- and post-experience.

  - ### Initial network sampling
    - Initial connectivity is sampled per-edge with probability ~ N_[0,1](μ_conn, σ_conn). The model is tested at μ_conn ∈ {0, 0.5, 1.0} (empty / sparse / fully connected) and σ_conn ∈ {0, 0.1}.
    - Empty-init (μ_conn = 0) tests the *grow-from-nothing* regime; fully-connected tests the *prune-from-everywhere* regime.

- ## Experimental Findings

  - ### CartPole (fast adaptation)
    - **Models without structural plasticity completely fail.** Models with SP find well-performing solutions even at empty initialisation.
    - SP models reach higher rewards in the *first* episode (innate skill) and continue improving across episodes (lifetime learning).
    - Models with SA train ~25× faster on innate skills (≤2000 generations for first-episode performance vs 50,000 generations without SA).
    - Synergy: lifetime learning + SA together produce stronger episode-to-episode improvement than either alone.

  - ### Foraging (non-stationary reward)
    - 5-cell 1D grid with food location switching probability p_switch = 0.5 between resets. Agent only sees its current cell.
    - SP models reach higher *average* population fitness than non-SP models — both reach similar max fitness (max is noisy / lucky).
    - Found dynamics: agent goes to last-rewarded side, switches if food not found. The switch is implemented either via weight changes OR via *new excitatory connections* to the new best output — direct evidence of structural plasticity playing a functional role in adaptation.

  - ### Acrobot, Pendulum
    - Acrobot: no significant SP/non-SP difference except at fully-connected init where non-SP is slightly better.
    - Pendulum (continuous, hardest): solutions found *only* by SP models with empty init and σ_conn = 0.1. Failed runs converge to producing empty networks — a degenerate attractor in the optimisation landscape.

  - ### Critical periods
    - Networks display short critical periods during which most structural changes happen, after which behaviour stabilises.
    - In some failed runs, abnormal *bifurcations* during the critical period caused failure — a developmental analogue of biological critical-period sensitivity.
    - Average network densities at end of training: CartPole 0.79, Foraging 0.72, Acrobot 0.69, Pendulum 0.24 (low because many failed runs converged to empty networks).

- ## Theoretical Framing

  - **EPANNs lineage**: Evolved Plastic Artificial Neural Networks (Soltoggio, Stanley & Risi 2018) is the umbrella programme. LNDP sits at the intersection of EPANNs and developmental encodings.
  - **Structural plasticity as architectural prior** (Bhattasali et al. 2022; Caroni et al. 2012; May 2011): the paper explicitly motivates SP from neuroscience evidence that the *topology* of biological networks changes with experience, not just synaptic weights.
  - **Spontaneous activity in biology**: cited heavily — Luhmann et al. 2016, Leighton & Lohmann 2016, Kirkby et al. 2013. SA is a developmental neuroscience phenomenon that hasn't been well-explored in ANNs (Raghavan & Thomson 2019 is the only prior work the authors point to).
  - **Open challenges flagged**:
    - Scaling to higher-dimensional environments — current optimisation is hard because of long horizons and tight coupling between wiring rules and synaptic plasticity.
    - Better evolutionary methods — novelty search, quality-diversity, intrinsically motivated optimisation.
    - Better priors on the LNDP output space — drawing from developmental neuroscience plasticity rules (e.g. Lynn et al. 2024 Hebbian heavy-tailed connectivity; **Achterberg et al. 2023** — already in this wiki at [[wiki/refs/achterberg-2023-sernns]]).

- ## Connections to Gabriel's Research

  - ### Direct extension of NDP (closes the activity-dependent gap)
    - **[[wiki/refs/najarro-2023-neural-developmental-programs]]** — LNDP is the direct sequel. NDP grew a network in a pre-environmental phase that was then frozen; LNDP keeps the developmental rule active throughout the agent's lifetime, adds reward-modulation, and adds SA-driven pre-experience development. **The "no activity-dependent growth" limitation explicitly flagged in the NDP page is what LNDP fixes.**
    - The mechanism is now closer to the Discussion's grand vision in [[wiki/research/phd-thesis]]: a single local rule governs growth + learning + adaptation. NDP did growth-only; LNDP does growth + learning. The remaining gap is *integration with task-specific function configuration* — which is what SODC supplies on a fixed topology.

  - ### NDP + LNDP + SODC = the unified rule (closer than ever)
    - **[[wiki/research/self-organising-digital-circuits]]** configures function on a fixed topology via the [[wiki/concepts/topology-masked-transformer]]. LNDP grows topology with activity-dependent rewiring + lifetime weight updates. **The composition NDP/LNDP + SODC** is now an extremely close operationalisation of the [[wiki/research/phd-thesis]] grand vision — only the integration step remains, where the same shared rule produces both the wiring decisions of LNDP and the LUT-configuration decisions of SODC. ^[inferred]
    - LNDP uses Graph Transformer over a graph representation; SODC uses topology-masked Transformer. **Both converge on attention-over-graph as the right per-cell primitive** — same finding as BraiNCA ([[wiki/refs/pio-lopez-2026-brainca]]). Three independent groups now arrive at this design choice. ^[inferred]
    - LNDP's node-state-collapse problem (and the GT-vs-GraphConv fix) is a *direct architectural lesson* for any unified extension of SODC into the structural-plasticity regime — straight GraphConv on a learned-developmental task is fragile in this lineage. ^[inferred]

  - ### Achterberg connection — Ch2's spatial priors loop in
    - LNDP's Discussion flags [[wiki/refs/achterberg-2023-sernns]] as a target source of inductive bias on plasticity rules — the Risi group is reading the same wiring-cost / spatially-embedded literature that powers [[wiki/research/spatial-neuromorphic-priors]] (Ch2). Cross-pollination is plausible: a *spatially-embedded LNDP* with wiring-cost regularisation would unify three threads (developmental encoding, lifelong learning, brain-economy spatial priors). ^[inferred]

  - ### Functionalism — narrow MR in the lifelong regime
    - **[[wiki/concepts/functionalism]]** — LNDP exhibits *narrow MR* across multiple axes: (a) different initial topologies (μ_conn ∈ {0, 0.5, 1}) all reach functional networks; (b) reward switches in the foraging task can be implemented via *either* weight changes or *new structural connections* — same function, different implementation, within-substrate. The LNDP's policy genotype (CMA-ES vector) is a much smaller object than its many possible phenotypic graphs.
    - **[[wiki/concepts/solution-degeneracy]]** — the foraging-task adaptation strategy ("two routes to the same updated policy") is degeneracy in action.

  - ### NDP follow-up axes worth tracking
    - **Pedersen et al. 2024 — Structurally Flexible Neural Networks (SFNN)** — same Risi group; another companion paper to LNDP. Cited as the source of the node-state-collapse problem fix. Could be a stub.
    - **Najarro & Risi 2020 — Hebbian meta-learning** — earlier Risi-group work on evolved plasticity rules; predates NDP.
    - **Najarro et al. 2022 — HyperNCA** — already cited from NDP; the immediate precursor that uses NCA to grow weight matrices via 3D pattern.
    - **Sandler et al. 2021** — Meta-Learning Bidirectional Update Rules; notable because Aguera y Arcas is a co-author. Connects this thread to the [[wiki/refs/aguera-y-arcas-2025-functional-perspective]] / functionalism angle. ^[inferred]

- ## Limitations the Authors Acknowledge

  - Performance lags task-specific RL/SOTA architectures — LNDP is a research artifact, not a drop-in replacement.
  - Only tested on simple low-dimensional environments. Scaling to higher dimensions is the main open question.
  - Strong dependencies between wiring rules and synaptic plasticity make the optimisation problem hard — failed Pendulum runs collapse to empty networks.
  - General LNDP framework is intentionally low-bias — future work should add inductive priors from developmental neuroscience.

- ## Theoretical Anchor
  - **[[wiki/refs/hiesinger-2021-self-assembling-brain]]** — Hiesinger Seminar 9 ([[wiki/refs/hiesinger-2021-seminar9-algorithmic-ai]]) *prescribes* exactly the architecture LNDP delivers: continuous developmental algorithm with no separation between development and function, structural plasticity throughout the agent's lifetime, spontaneous-activity pre-experience phase. Reading Hiesinger Seminar 9 alongside this paper makes the design choices feel inevitable rather than arbitrary.

- ## Cited By (in this wiki)
  - [[wiki/refs/najarro-2023-neural-developmental-programs]] — direct predecessor (Najarro et al. 2023)
  - [[wiki/concepts/neural-cellular-automata]]
  - [[wiki/research/self-organising-digital-circuits]]
  - [[wiki/research/phd-thesis]]
