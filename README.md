# Research Wiki

Personal knowledge base on neural cellular automata, self-organising boolean circuits, modularity, and brain networks. Maintained as part of my postdoctoral research at the [Institute of Neuroinformatics (INI), University of Zurich / ETH Zurich](https://www.ini.uzh.ch/).

**Browse the wiki →** https://gabrielbena.github.io/logseq-wiki

---

## What this is

A [Logseq](https://logseq.com/) graph published as a static site using [logseq/publish-spa](https://github.com/logseq/publish-spa). Pages are distilled research notes — summaries of papers, concepts, and code I work with, maintained with Claude Code.

The idea (from Andrej Karpathy): instead of asking an LLM the same question repeatedly, compile the answer once into an interconnected page and keep it current. The wiki is a compiled artifact, not a chat log.

## What you will find here

| Namespace | Contents |
|---|---|
| `concepts/` | Ideas and mental models — modularity, self-organisation, neural computation |
| `research/` | Finished papers and projects (my own and closely related work) |
| `refs/` | Cited papers — abstract-level summaries with DOI / arXiv links |
| `code/` | Repos and tools relevant to the research |

## Quality signals

Every page carries two orthogonal quality signals:

- **Confidence** (0–1) — how well-sourced the content is. Abstract-only paper ingests score ~0.5; full PDF reads ~0.8; hand-curated synthesis ~0.9.
- **Lifecycle** — how much human attention the page has received. The states are `draft → in-review → reviewed → published`. Only pages at `published` reach this repo; everything below stays private.

Provenance markers flag the nature of each claim: `^[inferred]` means the claim goes beyond what the source explicitly states; `^[ambiguous]` means sources disagree.

## How it is built

The source of truth is a private Logseq vault. A GitHub Action in that vault fires on every push that touches `pages/wiki/**`, finds all pages with `lifecycle: published` plus all reference pages, assembles a minimal Logseq graph, and syncs it here. A second action in this repo then runs `logseq/publish-spa` and deploys to GitHub Pages.

No manual copying. Single source of truth.

## Authors

[Gabriel Béna](https://gabrielbena.github.io/) — postdoc at INI (UZH/ETH Zurich), working on neural cellular automata and self-organising boolean circuits.

[Claude](https://claude.ai/) — AI chad.
