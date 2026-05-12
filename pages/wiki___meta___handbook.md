title:: wiki/meta/handbook
category:: reference
type:: reference
tags:: meta, wiki, workflow, methodology, conventions
summary:: How to use this wiki — philosophy (L1/L2 split, RAM vs HD), workflow (skills, weekly routine), conventions (page types, lifecycle), and the three-tier file model.
confidence:: 0.90
lifecycle:: published
lifecycle-changed:: 2026-05-11
lifecycle-reason:: Hand-curated operational manual; user-promoted on creation
created:: 2026-05-11
updated:: 2026-05-11
sources:: distilled from `.claude/skills/wiki-conventions/SKILL.md`, `.claude/skills/llm-wiki.md`, prior `pages/Wiki Home.md`, lived workflow
wiki-generated:: true
exclude-from-graph-view:: true

- ## What This Is
	- A personal knowledge base maintained with Claude Code inside Logseq.
	- The idea (from Andrej Karpathy): instead of asking an LLM the same question repeatedly, compile the answer once into an interconnected page and keep it current. The wiki is a compiled artifact — not a chat log.
	- Think of it as the difference between RAM (asking Claude each time) and a hard drive (writing it down once, reading it forever).
- ## The Three-Tier File Model
	- The vault is split into three tiers by audience, distinguished by location and an underscore-prefix rule:
	- | Tier | Location | Convention | What lives here |
	  |---|---|---|---|
	  | **Machine state** | `wiki/_*` | underscore prefix | `_manifest.json`, `_log.md`, `_lint_report.md`, `_archives/`, `_tools/`, `_raw/`, `_meta/` — written and read by Claude/scripts only |
	  | **Navigation** | `pages/Wiki.md` + `pages/wiki/<namespace>-hub.md` + `pages/wiki/hot.md` | no underscore; top hub titled `Wiki Index` (alias `wiki`); per-namespace hubs titled `Wiki <Ns> Hub` (alias `wiki/<ns>`); hub filename must not collide with the sibling `pages/wiki/<ns>/` subfolder | top-level hub, per-namespace hubs, hot cache — what you browse |
	  | **Content** | `pages/wiki/<namespace>/<slug>.md` | namespaced title `wiki/<ns>/<slug>` | the actual pages |
	- **The rule:** anything starting with `_` is for Claude. Anything else is for you. If something I use daily is under `wiki/_*`, that's a misplacement and it should move to `pages/`.
	- Personal/journal-like content (drafts, source PDFs, scratchpads) lives under `pages/` (no `wiki/` prefix) and `journals/`. These are *not* wiki pages — they're the raw inputs the wiki distills from.
- ## The L1 / L2 Split
	- Not everything belongs in the wiki. The knowledge system has two layers:
	- **L1 — always loaded** → `CLAUDE.md` and `.claude/memory/` files
		- Critical rules, daily-reference gotchas, identity, formatting standards, credentials references
		- Use when: *"making a mistake without this would be embarrassing or harmful"*
	- **L2 — this wiki** → `pages/` and `journals/`
		- Projects, workflows, research, concepts, lessons learned, ingested external sources
		- Use when: *"missing this is inconvenient but recoverable"*
	- **The signal:** if you find yourself explaining the same thing to Claude twice, it belongs in the wiki. If you find yourself referencing a wiki page every single session, it belongs in L1.
	- **Hard rule:** never put credentials in wiki pages. The wiki is git-tracked. Use L1 memory for credential references (e.g. the Semantic Scholar API key reference in `.claude/projects/.../memory/reference_semantic_scholar_api.md`).
