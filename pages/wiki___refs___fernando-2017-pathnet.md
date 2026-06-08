title:: wiki/refs/fernando-2017-pathnet
category:: reference
type:: external-ref
tags:: continual-learning, modularity, path-selection, transfer, neuroevolution
authors:: Fernando, Chrisantha; Banarse, Dylan; Blundell, Charles; Zwols, Yori; Ha, David; Rusu, Andrei A.; Pritzel, Alexander; Wierstra, Daan
year:: 2017
venue:: arXiv 1701.08734 (DeepMind)
arxiv:: 1701.08734
citation-count:: 958
summary:: Agents are *pathways* through a giant network that discover which modules to reuse per task; a task's path is frozen and later paths re-evolve around it → transfer without catastrophic forgetting. The closest prior art to growing-computation's recruit/freeze/reuse.
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-08
updated:: 2026-06-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **PathNet: Evolution Channels Gradient Descent in Super Neural Networks** — Fernando et al. (2017), arXiv:1701.08734 (DeepMind). 958 citations.
	- Flagged on the `growing-computation-lab-talk` deck (continual-learning demo) as the closest prior art to recruiting/freezing/reusing tiles.

- ## Abstract (extracted)
	- For artificial general intelligence (AGI) it would be efficient if multiple users trained the same giant neural network, permitting parameter reuse, without catastrophic forgetting. PathNet is a first step in this direction. It is a neural network algorithm that uses agents embedded in the neural network whose task is to discover which parts of the network to re-use for new tasks. Agents are pathways (views) through the network which determine the subset of parameters that are used and updated by the forwards and backwards passes of the backpropogation algorithm. During learning, a tournament selection genetic algorithm is used to select pathways through the neural network for replication and mutation. Pathway fitness is the performance of that pathway measured according to a cost function. We demonstrate successful transfer learning; fixing the parameters along a path learned on task A and re-evolving a new population of paths for task B, allows task B to be learned faster than it could be learned from scratch or after fine-tuning. Paths evolved on task B re-use parts of the optimal path evolved on task A. Positive transfer was demonstrated for binary MNIST, CIFAR, and SVHN supervised learning classification tasks, and a set of Atari and Labyrinth reinforcement learning tasks, suggesting PathNets have general applicability for neural network training. Finally, PathNet also significantly improves the robustness to hyperparameter choices of a parallel asynchronous reinforcement learning algorithm (A3C).

- ## Key Ideas
	- **Agents = pathways** through a large module network; a path picks the *subset* of parameters used/updated for a task. ^[inferred]
	- Paths are selected by a **tournament-selection genetic algorithm** (fitness = the path's task performance). ^[inferred]
	- **Freeze + reuse**: fix the parameters along task-A's learned path, re-evolve paths for task B → B learns faster *and* reuses parts of A's path. Transfer without catastrophic forgetting. ^[inferred]
	- Positive transfer across supervised (MNIST/CIFAR/SVHN) and RL (Atari/Labyrinth); also stabilises A3C against hyperparameters. ^[inferred]
	- *Abstract-mode — upgrade with `/paper-ingest full` for the module-graph + GA details.* ^[inferred]

- ## Why it matters for [[wiki/projects/growing-computation]] (load-bearing)
	- PathNet is the **closest prior art to Stage-3 continual-learning-by-recruiting**: a task's path = an active tile configuration; *freezing* a path = the deck's "dormant-but-preserved" state; a new task *re-evolves a path reusing the old one* = recruit + reuse. ^[claude-synth]
	- The **key difference is the open problem**: PathNet selects paths with a **global tournament GA**; growing-computation wants path-selection by a **local, learned regulatory rule under local-only comms**. So PathNet *is* the mechanism, globally; the "do it locally" gap is exactly the encoder-ensemble key-matching open question in [[wiki/projects/growing-computation]] §Open Questions. ^[claude-synth]

- ## Connections to Wiki
	- [[wiki/projects/growing-computation]] — Stage 3 (continual learning by recruit/freeze/reuse); the local recast of PathNet.
	- [[wiki/refs/shanahan-2021-encoders-ensembles-continual]] — sibling continual-learning-by-modularity (frozen encoder + specialising ensemble); both = reuse + freeze, different selection mechanism.
	- [[wiki/concepts/substrate-rule-co-location]] — a "path" is the active configuration; freezing = dormant preserved tiles (degenerate substrate).
	- [[NORACL]] — grow-capacity-on-demand cousin.

- ## Cited By (in this wiki)
	- `growing-computation-lab-talk` deck — Step 3 (continual learning) + the demo speaker note.
