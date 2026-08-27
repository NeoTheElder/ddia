# Chapter 05: Replication

- **Type**: wayfinder:task (AFK build, user review)
- **Status**: closed
- **Assignee**: yagyesh (session, 2026-08-27)
- **Blocked by**: [04-pilot-chapter-03-template-lock](04-pilot-chapter-03-template-lock.md)

## Question

Build `chapters/ch05-replication.html` to the locked template (`docs/template.md`): every concept from the chapter's section headings (walk `reference/ddia-1st-edition.pdf`), Feynman explanations, figures, click-through animations, cross-references via the concept registry, core takeaways, MCQ quiz + explained answer key. Fold in 2nd-edition deltas from `research/02-second-edition-deltas.md`. Update `index.html` status. User reviews before close.

## Resolution

Built to the locked template and approved by the user (closed 2026-08-27). `chapters/ch05-replication.html` (~170KB — the Part II introduction is folded in as a framing section): every section from Leaders and Followers through Detecting Concurrent Writes; 6 steppers (sync/async replication timeline, failover + split brain, replication-lag anomalies, multi-leader write conflict, Dynamo-style quorum read/write, the shopping-cart version-merging algorithm), 13 static figures, 15-question quiz with explained key; 2nd-edition asides on replication's rising prominence, sync engines/CRDTs, session guarantees, version vectors vs vector clocks. Chapter 5 `definition`s filled in `concepts.json`; stub replaced.
