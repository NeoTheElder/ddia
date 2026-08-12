# Pilot: Chapter 3 (Storage and Retrieval) + template lock

- **Type**: wayfinder:prototype (HITL)
- **Status**: open
- **Assignee**:
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

_(recorded on close: link to chapter file + template doc)_
