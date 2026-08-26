# Pilot: Chapter 3 (Storage and Retrieval) + template lock

- **Type**: wayfinder:prototype (HITL)
- **Status**: closed (2026-08-26)
- **Assignee**: yagyesh (pilot session, 2026-08-26)
- **Blocked by**: [01-bootstrap-repo](01-bootstrap-repo.md), [02-research-2nd-edition-deltas](02-research-2nd-edition-deltas.md), [03-crossref-scheme](03-crossref-scheme.md)

## Question

Build `chapters/ch03-storage-and-retrieval.html` full-depth as the pilot, and through user review lock the **chapter template** every other chapter follows.

Chapter 3 is the stress test: hash indexes, SSTables/LSM-trees (memtable flush, compaction, merging), B-trees (page splits), B-tree-vs-LSM trade-offs, secondary indexes, in-memory stores, OLTP vs OLAP, star/snowflake schemas, column storage, compression, materialized views — the most animation-demanding chapter in the book.

Template dimensions to lock via the pilot:

- **Page structure**: concept sections (Feynman explanation → figure → animation → cross-refs), core-takeaways placement, quiz + answer key at end.
- **Animation mechanics**: the next/next/next stepper — controls, step captions, reset; inline SVG per `artifact-diagramming`.
- **Quiz mechanics**: MCQ interaction, per-question reveal vs end answer key, explanation depth, question count.
- **Visual design**: typography, light/dark, figure style per `dataviz`/`frontend-design`.
- **Depth calibration**: is "as much detail as possible" landing right for the user?

Process: Read the chapter's section headings from `reference/ddia-1st-edition.pdf` first; consult `research/02-second-edition-deltas.md`; use anchors from the concept registry (ticket 03). User reviews the built page; feedback rounds until locked. Record the locked template as `docs/template.md`.

## Resolution

Pilot built and approved as the template baseline; template **locked** at [docs/template.md](../../template.md).

- Chapter: [chapters/ch03-storage-and-retrieval.html](../../../chapters/ch03-storage-and-retrieval.html) — 134KB self-contained; 6 steppers, ~7 static SVG figures, Feynman box per concept, 2e asides, xref tooltips, 11 takeaways, 16-question quiz with explained answer key, dark/light themes, "sparse index" sidebar.
- Locked decisions: page anatomy (header → framing intro → concept sections keyed to `concepts.json` slugs → takeaways → quiz+answer key → footer); ember=write/cyan=read color language book-wide; stepper mechanics (`data-on`/`data-hot` + caption list); quiz sizing 12–16 MCQs; build process (extract PDF text → build → fill definitions → validate → commit).
- User verdict: "good for the start" — with the expectation that detailed study will surface sections needing more diagrams/animations (first candidate: B-tree optimizations). Resolved as a **standing enrichment workflow**: additive figure/stepper requests on any chapter, any time; recorded in the template doc and map Notes. Chapter 3's ch-3-specific enrichment backlog tracked on the map under Not yet specified.
- Ch 3 definitions filled in `concepts.json` (14 concepts).
