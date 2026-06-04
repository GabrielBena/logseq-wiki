title:: wiki/refs/whitley-2021-fpga-evolvable-hardware
category:: reference
type:: external-ref
tags:: fpga, evolvable-hardware, evolutionary-algorithms, bitstream, robustness, hardware
authors:: Whitley, Darrell; Yoder, Jason A.; Carpenter, Nicklas
year:: 2021
venue:: IEEE Symposium on Artificial Life (ALIFE)
doi:: 10.1162/isal_a_00448
citation-count:: 6
summary:: Open-source platform for intrinsic analog evolvable hardware on FPGAs — evolving unclocked-FPGA bitstreams directly (à la Thompson), demonstrating amplitude-maximisation and pulse-oscillation circuits and probing robustness to temperature and across-chip translation.
confidence:: 0.50
lifecycle:: draft
lifecycle-changed:: 2026-06-04
created:: 2026-06-04
updated:: 2026-06-04
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Resurrecting FPGA Intrinsic Analog Evolvable Hardware** — Whitley, Yoder & Carpenter (2021), IEEE Symposium on Artificial Life. doi:10.1162/isal_a_00448.
	- Revives the "intrinsic evolvable hardware" tradition: apply evolutionary algorithms directly to FPGA bitstreams and let analog dynamics emerge on unclocked fabric.

- ## Abstract (extracted)
	- In the spirit of past century evolvable hardware, we explore the application of evolutionary algorithms to field programmable gate arrays and provide an open-source platform for performing intrinsic analog evolvable hardware experiments. We target the reproduction of seminal field experiments that generated complex analog dynamics of unclocked FPGAs which were evolved through genetic manipulation of their binary circuit representation: the bitstream. Further, we demonstrate the intrinsic evolution of two non-trivial analog circuits with intriguing properties: amplitude maximization and pulse oscillation. Lastly, we explore the robustness of evolved circuits to temperature variation and across-chip circuit translation.

- ## Key Ideas
	- Evolution operates on the **binary bitstream** of an *unclocked* FPGA, exploiting intrinsic analog dynamics rather than the clocked digital abstraction. ^[inferred]
	- Reproduces the spirit of Thompson's seminal evolved-FPGA experiments and provides an **open-source platform** for re-running them. ^[inferred]
	- Evolves two non-trivial analog circuits: amplitude maximisation and pulse oscillation. ^[inferred]
	- Probes **robustness** of evolved circuits to temperature variation and across-chip translation — the classic fragility of intrinsic evolution. ^[inferred]

- ## Connections to Wiki
	- [[wiki/concepts/fpga]] — bitstream-level evolution sits opposite the LUT-as-clean-digital-gate view; surfaces the analog/unclocked tension on the very same substrate. ^[inferred]
	- [[wiki/projects/growing-computation]] — an alternative "self-organising hardware" lineage (evolve the bitstream) vs the project's learned-regulatory-rule approach; relevant to the 2026-06-04 hardware-realism arc. ^[inferred]
	- [[wiki/research/self-organising-digital-circuits]] — both target trained/evolved circuits on real FPGA fabric, but SODC stays in the clean digital LUT regime. ^[inferred]

- ## Open Questions / To Read
	- The robustness / temperature findings bear directly on the self-healing-hardware thread (cf. the Woods & Lightbody chapter staged in `wiki/_raw/`). ^[inferred]
	- Related follow-ups surfaced in the same search (not yet ingested): Loyd et al. 2025 "Bitstream Evolution: An Open-Source FPGA Intrinsic Evolvable Hardware Toolkit" (doi:10.1109/ACCESS.2025.3631393) and "Scalable and Accelerated Self-healing Control Circuit Using Evolvable Hardware" (2023, doi:10.1145/3634682). ^[wiki-gap]
	- Abstract-only; full mode would need the closed-access PDF (doi:10.1162/isal_a_00448).

- ## Cited By (in this wiki)
	- (none yet)
