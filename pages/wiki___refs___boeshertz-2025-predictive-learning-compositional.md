title:: wiki/refs/boeshertz-2025-predictive-learning-compositional
category:: reference
type:: external-ref
tags:: predictive-coding, compositional-learning, autoencoder, functional-disentanglement
authors:: Boeshertz, Gauthier; Clopath, Claudia
year:: 2025
venue:: bioRxiv
doi:: 10.1101/2025.09.26.678731
biorxiv:: 2025.09.26.678731
citation-count:: 2
summary:: Stub — Boeshertz & Clopath 2025 bioRxiv preprint on how predictive learning produces compositional representations. Cited in growing-networks brainstorm as motivation for predictive-coding pressure → functional disentanglement. Abstract not available from Semantic Scholar.
confidence:: 0.30
lifecycle:: stub
lifecycle-changed:: 2026-05-14
created:: 2026-05-14
updated:: 2026-05-14
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: needs-fetch

- **Predictive learning enables compositional representations** — Boeshertz & Clopath (2025), bioRxiv preprint. DOI:10.1101/2025.09.26.678731. 2 citations.
	- [[wiki/projects/growing-networks]] — cited in the seed brainstorm as the recent Clopath-lab finding motivating the "predictive coding pressure" thread in the constraint set.
- ## Status
	- Stub. Abstract not available via Semantic Scholar; preprint is fresh (Sep 2025) so indexing is incomplete.
	- TODO: full-text read via `/paper-ingest full DOI:10.1101/2025.09.26.678731`. The preprint is presumably open on bioRxiv.
- ## Reported framing (from growing-networks brainstorm) ^[author]
	- When training an autoencoder vs a *predictive* autoencoder (predicting T+1 vs reconstructing T) on a visual task with clearly different modules (shape, color, position), the **predictive variant becomes much more functionally disentangled**. This is the specific finding the growing-networks proposal cites.
- ## Connections to Wiki
	- [[wiki/projects/growing-networks]] — the constraint set in growing-networks includes "predictive coding pressure" as one of the ingredients for emergent structure; this paper is the cited empirical anchor.
	- [[wiki/concepts/compositional-learning]] — direct relevance: the paper's claim is that predictive learning *causes* compositional representations to emerge.
	- [[wiki/concepts/modularity]] — adjacent: if predictive learning produces *functionally disentangled* modules, this is one of the few mechanisms in the literature that crosses the structure-function gap from the *training-objective* side. ^[inferred]
- ## Cited By (in this wiki)
	- [[wiki/projects/growing-networks]]
- ## Open Questions
	- Does the paper claim disentanglement at the *representation* level or at the *module* level (i.e. neurons cluster by shape/color/position)? Affects the structure-function-gap relevance.
	- Comparison with other functional-disentanglement methods (β-VAE, etc.) — is predictive coding doing something qualitatively different or just better?
	- Is the effect robust to architecture choice, or specific to autoencoder topologies?
