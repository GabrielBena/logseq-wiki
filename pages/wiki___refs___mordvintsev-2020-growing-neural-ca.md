title:: wiki/refs/mordvintsev-2020-growing-neural-ca
category:: reference
type:: external-ref
tags:: nca, morphogenesis, self-organisation, distill
authors:: Mordvintsev, Alexander; Randazzo, Ettore; Niklasson, Eyvind; Levin, Michael
year:: 2020
venue:: Distill
doi:: 10.23915/DISTILL.00023
citation-count:: 263
summary:: Foundational NCA paper — trains a neural CA to grow and maintain textures from a single seed cell using local update rules and gradient descent. Introduced the NCA paradigm for morphogenesis.
confidence:: 0.42
lifecycle:: draft
lifecycle-changed:: 2026-05-08
created:: 2026-05-08
updated:: 2026-05-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Growing Neural Cellular Automata** — Mordvintsev, Randazzo, Niklasson & Levin (2020), Distill.
  - [[wiki/concepts/neural-cellular-automata]] — this paper introduced the NCA paradigm.

- ## Abstract (extracted)
  - No abstract available from Semantic Scholar (Distill interactive article). See https://distill.pub/2020/growing-ca/

- ## Key Ideas
  - Local update rule is a small MLP; all cells share weights and update in parallel. ^[inferred]
  - Training via gradient descent from target pattern — "grow from a seed" objective. ^[inferred]
  - Demonstrates robustness to damage: perturbed cells can regenerate the target pattern. ^[inferred]
  - Introduced the key ideas of perception (sobel filters), state channels, and stochastic updates. ^[inferred]

- ## Connections to Wiki
  - [[wiki/concepts/neural-cellular-automata]] — this paper defined the NCA paradigm.
  - [[wiki/research/universal-nca]] — UNCA extends this toward universal computation.
  - [[wiki/research/self-organising-digital-circuits]] — SODC applies the same NCA paradigm to Boolean circuits.

- ## Open Questions / To Read
  - Full paper content at https://distill.pub/2020/growing-ca/ — worth reading for implementation details.
  - `ingest-mode:: abstract` — upgrade with `/paper-ingest full` if deeper content is needed.

- ## Cited By (in this wiki)
  - [[wiki/research/self-organising-digital-circuits]]
  - [[wiki/research/universal-nca]]
  - [[wiki/concepts/neural-cellular-automata]]
