title:: wiki/refs/bena-2025-universal-nca
category:: reference
type:: external-ref
tags:: nca, universal-computation, analog-computing, meta-learning
authors:: Béna, Gabriel; Faldor, Maxence; Goodman, Noah D.; Cully, Antoine
year:: 2025
venue:: GECCO Companion
arxiv:: 2505.13058
doi:: 10.1145/3712255.3734310
citation-count:: 2
summary:: Trains NCAs toward universal computation via mutable/immutable state separation; demonstrates matrix multiplication and MNIST-in-NCA-state emulation.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **A Path to Universal Neural Cellular Automata** — Béna, Faldor, Goodman & Cully (2025), GECCO.
  - This is Gabriel's own paper — the primary reference for [[wiki/research/universal-nca]].

- ## Abstract (extracted)
  - Cellular automata have long been celebrated for their ability to generate complex behaviours from simple, local rules, with well-known discrete models like Conway's Game of Life proven capable of universal computation. Recent advancements have extended cellular automata into continuous domains, raising the question of whether these systems retain the capacity for universal computation. In parallel, neural cellular automata have emerged as a powerful paradigm where rules are learned via gradient descent rather than manually designed. This work explores the potential of neural cellular automata to develop a continuous Universal Cellular Automaton through training by gradient descent. We introduce a cellular automaton model, objective functions and training strategies to guide neural cellular automata toward universal computation in a continuous setting. Our experiments demonstrate the successful training of fundamental computational primitives — such as matrix multiplication and transposition — culminating in the emulation of a neural network solving the MNIST digit classification task directly within the cellular automata state.

- ## Key Ideas
  - Mutable/immutable state separation: some cells hold fixed program weights, others are dynamic activations. ^[inferred]
  - NCA trained to emulate arbitrary computational primitives (matmul, transposition, MNIST classifier). ^[inferred]
  - Foundational step toward analog general-purpose computers via continuous cellular dynamics. ^[inferred]

- ## Connections to Wiki
  - [[wiki/research/universal-nca]] — this IS the paper.
  - [[wiki/concepts/neural-cellular-automata]] — extends NCA paradigm to universal computation.
  - [[wiki/research/self-organising-digital-circuits]] — predecessor work; SODC extends the universal-computation theme to discrete Boolean circuits.
  - [[wiki/code/maxencefaldor-universal-nca]] — the implementation.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
  - [[wiki/research/universal-nca]]
