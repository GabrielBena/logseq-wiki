title:: wiki/refs/wagner-2005-ch20-man-made-systems
category:: reference
type:: external-ref
tags:: robustness, evolvable-hardware, fpga, distributed-robustness, evolved-circuits
authors:: Wagner, Andreas
year:: 2005
venue:: Robustness and Evolvability in Living Systems, Ch20 (Princeton UP)
summary:: The same robustness principles — distributed robustness and evolved robustness — appear in engineered systems; shown on telecom networks and on field-programmable transistor arrays whose fault-tolerance evolves under fault pressure.
confidence:: 0.7
lifecycle:: draft
lifecycle-changed:: 2026-06-05
created:: 2026-06-05
updated:: 2026-06-05
sources:: wiki/_pdfs/wagner-2005-robustness-evolvability.pdf (Ch20, pp. 310–320)
wiki-generated:: true
ingest-mode:: full

- **Ch20 — Robustness in Man-made Systems** (parent: [[wiki/refs/wagner-2005-robustness-evolvability]]). The most directly relevant chapter for [[wiki/projects/growing-computation]].

- ## TL;DR
	- Robustness principles cross the bio/engineering divide. Apparent differences (biological parts are *noisy*; biological architecture is *byzantine*) dissolve — robust engineered systems (a commercial airliner: 100k+ subsystems, 1000+ CPUs) are no simpler than organisms, and complexity itself may *be* the robustness. The two transferable principles: **distributed robustness** and **evolved robustness**. ^[extracted]

- ## Distributed robustness in engineering
	- The public telephone network is 99.999% available; hardware failures cause only ~7% of downtime. Robustness comes from the **distributed network**: switches **reroute traffic dynamically** around a failed switch. "Although switches do similar things, their *different positions in the topology* give them different roles" — not redundancy. Price paid: each node stores **global path information** and exchanges status continually. The internet (packet-switched) gets the same robustness the same way. ^[extracted]

- ## Evolved integrated circuits (Keymeulen et al. 2000) — the key result
	- A **field-programmable transistor array** (Fig 20.1: 8 transistors, 24 programmable switches; the switch configuration *is* the circuit) evolved by a **genetic algorithm** to compute XNOR / analog multiplication. ^[extracted]
	- A circuit evolved *without* faults was robust to 2 of 6 never-seen switch faults. But when **performance was evaluated under faulty switches during evolution**, after 60 generations the circuit computed XNOR correctly under *any one of six* switch failures — **robustness itself evolved.** ^[extracted]
	- Critically: this fault-tolerance "does **not** simply stem from redundancy of parts. Although the transistors are 'redundant' (many, identical), fault tolerance emerges from a **global configuration of switches**, not from duplication" — i.e. *distributed* robustness in silicon. Evolved circuits also resist clean decomposition into function-specific parts (cf. [[wiki/refs/thompson-1997-evolved-circuit]]). ^[extracted]
	- **Engineering's advantage over biology:** you can inject faults at **high, targeted rates** during the search (biology's mutations are rare & random), so you can drive a device to be *maximally* robust to a chosen fault spectrum. ^[extracted]

- ## Why it's relevant to [[wiki/projects/growing-computation]]
	- A concrete **precedent** worth knowing: on a reconfigurable [[wiki/concepts/fpga]]-style substrate, fault-tolerance can be *distributed* (global config, not spare copies) and *learned/evolved* by training under damage pressure — close in spirit to Stage-3-bis. Loosely, the NCA rule would play a role like Keymeulen's GA (a search for distributed-robust configurations), but *local and learned*. A precedent to build past, not a blueprint. ^[claude-synth]
	- A rough lineage it sits near: [[wiki/refs/thompson-1997-evolved-circuit]] (1997) → Keymeulen (2000) → [[wiki/refs/whitley-2021-fpga-evolvable-hardware]] → (one direction) growing-computation, which would add *locality + a learned developmental rule*. ^[claude-synth]
	- "Inject faults at high targeted rates" = the curriculum for the recover-from-damage objective; "robustness only to encountered faults" (Ch19) sets what to put in that curriculum. ^[claude-synth]

- ## Connections to Wiki
	- [[wiki/projects/growing-computation]] — the engineering grounding for self-healing hardware.
	- [[wiki/concepts/fpga]] — field-programmable arrays are the substrate here.
	- [[wiki/refs/whitley-2021-fpga-evolvable-hardware]] / [[wiki/refs/thompson-1997-evolved-circuit]] / [[wiki/refs/haddow-2011-evolvable-hardware]] — the evolvable-hardware lineage.
	- [[wiki/refs/woods-2008-robustness]] — FPGA self-repair / partial-reconfig; the fault-tolerance engineering counterpart.
	- [[wiki/concepts/substrate-rule-co-location]] — see §Robustness.

- ## Cited By (in this wiki)
	- `growing-computation-lab-talk` deck — Biology II / substrate slides.
