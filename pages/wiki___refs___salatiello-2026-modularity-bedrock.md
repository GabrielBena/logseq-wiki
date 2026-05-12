title:: wiki/refs/salatiello-2026-modularity-bedrock
category:: reference
type:: external-ref
tags:: modularity, brain-inspired-ai, review, mixture-of-experts, compositional-generalization, brain-networks, no-free-lunch
authors:: Salatiello, Alessandro
year:: 2026
venue:: arXiv preprint
arxiv:: 2602.18960
doi:: 10.48550/arXiv.2602.18960
citation-count:: 3
summary:: Single-author review arguing modularity is a unifying computational principle across engineering, evolutionary biology, neuroscience, and AI. Proposes implicit/emergent/architectural taxonomy and a formal modular-model definition.
confidence:: 0.70
lifecycle:: draft
lifecycle-changed:: 2026-05-12
created:: 2026-05-12
updated:: 2026-05-12
sources:: api:semanticscholar, pdf:arxiv
wiki-generated:: true
ingest-mode:: full

- **Modularity is the Bedrock of Natural and Artificial Intelligence** — Salatiello (2026), University of Tübingen, arXiv:2602.18960.
	- Review/synthesis paper, 7-page body + extensive references. Single author (Salatiello also has a companion paper *From Modules to Movement* on motor-system modularity, cited internally).
	- Thesis: modularity is not merely a structural choice or biological epiphenomenon but a fundamental computational principle underlying both natural and artificial intelligence — and aligns with the No Free Lunch Theorem's demand for problem-specific inductive biases.
- ## Core Argument
	- Modern AI achieves remarkable performance but at vastly inflated data/compute/energy costs vs human intelligence (GPT-3 ≈ 1287 MWh, human brain ≈ 3.15 MWh over 18 years).
	- This disparity motivates drawing inspiration from brain organisational principles. Among these, **modularity** is theorised to support the efficient learning and strong generalization humans exhibit.
	- Modular architectures align with the No Free Lunch Theorem ([[wiki/refs/woods-2008-robustness]] adjacency — Wolpert & Macready 1997) — there is no universal general-purpose inductive bias, so problem-specific specialised components are necessary.
	- Yet despite ubiquity in AI subfields, modularity remains "relatively underappreciated in mainstream AI research."
- ## Unified Conceptual Framework (Table 1)
	- The paper's central synthesis maps properties of modular systems across four domains:
	  
	  | Evolutionary Biology | Neuroscience | AI | Engineering |
	  |---|---|---|---|
	  | Robustness | Energy efficiency | Compositional generalization | Splitting |
	  | Adaptability | Functional specialization | Continual learning | Substituting |
	  | Evolvability | Information factorization | Transfer learning | Augmenting |
	  | | Partial autonomy | Multi-task learning | Excluding |
	  | | Dynamical richness | Amortized learning | Inverting |
	  | | Timescale separation | Multi-modal learning | Porting |
	  | | | Neuro-symbolic learning | |
	- Each domain has typically studied these properties in isolation; the paper's claim is that they are all manifestations of the same underlying principle. ^[inferred]
- ## Formal Definition
	- A model $f(x): \mathbb{R}^i \to \mathbb{R}^o$ is modular with modules $\mathcal{M} = \{m_{\mu_i}(x)\}_{i=1}^M$ if it can be written:
		- $f(x) = g_\gamma(r_\rho(x))$
		- where $r_\rho$ is a **routing function** (selects active modules) and $g_\gamma$ is an **aggregation function** (combines module outputs).
	- **Hard routing** (binary on/off): sparse, efficient inference, but not end-to-end differentiable — requires RL, evolutionary algorithms, or stochastic parametrization.
	- **Soft routing**: all modules active with probability $p_i$; trainable via gradient descent, computationally expensive.
	- In transfer learning, an additional **modifier function** $d_\delta^{(f)}(l_\lambda(x))$ specifies how a modular fine-tune alters a base network's layer (e.g., simple summation as in adapters, or function composition as in residual adapters).
