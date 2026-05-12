title:: wiki/refs/miotti-2025-differentiable-logic-ca
category:: reference
type:: external-ref
tags:: nca, differentiable-logic-gates, boolean-circuits, cellular-automata
authors:: Miotti, Lorenzo; Niklasson, Eyvind; Randazzo, Ettore; Mordvintsev, Alexander
year:: 2025
venue:: IEEE Symposium on Artificial Life
arxiv:: 2506.04912
doi:: 10.48550/arXiv.2506.04912
citation-count:: 5
summary:: DiffLogic CA: combines NCA with differentiable logic gate networks; trains discrete update rules end-to-end; first successful application of DLGNs in a recurrent architecture.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Differentiable Logic Cellular Automata: From Game of Life to Pattern Generation** — Miotti, Niklasson, Randazzo & Mordvintsev (2025), IEEE ALIFE.

- ## Abstract (extracted)
  - This paper introduces Differentiable Logic Cellular Automata (DiffLogic CA), a novel combination of Neural Cellular Automata (NCA) and Differentiable Logic Gates Networks (DLGNs). The fundamental computation units of the model are differentiable logic gates, combined into a circuit. During training, the model is fully end-to-end differentiable allowing gradient-based training, and at inference time it operates in a fully discrete state space. This enables learning local update rules for cellular automata while preserving their inherent discrete nature. We demonstrate the versatility of our approach through a series of milestones: (1) fully learning the rules of Conway's Game of Life, (2) generating checkerboard patterns that exhibit resilience to noise and damage, (3) growing a lizard shape, and (4) multi-color pattern generation.

- ## Key Ideas
  - DiffLogic CA = NCA with differentiable logic gate circuits as the update rule. ^[inferred]
  - Fully discrete at inference; train continuously with relaxed logic gates. ^[inferred]
  - First recurrent application of DLGNs — directly adjacent to SODC's approach. ^[inferred]
  - Demonstrates robustness to perturbation in learned cellular automata update rules. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/differentiable-logic-gates]] — directly implements this concept in a CA setting.
  - [[wiki/concepts/neural-cellular-automata]] — extends NCA to discrete logic gate substrates.
  - [[wiki/research/self-organising-digital-circuits]] — very close sibling work: SODC uses NCA to optimise circuits; DiffLogic CA uses circuits as the NCA update rule.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
