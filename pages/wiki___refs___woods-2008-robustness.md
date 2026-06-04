title:: wiki/refs/woods-2008-robustness
category:: reference
type:: external-ref
tags:: robustness, fault-tolerance, fpga, self-healing, self-repair, evolvable-hardware, reconfiguration, hardware
authors:: Woods, Roger; Lightbody, Gaye
year:: 2008
venue:: Robust Intelligent Systems (ed. A. Schuster), Springer-Verlag London — book chapter
doi:: 10.1007/978-1-84800-261-6_1
summary:: Survey chapter on robustness in digital hardware — fault taxonomy (open/short/latch-up/SEU) and the robustness toolkit (redundancy/TMR, diversity, granularity, recovery, self-healing & self-repair). Its self-repair rationale frames FPGA partial-reconfiguration and self-rewiring evolvable systems as the route to self-healing hardware.
confidence:: 0.62
lifecycle:: draft
lifecycle-changed:: 2026-06-04
created:: 2026-05-08
updated:: 2026-06-04
sources:: wiki/_archives/_raw/978-1-84800-261-6_1.pdf, pp.1-21 (self-healing section deep-read)
wiki-generated:: true
ingest-mode:: full

- **Robustness in Digital Hardware** — Roger Woods & Gaye Lightbody (2008), Ch.1 of *Robust Intelligent Systems* (ed. A. Schuster), Springer-Verlag London. doi:10.1007/978-1-84800-261-6_1.
	- Resolves the former `woods_robustness_2008` stub cited from [[wiki/research/self-organising-digital-circuits]]. Full-ingested focused on §1.4 (Robustness Approaches), esp. self-healing / self-repair.

- ## Abstract (extracted)
	- The growth in electronics has probably been the equivalent of the Industrial Revolution in the past century in terms of how much it has transformed our daily lives… Despite this reliance, there is still a danger that at some stage devices will fail within the equipment's lifetime. The purpose of this chapter is to look at the factors causing failure and address possible measures to improve robustness in digital hardware technology and specifically chip technology, giving a long-term forecast that will not reassure the reader!

- ## Chapter map
	- **1.1 Introduction** — silicon scaling, Moore's law, the *design-productivity gap* (58% complexity growth vs 21% productivity), system-on-chip.
	- **1.2 Digital Hardware Technologies** — ASIC / DSPμ / microprocessor / **FPGA** / ASSP comparison; Makimoto's wave (standardization ↔ customization).
	- **1.3 Testing & Verifying** — fault taxonomy: open circuit, short circuit, latch-up, **single-event upsets (SEU)**; static vs dynamic faults.
	- **1.4 Robustness Approaches** — *the focus of this ingest* (see below).
	- **1.5 Summary** — robustness as engineering "luxury" today, but process-variation unreliability may make self-healing a *required* step ("a horrendous nightmare… signalling an end to Moore's Law?").

- ## §1.4 Robustness Approaches — key ideas (focus section)
	- Robustness is decomposed into: **redundancy, diversity, granularity, recovery, self-healing, self-repair** (the authors' load-bearing set). ^[inferred]
	- **Redundancy / TMR.** Triple-Mode Redundancy (logic tripled + majority vote) protects against SEUs in safety-critical use; design-for-test (scan path, BIST) costs ~10% silicon as a pure-test overhead. FPGAs supply redundancy "for free" from unused logic resources. ^[inferred]
	- **Recovery, self-healing, self-repair (§1.4.4).** The *programmable* nature of FPGAs is a low-risk route to robustness: reconfigurability is an engineering safety net that allows change during *and after* the design cycle; taken to the extreme, circuits that **self-repair / self-heal** (Gokhale 2006; Andraka & Brady 2002; Samudrala 2004). ^[inferred]
	- **The self-repair rationale (§1.4.4.2).** FCCMs (FPGA Custom Computing Machines) = FPGA + microprocessor holding reconfiguration data; reconfiguration is **full** (device offline for ms) or **partial** (rewire part while the rest runs — split the app into sequential stages, à la Sezer et al. 1998). The "real panacea" is a system where **the designer doesn't write the programming and the hardware reconfigures itself** — i.e. **evolvable systems** (Stoica et al. 2001), an active research area exploiting FPGA reconfigurability. ^[inferred]
	- **The engineer's objection.** "Laden with trouble": *how can you be sure the system reconfigured correctly?* Is there an ideal specification, or must the user accept varying quality of operation? ^[inferred] — this is the same worry Gabriel raised on [[wiki/concepts/fpga]] ("how do we get the host out of the loop?", "you still need inputs").

- ## Connections to Wiki
	- [[wiki/concepts/fpga]] — Woods's self-repair rationale (SRAM reconfig, full vs partial reconfiguration, FCCMs) is the 2008 antecedent of this page's reconfiguration model.
	- [[wiki/refs/whitley-2021-fpga-evolvable-hardware]] — Whitley *resurrects* exactly the evolvable-FPGA tradition Woods points at (Stoica 2001, Thompson lineage); read as the modern follow-up.
	- [[wiki/projects/growing-computation]] — "the hardware reconfigures itself" via partial-reconfig is precisely the project's self-organising-hardware vision; Woods names both the appeal and the verification problem.
	- [[wiki/concepts/substrate-rule-co-location]] — self-healing-via-reconfiguration is the robustness payoff of the Level-1/2 differentiation story.
	- [[wiki/research/self-organising-digital-circuits]] — original citing page (robustness of trained boolean circuits).

- ## Open Questions / To Read
	- §1.1–1.3 (silicon scaling, fault taxonomy) and §1.4.1–1.4.3 (redundancy/diversity/granularity) were skimmed, not deep-read — upgrade if the fault taxonomy becomes load-bearing.
	- Cited evolvable-HW thread to chase: Stoica et al. 2001 (reconfigurable VLSI for evolvable hardware), Sezer et al. 1998 (fast partial reconfig for FCCMs), Andraka & Brady 2002 (SRAM-FPGA config-upset detection). ^[wiki-gap]

- ## Cited By (in this wiki)
	- [[wiki/research/self-organising-digital-circuits]]
