title:: wiki/refs/fernando-2017-pathnet
category:: reference
type:: external-ref
tags:: continual-learning, modularity, path-selection, transfer, neuroevolution
authors:: Fernando, Chrisantha; Banarse, Dylan; Blundell, Charles; Zwols, Yori; Ha, David; Rusu, Andrei A.; Pritzel, Alexander; Wierstra, Daan
year:: 2017
venue:: arXiv 1701.08734 (DeepMind)
arxiv:: 1701.08734
citation-count:: 958
summary:: Agents are *paths* through a module net; freeze a task's learned path, then re-evolve later paths reusing it → transfer without forgetting. Path selection is a global tournament GA — a precedent and foil for recruit/freeze/reuse.
confidence:: 0.75
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-08
updated:: 2026-06-08
sources:: arxiv:1701.08734 (full PDF read 2026-06-08)
wiki-generated:: true
ingest-mode:: full

- **PathNet: Evolution Channels Gradient Descent in Super Neural Networks** — Fernando et al. (2017), arXiv:1701.08734 (Google DeepMind). 958 citations. Full PDF read 2026-06-08.
	- A **precedent and foil** for growing-computation's Stage-3 recruit/freeze/reuse — *one inspiration among several*, not a 1:1 map.

- ## Abstract (extracted)
	- For artificial general intelligence (AGI) it would be efficient if multiple users trained the same giant neural network, permitting parameter reuse, without catastrophic forgetting. PathNet is a first step in this direction. It is a neural network algorithm that uses agents embedded in the neural network whose task is to discover which parts of the network to re-use for new tasks. Agents are pathways (views) through the network which determine the subset of parameters that are used and updated by the forwards and backwards passes of the backpropagation algorithm. During learning, a tournament selection genetic algorithm is used to select pathways through the neural network for replication and mutation. Pathway fitness is the performance of that pathway measured according to a cost function. We demonstrate successful transfer learning; fixing the parameters along a path learned on task A and re-evolving a new population of paths for task B, allows task B to be learned faster than it could be learned from scratch or after fine-tuning… Positive transfer was demonstrated for binary MNIST, CIFAR, and SVHN supervised tasks, and a set of Atari and Labyrinth reinforcement learning tasks…

- ## Architecture
	- A **modular** deep net: `L` layers, each with `M` modules; **each module is itself a small NN** (a Conv2D block or linear+ReLU). The Atari net: `L=4`, `M=10`, 3 conv layers (8 kernels/module, kernel sizes 8/4/3) + 1 linear layer (50 units/module).
	- A **pathway** = a genotype: an `N×L` integer matrix naming the **≤ N active modules per layer** (typically `N = 3–4`). Within a layer the active modules' outputs are **summed** (a ReduceSum) before feeding the next layer's active modules.
	- The `N`-cap is load-bearing: *"otherwise evolution would simply grow the pathway to include the whole network"* (more params = easier to fit). The final readout layer is **task-specific and unshared** (in A3C, a per-task value + policy head).
	- The slogan: **evolution decides *which subset of parameters* gets trained; gradient descent (backprop) trains them.** Evolution channels GD — it only chooses *where* GD applies.

- ## Pathway evolution — a tournament GA
	- `P` genotypes initialised randomly (e.g. `P=64`).
	- **Serial (supervised) — binary tournament (`B=2`, the microbial GA):** pick a random genotype, train its path by SGD for `T` epochs; fitness = classification accuracy over that window. Pick a second, train for `T`. The **loser is overwritten by a copy of the winner**, then **mutated** (each gene flips with prob ~`1/(N·L)`, adding an integer in `[−2,2]`; a *local neighbourhood* gives spatial locality of function).
	- **Parallel (A3C / RL):** all 64 genotypes run in parallel, one per worker; each worker updates **only its path's modules**. Fitness = return over `T` episodes, written to a shared array; asynchronous tournament against `B` random workers.
	- **The selection signal is global and external:** a path is scored by *actually training/running it* and reading its task performance — a population-level fitness tournament, not a learned local decision.

- ## Transfer paradigm (the continual-learning move)
	- Train task A to threshold → **fix the best pathway** (its module params frozen forever). **Reinitialise *all* params not on that path**, then evolve a fresh population for task B. Paths for B re-use parts of A's frozen optimal path → transfer without forgetting.
	- **Detail that matters:** *"without reinitialization, transfer performance did not exceed that of fine-tuning."* The reinit of off-path capacity is what makes the frozen path a useful scaffold. (Contrast growing-computation, which wants to *preserve* dormant-but-intact paths, not reinit them — see divergences below.)
	- In A3C the frozen path stays *active in the forward pass* for task B but is not updated by the backward pass — resembling Progressive Neural Networks, but with the columns *evolved* rather than hand-wired.

