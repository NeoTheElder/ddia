# Research: 2nd-edition deltas per 1st-edition chapter

- **Type**: wayfinder:research (AFK)
- **Status**: closed (2026-08-13)
- **Assignee**: research subagent (fired at charting, 2026-08-12)
- **Blocked by**: —

## Question

For each of the 12 chapters of DDIA 1st edition (2017), what did the 2nd edition (Dec 2025) change, add, or drop? The chapter artifacts follow the 1st-edition structure but must fold in what the field (and Kleppmann's treatment of it) changed in 8 years.

Wanted, per 1st-edition chapter:

- New concepts/sections the 2nd edition introduces that map to this chapter (e.g. newer consensus deployments, cloud-native/object-storage architectures, streaming maturity).
- Concepts the 2nd edition de-emphasizes or drops as dated.
- Terminology shifts and corrected/refined claims.
- Notable new example systems replacing 2017-era ones.
- Structural notes: where the 2nd edition's TOC diverges (chapters split/merged/reordered) so cross-references can note "in 2nd ed this lives in ch. X".

Sources: O'Reilly's official 2nd-edition page/TOC, Kleppmann's blog and announcements, reputable reviews/comparisons. Cite sources.

Output: `research/02-second-edition-deltas.md`, one section per 1st-edition chapter.

## Resolution

Findings: [research/02-second-edition-deltas.md](../research/02-second-edition-deltas.md) — per-chapter deltas with cited sources (O'Reilly catalog, Kleppmann's site, the official `ept/ddia2-references` repo, author interviews). Highest-impact:

- **Structure**: 12 chapters/3 parts → 14 chapters/4 parts. 1st-ed Ch 1 splits into "Trade-Offs in Data Systems Architecture" + "Defining Nonfunctional Requirements"; Ch 2–11 map one-to-one to 2nd-ed Ch 3–12; 1st-ed Ch 12 splits into Ch 13 (streaming philosophy) + Ch 14 "Doing the Right Thing" (ethics, new Part IV).
- **Rename**: Partitioning → **Sharding**, with new multitenancy/shard-manager content, and de-emphasized overall (bigger machines/cloud reduce the need).
- **Biggest deletion**: MapReduce reduced to a teaching device — Spark/Flink replace it; S3/object storage replaces HDFS.
- **Cloud-native throughout**: compute/storage separation, object storage as substrate, Aurora/Socrates/Snowflake, serverless.
- **AI/ML additions**: vector indexes/HNSW, dataframes, embeddings/RAG, training-data pipelines.
- **Replication**: new sync-engines/local-first/CRDT thread (Figma, Linear); Consistency & Consensus expanded with proper Raft coverage.
- Co-author Chris Riccomini added; ~670pp; print March 2026.

Inferences from the refs repo are flagged in the file; thin-record chapters are called out explicitly.