- ## Taxonomy of AI Modularity (Table 2)
	- **Implicit modularity** — intrinsic to virtually all modern DNNs by virtue of stacked-layer hierarchy. Examples: units in NNs, layers in DNNs, winning tickets in the Lottery Ticket Hypothesis (Frankle & Carbin 2018).
	- **Emergent modularity** — arises during training when units self-organise into structural/functional subcomponents. Examples: functional modules in multi-task learning, knowledge neurons in LLMs (Dai et al. 2021), induction-head circuits in LLMs (Olsson et al. 2022).
	- **Architectural modularity** — explicitly designed modular priors. Examples: Mixture-of-Experts (MoE) layers (Shazeer 2017, Fedus 2022 Switch Transformers, Mixtral, He 2024 PEER), RAG databases in chatbots, multi-agent systems.
	- Section 3.3 deep-dives into five application areas: compositional generalization, continual learning, transfer learning & LLMs, autonomous agents (LeCun 2022 world-model architecture), hybrid neuro-symbolic architectures.
- ## Modularity in Brains (multi-scale)
	- **Neurons as modules** (§4.1): biological neurons are not simple weighted sums — dendritic nonlinearities make a single neuron behave like a multi-layer network (Beniaguev et al. 2021, London & Häusser 2005). Recent KAN-style work (Liu et al. 2024b) leverages this.
	- **Canonical microcircuits** (§4.2): stereotyped 6-layer cortical column motifs (Harris & Shepherd 2015, Douglas & Martin 2004). Linked to predictive coding (Bastos et al. 2012) and the Thousand Brains Theory (Hawkins 2021). Recent work (Chen et al. 2022, Billeh et al. 2020) shows initializing RNN weights from V1 connectivity improves OOD generalization vs feedforward/recurrent CNNs.
	- **Cortical areas & networks** (§4.3): semi-automated parcellations (Glasser et al. 2016) identify ~180 areas/hemisphere; fMRI functional-network analysis (Yeo, Power, Uddin) identifies 6 canonical large-scale networks — occipital, pericentral, dorsal frontoparietal, lateral frontoparietal, midcingulo-insular, medial frontoparietal.
	- **Cattell-Horn-Carroll behavioral decomposition** (§4.4): three-tier hierarchy — g-factor (general intelligence), broad abilities (fluid, crystallized), narrow abilities. Provides behavioral evidence for modular cognition.
	- **Phylogenetic identification** (§4.5): Cisek's view — true brain modules must be identified through evolutionary history, tracing how primitive feedback-control mechanisms in single cells were elaborated into mammalian decision-making systems.
- ## Open Questions (the paper's framing of the debates)
	- **Modularity or Scaling?** (§6.1) — direct engagement with the *Bitter Lesson* (Sutton 2019). Scaling has known downsides (cost, data exhaustion, model collapse from synthetic data — Shumailov 2024) so modular priors gain importance as scaling hits walls.
	- **Are brains still relevant?** (§6.2) — yes: AI still requires orders of magnitude more data than brains for narrow tasks; general intelligence remains out of reach; functional linguistic deficits persist in LLMs (Mahowald et al. 2024).
	- **How to bridge the gap?** (§6.3) — proposed path: identify functional modules the brain uses (e.g., dedicated memory systems — Squire 2009; separated language vs thought networks — Fedorenko 2024) and implement analogues in AI. RAG (Lewis 2020) is an early example of a memory-module pattern that reduces hallucination. The harder challenge is dedicated reasoning modules — current LLMs generate reasoning implicitly via extended output (Guo et al. 2025 / DeepSeek-R1).
