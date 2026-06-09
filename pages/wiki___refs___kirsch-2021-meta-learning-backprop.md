title:: wiki/refs/kirsch-2021-meta-learning-backprop
category:: reference
type:: external-ref
tags:: meta-learning, learned-learning-rules, weight-sharing, message-passing, in-context-learning
authors:: Kirsch, Louis; Schmidhuber, Jürgen
year:: 2021
venue:: NeurIPS 2021
arxiv:: 2012.14905
citation-count:: 67
summary:: VSML: replace each weight with a tiny shared LSTM, so one local rule's messages *become* the learning algorithm; weight-sharing makes the meta-learned rule generalise to unseen datasets & I/O sizes.
confidence:: 0.78
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-08
updated:: 2026-06-08
sources:: arxiv:2012.14905 (full PDF read 2026-06-08)
wiki-generated:: true
ingest-mode:: full

- **Meta Learning Backpropagation And Improving It (VSML)** — Louis Kirsch & Jürgen Schmidhuber (2021), NeurIPS 2021. arXiv:2012.14905 (IDSIA/USI/SUPSI + KAUST). Full PDF read 2026-06-08.
	- Gabriel flagged this for *when meta-learners start to generalise* → how we'd like an [[NCA]] optimiser (e.g. [[SODC]]) to become **task / topology agnostic**. VSML's answer: **weight-sharing**.

- ## Abstract (extracted)
	- Many concepts have been proposed for meta learning with neural networks (NNs)… Our *Variable Shared Meta Learning (VSML)* unifies the above and demonstrates that simple weight-sharing and sparsity in an NN is sufficient to express powerful learning algorithms (LAs) in a reusable fashion. A simple implementation of VSML where the weights of a neural network are replaced by tiny LSTMs allows for implementing the backpropagation LA solely by running in forward-mode. It can even meta learn new LAs that differ from online backpropagation and generalize to datasets outside of the meta training distribution without explicit gradient calculation. Introspection reveals that our meta learned LAs learn through fast association in a way that is qualitatively different from gradient descent.