- ## Results (orientation)
	- **Binary MNIST:** PathNet 167 generations-to-solution vs fine-tuning 229 vs independent 195 (speedup 1.18). Early layers converge fast (commit), final layer keeps exploring.
	- **CIFAR/SVHN:** learned *second*, accuracies rise (cSVHN 25.5→35.7%, CIFAR 35.3→39.8%) — positive transfer.
	- **Atari:** fine-tuning speedup ≈ **1.00** (no faster than scratch); **PathNet ≈ 1.33**. Labyrinth: 1.26 (with a Net2Net-style *module-duplication* operator that copies globally-useful modules into other slots).
	- **Overlap is not correlated with speedup (Fig 4):** PathNet *discovers how much overlap to use* depending on whether the tasks benefit — it modulates reuse rather than forcing it.

- ## Interpretations + the authors' own "make it learned" pointer
	- Framed as **evolutionary dropout** (evolved "thinned networks") and, by analogy, the **basal ganglia** gating which cortical subsets are active/trainable under prefrontal goal signals.
	- Crucially, the authors flag the *learned* successor themselves: *"a population (ensemble) of **soft** gate matrices could be maintained and an RL algorithm permitted to 'mutate' these values… policy-gradient methods may be used to learn the distribution of pathways as a function of long-term returns."* — i.e. replace the discrete global GA with a **learned, differentiable** selection. That gesture is exactly the direction growing-computation wants (local + learned), and the [[wiki/concepts/grow-and-learn]] oracle thread formalises.

- ## Why it's relevant to [[wiki/projects/growing-computation]] (nuanced)
	- **The loose resonance:** a task's path ≈ an active tile configuration; *freezing* a path ≈ a "dormant-but-preserved" state; re-evolving a path that reuses A's path ≈ recruit + reuse. PathNet shows freeze-and-reuse genuinely transfers across supervised *and* RL tasks.
	- **The divergences matter more, and are where the project goes its own way:** (1) PathNet selects paths with a **global tournament GA** by *training each candidate* — growing-computation wants a *local, learned* rule under nearest-neighbour comms (the encoder-ensemble key-matching open question). (2) PathNet **reinitialises** off-path capacity; growing-computation wants to **protect dormant-but-valuable** tiles (its "don't overwrite dormant function" open Q). (3) PathNet's selection signal is an **external fitness oracle** — precisely the kind of global signal [[wiki/concepts/grow-and-learn]] asks whether a local rule could *internalise*. Scaffolding to build past, not a template to match. ^[claude-synth]

- ## Connections to Wiki
	- [[wiki/projects/growing-computation]] — Stage 3 (continual learning by recruit/freeze/reuse); a loose local-and-learned cousin of PathNet's global path-evolution (expect divergence as the project grows).
	- [[wiki/concepts/grow-and-learn]] — PathNet's tournament-GA fitness as a *path-selection oracle*; the authors' soft-gate / policy-gradient successor is the learned/internalised version the oracle thread is about.
	- [[wiki/refs/shanahan-2021-encoders-ensembles-continual]] — sibling continual-learning-by-modularity (frozen encoder + specialising ensemble); both freeze + reuse, different selection mechanism (competitive ensemble vs GA tournament).
	- [[wiki/refs/wortsman-2020-supermasks-superposition]] — both select a *subnetwork/path* per task over a fixed-or-shared net; SupSup masks + infers by entropy, PathNet evolves paths by fitness — different selection, same "configuration not weights" spirit.
	- [[wiki/refs/cook-2025-heterogeneous-experts-pathways]] — "pathways through a module net" recast as a brain-matched Mixture-of-Experts under routing-cost biases; PathNet evolves the path, Cook *routes* it.
	- [[wiki/concepts/substrate-rule-co-location]] — a "path" is the active configuration; freezing = dormant preserved tiles (degenerate substrate).
	- [[NORACL]] — grow-capacity-on-demand cousin; PathNet *selects* within fixed capacity, NORACL *adds* capacity.

- ## Cited By (in this wiki)
	- [[wiki/projects/growing-computation]] — Stage 3 Selected References; `growing-computation-lab-talk` deck Step 3.
	- [[wiki/concepts/grow-and-learn]] — oracle-route examples.
