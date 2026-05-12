# Research Wiki

Personal knowledge base on neural cellular automata, self-organising boolean circuits, modularity, and brain networks. Maintained as part of my postdoctoral research at [Imperial College London](https://www.imperial.ac.uk/).

**Browse the wiki →** https://gabrielbena.github.io/logseq-wiki

---

## What this is

A [Logseq](https://logseq.com/) graph published as a static site using [logseq/publish-spa](https://github.com/logseq/publish-spa). Pages are distilled research notes — summaries of papers, concepts, and code I work with, maintained with Claude Code.

The idea (from Andrej Karpathy): instead of asking an LLM the same question repeatedly, compile the answer once into an interconnected page and keep it current. The wiki is a compiled artifact, not a chat log.

## What you will find here

| Namespace | Contents |
|---|---|
|  | Ideas and mental models — modularity, self-organisation, neural computation |
|  | Finished papers and projects (my own and closely related work) |
|  | Cited papers — abstract-level summaries with DOI / arXiv links |
|  | Repos and tools relevant to the research |

## Quality signals

Every page carries two orthogonal quality signals:

- **** (0–1) — how well-sourced the content is. Abstract-only paper ingests score ~0.5; full PDF reads ~0.8; hand-curated synthesis ~0.9.
- **** — how much human attention the page has received. Only pages at  reach this repo; everything below that stays private.

Provenance markers flag inference:  means the claim goes beyond the source;  means sources disagree.

## How it is built

The source of truth is a private Logseq vault. A GitHub Action in that vault fires on every push that touches , finds all pages with  plus all reference pages, assembles a minimal Logseq graph, and syncs it here. A second action in this repo then runs  and deploys to GitHub Pages.

No manual copying. Single source of truth.

## Author

[Gabriel Béna](https://gabrielbena.github.io/) — postdoc at Imperial College London, working on neural cellular automata and self-organising boolean circuits.
