title:: wiki/refs/wagner-2005-ch19-self-organization
category:: reference
type:: external-ref
tags:: robustness, self-organisation, complex-systems, attractor
authors:: Wagner, Andreas
year:: 2005
venue:: Robustness and Evolvability in Living Systems, Ch19 (Princeton UP)
summary:: Robustness in non-living systems arises from self-organisation, not natural selection — perturbations themselves drive a system toward robust states; "fragile systems are fleeting."
confidence:: 0.7
lifecycle:: draft
lifecycle-changed:: 2026-06-05
created:: 2026-06-05
updated:: 2026-06-05
sources:: wiki/_pdfs/wagner-2005-robustness-evolvability.pdf (Ch19, pp. 297–309)
wiki-generated:: true
ingest-mode:: full

- **Ch19 — Robustness in Natural Systems and Self-Organization** (parent: [[wiki/refs/wagner-2005-robustness-evolvability]]).

- ## TL;DR
	- Non-living systems can't be made robust by natural selection (no reproduction/heritability). Their robustness has a different origin: **self-organisation**. The one-line statement of the mechanism — *"A system will spend most of its time in a robust state, precisely because such a state is more robust. If the world is rife with robust systems, it is because fragile systems are fleeting."* ^[extracted]

- ## The mechanism
	- **Perturbation drives robustness.** Random perturbations push a system between states; it lingers longest in the most perturbation-resistant states, so over time it accumulates there. Crucially, a system develops robustness *only to perturbations it has actually encountered.* ^[extracted]
	- **Examples across scales** with the *same* shape: community assembly → rising invasion-resistance; protein folding & macromolecular-complex assembly → most-stable conformation; the basin/valley metaphor (the ball settles in the widest valley). ^[extracted]
	- **Directed-graph view**: among permanent community states, completely-invasion-resistant "absorbing" nodes exist — maximally robust *endpoints*. It is the *directionality* (you can reach them but not leave) that makes perfect robustness possible. ^[extracted]
	- In living systems the same self-organisation operates, but selection can additionally *shape the landscape* (Fig 19.3) for fast, intermediate-free assembly. ^[extracted]

- ## Why it's relevant to [[wiki/projects/growing-computation]]
	- A nice mechanistic story for the **self-healing idea**: a *self-organising* substrate under damage pressure might settle into damage-robust configurations on its own — robustness as an attractor rather than a stored backup. Suggestive, and worth testing — not established for this substrate. ^[claude-synth]
	- "Develops robustness only to perturbations encountered" is a concrete training prescription: expose the NCA rule to the damage / power / routing pressures you expect at deployment (Stage 2 / 3-bis), and distributed robustness to *those* emerges. ^[claude-synth]
	- Directly parallels [[SODC]]'s self-repair as **basin-hopping over solution-degeneracy** (already in the wiki) — same valley-landscape picture, now with Wagner's self-organisation argument behind it. ^[claude-synth]

- ## Connections to Wiki
	- [[wiki/concepts/self-organisation]] — Wagner's robustness-from-self-organisation is a sharp, quotable instance.
	- [[wiki/concepts/substrate-rule-co-location]] — see §Robustness.
	- [[wiki/projects/growing-computation]] — self-healing / Stage-3-bis grounding.
	- [[wiki/refs/shannon-1956-reliable-organisms]] — reliability from unreliable components; the complementary engineering-redundancy pole.

- ## Cited By (in this wiki)
	- `growing-computation-lab-talk` deck — Biology II.
