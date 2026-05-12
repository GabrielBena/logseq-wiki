title:: wiki/refs/najarro-2023-neural-developmental-programs
category:: reference
type:: external-ref
tags:: nca, self-organisation, developmental-encoding, neuroevolution, graph-neural-networks
authors:: Najarro, Elias; Sudhakaran, Shyam; Risi, Sebastian
year:: 2023
venue:: ALIFE 2023 (The 2023 Conference on Artificial Life)
doi::
arxiv:: 2307.08197
citation-count:: 23
summary:: Neural Developmental Program (NDP) — a small NN that runs at every node of a graph, taking node embeddings and deciding (a) whether to replicate and (b) edge weights. Grows policy networks from a single seed via local message passing alone. Direct structural-plasticity counterpart to SODC's functional configuration.
confidence:: 0.78
lifecycle:: draft
lifecycle-changed:: 2026-05-09
created:: 2026-05-09
updated:: 2026-05-09
sources:: arXiv:2307.08197 (full PDF, 6486 words)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Towards Self-Assembling Artificial Neural Networks through Neural Developmental Programs** — Najarro, Sudhakaran & Risi (IT University of Copenhagen), ALIFE 2023, arXiv:2307.08197. Code: https://github.com/enajx/NDP. Funded by GoodAI + ERC "GROW-AI" (GA 101045094).

- ## TL;DR
  - **Neural Developmental Program (NDP)**: a small neural network that runs in every node of a target graph. It takes node embeddings as input and decides (a) which nodes should *replicate* (grow new nodes) and (b) what *edge weight* each new connection should have.
  - Starting from a single seed node, the NDP *grows* a functional policy network entirely through **local message passing** — there is no global controller, the same network is replicated in every cell (DNA-like).
  - Two instantiations: **evolutionary** (trained with CMA-ES) and **differentiable** (trained with PPO / behavioural cloning / supervised cross-entropy).
  - Tasks: XOR, CartPole (solved), LunarLander (≈solved), HalfCheetah (offline RL), MNIST (91% test acc on 8×8 images), and target topology growth (small-world coefficients σ ≈ 1.27, ω ≈ 0).
  - **Conceptual claim**: a step toward neural networks that grow rather than are designed. The NDP is the genotype; the policy network is the phenotype; the genotype-phenotype map is *developmental* (unfolds over time via local rules) rather than indirect-but-instantaneous (CPPN/HyperNEAT/Hypernetworks).

- ## Core Architecture

  - ### Components (all are small MLPs, identical per node — the "DNA" metaphor)
    1. **Graph Convolution / Graph CA**: aggregates neighbour embeddings into each node's updated state. The propagation step uses the *network diameter* (D) for message-passing depth in the evolutionary version, a fixed number for the differentiable version.
    2. **Replication MLP** (R): per-node binary decision — should this node grow a new neighbour? In the differentiable version, replication is treated as a probability sampled per step.
    3. **Weight Prediction MLP** (W): for each edge, takes the concatenated source/destination embeddings and outputs the edge weight. Skipped if the target network is unweighted.
    4. **Optional pruning**: edges below a threshold P are removed, allowing networks to *retract* connections.

  - ### Per-cell state representation
    - Each node has an **n-dimensional latent embedding** ("cell state").
    - Differentiable version: first element = bias, second = activation, rest = hidden state for development. *Function-relevant fields are baked into the embedding.*
    - Evolutionary version: full embedding is treated as a black-box latent — more flexible, less interpretable.

  - ### Genomic bottleneck framing (Zador 2019)
    - 100 trillion human cortical synapses encoded by ~30k active genes. NDP is the AI version of that compression.
    - A 14-parameter NDP grows a 4-node, 7-edge XOR solver. A 162-parameter NDP grows a 10-node, 33-edge CartPole solver (reward 500 ± 0). An 868-parameter NDP grows a 16-node LunarLander solver.
    - The NDP can be *larger* than the policy network it grows when the task is small. The bottleneck is meaningful only at scale.

  - ### Two seeding regimes
    - **Single-node seed** (evolutionary version): start from a literal one-node graph, grow everything.
    - **Pre-wired I/O seed** (differentiable version): start with input nodes fully connected to output nodes, then grow hidden layers in between. Found to train better with backprop.