- ## Skills Quick Reference
	- Run any skill by typing `/skill-name` in Claude Code. All skills live in `.claude/skills/`.
	- ### Routine
		- | Skill | When to use |
		  |---|---|
		  | `/weekly` | **One-shot weekly orchestrator.** Detects new notes/journals, runs `/wiki-ingest`, auto-detects mentioned repos+papers, runs `/code-ingest`+`/paper-ingest`, weaves links, heals manifest drift, reports. Default Sunday command. |
		  | `/wiki-status` | Dashboard: health, freshness, drift, lifecycle distribution, top hubs |
		  | `/wiki-ingest` | Point at a specific source (page, journal, PDF) to distill it. Use directly only for one-offs; otherwise let `/weekly` drive it. |
		  | `/wiki-query` | Ask a question against the wiki ("what do I know about X?") |
		  | `/cross-linker` | Find unlinked mentions and weave them into `[[links]]` |
	- ### Targeted ingestion
		- | Skill | When to use |
		  |---|---|
		  | `/paper-ingest <id>` | Pull a specific paper (arXiv/DOI) into `wiki/refs/`. Defaults to abstract mode (cheap); `full` reads the PDF. |
		  | `/code-ingest <repo>` | Pull a GitHub repo into `wiki/code/`. Defaults to shallow (README + metadata); `structure` adds file tree; `deep` reads source files. |
	- ### Maintenance
		- | Skill | When to use |
		  |---|---|
		  | `/wiki-setup` | First-time bootstrap. Creates `wiki/` infrastructure, manifest, index. |
		  | `/wiki-lint` | Audit: broken links, credentials, orphans, schema errors |
		  | `/wiki-update` | Re-index changed pages and heal manifest drift (lighter than `/weekly`) |
		  | `/wiki-rebuild` | Nuclear option: archive + full re-ingest from scratch |
		  | `/tag-taxonomy` | Audit, normalize, add canonical tags |
		  | `/llm-wiki` | Foundation reference (templates, schemas) — read by other skills, not invoked directly |
- ## Everyday Workflow
	- **Capture** — drop quick notes into the daily journal (or `wiki/_raw/` for things you want to formalize). Don't worry about structure. Paste GitHub URLs, arXiv IDs, paper DOIs freely — `/weekly` will pick them up.
	- **Ingest** (weekly) — at the end of the week, run `/weekly`. It detects every new/modified note, distills them into wiki pages, auto-finds the GitHub repos and papers you cited, and pulls them in too. Single command.
	- **Cross-link** — `/weekly` runs `/cross-linker` automatically. Run it manually after a big ingest if you want extra link suggestions.
	- **Query** — ask questions with `/wiki-query`. "What do I know about X?" "Which pages link to `[[Y]]`?"
	- **Health checks** — `/wiki-status` is fast; run it whenever you want a dashboard. Run `/wiki-lint` after bulk imports — fix CRITICALs immediately.
- ## The Weekly Routine (recommended)
	- One command at the end of the week:
	- `/weekly`
	- That's it. The skill walks 6 stages: pre-flight → source delta → wiki-ingest → resource detection → batch confirm → sub-ingests → cross-link → status. You'll see one confirmation prompt (the batch of detected repos+papers) and one summary at the end.
	- Throwaway URLs in journals are fine — at the confirm step you can `select` instead of approving the whole batch.
	- For one-off ingests in the middle of the week (e.g., "I want to read this paper now"), use the targeted skills directly: `/paper-ingest arXiv:2401.04125 full`.
