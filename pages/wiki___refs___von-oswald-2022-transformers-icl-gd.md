title:: wiki/refs/von-oswald-2022-transformers-icl-gd
category:: reference
type:: external-ref
tags:: meta-learning, transformers, in-context-learning, mesa-optimization, gradient-descent
authors:: von Oswald, Johannes; Niklasson, Eyvind; Randazzo, Ettore; Sacramento, João; Mordvintsev, Alexander; Zhmoginov, Andrey; Vladymyrov, Max
year:: 2022
venue:: ICML 2023 (PMLR 202)
arxiv:: 2212.07677
doi:: 10.48550/arXiv.2212.07677
citation-count:: 744
summary:: Linear self-attention can implement one step of gradient descent on a regression loss via an explicit weight construction; trained Transformers actually converge to it and surpass plain GD via learned curvature correction. The clean mechanistic case for "Transformers are mesa-optimizers".
confidence:: 0.82
lifecycle:: draft
lifecycle-changed:: 2026-05-20
created:: 2026-05-20
updated:: 2026-05-20
sources:: arXiv:2212.07677 (full PDF, 24 pages, deep-ingested)
wiki-generated:: true
ingest-mode:: full
provenance-extracted:: 0.85
provenance-inferred:: 0.13
provenance-ambiguous:: 0.02

- **Transformers Learn In-Context by Gradient Descent** — Johannes von Oswald (ETH Zürich), Eyvind Niklasson, Ettore Randazzo, João Sacramento, Alexander Mordvintsev, Andrey Zhmoginov, Max Vladymyrov (Google Research). ICML 2023 (PMLR 202). Code: github.com/google-research/self-organising-systems/tree/master/transformers_learn_icl_by_gd

- ## TL;DR
  - **Hypothesis 1 (the headline)**: training Transformers on auto-regressive tasks makes in-context learning emerge as gradient-based optimization of an *implicit* auto-regressive inner loss, run inside the forward pass.
  - **Proposition 1 (the proof of concept)**: a *single linear self-attention (LSA) layer* with explicit weight matrices is exactly equivalent to one step of gradient descent on a mean-squared-error regression loss. Stack K layers → K GD steps.
  - **Empirical match**: trained linear-self-attention-only Transformers on linear regression tasks actually converge to this construction (up to scaling) — verified by loss alignment, cosine similarity, weight inspection, and successful linear interpolation between trained and constructed weights.
  - **GD++ — Transformers surpass plain GD** by learning a curvature-correcting data transformation `x ← (I − γ X X^T) x`, a truncated Neumann series approximation of the inverse Hessian. Trained multi-layer Transformers match GD++, not vanilla GD.
  - **Mesa-optimization (Hubinger et al. 2019)**: the trained model becomes an inner optimizer running gradient descent on data it sees in context. Same group as the [[wiki/concepts/neural-cellular-automata]] line — code hosted in `google-research/self-organising-systems`.

- ## Setup and Notation
  - Linear self-attention (LSA) layer — like a standard attention block with the softmax removed:
    - `e_j ← e_j + Σ_h P_h V_h K_h^T q_{h,j}`
  - Token construction for in-context regression:
    - Context tokens `e_j = (x_j, y_j)` for `j = 1..N`.
    - Query token `e_{N+1} = (x_test, −W_0 x_test)` (or `(x_test, 0)` if `W_0 ≈ 0` at init).
    - Test prediction is read off the y-slot of the updated query token.
  - Reference linear model: `y = Wx`, MSE loss `L(W) = (1/2N) Σ ‖W x_i − y_i‖²`. One GD step: `ΔW = −(η/N) Σ (W x_i − y_i) x_i^T`.

- ## Proposition 1 — Single LSA Layer = One GD Step
  - **Construction** (Appendix A.1, block-matrix form):
    - `W_K = W_Q = [[I_x, 0], [0, 0]]` (identity on input slot, zero on target slot)
    - `W_V = [[0, 0], [W_0, −I_y]]` (encodes the current linear model `W_0`)
    - `P = (η/N) I`
  - **Effect**: every token `e_j = (x_j, y_j)` gets updated to `(x_j, y_j − ΔW x_j)`. For the test query `(x_test, −W_0 x_test)`, the y-slot becomes `−W_0 x_test − ΔW x_test = −(W_0 + ΔW) x_test`, which after multiplication by −1 recovers `ŷ = (W_0 + ΔW) x_test` — exactly the prediction of the linear model after one gradient step.
  - The construction is *not unique* — any equivalent `(P W_V, W_K W_Q)` product works, so trained weights will land in a *family* of equivalent solutions, not a single point. Authors verify both up to rescaling.

