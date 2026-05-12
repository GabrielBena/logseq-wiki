title:: wiki/refs/dalgaty-2024-mosaic
category:: reference
type:: reference
tags:: neuromorphic, memristor, hardware, mosaic, small-world
summary:: Mosaic neuromorphic chip architecture: memristor-based, comprising Neuron Tiles (dense local connections) and Router Tiles (sparse global communication). Provides the hardware topology used as a spatial prior in Gabriel's Spatial DEEP-R framework.
confidence:: 0.40
lifecycle:: stub
ingest-mode:: abstract
created:: 2026-05-08
updated:: 2026-05-08
wiki-generated:: true

- **Title:** (Mosaic neuromorphic architecture paper)
- **Authors:** Dalgaty, T., et al.
- **Year:** 2024
- **Key idea:** Memristor-based neuromorphic chip with Neuron Tiles (dense local connections) and Router Tiles (sparse global routing). Connection cost = integer hop count between tiles. Enables hardware-compliant training through the Spatial DEEP-R prior: d_eff ∝ 1/P(h) where P(h) is target connection probability at hop distance h.
- **Relevance:** Provides the neuromorphic embedding for [[wiki/research/spatial-neuromorphic-priors]]. The Mosaic prior achieves hardware-compliant small-world topologies while maintaining performance gains.
