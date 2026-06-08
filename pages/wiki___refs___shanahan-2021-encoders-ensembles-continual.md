title:: wiki/refs/shanahan-2021-encoders-ensembles-continual
category:: reference
type:: external-ref
tags:: continual-learning, task-free, ensembles, representation-learning, key-matching
authors:: Shanahan, Murray; Kaplanis, Christos; Mitrović, Jovana
year:: 2021
venue:: arXiv
arxiv:: 2105.13327
citation-count:: 26
summary:: Task-free continual learning: a frozen pre-trained encoder + an ensemble of simple key-addressed classifiers; top-k key-matching + competitive specialisation beat any single member, with no catastrophic forgetting.
confidence:: 0.75
lifecycle:: draft
lifecycle-changed:: 2026-06-08
created:: 2026-06-04
updated:: 2026-06-08
sources:: arxiv:2105.13327 (full PDF read 2026-06-08)
wiki-generated:: true
ingest-mode:: full

- **Encoders and Ensembles for Task-Free Continual Learning** — Shanahan, Kaplanis & Mitrović (2021), arXiv:2105.13327 (DeepMind + Imperial). Full PDF read 2026-06-08.
	- **The source of growing-computation's "engrams = keys" framing** (project §Open Questions) — and of its hardest sub-problem (key-matching under local-only comms).

- ## Abstract (extracted)
	- We present an architecture that is effective for continual learning in an especially demanding setting, where task boundaries do not exist or are unknown, and where classes have to be learned online (with each example presented only once). To obtain good performance under these constraints, while mitigating catastrophic forgetting, we exploit recent advances in contrastive, self-supervised learning, allowing us to use a pre-trained, general purpose image encoder whose weights can be frozen, which precludes forgetting. The pre-trained encoder also greatly simplifies the downstream task of classification, which we solve with an ensemble of very simple classifiers. Collectively, the ensemble exhibits much better performance than any individual classifier, an effect which is amplified through specialisation and competitive selection…

- ## Architecture — the Ensemble Memory
	- A **frozen, pre-trained** general-purpose encoder `f` (self-supervised contrastive — ReLIC or BYOL, ResNet-50 on ImageNet; a VAE pre-trained on Omniglot for MNIST). Freezing `f` means the *representation never moves* → forgetting cannot enter through it. (The encoder must be pretrained on a *different* dataset than the CL benchmark.)
	- A downstream **ensemble of very simple single-layer classifiers** ("t-classifiers"). **Each classifier carries a fixed key** drawn from the encoder's latent space — **the key space *is* the encoder's latent space**, so the ensemble is literally an addressable *memory*.
	- **Inference = key-matching:** image → `z = f(x)` → retrieve the **top-`k` nearest keys** by cosine similarity → run `z` through those `k` classifiers → **weighted average** of their outputs, weight = cosine similarity to each key. `V_M(z) = Σ_i γ(key_i,z)·v_i(z) / Σ_i γ(key_i,z)`.
	- **Three unconventional ingredients** that confine updates to the current sample's class (the per-classifier anti-forgetting mechanism): a **dot-product loss** `L = −(y·ŷ)` (no softmax), a **tanh activation** `φ(x)=τ·tanh(x/τ)` (saturates toward `τ`), and a **sign-only optimiser** (discard gradient magnitude, step each weight by ±lr).

- ## Why the ensemble helps — specialisation + competitive selection
	- Mechanistically (§4): for a single classifier, *targeted* increases in the right output `E(i,i)` outpace *collateral* increases `E(i,j)` when data is roughly class-balanced — a weak anti-forgetting trend. **Averaging over many classifiers amplifies it.**
	- **top-`k` key-based selection induces specialisation**: a classifier is updated mostly by inputs whose encoding is near its key, so it specialises to a region of latent space; the keys exploit class-relevant clustering in the encoder's space. Competition + specialisation = the ensemble beats any member. (Performance degrades for `k > 32` — too much sharing dilutes specialisation; 1024 classifiers best, but 128 already beats prior SOTA.)
	- Framed in the lineage of **Selfridge's Pandemonium, Minsky's Society of Mind, blackboard systems, mixture-of-experts, and global-workspace architecture** ([[wiki/concepts/global-workspace-theory]]) — three maxims: *competition* (specialisation), *co-operation* (compositional combination), *collectivity* (wisdom of the crowd).