- ## Empirical Result — Trained LSA-only Transformers Converge to the Construction
  - On synthetic linear regression with a teacher model `W_τ ~ N(0, I)`, `x ~ U(−1, 1)`:
    - Loss of trained 1-layer LSA matches one-step GD with hand-tuned learning rate exactly (Figure 2).
    - Cosine similarity between trained and constructed weight matrices is ≈ 1 after training.
    - Linear interpolation between trained and constructed weights stays at the same loss → *linear mode connectivity* (Entezari et al. 2021) — they're in the same loss basin.
  - **Out-of-distribution check**: rescaling test inputs by α and weights by αW (testing far outside training scale) — trained Transformer and GD degrade in lockstep, confirming the trained model implements GD even on inputs it never saw.

- ## Multi-Layer Extension — GD++
  - **Recurrent / looped**: applying the *same* LSA layer K times → K iterative GD steps (with a learned dampening `λ ≈ 0.75` for stability, Figure 10).
  - **Non-recurrent K-layer**: surprisingly *outperforms* K-step plain GD. Aligns instead with `GD++`, which adds a *data transformation* per step: `x ← (I − γ X X^T) x`.
  - Mathematically `GD++` is a single-step preconditioned GD whose `(I − γ X X^T)` factor is a heuristically truncated Neumann series approximation of `(X X^T)⁻¹` — i.e. **learned curvature correction**. Effective for non-Gaussian distributions and OOD scales (Appendix A.10).
  - Implication: Transformers don't just learn vanilla GD — they learn *better* optimizers in-context. This is real meta-learning, not mere mechanical mimicry.

- ## Proposition 2 — Nonlinear Regression via MLPs Inside the Block
  - A standard Transformer block (`MLP m(·)` then `LSA`) implements GD on a *kernelized* squared-error loss with kernel `k(x, y) = m(x)^T m(y)`.
  - When `W_0 = 0`, a single block ≈ Nadaraya-Watson kernel smoother. Multiple blocks → iterative kernelized GD.
  - Sine-wave regression: trained 2-layer Transformer + MLP matches a meta-learned MLP fine-tuned by one GD step on its output layer (Figure 4). Empirical evidence that the "linear model on deep representations" picture lifts to nonlinear tasks.

- ## Proposition 3 — Lifting the Token Construction
  - The construction in Prop 1 assumes inputs and targets are pre-concatenated into one token `e_j = (x_j, y_j)`. Real Transformers see them as separate tokens (`e_{2j} = (x_j)`, `e_{2j+1} = (y_j)`).
  - Proposition 3 shows a 1-layer SA can *learn to copy* targets into preceding tokens, producing the required joined structure. Authors verify empirically with a 2-layer softmax Transformer: layer 1 copies (induction-head-like), layer 2 implements GD. This connects to **induction heads** (Olsson et al. 2022) — induction-head copying is the first half of the picture; gradient-descent learning is the second half.

