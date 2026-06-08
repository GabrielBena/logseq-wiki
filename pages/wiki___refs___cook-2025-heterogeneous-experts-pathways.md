title:: wiki/refs/cook-2025-heterogeneous-experts-pathways
category:: reference
type:: external-ref
tags:: mixture-of-experts, modularity, routing, brain-networks, pathways, heterogeneity
authors:: Cook, Jack; Akarca, Danyal; Costa, Rui Ponte; Achterberg, Jascha
year:: 2025
venue:: arXiv 2506.02813
arxiv:: 2506.02813
citation-count:: 4
summary:: Heterogeneous experts don't form pathways alone; three inductive biases (routing cost, low-performance cost-scaler, expert dropout) make brain-like task pathways emerge — a "Mixture-of-Pathways".
confidence:: 0.47
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-08
updated:: 2026-06-08
sources:: api:semanticscholar
wiki-generated:: true
ingest-mode:: abstract

- **Brain-Like Processing Pathways Form in Models With Heterogeneous Experts** — Cook, Akarca, Costa & Achterberg (2025), arXiv:2506.02813.
	- Flagged (Gabriel) as relevant to a **hierarchical / diverse-size tile** implementation — and a cool paper in its own right.

- ## Abstract (extracted)
	- The brain is made up of a vast set of heterogeneous regions that dynamically organize into pathways as a function of task demands. Examples of such pathways can be found in the interactions between cortical and subcortical networks during learning, or in sub-networks specializing for task characteristics such as difficulty or modality. Despite the large role these pathways play in cognition, the mechanisms through which brain regions organize into pathways remain unclear. In this work, we use an extension of the Heterogeneous Mixture-of-Experts architecture to show that heterogeneous regions do not form processing pathways by themselves, implying that the brain likely implements specific constraints which result in the reliable formation of pathways. We identify three biologically relevant inductive biases that encourage pathway formation: a routing cost imposed on the use of more complex regions, a scaling factor that reduces this cost when task performance is low, and randomized expert dropout. When comparing our resulting *Mixture-of-Pathways* model with the brain, we observe that the artificial pathways in our model match how the brain uses cortical and subcortical systems to learn and solve tasks of varying difficulty. In summary, we introduce a novel framework for investigating how the brain forms task-specific pathways through inductive biases, and the effects these biases have on the behavior of Mixture-of-Experts models.

- ## Key Ideas
	- Heterogeneous experts **don't** self-organise into pathways on their own — extra constraints are needed. ^[inferred]
	- Three biologically-motivated inductive biases encourage pathways: (1) a **routing cost** on using more complex experts, (2) a **scaling factor** that lowers that cost when task performance is poor, (3) **randomised expert dropout**. ^[inferred]
	- The resulting **"Mixture-of-Pathways"** matches how the brain recruits cortical vs subcortical systems across task difficulty. ^[inferred]
	- Offered as a framework for studying how task-specific pathways form from inductive biases (and how those biases shape MoE behaviour). ^[inferred]
	- *Abstract-mode — `/paper-ingest full` for the MoE extension, the biases' formalisation, and the brain-comparison metrics.* ^[inferred]

- ## Connections to Wiki (provisional)
	- [[wiki/projects/growing-computation]] — *heterogeneous experts of differing complexity* rhyme with the **diverse-size / hierarchical tiles** idea, and the **routing cost on complex experts** echoes the project's data-movement/energy cost (Step 1's "data movement is huge"). A suggestive framing to borrow — cost biases shaping which tiles get recruited — not a 1:1 map. ^[claude-synth]
	- [[wiki/refs/fernando-2017-pathnet]] — also "pathways through a module net"; here the substrate is MoE and the pathways are brain-matched. A sibling inspiration for recruit/route.
	- [[wiki/refs/meszaros-2025-space-as-time]] / [[wiki/refs/achterberg-2023-sernns]] — same Akarca/Achterberg spatially-embedded-networks lineage (cost/structure → function).
	- [[wiki/concepts/modularity]] — pathways as emergent functional modularity under routing pressure; relevant to the structure-function thread.

- ## Open Questions / To Read
	- Does the routing-cost-on-complexity bias have a clean analogue in the tile setting (e.g. cost ∝ tile size / distance)? Worth a look when designing recruitment objectives. ^[claude-synth]

- ## Cited By (in this wiki)
	- (none yet — staged 2026-06-08 from a deck-comment pass)