- ## Cites Gabriel's work (notable)
	- §3.3.1 Compositional Generalization explicitly cites **Béna & Goodman 2021** (arXiv:2106.02626, the basis for [[wiki/research/dynamics-specialization]]):
		- "(Béna & Goodman, 2021) showed that strong inter-module connection sparsity and resource constraints (measured by the number of units in a module) facilitate module specialization."
	- This is a partial reading of Gabriel's thesis result — Salatiello takes the resource-constraint half but does not engage with the more nuanced negative finding that **structural modularity alone does not guarantee functional specialization** ([[wiki/concepts/modularity]]'s "Modularity Trap"). The paper sits squarely in the *pro-modularity* camp; it would benefit from engaging with the anti-localisation critique (e.g., Pessoa's *Entangled Brain* — not cited).
	- > This is where the #position-paper is needed ! We can start to see the pieces falling into place hehe
	-
- ## Tension with the wiki's existing framing
	- This paper is *the* contemporary pro-modularity review. It complements but **does not engage with** [[wiki/refs/pessoa-2022-entangled-brain]] — the canonical anti-localisation critique. The two should be read together.
	- Salatiello accepts that "brains are modular" largely uncritically and pursues the engineering implications. Pessoa argues the structure-function mapping is many-to-many, M5 (spatial localisation) is overrated, and modularity claims often smuggle in unjustified assumptions.
	- Gabriel's own thesis ([[wiki/research/dynamics-specialization]], [[wiki/research/spatial-neuromorphic-priors]]) sits between these poles: structural modularity is a real and measurable property, but it does not deterministically produce functional specialization — resource constraints and task separability are the load-bearing factors.
- ## Connections to Wiki
	- [[wiki/concepts/modularity]] — direct conceptual overlap; this paper is the broadest synthesis of pro-modularity arguments currently in the wiki. The Salatiello taxonomy (implicit/emergent/architectural) is orthogonal to Gabriel's PP/PS/UP/US 2×2 — both could be combined.
	- [[wiki/refs/pessoa-2022-entangled-brain]] — companion (and counterpoint) review. Salatiello = modularity-is-the-answer; Pessoa = modularity-claims-are-overstated.
	- [[wiki/research/dynamics-specialization]] — Gabriel's Ch1 result, explicitly cited by Salatiello §3.3.1 (with partial framing — see "Cites Gabriel's work" above).
	- [[wiki/research/spatial-neuromorphic-priors]] — Gabriel's Ch2 result on spatial-constraint-induced structural modularity; relevant to Salatiello's §4 (energy efficiency / wiring cost as a modularity driver, citing Clune et al. 2013 and Achterberg et al. 2023).
	- [[wiki/refs/achterberg-2023-sernns]] — cited as evidence that modular brain-like topologies emerge from wiring-cost regularisation; central to the §2.2.3 argument.
	- [[wiki/concepts/compositional-learning]] — Salatiello §3.3.1 frames compositional generalization as *the* primary computational advantage of modular AI; cites Béna & Goodman 2021, Mittal et al. 2022, Bahdanau et al. 2018, Boopathy et al. 2025.
	- [[wiki/refs/petersen-2022-deep-differentiable-logic]] — not cited by Salatiello, but Salatiello's "implicit modularity" framing (layers in DNNs as hierarchical modules) applies to differentiable logic networks as a natural fit.
	- [[wiki/concepts/neural-cellular-automata]] — Salatiello does not discuss NCAs explicitly, but the framing "every cell uses the same module" is a *parameter-shared architectural modularity* not captured in the paper's taxonomy — possible extension. ^[inferred]
	- [[wiki/refs/hiesinger-2021-self-assembling-brain]] — Salatiello discusses phylogenetic identification of brain modules (Cisek 2019, 2022) as an alternative to direct measurement; resonates with Hiesinger's algorithmic-growth thesis but with no cross-citation.
- ## Open Questions / To Read
	- Salatiello's companion paper *From Modules to Movement* (arXiv 2026, also cited internally) extends the framework specifically to motor-system modularity — worth ingesting as a sibling ref.
	- The paper's taxonomy *omits* parameter-shared architectures (NCAs, transformers across positions). Whether that's "implicit" or a missing fourth category is open. ^[inferred]
	- The Cattell-Horn-Carroll three-tier intelligence model (§4.4) is interesting as a *behavioral* modularity decomposition — could it be operationalised as a benchmark suite for AI?
	- Cisek's "neuroscience needs evolution" framing (§4.5) deserves a concept-page treatment.
- ## Cited By (in this wiki)
	- None yet — this is the first ingest.