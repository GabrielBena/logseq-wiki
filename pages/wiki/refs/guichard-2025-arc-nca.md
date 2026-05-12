title:: wiki/refs/guichard-2025-arc-nca
category:: reference
type:: external-ref
tags:: nca, arc-agi, abstraction-reasoning, test-time-training, developmental-encoding
authors:: Guichard, Etienne; Reimers, Felix; Kvalsund, Mia; Lepperød, Mikkel; Nichele, Stefano
year:: 2025
venue:: IEEE Symposium on Artificial Life (ALIFE 2025)
doi::
arxiv:: 2505.08778
citation-count:: 6
summary:: ARC-NCA — applies standard NCA + EngramNCA variants to ARC-AGI via test-time training (one NCA per task). Best single model 12.9% solve rate; 4-model union 17.6%; up to 27% with looser threshold. Comparable to ChatGPT 4.5 at ~1000× lower cost.
confidence:: 0.78
lifecycle:: draft
lifecycle-changed:: 2026-05-09
created:: 2026-05-09
updated:: 2026-05-09
sources:: arXiv:2505.08778 (full PDF, 6551 words)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **ARC-NCA: Towards Developmental Solutions to the Abstraction and Reasoning Corpus** — Guichard, Reimers, Kvalsund, Lepperød & Nichele (Østfold UC + Oslo Met + Simula + U. Oslo), ALIFE 2025, arXiv:2505.08778. Code: https://github.com/etimush/ARC_NCA. Videos: https://etimush.github.io/ARC-NCA-Videos.

- ## TL;DR
  - First application of NCA / EngramNCA to the **2D ARC-AGI** benchmark (Chollet 2019) — a few-shot abstraction-and-reasoning challenge that's easy for humans (median 3 examples → solve) but extremely hard for AI.
  - Approach: **test-time training (a.k.a. inference-time fine-tuning)** — train a fresh NCA per ARC task on the 2-3 provided examples, evaluate on the unseen test pair. The NCA is the "program" being synthesised.
  - Compares vanilla NCA against four EngramNCA variants ([[wiki/refs/guichard-2025-engramnca]]) with augmentations: (v2) learnable sensing filters; (v3) +toroidal/non-toroidal split between GeneCA/GenePropCA; (v4) +patch-based local-info training.
  - **Best single model**: EngramNCA v3 at 12.9% solve rate. **Best 4-model union**: 17.6% (each task gets two submission attempts; different models cover different tasks). With looser pixel-error threshold and grid padding: up to 27% partial-solution rate.
  - **Comparable to ChatGPT 4.5 (10.3%) at ≈1000× lower cost** ($5e-4 vs $0.29 per task on consumer GPU).
  - Conceptual claim: *developmental computation* (local cell rules unfolding over time) is a structurally promising substrate for abstraction and reasoning — orthogonal to LLM-based program synthesis.