- ## Softmax and LayerNorm (Appendix A.9)
  - Single-head *softmax* SA cannot match GD on its own — the softmax denominator introduces a bias term proportional to all tokens.
  - **Two-head softmax SA can recover GD** — the second head cancels the bias via a sign-reversed weight, restoring `PV K^T q`. Verified in trained weights (Figure 11 shows the two heads' `W_KQ` matrices have approximate diagonal-with-opposite-signs structure).
  - LayerNorm slightly degrades alignment with GD but doesn't qualitatively change the picture.

- ## Connections to Gabriel's Research
  - ### Mesa-optimization → NCA-as-meta-optimizer
    - **[[wiki/research/self-organising-digital-circuits]]** — SODC's [[wiki/concepts/topology-masked-transformer]] is structurally a sparse-attention Transformer. If trained Transformers implement gradient descent in their forward pass, the TMT *inherits this property for free*: the local rule isn't just "doing message passing" — it's plausibly running an implicit GD on the LUT configurations of its neighbours, with the meta-optimisation done at training time. ^[inferred]
    - **[[wiki/concepts/neural-cellular-automata]]** — the NCA-as-optimizer angle (Ch4 of [[wiki/research/phd-thesis]]) is the *outer-loop trained, inner-loop optimises* pattern. Von Oswald formalises the inner-loop side mechanistically. The two views compose: outer training shapes a local rule that implements gradient-based learning in its forward pass — that *is* what an NCA-meta-optimizer-with-attention does. ^[inferred]
    - **[[wiki/projects/growing-networks]]** — the [[NCA as Gardener]] thesis explicitly relies on "Transformers are universal meta-learners" to argue the architecture scales beyond Boolean circuits. This paper supplies the mechanistic backbone for that claim.
  - ### Same group — through-line with NCA work
    - Mordvintsev co-authors both [[wiki/refs/mordvintsev-2020-growing-neural-ca]] (the foundational NCA paper) and this paper. The code lives in the same `google-research/self-organising-systems` repository as the NCA work.
    - The intellectual through-line: same Google group asking "how do simple local rules give rise to coordinated behaviour" — first via cells on a grid (NCA), then via tokens in a sequence (Transformers-as-mesa-optimizers). The architectural primitive (shared local rule + iterated updates) is the same; only the topology changes. ^[inferred]
  - ### UNCA's mutable/immutable split rhymes with outer/inner loop
    - **[[wiki/research/universal-nca]]** — UNCA splits cellular state into mutable (computational workspace) and immutable (task-specific hardware). Von Oswald's setup is structurally identical at the meta-learning level: meta-parameters `θ` (slow, task-shared, outer loop) configure the inner `W` (fast, task-specific, inner loop). Both architectures realise *two timescales of optimisation*. ^[inferred]
  - ### Sister citation — Kirsch GPICL
    - **[[wiki/refs/kirsch-2022-general-purpose-icl]]** — companion paper from the same arXiv batch (Dec 2022) showing Transformers can be meta-trained as *general-purpose* in-context learners. Von Oswald provides the *mechanism* (GD in the forward pass); Kirsch provides the *capability* (general-purpose ICL across diverse tasks). Together they justify the [[NCA as Gardener]] slide claim that "Transformers are universal meta-learners".
    - **[[wiki/refs/kirsch-2022-self-referential-meta-learning]]** — earlier Kirsch paper on self-referential meta-learning; theoretical ancestor of GPICL.
  - ### Functionalist reading
    - **[[wiki/concepts/functionalism]]** — the mesa-optimization picture is *narrow* multiple realizability at the algorithm level: many different weight settings (the family of equivalent constructions) implement the *same* optimization algorithm. The function (GD on regression) is decoupled from the substrate (specific attention weights). Same logic as SODC's basin-hopping recovery. ^[inferred]

- ## Open Questions
  - **Does the result lift to large-scale Transformers?** Authors restrict to small models and simple regression problems. Whether GPT-3-style ICL on language is GD-based is empirically suggestive (Dai et al. 2023, "Why Can GPT Learn In-Context?") but not formally proven.
  - **Beyond linear models** — Proposition 2 lifts to nonlinear regression via kernel-on-MLP-representation, but the proof doesn't extend to GD on the MLP weights themselves. Zhmoginov 2022 (HyperTransformer) is flagged as a candidate next step.
  - **Noisy data + regularisation** — analyses assume noiseless teachers. Real ICL with noisy contexts and implicit weight regularisation is open.
  - **Softmax architecture caveat** — single-head softmax can't match GD; two-head softmax recovers it via head cancellation. Whether this "two-head correction" is what *actually* happens in trained softmax Transformers at scale is open.

- ## Memorable Lines
  - "*Trained Transformers become mesa-optimizers i.e. learn models by gradient descent in their forward pass.*" — Abstract
  - "*Transformers learn to learn by gradient descent based on their context.*" — Discussion (Section 5)
  - "*Solely through the pressure to predict correctly Transformers discover learning algorithms inside their forward computations, effectively meta-learning a learning algorithm.*" — Section 1

- ## Cited By (in this wiki)
  - [[wiki/projects/growing-networks]] — Transformers-as-universal-meta-learners is load-bearing for the [[NCA as Gardener]] thesis.
  - [[wiki/research/self-organising-digital-circuits]] (citation pending) — TMT inherits ICL-as-GD by being a Transformer.