- ## What Makes a Good Wiki Page
	- **A strong `summary::` line (≤200 chars)** — answers "what is this page about?" in one sentence. This is what shows up in search/retrieval.
	- **Provenance markers** — every claim should be honest about its origin:
		- No marker = extracted directly from a source (default)
		- `^[inferred]` = synthesized — treat with skepticism
		- `^[ambiguous]` = sources disagree
	- **At least 2 wikilinks** — an isolated page is a dead page. Links must go to *peer* content pages (other `wiki/refs/*`, `wiki/concepts/*`, `wiki/research/*`, `wiki/code/*`). Links to hubs/meta don't count toward the minimum.
	- **`confidence::` in [0.0, 1.0]** — see the Confidence Scoring section in `/llm-wiki`. Stub: 0.20–0.30. Abstract-only: 0.45–0.50. Full paper: 0.70–0.85. Hand-curated synthesis: 0.90+.
	- **`lifecycle::`** — see [§ Lifecycle](#lifecycle) below.
	- **`ingest-mode::`** for refs and code — `abstract` / `full` / `shallow` / `structure` / `deep` / `needs-fetch`.
- ## Page Types
	- `concept` — an idea, theory, or mental model worth preserving
	- `entity` — a person, tool, project, or organization
	- `skill` — a procedure, workflow, or technique
	- `reference` (also `external-ref`, `code-repo`) — a summary of a specific external source
	- `synthesis` — cross-cutting analysis connecting multiple sources
	- `hub` — a structural navigator listing all pages in a domain (auto-created at 3+ pages per namespace)
	- `feedback` — a gotcha, lesson-learned, or issue with `severity::`
	- `MOC` — Map of Content; conceptual, not structural
- ## Lifecycle
	- Every wiki page carries a `lifecycle::` state. It tracks how much **human attention** the page has received — orthogonal to `confidence::`, which tracks **source quality**. You need both: a high-confidence page from a great source can still be untrusted if you've never read what Claude wrote about it, and a hand-curated synthesis can be trustworthy even when its underlying sources are sparse.
	- ### State machine
		- ```
		  draft → in-review → reviewed → published
		                                      ↓
		                                  archived
		  ```
		- `in-review` is a **durable working state** — it persists across review passes (Claude addressing your comments) until you manually promote. Whose turn it is is derived from page content, not lifecycle (see [Review workflow](#Review-workflow)).
	- ### States
		- | State | Set by | Meaning |
		  |---|---|---|
		  | `draft` | any ingest skill (auto) | Default for new pages. Once a page enters `in-review`, it does NOT drop back to `draft`. |
		  | `stub` | `/paper-ingest` when a paper has no abstract or can't be found | Pre-draft placeholder; lower trust than draft. |
		  | `in-review` | **you** (or auto-detected: see "Review workflow") | "I've added comments — Claude please address" *or* "Claude has addressed; my turn to re-read." Durable until you promote. |
		  | `reviewed` | **you** (manually) | "I read it and it looks accurate." |
		  | `published` | **you** (manually) | "I trust this and it's public. Age never demotes it." |
		  | `archived` | you, or auto when superseded | Terminal. Pair with `superseded-by:: [[wiki/namespace/new-page]]`. |
	- `stale` is **not** a state — it's a computed overlay (`is_stale = (today − updated::) > 90 days`). `/wiki-lint` flags stale pages but never edits `lifecycle::`.
	- ### Why "human only" for `reviewed` / `published`
		- The whole point is to surface what *you* have actually engaged with vs. what's still raw machine output. If skills auto-promoted, the distinction collapses.
		- That said — "human only" is about the **decision**, not the typing. If you tell Claude "promote `wiki/research/dynamics-specialization` to published", that's your decision; Claude just executes the file edit. What's *not* fine is asking Claude to choose which pages to promote — that's offloading the judgment.
	- ### Promotion guidance
		- **`reviewed`** is the everyday promotion. After you read a wiki page and find it accurate, bump it. Cheap, reversible.
		- **`published`** is the terminal gate. Content you trust deeply enough to be public — your own papers, canonical references you've worked with for years. Pages at this state are synced to the public wiki on the next `/wiki-publish` run.
		- **`archived`** is when the page has been replaced by a better one (set `superseded-by::`) or the topic is no longer relevant.
	- ### Optional metadata
		- `lifecycle-changed:: 2026-05-08` — bump whenever you change state.
		- `superseded-by:: [[wiki/namespace/new-page]]` — required when archiving a page that's been replaced.
	- ### Per-pass tracking (in-review only — set by `/wiki-review`)
		- `review-pass:: N` — counter, incremented per Claude pass.
		- `review-pass-changed:: <ISO date>` — when the last pass occurred.
		- `review-pass-result:: pass-N-addressed (M of M)` or `pass-N-partial (M of K)` — outcome of last pass.
		- These properties exist *underneath* `lifecycle:: in-review` and never change the lifecycle. `/wiki-status` uses them to surface the *Awaiting re-read* backlog.
- ## Review workflow
	- **Annotation scheme.** Add comments inline using markdown blockquote:
		- ```
		  - The thesis pivots toward self-organisation in Part II ^[inferred]
		    > G: not quite — Part II isn't a pivot, it's the *answer* to Part I. Reframe.
		  ```
		- The `> ` prefix marks the line as **your voice**. Claude never writes `> ` blocks in distilled content (source quotes use code fences or italics), so any `> ` line is unambiguously yours. The `G:` is optional, useful only if multiple people review.
	- **Section-level feedback.** For whole-section critique or new direction proposals, use a `## Review Notes` section at the end of the page:
		- ```
		  - ## Review Notes
		    - The "self-organisation side" framing feels too clean. Pessoa would call this a metaphor; needs hedging.
		    - Missing: Edelman's degeneracy as a third pillar.
		  ```
		- Anything in this section is yours. Anything outside is Claude's distillation.
	- **The cycle (lifecycle stays `in-review` throughout).**
		1. You add `> ` comments / `## Review Notes` → page enters `lifecycle:: in-review` (auto-detected; you don't have to set it).
		2. Run `/wiki-review <page>` (or wait for `/weekly` to pick it up).
		3. **Effort-tier handling:**
			- *cheap / light* edits (typos, wikilink-adds, hedges, single-fact rewrites) → Claude applies silently, shows diffs in the batched end-of-page summary.
			- *medium* edits (semantic reframes, multi-line rewrites) → Claude proposes; you `[a]ccept`, `[m]odify`, `[s]kip`, or `[d]iscuss`.
			- *expensive* (re-read PDF, ingest new paper) → Claude asks *before* doing the work.
		4. Claude removes resolved `> ` blocks and updates the per-pass tracking properties (`review-pass::`, `review-pass-result::`, `review-pass-changed::`). **`lifecycle::` stays `in-review`.**
		5. The page is now in your *Awaiting re-read* queue (visible in `/wiki-status`). Re-read in Logseq:
			- If something's off → add new `> ` comments. Next `/weekly` re-queues the page.
			- If happy → manually bump `lifecycle:: reviewed`.
	- **Why `in-review` doesn't auto-revert to `draft`.** Easier to lose track of pages that have rotated through Claude than to see them clearly on the in-review backlog. The lifecycle stays load-bearing for *your* attention queue; per-pass tracking is what Claude updates.
	- **Auto-detection.** `/wiki-update` and `/weekly` scan for hash-delta'd pages containing `> ` lines and auto-flag them as `in-review`. You don't have to manually bump lifecycle — just write your comments and save.
- ## Projects — living-document collaborative workspace
	- The `wiki/projects/` namespace is for **artifacts in genesis** (papers, grant proposals, talks, anything with an external deliverable). It's structurally different from `wiki/research/` because the artifact doesn't exist yet — the wiki page is the *workshop*, not a mirror of finished work.
	- ### When to use a project page
		- A new paper you're conceptualising (e.g. a position paper emerging from the thesis)
		- A grant proposal being drafted
		- A talk being scaffolded
		- Any output that will eventually leave the wiki for an external editor (LaTeX, Google Doc, journal submission system) — the project page is the planning surface, not the prose
	- ### Workflow stages
		- **Seed.** Drop a free-form note in `pages/<project-name>.md` or in a journal under a `[[wiki/projects/<project-name>]]` tag block. No structure required — just dump thoughts, references, framing.
		- **Distill.** Run `/project-update <name>`. Claude reads the seed + any tagged journal entries since the last update, asks 2-3 clarifying questions, and writes/updates `pages/wiki/projects/<name>.md`. This is just `/wiki-ingest` tuned for the project tag + a fixed page template.
		- **Iterate.** Add `> G:` review comments directly on the wiki project page. `/wiki-review` (or the next `/weekly`) addresses them in the ping-pong cycle you'd use for any other wiki page. Same mechanism, no new rules.
		- **Capture mid-week thoughts.** Drop bullets in any journal under `[[wiki/projects/<name>]]`. They'll be picked up on the next `/project-update` or `/weekly`.
		- **Ship.** When the artifact is externally published (arxiv, journal, granted, presented), bump the project page to `lifecycle:: archived` with `superseded-by:: [[wiki/research/<name>]]` and create the research mirror as you would for any finished research output.
	- ### Author voice vs Claude distillation
		- The project page has two distinct surfaces:
			- **`## Argument`** (or **`## Aims`** for a grant, **`## Outline`** for a talk) — your voice. Claude reads, never edits without an explicit request. Claims you stand behind carry `^[author]`.
			- **`## Synthesis`** — Claude's voice. Cross-links to wiki refs, summarises related literature, drafts counter-arguments for you to react to. Marked `^[claude-synth]`.
		- Plus standard sections (Open Questions, Selected References with one-line annotations, Decisions log).
	- ### What the page contains — and what it doesn't
		- The project page is **not** the paper. It's the *planning map*: thesis statement, argument structure, references with rationale, open questions, decisions log. Prose drafting happens in your real writing tool (LaTeX, Word, whatever).
		- Structure is **loose by design** — different projects want different sections. Position paper = thesis + sources + counters. Grant = aims + budget + timeline. The shared scaffolding is just: frontmatter, Status, Sources, Open Questions, Argument (yours), Synthesis (Claude's).
	- ### Claude's active vs passive role on projects
		- **Active by default:** retrieval, cross-linking, summarisation, refreshing the page from raw input, lit-search on request, surfacing contradictions in your own notes, drafting counter-arguments.
		- **Passive (only on explicit request):** generating new claims/theses, making editorial decisions, drafting the actual paper prose. New ideas come from you and the literature, not from Claude's prior.
	- ### Tag convention recap
		- Journal entries tagged with `[[wiki/projects/<name>]]` (full namespace wikilink) are picked up by `/project-update` and `/weekly`. This is the single signal — no parallel mirror, no `_todo.md`.
- ## What Not To Put Here
	- **Credentials, tokens, passwords** — never. Use L1 memory for references; a password manager for the secrets themselves.
	- **Ephemeral notes** — daily tasks, meeting agendas, fleeting thoughts go in journals, not wiki pages.
	- **Exact copies of external documents** — summarize and link. The wiki is for distilled knowledge.
	- **Everything** — a focused, well-linked 50-page wiki is more valuable than a sprawling 500-page one.
- ## Building Forward
	- **Let journals feed the wiki** — write freely; `/weekly` distills them.
	- **Grow hubs as namespaces fill** — when a domain hits 3+ pages, a hub is created automatically. These become navigation anchors.
	- **Review stale pages** — `/wiki-lint` flags pages not updated in 90 days. Prompt to re-evaluate or promote.
	- **Migrate hot knowledge to L1** — if you reference a wiki page in every session, extract its key rule into `.claude/memory/`.
	- **Trust the graph view** — Logseq's graph view shows the shape of your knowledge. Isolated clusters reveal orphans; dense hubs reveal real depth.
- ## Git Tracking
	- This vault is tracked in git. See [[Wiki Git Setup]] for:
		- What commits (pages, journals, manifest, skills, taxonomy) vs. what doesn't (`_raw/`, `.recycle/`, credentials)
		- Logseq's auto-git on Linux (hooks, not a plugin), correct setup for Windows + WSL
		- Security checklist before first push
- ## Where to Find Current State
	- This page is the *evergreen* manual. For *current* state:
		- `[[wiki]]` (top hub) — page counts, lifecycle distribution, current namespaces
		- `[[wiki/hot]]` — recent activity, active threads, key takeaways
		- `wiki/_manifest.json` — machine-readable state (page graph, hashes, stats)
		- `wiki/_log.md` — append-only operation log
