title:: wiki/refs/payvand-2022-memsorn
alias:: MEMSORN
category:: reference
type:: external-ref
tags:: neuromorphic, memristor, rram, self-organisation, plasticity, in-memory-computing, variability-as-feature
authors:: Payvand, Melika; Moro, Filippo; Nomura, K.; Dalgaty, Thomas; Vianello, Elisa; Nishi, Y.; Indiveri, Giacomo
year:: 2022
venue:: Nature Communications
doi:: 10.1038/s41467-022-33476-6
pmid:: 36184665
summary:: The host's (Payvand, first-author) self-organising memristive SNN — Hebbian + homeostatic rules derived from measured RRAM statistics make device variability a feature for sequence learning (+30%).
confidence:: 0.70
lifecycle:: draft
lifecycle-changed:: 2026-07-02
created:: 2026-07-02
updated:: 2026-07-02
sources:: api:semanticscholar, api:pubmed, pdf:wiki/_pdfs/payvand-2022-memsorn.pdf
wiki-generated:: true
ingest-mode:: full

- **Self-organization of an inhomogeneous memristive hardware for sequence learning** — Payvand, Moro, Nomura, Dalgaty, Vianello, Nishi, Indiveri (2022), *Nature Communications* 13:5793 (DOI 10.1038/s41467-022-33476-6). **Melika Payvand is first author.** A demonstration that self-organisation *exploiting* device variability works on real memristive silicon. **Full-ingested 2026-07-02** from the OA PDF. ^[author]
- ## What it is
	- **MEMSORN** (Memristive Self-organizing Spiking Recurrent Neural Network) — a hardware architecture inspired by the SORN model: a recurrent pool of Leaky-Integrate-and-Fire neurons, **80% excitatory (160) / 20% inhibitory (40)**, where excitatory synapses *and* neuron state are held by **HfO₂ 1T-1R RRAM** devices. ^[extracted]
	- **Core idea:** rather than fighting the intrinsic cycle-to-cycle + device-to-device variability of the memristors, the network **self-organizes** via two on-chip plasticity rules — **Hebbian** synaptic + **Homeostatic** neuronal — **derived to match the devices' measured stochastic switching**. ^[extracted]
	- **Device–circuit–algorithm co-design** is explicit: RRAMs set both synapse strength (1T-1R crosspoints) and neuron parameters (gain, time-constant, refractory period, via a hybrid CMOS/RRAM LIF circuit), and the learning rules are shaped to exploit that same physics. ^[extracted]
	- Only excitatory neurons + E→E connections carry the rules; the baseline is a **"static" control** — identical topology, connections set randomly, no plasticity. ^[extracted]
- ## Methods
	- **Devices first:** a 4 kb 1T-1R HfO₂ RRAM array (130 nm CMOS, CEA-Leti) was fabricated + measured. Two statistics anchor the rules: (i) SET probability rises **sigmoidally** with SET voltage (sub-threshold SET is stochastic); (ii) the post-RESET High-Resistance-State is **log-normal**. ^[extracted]
	- **Hebbian = modified SDSP:** on a pre-synaptic spike, if post-synaptic V_mem ≥ V_θ the synapse is potentiated (SET) else depressed (RESET); learning rate 0.01–0.1. ^[extracted]
	- **Homeostatic = Intrinsic Plasticity (IP):** keeps each neuron's rate near **f_T = 50 Hz** (±15 Hz). If off-target, a **stochastic sub-threshold SET** is applied with SET-voltage ∝ rate error (using the measured sigmoid); a device below 50 kΩ is RESET, **re-sampling a fresh HRS** from the log-normal → a new neuron gain/time-constant. ^[extracted]
	- **Variability-as-feature:** the RESET-driven log-normal resampling gives IP a *free stochastic search* over neuron parameters, and device noise on SDSP decorrelates the recurrent attractors — both from RRAM physics, not added pseudo-randomness. ^[extracted]
	- **Task = SORN counting:** predict the next character in shuffled sequences S1 = A B…B C / S2 = D E…E F (middle symbol repeated *n* times) — requires *counting* repetitions via a persistent dynamical state. Two-phase: unsupervised SDSP+IP self-organization, then RRAM states frozen + a **logistic-regression readout**. Main comparison at n = 10. ^[extracted]
- ## Results
	- **n = 10, 1000 random nets:** MEMSORN accuracy **0.756 vs 0.596** static — a **~16% (>15%) absolute gain**; MEMSORN resolves the full repetition sequence, the static net only the first repetitions. ^[extracted]
	- **~4× more "good" networks** (accuracy > 0.8) than static. ^[extracted]
	- **Ablating device variability:** introducing RRAM variability improves sequence-learning accuracy by **~30%** across lengths (best = variability in *both* SDSP and IP); variability also **de-sensitizes** the net to hyper-parameters (esp. learning rate). ^[extracted]
	- **Structure emerges:** better-separated, more cyclic cell-assemblies, ~11% more explained variance in the top PCs. Cost: converges in ~1000 samples ≈ **13 min, ~936 µJ**. ^[extracted]
- ## Why it matters / scope
	- **Variability-as-feature + co-design, proven on silicon:** rules "derived directly from the statistical measurements" of real RRAM turn a manufacturing nuisance (stochastic switching, log-normal spread) into the *search noise* that drives self-organization + hyper-parameter robustness — an existence proof that intrinsic device physics can *be* the learning substrate. **This is the bid's ② "self-org exists, in the small" + ⑥ lab-fit anchor.** ^[extracted]
	- **Materially narrower than compile / remap / grow:** it *tunes a fixed network* (topology + neuron count fixed a priori; never grows/recruits) on one sequence-learning family; it does not compile/map a specified computation, and the readout is a separate supervised regression. ^[inferred]
	- **Device-derived, not meta-learned:** SDSP + IP are hand-designed to match device statistics + a single target rate; self-organization is one-shot unsupervised tuning — no continual/online task adaptation, no *learned* learning rule — the key contrast with a *meta-learned* rule that compiles, remaps, and continually-learns (cf. [[wiki/projects/self-organising-mosaic-compiler]]). ^[inferred]
- ## Connections to Wiki
	- [[wiki/projects/self-organising-mosaic-compiler]] — extends this self-organisation-on-hardware line *toward a compiler*.
	- [[wiki/refs/dalgaty-2024-mosaic]] — same lab / substrate family (Dalgaty, Vianello, Indiveri, Payvand co-authors).
	- [[wiki/refs/maryada-2025-cross-homeostatic]] — sibling host-institute self-org-on-hardware (that one tunes *dynamics*; this one tunes *weights*).
	- [[wiki/concepts/substrate-rule-co-location]] — device–circuit–algorithm co-design; variability-as-feature.
	- [[wiki/concepts/solution-degeneracy]] — variability-as-a-resource rhymes with degeneracy, but MEMSORN uses it as *search noise*, not functional-config basin-hopping.
	- [[wiki/refs/kudithipudi-2025-neuromorphic-at-scale]] — the roadmap's "variability exploited as features … in self-organized dynamical networks" = this line (scalability = open).
- ## Cited By (in this wiki)
	- [[wiki/projects/self-organising-mosaic-compiler]]
