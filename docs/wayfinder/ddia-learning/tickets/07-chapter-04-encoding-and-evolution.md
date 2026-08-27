# Chapter 04: Encoding and Evolution

- **Type**: wayfinder:task (AFK build, user review)
- **Status**: closed
- **Assignee**: yagyesh (session, 2026-08-26)
- **Blocked by**: [04-pilot-chapter-03-template-lock](04-pilot-chapter-03-template-lock.md)

## Question

Build `chapters/ch04-encoding-and-evolution.html` to the locked template (`docs/template.md`): every concept from the chapter's section headings (walk `reference/ddia-1st-edition.pdf`), Feynman explanations, figures, click-through animations, cross-references via the concept registry, core takeaways, MCQ quiz + explained answer key. Fold in 2nd-edition deltas from `research/02-second-edition-deltas.md`. Update `index.html` status. User reviews before close.

## Resolution

Built to the locked template and approved by the user (closed 2026-08-27). `chapters/ch04-encoding-and-evolution.html` (~125KB): every section from Formats for Encoding Data through Message-Passing Dataflow; 6 steppers (rolling upgrade, JSON→binary bytes, Thrift/Protobuf field tags, Avro writer/reader schema resolution, the lost-field round-trip through an old client, RPC request/response), 7 static figures, 14-question quiz with explained key; 2nd-edition asides on schema-evolution-as-migration framing and newer format/system examples. Chapter 4 `definition`s filled in `concepts.json`; stub replaced.
