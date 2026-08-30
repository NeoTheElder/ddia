# Map: DDIA learning artifacts <!-- wayfinder:map -->

## Destination

A repo (`~/ddia`, private personal GitHub) containing 12 self-contained interactive HTML chapter artifacts — one per DDIA 1st-edition chapter, with 2nd-edition (2025) updates folded in — plus an index page. Every chapter: Feynman-style explanation of **every concept** (walked from the book's actual section headings), figures, click-through (next/next/next) animations, backward/forward cross-references to concepts in other chapters, a core-takeaways section, and an MCQ quiz with an answer key + explanations at the end. Maximum detail — this is a long-term personal reference.

## Notes

- **Tracker**: local markdown. Tickets live in `tickets/`; claim = fill the `Assignee:` field; blocking = `Blocked by:` links in the ticket header. Frontier = open tickets with no open blockers and no assignee.
- **Execution override**: unlike wayfinder's plan-only default, this map **carries execution** — chapter tickets are resolved by *building the chapter*, one chapter per session.
- **Source of truth**: the book PDF at `reference/ddia-1st-edition.pdf` (gitignored). Each chapter session must Read the actual chapter's section headings from the PDF to guarantee concept coverage — never build from memory alone.
- **2nd-edition deltas**: consult `research/02-second-edition-deltas.md` in every chapter session; fold in what changed since 2017 where relevant.
- **Skills to consult per session**: `artifact-design` + `artifact-diagramming` + `dataviz` when building chapter pages; `frontend-design` for the template design; `/grilling` for decision tickets; `/prototype` for the pilot.
- **Template discipline**: the template is locked (`docs/template.md`) — chapter sessions follow it; structural changes go back through a decision, not ad-hoc drift.
- **Enrichment passes (standing)**: detailed study will surface sections wanting extra figures/steppers. Enrichments are additive, requestable on any chapter at any time, and don't reopen chapter tickets or the template.
- **User review**: every chapter ticket ends with the user reviewing the built page before close.
- **No Jira**: personal repo — no SCAL tickets, no co-author trailers in commits.

## Decisions so far

- Edition fixed as **1st-edition 12-chapter structure + 2nd-edition updates folded in** (charting session, 2026-08-12).
- Home fixed as **new dedicated repo `~/ddia`, pushed to private personal GitHub**; map lives in-repo (charting session, 2026-08-12).
- Format fixed as **one self-contained HTML file per chapter** (inline CSS/JS; animations, quizzes, relative cross-links; viewable offline / GitHub Pages / publishable as claude.ai Artifacts for convenience) (charting session, 2026-08-12).
- Production fixed as **pilot-first**: Chapter 3 (Storage & Retrieval, the most animation-demanding) built full-depth first, user reviews, template locks, then the other 11 chapters roll out one per session (charting session, 2026-08-12).
- Source fixed as **user's PDF** at `reference/ddia-1st-edition.pdf` — section-heading walk per chapter for completeness (charting session, 2026-08-12).

<!-- one line per closed ticket from here on: [ticket title](tickets/NN-file.md) — gist of the answer -->

- [Chapter 6: Partitioning](tickets/09-chapter-06-partitioning.md) — built to template and approved; 6 steppers (key-range hot spot, hash + compound key, local vs global index, hash mod N, fixed-partition join, request routing), 5 figures, 14-question quiz; ch 6 definitions filled; headless-Chrome stepper screenshots adopted as pre-push visual QA.
- [Chapter 7: Transactions](tickets/10-chapter-07-transactions.md) — built to template and approved; 6 steppers (lost update, read committed, MVCC snapshot, write skew, 2PL + deadlock, SSI tripwires), 5 figures, 15-question quiz; ch 7 definitions filled; full-step screenshot QA (43 shots) before first push.
- [Chapter 8: The Trouble with Distributed Systems](tickets/11-chapter-08-trouble-with-distributed-systems.md) — built to template and approved; 5 steppers (no-response ambiguity, switch queueing, LWW inversion, TrueTime commit wait, fencing tokens), 4 figures, 2 tables, 15-question quiz; ch 8 definitions filled.
- [Chapter 9: Consistency and Consensus](tickets/12-chapter-09-consistency-and-consensus.md) — built to template and approved; 6 steppers (linearizable register, quorum non-linearizability, Lamport timestamps, CAS via log, 2PC, epochs/quorums), 4 figures, 2 tables, 16-question quiz; ch 9 definitions filled.

- [Chapter 5: Replication](tickets/08-chapter-05-replication.md) — built to template and approved; Part II intro folded in as framing; 6 steppers (sync/async, failover, lag anomalies, write conflict, quorums, shopping-cart merge), 13 figures, 15-question quiz; ch 5 definitions filled.
- [Chapter 4: Encoding and Evolution](tickets/07-chapter-04-encoding-and-evolution.md) — built to template and approved; 6 steppers (rolling upgrade, binary bytes, field tags, Avro resolution, lost field, RPC), 7 figures, 14-question quiz; ch 4 definitions filled.

- [Bootstrap the ddia repo](tickets/01-bootstrap-repo.md) — PDF at `reference/ddia-1st-edition.pdf`; section-level TOC extracted to `reference/toc.md` (the completeness checklist); private repo pushed to https://github.com/NeoTheElder/ddia; hosting = local `file://` browsing (Pages deferred); pypdf venv at `.venv/` for chapter text extraction.
- [Chapter 2: Data Models and Query Languages](tickets/06-chapter-02-data-models-query-languages.md) — built to template and approved; 6 steppers (résumé, model history, declarative, MapReduce, Cypher, Datalog), 14-question quiz; ch 2 definitions filled.
- [Chapter 1: Reliable, Scalable, and Maintainable Applications](tickets/05-chapter-01-reliable-scalable-maintainable.md) — built to template and approved; Twitter fan-out and percentiles steppers, 5 figures, 14-question quiz; ch 1 definitions filled.
- [Pilot: Chapter 3 (Storage and Retrieval) + template lock](tickets/04-pilot-chapter-03-template-lock.md) — chapter built and approved; template locked at `docs/template.md` (page anatomy, ember/cyan color language, stepper + quiz mechanics, build process); enrichment passes established as a standing additive workflow.
- [Cross-reference scheme (concept anchor registry)](tickets/03-crossref-scheme.md) — anchors are `chNN-<slug>.html#<concept-slug>`; registry `concepts.json` pre-seeded with all 169 concepts (definitions filled per chapter build); stub pages hold every chapter's final URL so links never 404; inline refs with hover-definition tooltips.
- [Research: 2nd-edition deltas per 1st-edition chapter](tickets/02-research-2nd-edition-deltas.md) — 2nd ed is 14 chapters/4 parts (Ch 1 and Ch 12 split; middle chapters map one-to-one, shifted +1); Partitioning renamed Sharding; MapReduce demoted to teaching device (Spark/Flink + object storage replace it); cloud-native, vector-index/AI, and sync-engine/CRDT material added; findings with per-chapter detail in `research/02-second-edition-deltas.md`.

## Not yet specified

- **Shared animation library** — after 2–3 chapters exist, decide whether to extract common click-through-animation JS/CSS into a shared file (breaks strict self-containment) or keep duplicating inline.
- **Ch 3 enrichment backlog** — sections the user's detailed study flags for extra figures/steppers; first suspected candidate: "B-tree optimizations". Graduates to concrete enrichment work as study proceeds.
- **Revision workflow** — whether the repo later grows re-study aids (progress tracking on the index, re-quiz mode). Depends on how the reference gets used once several chapters exist.

## Out of scope

- **Preface, glossary, and appendices** — only the 12 numbered chapters.
- **Adopting the 2nd edition's restructured TOC** — deltas are folded into the 1st-edition structure, not a rebuild around the new edition.
- **claude.ai Artifact hosting as canonical** — the committed HTML files are canonical; publishing an artifact is a per-session viewing convenience only.
