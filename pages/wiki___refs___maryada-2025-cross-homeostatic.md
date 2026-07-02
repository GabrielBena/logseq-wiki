title:: wiki/refs/maryada-2025-cross-homeostatic
category:: reference
type:: external-ref
tags:: neuromorphic, plasticity, homeostasis, excitation-inhibition, dynap-se2, device-mismatch, host-institute
authors:: Maryada; Soldado-Magraner, Saray; Sorbaro, Martino; Laje, Rodrigo; Buonomano, Dean; Indiveri, Giacomo
year:: 2025
venue:: Nature Communications
doi:: 10.1038/s41467-025-60697-2
pmid:: 40595529
summary:: Host-institute (Indiveri/INI) cross-homeostatic E/I plasticity autonomously tunes a FIXED spiking net on DYNAP-SE2 to stable inhibition-stabilized dynamics despite analog mismatch — dynamics, not function.
confidence:: 0.70
lifecycle:: draft
lifecycle-changed:: 2026-07-02
created:: 2026-07-02
updated:: 2026-07-02
sources:: api:semanticscholar, api:pubmed, pdf:wiki/_pdfs/maryada-2025-cross-homeostatic.pdf
wiki-generated:: true
ingest-mode:: full

- **Stable recurrent dynamics in heterogeneous neuromorphic computing systems using excitatory and inhibitory plasticity** — Maryada, Soldado-Magraner, Sorbaro, Laje, Buonomano, **Indiveri** (2025), *Nature Communications* (DOI 10.1038/s41467-025-60697-2; bioRxiv 2024). **From the host's own institute (Indiveri, INI Zürich).** The **§4 pre-empt** for [[wiki/deliverables/eth-fellowship-2026]] — the closest-sounding prior art, characterised here precisely so we differentiate honestly. **Full-ingested 2026-07-02** from the OA PDF (`wiki/_pdfs/maryada-2025-cross-homeostatic.pdf`). ^[author]
- ## What it is
	- An on-chip spiking recurrent **E/I network** (200 excitatory "Pyr" / 50 inhibitory "PV", ~10% sparse, **four globally-shared weight classes** w_ee, w_ie, w_ei, w_ii) that autonomously self-tunes to robust, self-sustained recurrent dynamics via a biologically-plausible **cross-homeostatic** E/I plasticity rule. ^[extracted]
	- **Core idea:** balance E and I with a local homeostatic rule so recurrent-excitation positive feedback is held in check by inhibition → an **inhibition-stabilized network (ISN)** regime with **stable fixed-point attractor dynamics**, *without* chip-specific manual tuning, even under large analog mismatch. ^[extracted]
	- **Hardware = DYNAP-SE2** (mixed-signal multi-core neuromorphic chip; 1024 AdEx silicon neurons, DPI synapses, bias-DAC weights; Indiveri group, INI Zürich). *(Note: DYNAP-SE2, not Mosaic — but same host institute.)* ^[extracted]
	- Positioned as both validating a neuroscience homeostasis hypothesis on physical silicon *and* a route to automatic **post-fabrication calibration** of neuromorphic hardware despite chip-to-chip variability. ^[extracted]
- ## Methods
	- **Cross-homeostatic rule:** each weight class is tuned by the *opposite-polarity* population's rate error (e.g. Δw_ee ∝ +α·E·(I_target − I); Δw_ie ∝ −α·I·(E_target − E)). α = 0.05; set-points E_target = 20 Hz, I_target = 40 Hz. "**Cross**" = a neuron's plasticity targets the rate of its *presynaptic partners of the opposite sign*, not its own activity. ^[extracted]
	- Applied at the **population level** (weights shared per class), all four classes tuned in parallel; 400 iterations (each ≈ 1 s of real-time on-chip dynamics); convergence robust across random inits and multiple chips (57 trials). ^[extracted]
	- **Chip-in-the-loop:** DYNAP-SE2 has *no on-chip plasticity*, so spikes stream to a host that computes updates + writes weights back through a coarse/fine bias-DAC, with **stochastic rounding** for the discrete low-resolution weights. ^[extracted]
	- **Mismatch handled implicitly:** the homeostatic feedback drives *measured* population rates to set-points, **absorbing** per-neuron/per-chip heterogeneity (analog CV ~0.2) rather than characterizing or cancelling it. ^[extracted]
- ## Results
	- Reliable convergence to **stable self-sustained fixed-point attractors** at target rates in an **asynchronous-irregular** firing regime (CV² ≈ 0.95, minimal pairwise correlations) — cortical up-state-like, robust across inits/chips. ^[extracted]
	- Reproduces the cortical **"paradoxical effect"** on-chip (exciting the inhibitory PV population *reduces* its firing rate) — a hallmark ISN signature. ^[extracted]
	- **Inhibitory plasticity is necessary** (ablation → "exploding" rates > 300 Hz); excitatory plasticity is desirable but not strictly required. ^[extracted]
	- Supports **multiple coexisting stable memories** (up to 5 E/I sub-networks; up to 10 independently-recalled clusters) with **emergent soft-winner-take-all** dynamics — *without* a hand-crafted WTA motif. ^[extracted]
- ## Relation & contrast to a self-organising compiler (the §4 pre-empt)
	- **Shared spirit:** a local, biologically-inspired plasticity rule autonomously configures analog neuromorphic hardware into a useful regime **despite device mismatch**, on the host institute's own substrate — self-calibration without per-chip manual tuning. This is *why it reads as validation* of the bid's bet, from next door. ^[extracted] ^[inferred]
	- **Dynamics, not function:** it stabilises the *dynamics* of a **fixed, random** net (E/I balance → an ISN dynamical target / rate set-point). It does **not** compile/map an *arbitrary specified computation* onto the substrate; the "target" is dynamical stability, not "compute function F and hold it under drift." ^[extracted] ^[inferred]
	- **Fixed-net + hand-crafted, not compile/grow + meta-learned:** topology is fixed random; only **4 global weight scalars** are tuned — no structure growth, no recruitment, no continual/task learning (one-shot post-fab *calibration*; memories are *manually implanted* by weight-masking). The rule is a **hand-derived fixed homeostatic update** with hand-set targets — *not* a **meta-learned** compiler. **This is exactly the axis our niche differentiates on.** ^[extracted] ^[inferred]
- ## Connections to Wiki
	- [[wiki/deliverables/eth-fellowship-2026]] — the §4 positioning-risk pre-empt (name it; differentiate dynamics-vs-function).
	- [[wiki/projects/self-organising-mosaic-compiler]] — the contrast case: our compiler owns placement/routing/recruitment; this tunes a fixed net's dynamics.
	- [[wiki/refs/payvand-2022-memsorn]] — sibling host-institute self-org-on-hardware (weights vs these dynamics); both "local rule tolerates analog mismatch."
	- [[wiki/refs/marder-2006-variability-homeostasis]] — the homeostasis / multiple-parameter-sets → same-behaviour principle this instantiates in silicon.
	- [[wiki/concepts/substrate-rule-co-location]] · [[wiki/concepts/solution-degeneracy]] — local-rule-on-substrate; robustness-to-variability (here of dynamics, not functional configuration).
- ## Cited By (in this wiki)
	- [[wiki/deliverables/eth-fellowship-2026]]