- ## Results (orientation)
	- Task-free, online (each example once), no task boundaries. On the hardest benchmark (20-way split CIFAR-100) the ensemble reaches 55.3% — improving prior SOTA (CN-DPM) by 30%+; large gains on CIFAR-10 (79.0%) and on the gradual-shift *Gaussian schedule*. Forgetting much lower than ER-MIR.

- ## Why it's relevant to [[wiki/projects/growing-computation]] — the engrams=keys hook (nuanced)
	- **This paper is where the project's "engrams = keys" idea comes from.** growing-computation §Open-Questions recasts "where to go back to for an old task" as *encoder-ensemble key-matching*: the encoder maps input → a latent point; classifiers whose **keys** match are top-`k` recruited; untrained ⇒ grow a new tile, already-trained ⇒ reactivate. So **task re-localisation = a key-match in latent space, and engrams are those keys.** The full read confirms the mechanism (keys in latent space, cosine top-`k`, specialisation).
	- **And it surfaces the project's hardest sub-problem.** Shanahan's key-match is **global** — compare the input embedding against *every* key. growing-computation must do it on a 2D mesh with **nearest-neighbour comms only** (project §"Key-matching with LOCAL-ONLY communication"). Candidate directions there: a key-similarity diffusion across the mesh, hierarchical coarse-to-fine routing, or a local rule approximating the global match via depth-in-time (the [[wiki/concepts/grow-and-learn]] oracle thread). ^[claude-synth]
	- **The divergence that matters:** Shanahan **freezes a *pretrained* encoder**; a self-organising substrate has *none* to freeze — it must *grow* the class-relevant latent structure the keys rely on, rather than inherit it. Inspiration for the *mechanism* (keys + top-`k` + specialisation), not its *frozen-encoder + global-lookup* assumptions. ^[claude-synth]

- ## Why it's relevant to [[wiki/concepts/grow-and-learn]] — a key-match selection oracle
	- Shanahan's competitive top-`k` key-lookup is a **selection oracle**: "which stored expert/key handles this input?" — the same decision slot as [[wiki/refs/wortsman-2020-supermasks-superposition]]'s entropy-min task inference, but answered by **global k-NN key-matching** instead of entropy. On the oracle spectrum it is a *which-configuration* selector. The internalisation question: can a *local* rule reproduce the global k-NN match (diffusion / depth-in-time) without comparing against every key? ^[inferred]

- ## Connections to Wiki
	- [[wiki/projects/growing-computation]] — the engrams=keys recast of Stage-3 task re-localisation; the local-only key-match open problem.
	- [[wiki/concepts/grow-and-learn]] — key-match as a *selection oracle* on the oracle spectrum.
	- [[wiki/refs/wortsman-2020-supermasks-superposition]] — sibling *freeze-the-representation* CL: Shanahan freezes a pretrained encoder + ensemble, SupSup freezes a random net + masks; both then need a selection step (key-match vs entropy-min).
	- [[wiki/refs/fernando-2017-pathnet]] — continual-learning-by-modularity cousin (freeze + reuse); ensemble competitive selection vs GA tournament.
	- [[wiki/concepts/modularity]] — specialisation + competitive selection across an ensemble is a functional-specialisation mechanism.
	- [[wiki/concepts/global-workspace-theory]] — Shanahan situates the ensemble in the workspace/pandemonium lineage; competition + broadcast.

- ## Open Questions / To Read
	- Without a pretrained encoder to freeze, what plays the role of the class-clustered latent space the keys exploit — must the substrate *grow* it, and how is forgetting then precluded? ^[claude-synth]
	- Can the global top-`k` key-match be realised under nearest-neighbour locality (the project's hardest open sub-problem)? ^[inferred]

- ## Cited By (in this wiki)
	- [[wiki/projects/growing-computation]] — Stage-3 key-matching / engrams-as-keys.
	- [[wiki/concepts/grow-and-learn]] — oracle-spectrum (key-match selector).
