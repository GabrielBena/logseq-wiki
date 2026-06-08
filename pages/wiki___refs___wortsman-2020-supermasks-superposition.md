title:: wiki/refs/wortsman-2020-supermasks-superposition
category:: reference
type:: external-ref
tags:: continual-learning, supermasks, task-inference, subnetworks, catastrophic-forgetting
authors:: Wortsman, Mitchell; Ramanujan, Vivek; Liu, Rosanne; Kembhavi, Aniruddha; Rastegari, Mohammad; Yosinski, Jason; Farhadi, Ali
year:: 2020
venue:: NeurIPS 2020
arxiv:: 2006.14769
summary:: SupSup: fixed random net + per-task binary supermasks; task identity inferred by gradient-descending output entropy over a mask superposition (one step often suffices), up to 2500 tasks.
confidence:: 0.78
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-08
updated:: 2026-06-08
sources:: arxiv:2006.14769 (full PDF read 2026-06-08)
wiki-generated:: true
ingest-mode:: full

- **Supermasks in Superposition (SupSup)** — Wortsman, Ramanujan, Liu, Kembhavi, Rastegari, Yosinski & Farhadi (2020), NeurIPS 2020. arXiv:2006.14769. Code: `github.com/RAIVNLab/supsup`.
	- A long-liked reference (Gabriel) for the *fixed substrate + per-task configuration* framing — deep-ingested 2026-06-08 alongside the continual-learning / mixture-of-experts cluster.

- ## Abstract (extracted)
	- *"We present the Supermasks in Superposition (SupSup) model, capable of sequentially learning thousands of tasks without catastrophic forgetting. Our approach uses a randomly initialized, fixed base network and for each task finds a subnetwork (supermask) that achieves good performance. If task identity is given at test time, the correct subnetwork can be retrieved with minimal memory usage. If not provided, SupSup can infer the task using gradient-based optimization to find a linear superposition of learned supermasks which minimizes the output entropy. In practice we find that a single gradient step is often sufficient to identify the correct mask, even among 2500 tasks. We also showcase two promising extensions… the entire, growing set of supermasks can be stored in a constant-sized reservoir by implicitly storing them as attractors in a fixed-sized Hopfield network."*

