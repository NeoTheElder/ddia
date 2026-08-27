# Chapter 01: Reliable, Scalable, and Maintainable Applications

- **Type**: wayfinder:task (AFK build, user review)
- **Status**: closed (2026-08-26)
- **Assignee**: yagyesh (session, 2026-08-26)
- **Blocked by**: [04-pilot-chapter-03-template-lock](04-pilot-chapter-03-template-lock.md)

## Question

Build `chapters/ch01-reliable-scalable-maintainable.html` to the locked template (`docs/template.md`): every concept from the chapter's section headings (walk `reference/ddia-1st-edition.pdf`), Feynman explanations, figures, click-through animations, cross-references via the concept registry, core takeaways, MCQ quiz + explained answer key. Fold in 2nd-edition deltas from `research/02-second-edition-deltas.md`. Update `index.html` status. User reviews before close.

## Resolution

Built and user-approved: [chapters/ch01-reliable-scalable-maintainable.html](../../../chapters/ch01-reliable-scalable-maintainable.html) (103KB). All 14 TOC sections; 2 steppers (Twitter fan-out, percentiles — bars generated from data); 5 static figures (composite data system, fault→failure, tail latency amplification, scale up/out, SQL abstraction); 4 Feynman boxes; 5 2e asides (chapter split, cloud-native, metastable failures/circuit breakers, SLOs, lossy timelines); xrefs to ch 3/4/6/7/8/10/12; 11 takeaways; 14-question quiz + key. Ch 1 definitions filled in `concepts.json`. Assembly method: head/CSS and script spliced verbatim from ch03 — recommended for all chapters to guarantee template fidelity.
