# Chapter 07: Transactions

- **Type**: wayfinder:task (AFK build, user review)
- **Status**: closed
- **Assignee**: claude
- **Blocked by**: [04-pilot-chapter-03-template-lock](04-pilot-chapter-03-template-lock.md)

## Question

Build `chapters/ch07-transactions.html` to the locked template (`docs/template.md`): every concept from the chapter's section headings (walk `reference/ddia-1st-edition.pdf`), Feynman explanations, figures, click-through animations, cross-references via the concept registry, core takeaways, MCQ quiz + explained answer key. Fold in 2nd-edition deltas from `research/02-second-edition-deltas.md`. Update `index.html` status. User reviews before close.

## Resolution

Built to the locked template and approved by the user (closed 2026-08-28). `chapters/ch07-transactions.html` (~168KB): every section from The Slippery Concept of a Transaction through Serializable Snapshot Isolation; 6 steppers (Figure 7-1 counter race / lost update, read-committed old+new value with write lock, MVCC visibility with txids, write skew on the doctors rota, 2PL shared/exclusive locks + deadlock, SSI tripwires), 5 static figures (isolation vs atomicity, isolation-level × anomaly scorecard, copy-on-write B-tree, interactive vs stored procedure, predicate vs index-range locks), 15-question quiz with explained key; 2nd-edition asides on durability honesty (fsyncgate, Horizon, ACIDRain), MVCC internals / Elle / isolation-vs-consistency, and distributed SQL (CockroachDB, TiDB, Spanner, FoundationDB). Chapter 7 `definition`s filled in `concepts.json`; stub replaced. Headless-Chrome screenshots of all 43 stepper steps/figures used for visual QA before push (9 label overlaps fixed).