- ## Experimental Results

  - **XOR**: solved with 14-parameter NDP → 4-node 7-edge graph. Sanity check.
  - **CartPole**: 162-parameter NDP grows a 10-node 33-edge policy that scores 500 ± 0 over 100 rollouts (task solved). 4 growth cycles from single seed to final architecture.
  - **LunarLander (continuous)**: 868-parameter NDP grows 16 nodes, 78 edges. Mean reward 116 ± 124 over 100 rollouts — *not* quite solving (task threshold = 200), high variance from terrain stochasticity.
  - **MNIST (8×8)**: differentiable NDP scales to ~106 nodes after 64 growth steps. 91% test accuracy. Demonstrates supervised-learning regime.
  - **HalfCheetah (offline RL/BC)**: NDP grows 56-node policy, mean reward 29 — below the BC baseline of 43.1, but functional.
  - **Small-world topology growth**: NDP optimised against σ ≈ 1.27, ω ≈ 0 directly (no policy task) → grows graphs satisfying small-world criteria.
  - **Growth-step ablation**: more growth ≠ better. Performance plateaus and sometimes degrades past the optimal network size — *learning when to stop growing is a key open problem.*

- ## Theoretical Framing

  - Positions NDP as the *missing developmental piece* in neural network design:
    - **Direct encodings** (standard deep learning): every connection trained directly. Wasteful, unscalable, unbiological.
    - **Indirect encodings** (HyperNEAT, CPPN, Hypernetworks): genotype smaller than phenotype, but produced *atemporally* — no growth, no developmental unfolding.
    - **Developmental encodings** (NDP and lineage): genotype unfolds *over time* through local rules. Adds a growth-process dimension that indirect encodings abstract away.
  - Cites Hiesinger 2018 + [[wiki/refs/hiesinger-2021-self-assembling-brain]] as the biological touchstone — the brain wires itself up through local self-organisation, not by reading out a pre-specified blueprint. Hiesinger's *algorithmic information vs endpoint information* dichotomy ([[wiki/refs/hiesinger-2021-seminar2-algorithmic-growth]]) is the philosophical foundation NDP operationalises.
  - **Critical absence**: the current NDP is *activity-independent* — it grows the same network regardless of input experience. Authors flag activity-dependent / reward-modulated growth as the central future-work axis.

