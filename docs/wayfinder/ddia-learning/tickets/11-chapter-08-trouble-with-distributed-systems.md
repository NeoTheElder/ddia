# Chapter 08: The Trouble with Distributed Systems

- **Type**: wayfinder:task (AFK build, user review)
- **Status**: closed
- **Assignee**: claude
- **Blocked by**: [04-pilot-chapter-03-template-lock](04-pilot-chapter-03-template-lock.md)

## Question

Build `chapters/ch08-trouble-with-distributed-systems.html` to the locked template (`docs/template.md`): every concept from the chapter's section headings (walk `reference/ddia-1st-edition.pdf`), Feynman explanations, figures, click-through animations, cross-references via the concept registry, core takeaways, MCQ quiz + explained answer key. Fold in 2nd-edition deltas from `research/02-second-edition-deltas.md`. Update `index.html` status. User reviews before close.

## Resolution

Built to the locked template and approved by the user (closed 2026-08-28). `chapters/ch08-trouble-with-distributed-systems.html` (~141KB): every section from Faults and Partial Failures through System Model and Reality; 5 steppers (no-response ambiguity Fig 8-1, switch queueing Fig 8-2, LWW timestamp inversion Fig 8-3, TrueTime intervals + commit wait, lease/GC pause/fencing tokens Figs 8-4+8-5), 4 static figures (circuit vs packet switching, wall vs monotonic clock, system-model grid, safety vs liveness), 2 tables (HPC vs cloud, pause causes), 15-question quiz with explained key; 2nd-edition asides on gray failure + deterministic simulation testing, modern clock infrastructure (PTP at Meta, µs EC2 clocks, GPS jamming), XFT and real Byzantine incidents. Chapter 8 `definition`s filled in `concepts.json`; stub replaced. Headless-Chrome screenshots of all 35 stepper steps/figures used for visual QA before push (~12 overlaps fixed in two rounds).
