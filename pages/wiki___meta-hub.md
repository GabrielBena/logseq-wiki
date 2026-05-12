title:: Wiki Meta Hub
alias:: wiki/meta, wiki-meta
category:: hub
type:: hub
wiki-generated:: true
lifecycle:: published
lifecycle-changed:: 2026-05-12
updated:: 2026-05-11
exclude-from-graph-view:: true

- Hub for meta-pages in `wiki/meta/` — the wiki's own design, conventions, and infrastructure-adjacent decisions.

- ## Workflow & Conventions
  - [[wiki/meta/handbook]] — How to use this wiki: philosophy, three-tier file model, lifecycle states, review workflow, project workflow. The canonical user-facing reference.

- ## Publishing & External Presence
  - [[wiki/meta/github-pages-site]] — Gabriel's academic website (Jekyll/al-folio); hosts distill-format paper blog posts (UNCA, SODC).
  - [[wiki/meta/wiki-publishing]] — Architecture and pipeline for publishing `pages/wiki/` publicly via logseq/publish-spa. Push-sync GH Action from private vault to `GabrielBena/logseq-wiki`; gated by `lifecycle:: published`.
  - [[wiki/meta/wiki-home]] — Landing page stub for the public wiki SPA. Needs content before promotion to `published`.
