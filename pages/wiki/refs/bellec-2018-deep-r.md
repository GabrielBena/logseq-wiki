title:: wiki/refs/bellec-2018-deep-r
category:: reference
type:: reference
tags:: deep-r, sparse-networks, dynamic-rewiring, continual-learning
summary:: Deep Rewiring (DEEP-R): trains sparse neural networks by treating connectivity as a stochastic exploration problem. Parameters θ_k control active/dormant state; stochastic noise enables rewiring while maintaining fixed synapse count. Foundation for Spatial DEEP-R in Gabriel's Ch2.
confidence:: 0.55
lifecycle:: stub
ingest-mode:: abstract
created:: 2026-05-08
updated:: 2026-05-08
wiki-generated:: true

- **Title:** Training very deep networks with dynamic stochastic connections
- **Authors:** Bellec, G., Kappel, D., Maass, W., Legenstein, R.
- **Year:** 2018
- **Venue:** ICLR 2018
- **Key idea:** Each connection k has parameter θ_k and fixed sign s_k. Weight w_k = s_k · max(0, θ_k). Active if θ_k > 0. Update: gradient descent + L1 regularisation + stochastic noise. Connectivity budget enforced by reactivating dormant connections when total drops below target.
- **Relevance:** Foundation algorithm extended by [[wiki/research/spatial-neuromorphic-priors]] into Spatial DEEP-R with spatial distance penalties.
