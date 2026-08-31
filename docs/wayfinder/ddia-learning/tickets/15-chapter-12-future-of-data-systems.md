# Chapter 12: The Future of Data Systems

- **Type**: wayfinder:task (AFK build, user review)
- **Status**: closed
- **Assignee**: claude
- **Blocked by**: [04-pilot-chapter-03-template-lock](04-pilot-chapter-03-template-lock.md)

## Question

Build `chapters/ch12-future-of-data-systems.html` to the locked template (`docs/template.md`): every concept from the chapter's section headings (walk `reference/ddia-1st-edition.pdf`), Feynman explanations, figures, click-through animations, cross-references via the concept registry, core takeaways, MCQ quiz + explained answer key. Fold in 2nd-edition deltas from `research/02-second-edition-deltas.md`. Update `index.html` status. User reviews before close.

## Resolution

Built `chapters/ch12-future-of-data-systems.html` to the locked template (186KB) and approved by
the user 2026-08-31. All 15 sections walked from `reference/toc.md`; 6 steppers (unfriend/message
causality race, CREATE INDEX ≡ follower setup ≡ CDC bootstrap, write/read-path boundary shifting,
end-to-end duplicate suppression Ex 12-1→12-2, uniqueness via the log, multi-partition transfer
without 2PC), 7 static figures (derive-vs-dual-writes, lambda vs unified, federation vs unbundling,
RPC vs dataflow, end-to-end stream, Merkle tree, feedback loop), 1 table, 6 `.ed2` asides (2nd ed
splits this chapter into Ch 13 "A Philosophy of Streaming Systems" + Ch 14 "Doing the Right Thing"),
16-question quiz with explained key. Ch 12 definitions filled in `concepts.json` — the 169-concept
registry is now complete. Pre-push visual QA: 43 headless-Chrome screenshots caught 5 collisions,
fixed in 2 rounds. All 12 chapters are now built.