- ## Core mechanism
	- **The base net is never trained.** Weights `W` are frozen at a *signed Kaiming constant* init (`±c`); only the random seed is stored. For task `i` a **binary supermask** `M^i` selects a subnetwork: `p = f(x, W ⊙ M^i)`. Leans on the "expressive power of randomly-weighted subnetworks" line (Zhou et al. 2019; Ramanujan et al. 2019's *edge-popup*) — within a random net there already exist masks giving good performance, so capacity is *selected*, not learned.
	- **No forgetting by construction**: the representation (`W`) never moves, so past tasks can't be overwritten — the masks are the only per-task state.
	- **Task-identity inference = a gradient-based optimisation.** When task ID is unknown at test time, associate each learned mask `M^i` with a coefficient `α_i ∈ [0,1]` (init `1/k`) and run the **superposition** `p(α) = f(x, W ⊙ (Σ_i α_i M^i))`. The correct mask yields a **confident, low-entropy** output, so inference = *find `α` minimising output entropy* `H(p(α))` by gradient descent `α ← α − η∇_α H(p(α))`.
		- **One-Shot**: the inferred task is `argmax_i(−∂H/∂α_i)` from a *single* gradient step (one step of Frank-Wolfe). "A single gradient step is often sufficient… even among 2500 tasks."
		- **Binary**: a `log k`-step binary-search variant that rules out half the tasks per step.
	- **Superfluous neurons (s-neurons)**: adding output neurons beyond the `ℓ` classes sharpens inference; an alternative objective `G = logsumexp(p)` has the property (Lemma 1) that its gradient on the s-neurons *exactly mirrors the gradient from the supervised training loss* — a self-contained surrogate for "is this the right mask?".

- ## Two extensions
	- **NNs scenario (task ID never given, even at train).** SupSup *detects novelty*: if the post-inference distribution over masks is ~uniform (`max_i ν_i < 1+ε`), the datum belongs to no known task → **allocate a new supermask** and increment `k`. Grows up to 2500 masks with no task labels at all. This is grow-on-demand under an *uncertainty* signal.
	- **HopSupSup (constant memory).** The growing set of masks is stored implicitly as **attractors in a fixed-size Hopfield network** `Ψ`; at test time, gradient descent on the Hopfield energy + output entropy converges a learnable mask `m` to the right stored attractor in `< 30` steps. Memory stops scaling with task count.

- ## A taxonomy contribution (widely cited)
	- SupSup introduces a **three-letter taxonomy of continual-learning scenarios** — task identity *Given/Not* at train and at inference, plus *shared/unshared* labels: **GG / GNs / GNu / NNs**. It is used to situate prior methods (EWC, SI, PNN, PackNet, Piggyback, PSP, BatchE…) and remains a reference framing for the CL field. Regularisation methods (EWC/SI) sit in GNs; SupSup uniquely spans all four.

- ## Results (orientation)
	- **GG** (ID given): beats similar-size baselines (BatchE, PSP) on SplitImageNet/SplitCIFAR100 with far fewer bytes; a running-mean mask init gives strong **transfer**.
	- **GNu** (ID inferred): One-Shot SupSup outperforms methods that are *given* task ID (PSP, BatchE) on Permuted/Rotated-MNIST; ~94.9% after 250 MNIST permutations where Online-EWC/SI collapse.
	- **Limitation (the honest catch):** task inference fails when the model is **poorly calibrated** (overconfident on the *wrong* task). The authors flag better calibration / self-supervision / energy-based objectives as future work.

- ## Why it's relevant to [[wiki/projects/growing-computation]] (nuanced)
	- **Fixed substrate + per-task *configuration*, not new weights.** SupSup freezes the whole net and varies *which subnetwork is selected* — a software cousin of the project's fixed boolean fabric whose *logical configuration* (not its silicon) changes per task. The "many good subnetworks live in one random net" result rhymes with the project's solution-degeneracy / basin-hopping framing in [[wiki/concepts/substrate-rule-co-location]]. ^[inferred]
	- **The divergences matter more.** SupSup's selection is **global** (entropy over the whole output, a gradient over *all* mask coefficients at once) and its "capacity" is a *single shared* random net masked globally — not spatially-local tiles with nearest-neighbour comms. There is **no within-task growth** (capacity is fixed; only mask *count* grows in NNs). So SupSup is a concrete *foil + oracle example*, not a template — inspiration to build past, and likely to look different once localised. ^[claude-synth]

- ## Why it's relevant to [[wiki/concepts/grow-and-learn]] — a selection oracle
	- SupSup's **entropy-minimising task inference is exactly an external oracle**: a *global* signal (output entropy / `logsumexp` over the whole network) that answers *"which task / which stored configuration is this?"* in one gradient step. That is the mechanism-level answer to growing-computation's open **"where to go back to for an old task"** question (encoder-ensemble key-matching) — but computed globally, which a locally-constrained rule can't do directly. It belongs on the *oracle spectrum* in [[wiki/concepts/grow-and-learn]] (a *which-configuration* selection oracle, beside [[NORACL]]'s *when/where-to-grow* signal), and the NNs novelty-trigger is a second oracle (*when to grow*, under an uncertainty signal). The open question: can a local rule *internalise* "pick the low-entropy configuration" via message-passing + depth-in-time, instead of a global gradient over all masks? ^[inferred]

- ## Connections to Wiki
	- [[wiki/concepts/grow-and-learn]] — SupSup's entropy-minimising task inference as a *selection oracle* on the oracle spectrum; the NNs novelty-trigger as a *when-to-grow* oracle.
	- [[wiki/projects/growing-computation]] — fixed-substrate + per-task-configuration cousin; foil for Stage-3 recruit/reuse (global vs local-and-learned).
	- [[wiki/refs/shanahan-2021-encoders-ensembles-continual]] — sibling *freeze-the-representation* CL: Shanahan freezes a pretrained encoder + an ensemble; SupSup freezes a random net + masks. Both preclude forgetting by never moving the representation; both then need a *selection* step.
	- [[wiki/refs/fernando-2017-pathnet]] — both select a *subnetwork/path* through a fixed-or-shared net per task; PathNet evolves paths by a global GA, SupSup learns masks + infers by entropy — different selection mechanisms, same "configuration not weights" spirit.
	- [[wiki/concepts/substrate-rule-co-location]] — many good subnetworks in one random net ≈ solution degeneracy; configuration changes, substrate fixed.
	- [[NORACL]] — the *complementary* oracle: NORACL grows under representational/plasticity saturation; SupSup *selects/allocates* under output-entropy. Two oracle flavours for the same grow/select decision.

- ## Open Questions / To Read
	- Can the global entropy-minimisation selection be approximated by a **local** rule (the oracle-internalisation thread in [[wiki/concepts/grow-and-learn]])? ^[inferred]
	- The **calibration dependence** is a real constraint: a degenerate/self-organising substrate with no calibrated output head has no obvious entropy signal — what plays the role of "confidence" there? ^[inferred]
	- Predecessor *edge-popup* (Ramanujan et al. 2019, "What's hidden in a randomly weighted neural network?") not yet a wiki ref. ^[wiki-gap]

- ## Cited By (in this wiki)
	- [[wiki/concepts/grow-and-learn]]
	- [[wiki/projects/growing-computation]]