- ## Connections to Gabriel's Research — this paper "links to all of it"

  - ### Direct sibling to SODC (the structural half of the grand vision)
    - **[[wiki/research/self-organising-digital-circuits]]** is *NCA-as-optimizer* on a **fixed topology**: the cellular state IS the function being computed (LUT logits), and the topology-masked Transformer configures function while leaving structure alone.
    - **NDP** is *NCA-as-grower* with **mutable topology**: the cellular state encodes *whether to replicate* and *what edge weights to use*, and the topology itself is the output.
    - **Together they cover both halves of the [[wiki/research/phd-thesis]] grand vision**: SODC supplies the local meta-optimization rule on a fixed substrate; NDP supplies the local growth rule that produces the substrate. The Discussion's proposed unification — "a single shared NCA rule governing both growth and learning" — is the operational synthesis of NDP + SODC. ^[inferred]
    - Architectural compatibility: both use **graph message passing with a per-cell shared neural network**. NDP uses GraphConv + MLPs; SODC uses [[wiki/concepts/topology-masked-transformer]]. The TMT architecture is a richer instantiation of what NDP's GraphConv layer does — promoting NDP's growth rule to attention-based message passing is a natural next step. ^[inferred]
    - **Open challenge SODC explicitly flags** ("structural plasticity: NCA currently steers functional states; making it also rewire topology remains the central open challenge") — NDP is the proof-of-concept that this is feasible.

  - ### Direct lineage from UNCA / graph-NCA
    - **[[wiki/research/universal-nca]]** (Ch3) extends NCA to *graph* NCA over arbitrary topologies — both UNCA and NDP cite [[wiki/refs/grattarola-2021-learning-graph-ca]] as the precursor.
    - UNCA introduces mutable/immutable state separation (immutable = "hardware", mutable = "computation"). NDP could be read as the *generative* version: there is no pre-specified hardware; the immutable substrate is *grown*, and what's mutable is the developmental decision history. ^[inferred]
    - The Najarro et al. 2022 paper *HyperNCA* (cited here) is the immediate precursor — uses NCA to grow a 3D pattern then maps it to a policy weight matrix. NDP simplifies by having NCA operate directly on the policy graph itself.

  - ### Functionalism connection — narrow MR with developmental dynamics
    - **[[wiki/concepts/functionalism]]** — NDP exemplifies *narrow* multiple realizability with two layers: (a) the same NDP rule grows different networks across runs (stochastic narrow MR over phenotype), and (b) within a single grown network, the topology has degeneracy w.r.t. the task it solves.
    - **[[wiki/concepts/solution-degeneracy]]** — the small-world topology experiment is a clean narrow-MR demonstration: the NDP can grow many distinct graphs, all satisfying σ ≈ 1.27. The set of valid networks is the degenerate basin; the NDP is a sampler over that basin. ^[inferred]
    - **[[wiki/refs/edelman-2001-degeneracy-complexity]]** — direct parallel: degenerate gene networks produce robust phenotypes; NDPs produce degenerate phenotype distributions from a compact genotype. The genomic-bottleneck framing in NDP is essentially Zador's restatement of why degeneracy is selected for.

  - ### NCA Trilogy + 5th angle
    - **[[wiki/concepts/neural-cellular-automata]]** — the NCA Trilogy (Mordvintsev → UNCA → SODC → BraiNCA) gains a fifth angle here: **NCA-as-developer** (NDP). The trajectory is:
      - Mordvintsev (image NCA): NCA as pattern-former
      - Ch3/UNCA: NCA as computer (mutable/immutable state)
      - Ch4/SODC: NCA as optimizer (configures function on fixed topology)
      - BraiNCA: NCA as brain-economy substrate (attention + scale-free wiring)
      - **NDP: NCA as developer (grows the substrate itself)**
      - Each angle adds a new degree of freedom. The thesis grand vision = all five composed into a single rule. ^[inferred]

  - ### Spatial / neuromorphic priors connection
    - **[[wiki/research/spatial-neuromorphic-priors]]** (Ch2) imposes spatial wiring-cost regularisation on a *fixed-size* network. NDP imposes the *developmental* version: networks grow only as much as the genotype's growth-rule encodes.
    - The small-world experiment in NDP is the developmental analogue of Ch2's emergent topology under DEEP-R rewiring with distance penalty. ^[inferred]
    - The genomic-bottleneck framing is *also* the wiring-economy framing from a different angle: economy of representation (genotype size) rather than economy of physical wire (Ch2's distance penalty).

- ## Limitations the Authors Acknowledge

  - **No activity-dependent growth** — growth is independent of the inputs the agent receives. Biological development is activity-modulated; NDPs are not yet. (The 2024 follow-up Najarro et al. "Evolving Self-Assembling Neural Networks: From Spontaneous Activity to Experience-Dependent Learning", arXiv:2406.09787, addresses this — worth tracking.)
  - **Knowing when to stop growing** — performance often degrades past optimal size. No principled mechanism yet.
  - **Genome > phenotype on small tasks** — bottleneck argument bites only at scale.
  - **No comparison against gradient-trained equivalents at matched parameter counts** — performance is "competitive but not SOTA".
  - **Differentiable version is feedforward-only** — limits the architectural space substantially.

- ## Why This Paper Slipped Through the Cracks Until Now

  - It's an ALIFE 2023 conference paper, not in any of the major ML venues — easy to miss without an explicit ALIFE / artificial-life literature scan.
  - Risi's group is prolific but cite-distant from Mordvintsev's Distill thread; the connection runs through Grattarola's graph-CA work, which the wiki *does* track ([[wiki/refs/grattarola-2021-learning-graph-ca]]).
  - It belongs squarely in the developmental-encoding / neural-growth subgenre, which has been under-represented in the wiki's lit landscape until this ingest.

- ## Successors and Adjacent Work

  - **[[wiki/refs/plantec-2024-lifelong-ndp]]** — Lifelong NDP (LNDP, Plantec et al. ALIFE 2024, arXiv:2406.09787). The direct sequel from the same Risi lab. Adds structural plasticity (synaptogenesis + pruning), activity- and reward-dependent dynamics throughout the agent's lifetime, and spontaneous-activity pre-experience development. **Closes the activity-dependent gap explicitly flagged as a limitation in this paper.** Deep-ingested 2026-05-09.
  - **[[wiki/refs/hiesinger-2021-self-assembling-brain]]** *The Self-Assembling Brain* (Princeton UP 2021) — deep-ingested 2026-05-10 as 4 pages (parent + Seminars 2, 8, 9). The book-length treatment of biological self-assembly that grounds this whole research thread.
  - **Zador 2019** "A critique of pure learning" (Nature Comms) — the genomic-bottleneck paper. Foundational for the developmental-encoding case. Potential ref stub if the bottleneck thread grows.
  - **HyperNCA** (Najarro et al. 2022) — direct precursor to NDP. Could be added as a stub.
  - **EDANN** (Zhang & Yoder 2024, arXiv:2407.10359) — adjacent literature from a different lineage (Miller's CGP-based developmental ANNs with extended activity dependence). Not a direct NDP follow-up, but cites NDP as closely related and addresses the same activity-dependent question via different machinery.

- ## Cited By (in this wiki)
  - [[wiki/concepts/neural-cellular-automata]]
  - [[wiki/research/self-organising-digital-circuits]]
  - [[wiki/research/phd-thesis]]
  - [[wiki/research/universal-nca]]
  - [[wiki/concepts/self-organisation]]