- ## VSML — the idea
	- Replace each *weight* of an NN with a tiny **LSTM (a "sub-RNN") whose parameters `V_M` are shared** across all of them; the per-weight LSTM *states* `V_L` carry the actual "weights" of the inner learning. So `|V_L| ≫ |V_M|` — many learned states, a handful of shared meta-parameters (the FWP/learned-learning-rule property married to a Meta-RNN's simplicity).
	- Three equivalent views (their Fig. 1): **(a)** one Meta-RNN with a *sparse shared* weight matrix; **(b)** **message-passing between RNNs** — the authors note this is *"related to Graph Neural Networks"*; **(c)** "complex neurons with learned updates," blurring weight vs activation.
	- The shared rule passes **forward messages `m→` and backward messages `←m`**, so both the neural forward computation *and the learning algorithm that updates it* live in the recurrent dynamics — "generalizing the dynamics of an NN trained by backpropagation," with **no explicit gradient calculation** at inference.
	- Slogan: *simple weight-sharing + sparsity is enough to express powerful, reusable learning algorithms.*

- ## Two studies
	- **Learning-algorithm cloning (§3.2).** Directly optimise `V_M` so the VSML RNN *reproduces backprop*: store a weight `w`+bias `b` in the state, compute `y = tanh(x)w+b`, and regress the forward/`Δw`/`Δb` toward the **backprop targets**. The rule then runs learning purely by unrolling the LSTM (87/90% MNIST, 76/80% Fashion-MNIST, deep/shallow). *This is supervising a shared local rule against backprop as a teacher* — a concrete instance of the [[wiki/concepts/grow-and-learn]] "oracle route" at its hardest rung.
	- **Meta-learning from scratch (§3.1, §4.2).** Meta-train `V_M` end-to-end (ES or backprop-through-the-inner-loop) to minimise online prediction loss. The learned LA learns **online, one example at a time, faster than SGD/Adam**, and crucially **generalises to datasets outside the meta-training distribution** (meta-train on MNIST → test on Fashion-MNIST, EMNIST, Kuzushiji, Random, Sum-Sign). A standard (un-shared) Meta-RNN heavily *overfits* in the same setting.

- ## The generalisation result — task / topology agnostic via weight-sharing
	- **Why it generalises:** a plain Meta-RNN has `|V_M| = O(N²)` and is overparameterised → it encodes *task-specific* solutions and overfits. VSML's **variable sharing** (small `V_M`, reused coordinate-wise) forces a *general* LA. "VSML is the first neural meta learner without hard-coded backpropagation that shows such strong generalization."
	- **§4.3 (the part Gabriel wants):** the *same* `V_M` works under varying input/output sizes, and the meta-learned LA is **invariant to the order of inputs/outputs and to random projections** — meta-test on 3/4/5/10 classes, 14×14/28×28/32×32 pixels, random projection, shuffled inputs, all comparable to the reference. "The invariance to random projections suggests that we have meta learned a learning algorithm *beyond transferring learned representations*." This is the concrete sense in which a shared local rule becomes **task/topology agnostic**.
	- **Introspection (§5):** the LA learns by **fast association** — confident correct predictions after a few examples — *"qualitatively different from gradient descent"* (the "improving it" of the title).
	- **Honest caveats (§7):** proof-of-concept scale; premature convergence at meta-test; cost `O(WN²)` if one sub-RNN per weight; **meta-optimisation hits local minima as inner-loop depth grows (credit assignment over many ticks), partly mitigated by *diverse meta-task distributions* and by ES for longer horizons.** (That diversity-helps remark is the seed that [[wiki/refs/kirsch-2022-general-purpose-icl]] develops into a full memorise→generalise *transition*.)

- ## Why it matters here (nuanced)
	- **The NCA inductive bias is the generalisation mechanism.** VSML is *explicitly* a shared-local-rule, message-passing system ("related to GNNs"), and its generalisation comes from the **same weight-sharing an [[NCA]] uses** (one rule on every cell). So the wish "make our NCA optimiser task/topology-agnostic" and VSML's result are the *same bet* — share the rule, and the learned algorithm stops memorising. Rhyme, not identity: VSML shares an LSTM *per weight*; an NCA shares a rule *per cell*. Its reference list sits in this lineage (Mordvintsev Growing-NCA, Codd CA, Najarro/Risi Hebbian, Randazzo/Mordvintsev **MPLP**). ^[claude-synth]
	- **It grounds the [[wiki/concepts/grow-and-learn]] oracle route's hardest rung.** "A local rule approximating backprop" is no longer hypothetical: VSML *clones* backprop into a shared local rule's forward dynamics (the supervise-don't-condition move) **and** meta-learns rules that improve on it. ^[claude-synth]
	- **It's the [[wiki/concepts/in-context-learning]] "learning rule" made literal:** the message-passing dynamics *are* the learning process; deployment needs no off-substrate gradients (BPTT only at meta-training) — the locality bonus that page argues for. ^[inferred]
	- **The contrast with [[wiki/refs/kirsch-2022-general-purpose-icl]]:** VSML reaches generality via *strong* inductive bias (sharing); GPICL via *minimal* bias + heavy *task diversity*. Two routes to one general LA — and the NCA/SODC route is VSML's. ^[claude-synth]

- ## Connections to Wiki
	- [[wiki/concepts/in-context-learning]] — VSML as a learned learning algorithm living in recurrent dynamics; the "learning rule" half made concrete.
	- [[wiki/concepts/grow-and-learn]] — grounds the oracle route's "approximate backprop" rung (cloning) + the shared-rule learning-process framing.
	- [[wiki/refs/kirsch-2022-general-purpose-icl]] — sibling Kirsch paper; strong-inductive-bias (sharing) vs minimal-bias-plus-task-diversity routes to a general LA.
	- [[wiki/concepts/neural-cellular-automata]] — same shared-local-rule + message-passing inductive bias; weight-sharing as the generalisation mechanism.
	- [[wiki/refs/von-oswald-2022-transformers-icl-gd]] — both show a learning algorithm emerging in a network's forward dynamics (GD-in-attention vs LA-in-shared-LSTM).
	- [[wiki/projects/self-organising-boolean-circuits]] — the NCA-as-optimiser whose task/topology-agnosticism this paper's weight-sharing argument speaks to (cf. SODC scale-freedom from random-topology training).
	- [[NORACL]] · [[wiki/refs/song-2024-prospective-configuration]] — fellow "learn / approximate the update rule locally" references on the oracle spectrum.

- ## Open Questions / wiki-gaps
	- **MPLP** (Randazzo, Niklasson & Mordvintsev 2020, "Learning a Message Passing Learning Protocol", arXiv:2007.00970) — the NCA-group's direct cousin to VSML; no wiki page yet. ^[wiki-gap]
	- Does VSML-style sharing transfer to a *non-differentiable / on-substrate* setting (the project's growth case), or does it rely on the differentiable inner-loop it shares with backprop? ^[inferred]

- ## Cited By (in this wiki)
	- [[wiki/concepts/in-context-learning]]
	- [[wiki/concepts/grow-and-learn]]
