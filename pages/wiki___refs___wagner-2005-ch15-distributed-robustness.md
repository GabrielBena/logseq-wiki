title:: wiki/refs/wagner-2005-ch15-distributed-robustness
category:: reference
type:: external-ref
tags:: robustness, degeneracy, redundancy, distributed-robustness, complex-systems
authors:: Wagner, Andreas
year:: 2005
venue:: Robustness and Evolvability in Living Systems, Ch15 (Princeton UP)
summary:: Wagner's central empirical claim — distributed robustness (many different parts compensating by rerouting), not redundancy of parts (spare copies), is the dominant cause of robustness in biological systems.
confidence:: 0.7
lifecycle:: draft
lifecycle-changed:: 2026-06-05
created:: 2026-06-05
updated:: 2026-06-05
sources:: wiki/_pdfs/wagner-2005-robustness-evolvability.pdf (Ch15, pp. 228–246)
wiki-generated:: true
ingest-mode:: full

- **Ch15 — Redundancy of Parts or Distributed Robustness?** (parent: [[wiki/refs/wagner-2005-robustness-evolvability]]). A key chapter for the lab talk's Biology II.

- ## TL;DR
	- Two mechanistic causes of robustness: **redundancy of parts** (≥2 parts doing the *same* task — e.g. duplicate genes) vs **distributed robustness** (many *different* parts compensate through their interactions, *not* by standing in for the failed part). Wagner's verdict: **distributed robustness dominates** in living systems. ^[extracted]

- ## The evidence
	- **Gene-deletion studies undercut redundancy.** ~40% of yeast genes can be deleted with no detectable fitness effect — but the surprise is that *most of these are single-copy genes* (no duplicate). >40% of weak/no-effect genes have no duplicate; estimates put only ~23–59% (yeast) or ~3–36% (worm) of weak-deletion effects down to duplication. ^[extracted]
	- **Duplicates diverge fast.** Even recent duplicates differ sharply in expression pattern, transcriptional regulators, and protein-interaction partners — so duplicates rarely keep identical functions long enough to serve as backups. ^[extracted]
	- **Metabolic networks = the cleanest case.** No two reactions are identical (no redundancy), yet >50% of reactions can be removed without changing output in one environment — because the network **reroutes flux** through unaffected parts. Compensation often happens *far* from the lesion. ^[extracted]
	- Same story for regulatory networks, enzyme pathways, macromolecule folding, body plans: robustness comes from *cooperation of different parts*, not duplicates. ^[extracted]

- ## The subtle caveat (worth keeping honest)
	- Redundancy and distributed robustness can be **mathematically indistinguishable** at the level of an aggregate observable: control theory guarantees that for any system with redundant parts there is a non-redundant system with the *same transfer function*. So "how much redundancy?" is partly perspective-dependent (count parts vs measure control coefficients). ^[extracted]

- ## Why it's relevant to [[wiki/projects/growing-computation]]
	- The project's recovery story — recovering a damaged tile's function by **recruiting and reconfiguring *neighbouring, different* tiles** (Stage 3-bis), not by holding spare copies — fits the pattern Wagner calls *distributed robustness*. A useful name + some empirical grounding for the deck's "recovery by re-differentiation, not redundancy" — borrowed, not derived. ^[claude-synth]
	- It also justifies the **DNA-framing** in [[wiki/concepts/substrate-rule-co-location]]: the substrate need not store every workload (redundancy); a small rule re-differentiates available tiles (distributed). ^[claude-synth]
	- "Reroute flux through unaffected parts" is the metabolic-network analogue of the NCA rule re-routing computation around dead/over-pressured tiles (Stage 2). ^[claude-synth]

- ## Connections to Wiki
	- [[wiki/refs/edelman-2001-degeneracy-complexity]] — degeneracy (different structures, same function) is essentially distributed robustness named from the function side.
	- [[wiki/concepts/substrate-rule-co-location]] — see §Robustness.
	- [[wiki/projects/growing-computation]] — Stage-2 (rerouting) and Stage-3-bis (recovery) are distributed-robustness claims.
	- [[wiki/research/self-organising-digital-circuits]] — solution degeneracy as the SODC instance.

- ## Cited By (in this wiki)
	- `growing-computation-lab-talk` deck — Biology II.
