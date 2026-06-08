title:: wiki/refs/xilinx-2020-versal-acap-wp505
alias:: Versal ACAP, Xilinx WP505
category:: reference
type:: external-ref
tags:: hardware, fpga, acap, computing-substrate, versal
summary:: Xilinx whitepaper on Versal ACAP — a heterogeneous platform fusing Scalar (CPU), Adaptable (FPGA), and Intelligent (AI/DSP) engines on a hardened NoC; source of the CPU/GPU/FPGA/ACAP taxonomy.
confidence:: 0.55
lifecycle:: draft
lifecycle-changed:: 2026-06-02
created:: 2026-06-02
updated:: 2026-06-02
sources:: Xilinx White Paper WP505 (v1.1.1), 29 Sept 2020; PDF archived at wiki/_archives/_raw/wp505-versal-acap.pdf
authors:: Xilinx, Inc.
year:: 2020
venue:: Xilinx White Paper (WP505 v1.1.1)
url:: https://docs.amd.com/v/u/en-US/wp505-versal-acap
ingest-mode:: abstract
wiki-generated:: true
provenance-extracted:: 0.75
provenance-inferred:: 0.25

- Vendor whitepaper introducing **Versal ACAP** (Adaptive Compute Acceleration Platform), AMD/Xilinx's heterogeneous compute device. Staged into the wiki because Versal is a strong single-chip substrate candidate for [[wiki/projects/growing-computation]] (see [[wiki/concepts/fpga]] §Physical realizability). **Light ingest** — the conceptual introduction + the computing-systems taxonomy are distilled here; the per-engine microarchitecture (AI Engine array, NoC topology, memory hierarchy) is not. ^[wiki-gap: full microarchitecture undistilled — re-ingest from the PDF if Versal becomes a concrete deployment target]
- ## The computing-systems taxonomy
	- The whitepaper's framing motivation: the end of **Dennard scaling** + **Amdahl's law** broke the "one size fits all" CPU scalar model, pushing the industry toward **domain-specific architectures**. It sorts compute substrates into three kinds, then proposes a fourth that fuses them:
	- **Scalar processing (CPUs)** — efficient at complex algorithms with diverse decision trees and broad library support; limited in raw performance scaling.
	- **Vector processing (DSPs, GPUs)** — efficient at a narrower set of parallelizable compute functions; pays latency/efficiency penalties from an inflexible memory hierarchy.
	- **Programmable logic (FPGAs)** — precisely customizable to a particular compute function; best at latency-critical real-time work (e.g. automotive driver-assist) and irregular data structures (e.g. genomic sequencing); the cost is a hard hardware-development flow.
	- **ACAP (Versal)** — combines all three as *Scalar Engines + Adaptable Engines (FPGA fabric) + Intelligent Engines (AI/DSP)* on one die, with a tool flow spanning framework → C → RTL so users build a custom domain-specific architecture (DSA) from the three programmable elements.
	- This four-way split seeds the substrate taxonomy in [[wiki/concepts/computing-substrates]] (created 2026-06-02), which gathers [[wiki/concepts/fpga]], [[wiki/concepts/memristor-crossbar]], and [[wiki/concepts/programmable-matter]] and extends the spine with analog (memristor) and neuromorphic axes.
- ## Why it matters for growing-computation
	- Versal is the closest single-chip "best of both" for the project: it offers **SpiNNaker2-like local cells** (the AI-Engine array of local-memory vector cores), **reconfigurable LUT fabric** (the workload substrate that actually gets grown), **and a hardened NoC** — all on one die. ^[inferred — synthesis from the [[wiki/projects/growing-computation]] 2026-06-01 design session, not the whitepaper]
	- In the locality-spectrum framing (see [[wiki/concepts/fpga]]), Versal's heterogeneity is what lets the regulatory rule (a float MLP) live on DSP/Intelligent-Engine + BRAM islands *beside* the LUT workload it grows, rather than as off-chip "software in hardware". ^[inferred]
- ## Connections
	- [[wiki/concepts/fpga]] — the substrate primer; Versal is its heterogeneous, NoC-bearing endpoint.
	- [[wiki/projects/growing-computation]] — the project for which Versal is the top single-chip substrate candidate.
	- [[wiki/concepts/substrate-rule-co-location]] — Versal's separate-but-co-located engine types map onto the rule-vs-substrate layering.
	- [[wiki/concepts/programmable-matter]] — ACAP as a current commercial approximation of reconfigurable compute matter.