- ## Why NCAs for ARC-AGI?

  - ### The hypothesis (Section: Introduction)
    - ARC tasks emphasise *few-shot generalisation* and *abstract pattern transformation*. Humans solve these via developmental cognitive mechanisms: iterative refinement of mental schemas, hierarchical decomposition into sub-tasks, predictive modelling.
    - NCAs are intrinsically iterative, hierarchical (via [[wiki/refs/guichard-2025-engramnca]]'s public/private channel split), and predictive (state at t+1 emerges from t). The hypothesis: this matches the structure of ARC reasoning.
    - **EngramNCA in particular** is well-suited because it learns *primitives* (in GeneCA) and a *regulation mechanism* (in GenePropCA) that decides when and where primitives activate — analogous to ARC's "build the answer from a small library of grid transformations".

  - ### Test-time training as program synthesis
    - Standard ARC-AGI approaches: discrete program search (brute force) or LLM-based program synthesis (GPT-4-class models writing Python).
    - ARC-NCA's framing: *the trained NCA itself is the program*. For each task, fresh weights are optimised (3000 iterations, AdamW, LR=1e-3 with 66% drop at iter 2000) on the few training examples.
    - This is closer in spirit to neural fine-tuning than to discrete-program synthesis, but the artifact produced (a developmentally-unfolding spatial computation) is novel.

- ## ARC → NCA Lattice Conversion

  - ARC grids are 2D integer arrays (1×1 to 30×30, 10 colour values 0-9). NCAs operate on RGB-α + hidden channels.
  - Conversion: integer → HSL → RGB-α via fixed-saturation/lightness scheme; α=1 for non-zero (background = transparent black).
  - Augmented with a binary-encoded version of the colour value in extra channels (so the NCA sees both colour and identity).
  - Channels padded with ones to reach hidden-size budget.

- ## ARC-Specific Engineering Challenges

  - ### Toroidal vs non-toroidal
    - Standard NCAs run on a torus (wrap-around). Good for morphology-growth (positional invariance), bad for ARC tasks that depend on absolute position or grid edges.
    - **Solution in v3/v4**: split toroidality between EngramNCA's two networks. GeneCA acts non-toroidally (positional info preserved); GenePropCA acts toroidally (information can propagate around). The architecture *chooses* which mode to use via local self-attention. ^[inferred — paper says "imbuing it with attention, the EngramNCA might be able to choose"]

  - ### Changing grid sizes
    - Some ARC tasks have output grids of different size than input. NCAs can't change lattice size mid-run.
    - Two strategies: (a) **ignore problematic grids** (chosen for main experiments — 262 of 400 problems); (b) **maximal padding** (pad everything to 30×30 with a special padding-channel that the NCA can modify).

  - ### Local vs global solutions
    - Some ARC tasks need fine-grained local manipulation; standard NCA training (loss over the whole grid) trains for global pattern completion.
    - **Solution in v4**: patch training — accumulate loss over 3×3 patches instead of the full grid, forcing local-info focus.

  - ### Inappropriate sensing
    - Standard NCAs use Sobel + Laplacian convolution kernels (chemosensing analogue from morphogenesis origins). Too smooth for ARC.
    - **Solution in v3/v4**: replace fixed Sobel/Laplacian with **learnable sensing filters** of matched count.

- ## Results

  - ### Single-model performance (262-problem subset, log-loss threshold ≤ -7)
    - Vanilla NCA: 10.7% solve rate, mean log(loss) -4.31
    - EngramNCA v1 (no augmentations): 6.5% — *worse* than vanilla on ARC, surprisingly
    - EngramNCA v2 (learnable sensing): 9.2%
    - **EngramNCA v3 (sensing + toroidal split): 12.9%** — best single model
    - EngramNCA v4 (sensing + toroidal + patch): 10.3%
    - **ChatGPT 4.5 baseline**: 10.3% (ARC-AGI leaderboard, private eval — not directly comparable but same order)

  - ### Union performance (best 4 models)
    - Each ARC task allows 2 submission attempts. Taking unions effectively combines model strengths.
    - All-4 union: **17.6% solve rate** — every union outperforms its best constituent. Models are complementary, not redundant.

  - ### Looser threshold (almost-solved, log-loss ≤ -6)
    - Single-model best: EngramNCA v4 at 16.8%; vanilla NCA 15.6%
    - All-4 union: **24%** — strong evidence that many failures are "off by 1-3 pixels" rather than fundamentally wrong reasoning.

  - ### Larger / padded variant (Further Experiments)
    - EngramNCA v3 with hidden-size 132 instead of 32: 16.1% (strict) / 19.8% (loose)
    - + maximal padding: 16% / **27%** (loose) — best result in the paper
    - Cost: still ~$5-7e-4 per task.

  - ### Cost comparison
    - All NCA models: ~$3e-4 to $5e-4 per task (RTX 4070 Ti, $0.37/kWh).
    - ChatGPT 4.5 (per ARC-AGI leaderboard): $0.29 per task.
    - **~1000× cost reduction** at comparable performance — the headline takeaway.
    - (For context: OpenAI's o3-high, the best LLM-based ARC solver at the time of writing, scored 87.5% but at $172× cost again — not directly comparable but indicates scale.)

- ## Solved-Problem Examples (qualitatively)

  - **NCA**: a "growing line of decreasing length" task — the NCA correctly extrapolates from training examples to unseen y-coordinates, growing structured patterns incrementally.
  - **EngramNCA v1**: a "fill closed regions one colour, open another" task — fills the entire space with one colour first, then *changes* boundary cells to the right colour. Two-stage developmental solving.
  - **EngramNCA v3**: "connect single pixels by lines" — grows lines outward, then *prunes* the parts that overshoot. Active retraction, not just construction.
  - **EngramNCA v4**: a task involving toroidal-wrap reasoning — the v4 explicitly uses the toroidal mode to grow a diagonal across the grid via the wrap-around boundary.

- ## Reasoning Pitfalls

  - "Off by a few pixels" is the most common failure mode — suggests the architecture has the *right reasoning* but lacks *fine-grained pixel control*.
  - Generalisation gaps when test cases have edge cases (open spaces, large gaps) not in the 2-3 training examples.
  - The model can master *one* of the reasoning steps a problem requires while failing the other (e.g. growing the right shape but on the wrong location).

- ## Theoretical Framing

  - **Developmental computation as program synthesis** — the trained NCA is a *spatially-distributed iterative program* whose execution is the ARC solution. No discrete tokens, no symbolic search — but the same role as Chollet's program-generator framing.
  - **Bottom-up vs top-down**: LLM-based ARC approaches are top-down (read examples, write a Python program, run it). NCA-based is bottom-up (local rules unfold the answer). The paper argues both perspectives are valid and complementary — and an NCA + LLM hybrid is flagged as "promising future direction".
  - **Few-shot generalisation as developmental capacity**: the inductive bias of NCA (iterative, local, emergent-pattern) gives it the right shape for the few-example regime — distinct from LLMs' few-shot capability which leans on massive pretraining.

- ## Connections to Gabriel's Research

  - ### Direct successor to EngramNCA
    - **[[wiki/refs/guichard-2025-engramnca]]** — ARC-NCA is the same group operationalising EngramNCA on a hard reasoning benchmark. The EngramNCA paper itself flagged ARC as future work; this paper delivers.
    - Architectural lesson: vanilla EngramNCA (v1) underperforms vanilla NCA on ARC. The win comes from **adapting the inductive biases to the task domain** — learnable sensing filters, toroidal/non-toroidal split, patch training. Pure architectural substitution wasn't enough.

  - ### NCAs as universal computation substrate — ARC is the abstraction-reasoning test
    - **[[wiki/research/universal-nca]]** (Ch3) argued NCAs are a universal computation substrate; ARC-NCA tests whether they're also a universal *reasoning* substrate. The answer here: surprisingly competitive, even at minimal scale.
    - Test-time training in ARC-NCA echoes UNCA's two-level optimisation: a "training of training rules" applied per task. The structural similarity is striking — ARC-NCA trains a fresh NCA per task; UNCA uses task-specific immutable hardware with a globally trained rule. ^[inferred]

  - ### Test-time training as the natural NCA inference paradigm
    - **[[wiki/research/self-organising-digital-circuits]]** uses pool-based meta-learning where the meta-rule is global and the per-circuit configuration is fast. ARC-NCA inverts this: there's no shared meta-rule across tasks — each task gets its own NCA from scratch.
    - But the *approach* is the same: cheap optimisation per instance, expensive global learning *or* expensive per-task learning. ARC-NCA's success at $5e-4/task suggests per-task training can be more efficient than meta-learning when tasks are very heterogeneous (ARC has ~400 tasks, each with its own logic).
    - Possible synthesis: SODC-style pool meta-learning *across* ARC tasks could dramatically improve sample-efficiency. Currently each ARC-NCA training run is independent. ^[inferred]

  - ### NCA Six Angles update
    - **[[wiki/concepts/neural-cellular-automata]]** — adds a seventh angle to the lineage: **NCA-as-reasoner / per-task program**. Beyond pattern-formation, computation, optimisation, brain-economy, development, and engram-bearing, NCAs can be the *reasoning artifact* for few-shot abstraction.
    - The progression is now explicitly: pattern → computer → optimizer → brain-substrate → developer → engram-bearer → reasoner.

  - ### LLM contrast — the "two paths to AGI" framing
    - The paper's cost-comparison framing (NCA at $5e-4/task vs LLM at $0.29/task) reframes the AGI debate. If developmental computation is structurally well-matched to certain reasoning tasks, the path to AGI may not require ever-larger LLMs.
    - This connects to **[[wiki/refs/aguera-y-arcas-2025-functional-perspective]]**'s functionalist claim: intelligence is a *function*, multiply realisable across substrates. ARC-NCA is a candidate substrate that's structurally different from transformers. ^[inferred]

  - ### ARC-AGI as a north star for SODC-style work
    - SODC currently solves Boolean function tasks. ARC-AGI tests *visual abstraction over Boolean-like primitives* (colours, shapes, positions). A natural extension of SODC — using TMT-style attention over the ARC grid — could be the bridge from "configuring Boolean functions" to "configuring visual reasoning programs". ^[inferred]

- ## Limitations / Where the Paper Stops

  - Only the **public ARC-AGI eval set** (262 of 400 problems after filtering grid-size-changing tasks). Not the official semi-private leaderboard.
  - **Single-run results** — no statistical replication; per-task variance unknown. Authors flag this as future work.
  - The 17.6% / 24% / 27% headline numbers are compelling but well below the SOTA o3-high (75.7%-87.5%, at thousands of dollars per task).
  - **No combination with LLMs** — the authors flag NCA+LLM hybrids as a promising avenue but don't test it.
  - ARC-AGI-2 (Chollet et al. 2025) is not yet evaluated; would be a natural next step.

- ## Cited By (in this wiki)
  - [[wiki/refs/guichard-2025-engramnca]] — direct predecessor
  - [[wiki/concepts/neural-cellular-automata]]
