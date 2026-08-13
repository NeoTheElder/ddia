# Map: DDIA learning artifacts <!-- wayfinder:map -->

## Destination

A repo (`~/ddia`, private personal GitHub) containing 12 self-contained interactive HTML chapter artifacts — one per DDIA 1st-edition chapter, with 2nd-edition (2025) updates folded in — plus an index page. Every chapter: Feynman-style explanation of **every concept** (walked from the book's actual section headings), figures, click-through (next/next/next) animations, backward/forward cross-references to concepts in other chapters, a core-takeaways section, and an MCQ quiz with an answer key + explanations at the end. Maximum detail — this is a long-term personal reference.

## Notes

- **Tracker**: local markdown. Tickets live in `tickets/`; claim = fill the `Assignee:` field; blocking = `Blocked by:` links in the ticket header. Frontier = open tickets with no open blockers and no assignee.
- **Execution override**: unlike wayfinder's plan-only default, this map **carries execution** — chapter tickets are resolved by *building the chapter*, one chapter per session.
- **Source of truth**: the book PDF at `reference/ddia-1st-edition.pdf` (gitignored). Each chapter session must Read the actual chapter's section headings from the PDF to guarantee concept coverage — never build from memory alone.
- **2nd-edition deltas**: consult `research/02-second-edition-deltas.md` in every chapter session; fold in what changed since 2017 where relevant.
- **Skills to consult per session**: `artifact-design` + `artifact-diagramming` + `dataviz` when building chapter pages; `frontend-design` for the template design; `/grilling` for decision tickets; `/prototype` for the pilot.
- **Template discipline**: after the pilot (Chapter 3) locks the template, chapter sessions follow it — structural changes go back through a decision, not ad-hoc drift.
- **User review**: every chapter ticket ends with the user reviewing the built page before close.
- **No Jira**: personal repo — no SCAL tickets, no co-author trailers in commits.

## Decisions so far

- Edition fixed as **1st-edition 12-chapter structure + 2nd-edition updates folded in** (charting session, 2026-08-12).
- Home fixed as **new dedicated repo `~/ddia`, pushed to private personal GitHub**; map lives in-repo (charting session, 2026-08-12).
- Format fixed as **one self-contained HTML file per chapter** (inline CSS/JS; animations, quizzes, relative cross-links; viewable offline / GitHub Pages / publishable as claude.ai Artifacts for convenience) (charting session, 2026-08-12).
- Production fixed as **pilot-first**: Chapter 3 (Storage & Retrieval, the most animation-demanding) built full-depth first, user reviews, template locks, then the other 11 chapters roll out one per session (charting session, 2026-08-12).
- Source fixed as **user's PDF** at `reference/ddia-1st-edition.pdf` — section-heading walk per chapter for completeness (charting session, 2026-08-12).

<!-- one line per closed ticket from here on: [ticket title](tickets/NN-file.md) — gist of the answer -->

- [Research: 2nd-edition deltas per 1st-edition chapter](tickets/02-research-2nd-edition-deltas.md) — 2nd ed is 14 chapters/4 parts (Ch 1 and Ch 12 split; middle chapters map one-to-one, shifted +1); Partitioning renamed Sharding; MapReduce demoted to teaching device (Spark/Flink + object storage replace it); cloud-native, vector-index/AI, and sync-engine/CRDT material added; findings with per-chapter detail in `research/02-second-edition-deltas.md`.

## Not yet specified

- **Hosting mode** — GitHub Pages (needs GitHub Pro for private repos, or making the repo public) vs plain `file://` browsing; resolves inside the bootstrap ticket once `gh` account/plan is known.
- **Shared animation library** — after 2–3 chapters exist, decide whether to extract common click-through-animation JS/CSS into a shared file (breaks strict self-containment) or keep duplicating inline.
- **Quiz sizing & depth calibration** — how many MCQs per chapter and how deep the explanations go; calibrated by user feedback on the pilot.
- **Revision workflow** — whether the repo later grows re-study aids (progress tracking on the index, re-quiz mode). Depends on how the reference gets used once several chapters exist.

## Out of scope

- **Preface, glossary, and appendices** — only the 12 numbered chapters.
- **Adopting the 2nd edition's restructured TOC** — deltas are folded into the 1st-edition structure, not a rebuild around the new edition.
- **claude.ai Artifact hosting as canonical** — the committed HTML files are canonical; publishing an artifact is a per-session viewing convenience only.
