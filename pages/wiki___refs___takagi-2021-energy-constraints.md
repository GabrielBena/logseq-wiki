title:: wiki/refs/takagi-2021-energy-constraints
category:: reference
type:: research-paper
tags:: energy-constraints, brain-networks, wiring-cost, network-formation
summary:: A cost-minimization model coupling activity cost and wiring cost as a simple ratio reproduces characteristic brain-network structure — strong hubs and large clusters — matching real connectomes.
confidence:: 0.45
lifecycle:: draft
lifecycle-changed:: 2026-05-29
created:: 2026-05-29
updated:: 2026-05-29
sources:: DOI:10.1038/s41598-021-91250-y
authors:: Takagi, Kosuke
year:: 2021
venue:: Scientific Reports
doi:: 10.1038/s41598-021-91250-y
ingest-mode:: abstract
wiki-generated:: true

- Takagi (Scientific Reports 2021) shows that a simple **cost-minimization model** can reproduce structures characteristic of real brain networks, arguing energy constraints are central to how neuronal networks organise and form.

- ## Key Ideas
  - The brain is physically embedded in restricted space; both **building connections (wiring cost)** and **maintaining activity (activity cost)** are expensive. Characteristic network structure is read as the imprint of reducing these costs.
  - The cost function is **activity-dependent**, correlating activity cost and wiring cost as a **simple ratio**. Minimizing this ratio strengthens connections especially at **highly activated nodes** and induces formation of **large clusters**.
  - The resulting networks show **statistical similarity to connectome datasets** from various real brains — shared efficient structure maintained at low activity- and wiring-cost.
  - The activity↔wiring coupling is the key move: cost is not wiring length alone but a ratio that ties structure to usage. ^[inferred]

- ## Connections
  - [[wiki/refs/achterberg-2023-sernns]] — spatially-embedded RNNs penalised by a communicability/wiring cost; Takagi gives an activity-coupled cost variant of the same "structure as cost imprint" logic.
  - [[wiki/concepts/modularity]] — the emergent large clusters are a cost-driven route to modular structure.
  - [[wiki/projects/growing-computation]] — operationalises Gabriel's recurring "energy constraints seem to be key" intuition (journal 2026-05-29) for keeping growth from exploding. ^[inferred]

- ## Open Questions
  - How does the activity/wiring ratio translate to a *trainable* regulariser for a growing substrate (vs. a descriptive model of fixed connectomes)? ^[inferred]
  - Full-text upgrade pending — abstract mode only.

- ## Sources
  - DOI:10.1038/s41598-021-91250-y — *Energy constraints on brain network formation*, Scientific Reports 2021 (abstract mode).
