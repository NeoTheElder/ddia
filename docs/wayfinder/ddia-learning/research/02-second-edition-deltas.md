# DDIA 1st Edition (2017) → 2nd Edition (2025/2026): What Changed, Per Chapter

Research notes for study sessions. Structure and deltas are summarized in my own words; no book text is
reproduced. Claims are cited inline. Where a claim is inferred from the official references repo (the
literature each 2nd-edition chapter cites) rather than stated outright in prose, it is marked
**[inferred from refs repo]** — treat those as high-confidence topic coverage signals, not quotes.

## Sources

High-trust primary sources:

- **O'Reilly catalog page, 2nd edition** (ISBN 9781098119058): https://www.oreilly.com/library/view/designing-data-intensive-applications/9781098119058/
  (chapter pages, e.g. `ch01.html` "Trade-Offs in Data Systems Architecture", `ch14.html` "Doing the Right Thing", confirm titles).
- **Martin Kleppmann's publications page for the 2nd edition** (publication details, co-author, March 2026 print date):
  https://martin.kleppmann.com/2026/03/24/designing-data-intensive-applications-2e.html
- **Official references repository for the 2nd edition**, maintained by Kleppmann (`ept` = his GitHub account),
  one file per chapter listing every work each chapter cites — the primary evidence used here for what each
  2nd-edition chapter covers: https://github.com/ept/ddia2-references
- **Book's official site**: https://dataintensive.net/
- **ScyllaDB interview with Kleppmann and Riccomini about the revision** (March 2026):
  https://www.scylladb.com/2026/03/26/rethinking-designing-data-intensive-applications/
- **Pragmatic Engineer interview/podcast with Kleppmann** (explicit statements on dropped/de-emphasized content):
  https://newsletter.pragmaticengineer.com/p/designing-data-intensive-applications
- **Pragmatic Engineer 2nd-edition book excerpt post** (Ch 1 and Ch 14 excerpts, what's-new framing):
  https://newsletter.pragmaticengineer.com/p/designing-data-intensive-applications-book-excerpt

Secondary sources used only for corroboration:

- DDIA Companion study-notes site (full 2nd-edition TOC with parts): https://arunav-bhattacharya.github.io/ddia-companion/
- System Design Space short summary of the 2nd edition: https://system-design.space/en/chapter/ddia-book/
- Javarevisited (Medium) review of the 2nd edition: https://medium.com/javarevisited/i-read-designing-data-intensive-applications-2nd-edition-and-its-awesome-417103df5aab
- Amazon listing (publisher blurb): https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1098119061

**Publication timing note:** final content became available via O'Reilly early release in late 2025; the
print/ebook edition is dated 2026 (Kleppmann's site says March 2026; the Pragmatic Engineer podcast says
"released in April 2026"). The "~December 2025" date in circulation refers to the completed early-release
content, not the print edition.

**Authorship:** the 2nd edition adds Chris Riccomini as co-author (Kleppmann + Riccomini). ~670 pages
(vs ~550 in 1st ed). Same subtitle ("The Big Ideas Behind Reliable, Scalable, and Maintainable Systems"),
same goals and scope; per the publisher blurb the entire book was rewritten for clarity, cloud-native ideas
were "woven throughout," and AI/ML-supporting data systems were added (vector indexes, dataframes, training
pipelines). (Kleppmann publications page; O'Reilly/Amazon blurb via the Javarevisited review; ScyllaDB interview.)

---

## 2nd-Edition TOC Overview

12 chapters (3 parts) became **14 chapters (4 parts)** (DDIA Companion site; O'Reilly chapter pages;
ept/ddia2-references confirms exactly 14 chapters):

| 2nd ed | Title | Part |
|---|---|---|
| 1 | Trade-Offs in Data Systems Architecture | I. Foundations of Data Systems |
| 2 | Defining Nonfunctional Requirements | I |
| 3 | Data Models and Query Languages | I |
| 4 | Storage and Retrieval | I |
| 5 | Encoding and Evolution | I |
| 6 | Replication | II. Distributed Data |
| 7 | Sharding | II |
| 8 | Transactions | II |
| 9 | The Trouble with Distributed Systems | II |
| 10 | Consistency and Consensus | II |
| 11 | Batch Processing | III. Derived Data |
| 12 | Stream Processing | III |
| 13 | A Philosophy of Streaming Systems | III |
| 14 | Doing the Right Thing | IV. Data and Society |

Mapping from the 1st edition:

- **1st-ed Ch 1 was split in two**: the new Ch 1 (Trade-Offs) is largely new architectural material; the
  reliability/scalability/maintainability content became Ch 2 (Defining Nonfunctional Requirements). The
  publisher blurb names "Trade-offs in Data Systems Architecture", "Defining Nonfunctional Requirements",
  and "The Trouble with Distributed Systems" as the three new/heavily-revised chapters (Amazon blurb via
  Javarevisited review).
- **1st-ed Ch 2–11 map one-to-one to 2nd-ed Ch 3–12**, shifted by +1, with one rename: *Partitioning* →
  **Sharding** (2nd-ed Ch 7).
- **1st-ed Ch 12 (The Future of Data Systems) was split**: its technical half (data integration, unbundling
  databases, end-to-end correctness) became Ch 13 (*A Philosophy of Streaming Systems*); its "Doing the
  Right Thing" ethics section grew into a full closing chapter, Ch 14, in a new Part IV "Data and Society"
  (chapter titles from O'Reilly ch13/ch14 pages and DDIA Companion; content split **[inferred from refs repo]**
  — Ch 13's citations are the 1st-ed Ch 12 data-integration/unbundling/correctness literature, Ch 14's are
  the ethics/surveillance/GDPR literature).

Cross-cutting deltas the authors state directly (ScyllaDB interview; Pragmatic Engineer):

- **Cloud-native architecture woven throughout**: object storage instead of local disks as a first-class
  building block ("building on an abstraction like object storage lets you do fundamentally different things"),
  compute/storage separation, cloud vs self-hosting trade-offs, serverless.
- **Control plane / data plane / compute plane separation** as an accepted architectural pattern (Riccomini).
- **AI/ML as a workload**: embeddings, vector search, RAG, dataframes, training-data pipelines.
- **MapReduce is the biggest deletion** — kept only as a brief learning device for partitioned batch systems,
  because "practically nobody uses it" (Kleppmann, Pragmatic Engineer podcast).
- **Sharding de-emphasized relative to replication**: replication for fault tolerance matters at every scale,
  while bigger machines and cloud services mean fewer teams need to shard (Kleppmann, Pragmatic Engineer podcast).
- Consistency and consensus **significantly expanded** (publisher blurb).

---

## 1st-Ed Chapter 1: Reliable, Scalable, and Maintainable Applications

**Where it lives in 2nd ed:** split into **Ch 1 (Trade-Offs in Data Systems Architecture)** and
**Ch 2 (Defining Nonfunctional Requirements)** — both named as new/heavily-revised chapters (publisher blurb).

**New concepts introduced (mostly in the new Ch 1):**
- Framing the whole book around *trade-offs* rather than tool categories (O'Reilly ch01 title; ScyllaDB interview).
- Operational vs analytical systems moved up front: OLTP vs OLAP, data warehousing, **data lakes**, ETL and
  reverse ETL, HTAP, real-time OLAP stores **[inferred from refs repo — ch1 cites data-lake surveys, HTAP
  surveys, Pinot/Druid/ClickHouse comparisons, "reverse ETL"]**. In the 1st ed, OLTP-vs-OLAP/data-warehousing
  lived in Ch 3 (Storage and Retrieval).
- **Cloud vs self-hosting** as an explicit decision, including the counter-trend ("Why We're Leaving the
  Cloud", "Use One Big Server"), **cloud-native database architecture** (Amazon Aurora, Azure Socrates/
  Hyperscale, Snowflake's disaggregated storage, AlloyDB), **serverless**, and compute-storage separation
  **[inferred from refs repo]**; confirmed as a major theme by the ScyllaDB interview and the Pragmatic
  Engineer excerpt (Ch 1 excerpt is the cloud-vs-self-hosting section).
- Distributed vs single-node systems as a trade-off; microservices; data residency/GDPR pressures; even
  datacenter power/carbon considerations **[inferred from refs repo]**.

**In the new Ch 2 (successor of 1st-ed Ch 1's core):**
- The Twitter fan-out load case study returns, updated (now framed as a social-network home-timeline case
  study, with newer material like Bluesky's lossy timelines) **[inferred from refs repo]**.
- Reliability/fault-tolerance content is deepened with post-2017 production research: **metastable failures**,
  backoff/jitter, **circuit breakers, load shedding**, fail-slow hardware, silent data corruption
  ("Cores That Don't Count"), SSD/DRAM field-failure studies **[inferred from refs repo]**.
- Percentile-based performance description is expanded (tail latency, SLOs, histogram sketches such as
  HdrHistogram/t-digest/DDSketch) **[inferred from refs repo]**.

**De-emphasized/dropped:** nothing major reported dropped from this chapter; it grew. No public statement
found of specific deletions here.

**Terminology shifts:** "nonfunctional requirements" is now the umbrella term for reliability/scalability/
maintainability (chapter title, O'Reilly).

**New example systems:** Aurora, Azure Socrates, Snowflake, AlloyDB, serverless platforms, Bluesky
**[inferred from refs repo]** — replacing the 1st ed's mostly on-prem, single-org 2010s examples.

---

## 1st-Ed Chapter 2: Data Models and Query Languages

**Where it lives in 2nd ed:** **Ch 3, same title.**

**New concepts:** **[all inferred from refs repo unless noted]**
- **GraphQL** covered as a query language (Medium review lists GraphQL as a new topic; ch3 refs cite GraphQL
  critique posts).
- **Dataframes, matrices, and arrays** as a data model for analytics/ML (ch3 cites "Towards Scalable Dataframe
  Systems", ArcticDB) — part of the announced AI/ML additions (publisher blurb: "DataFrames for training datasets").
- Graph query standardization: **GQL (the ISO graph query standard)** and SQL/PGQ alongside Cypher/SPARQL/Datalog.
- Newer modeling material: star schema vs one-big-table (OBT) for analytics, fractional indexing/user-defined
  ordering, online schema-migration tooling (gh-ost, pgroll), schema-on-read vs schema-on-write.
- Modern graph-database examples: TAO (Facebook), LinkedIn's LIquid, KùzuDB, Neptune, knowledge graphs.

**De-emphasized/dropped:** the 1st ed's "MapReduce Querying" subsection is presumably gone with the overall
MapReduce deletion (Pragmatic Engineer podcast); no other explicit drop reported. The hierarchical/network-
model history (IMS/CODASYL) is retained (ch3 still cites "What Goes Around Comes Around" and its 2024 sequel).

**Terminology/refinements:** the NoSQL-vs-relational framing is treated as settled convergence — "What Goes
Around Comes Around… And Around…" (2024) is cited, arguing relational absorbed the challengers **[inferred
from refs repo]**.

**New example systems:** MongoDB/PostgreSQL remain; added Cosmos DB modeling, KùzuDB, LIquid, GQL-era tooling
**[inferred from refs repo]**.

---

## 1st-Ed Chapter 3: Storage and Retrieval

**Where it lives in 2nd ed:** **Ch 4, same title.** Note: the OLTP-vs-OLAP/data-warehousing intro material
moved forward into 2nd-ed Ch 1; Ch 4 keeps the storage-engine and column-storage internals.

**New concepts:** **[inferred from refs repo unless noted]**
- **Vector indexes for semantic search** — publisher-announced (blurb); ch4 refs cite word2vec embeddings,
  HNSW, IVF/ANN papers, pgvector internals. This is a brand-new index family vs the 1st ed.
- **Cloud/object-storage-era storage**: Delta Lake (ACID tables over object stores), Snowflake's elastic
  warehouse, BigQuery internals.
- Modern **columnar formats**: Parquet/Dremel record shredding, **Apache Arrow**, Lance, Nimble; composable
  query engines ("The Road to Composable Data Systems").
- **Embedded/in-process databases**: DuckDB, SQLite (Bluesky's single-tenant SQLite), LanceDB.
- Query-execution modernization: vectorized vs compiled execution (MonetDB/X100 lineage), SIMD.
- NVMe/SSD-aware storage-engine design (WiscKey, NVMe performance studies); RocksDB as the LSM workhorse;
  multidimensional/spatial indexes (Uber H3, bkd-trees) and fuller full-text coverage (Lucene internals,
  Postgres GIN).

**De-emphasized/dropped:** data-warehousing overview moved out (to Ch 1); star-schema modeling largely to
Ch 3. No public statement of outright deletions; B-tree vs LSM remains the backbone.

**Terminology/refinements:** more careful read/write/space-amplification treatment (RUM conjecture cited)
**[inferred from refs repo]**.

**New example systems:** DuckDB, RocksDB (much more prominent), Delta Lake, Parquet/Arrow, ClickHouse-class
real-time OLAP, pgvector — vs 2017-era emphasis on Bitcask/Cassandra/HBase-style examples.

---

## 1st-Ed Chapter 4: Encoding and Evolution

**Where it lives in 2nd ed:** **Ch 5, same title.**

**New concepts:** **[inferred from refs repo unless noted]**
- **Durable execution and workflow engines** (Temporal, Restate) as a new mode of dataflow — matches the
  Medium review's "workflow engines, durable execution" list.
- **Schema registries** (Confluent-style) for managing schema evolution in event streams.
- Real-world **API versioning** practice (e.g., Stripe's versioning approach), idempotency in API design.
- Event-driven architecture framing for message-passing dataflow; virtual actors (Orleans).

**De-emphasized/dropped:** no explicit public statement. SOAP/WS-*/CORBA remain only as cautionary history
(refs retained). Expect Thrift to be a smaller presence than in 2017 (Avro/Protobuf dominate the refs) —
**low-confidence inference**.

**Terminology/refinements:** none publicly documented beyond the general rewrite.

**New example systems:** Temporal, Restate, Confluent Schema Registry, Stripe API versioning
**[inferred from refs repo]**.

---

## 1st-Ed Chapter 5: Replication

**Where it lives in 2nd ed:** **Ch 6, same title.** Kleppmann explicitly says replication-for-fault-tolerance
remains relevant at every scale and gained relative prominence over sharding (Pragmatic Engineer podcast).

**New concepts:** **[inferred from refs repo unless noted]**
- A major new thread on **sync engines, offline-first and local-first software, and collaborative editing**:
  CRDTs (now with substantial treatment — Kleppmann's own research area), operational transformation,
  eg-walker, Figma multiplayer, Google Docs, Linear's sync engine. Corroborated by system-design.space
  ("local-first applications and CRDTs" added) and the Medium review ("sync engines, local-first software").
- Updated consistency-model exposition ("Replicated Data Consistency Explained Through Baseball", session
  guarantees) and dotted version vectors.
- Newer multi-region/cloud examples: Cosmos DB global distribution, Aurora DSQL, Fly.io; Flexible Paxos
  appears in the quorum discussion.

**De-emphasized/dropped:** no explicit public deletions; the leader-based/multi-leader/leaderless skeleton
is intact (O'Reilly ch06 exists under the same title; refs cover the same trio).

**Terminology/refinements:** clearer separation of version vectors vs vector clocks **[inferred from refs repo]**.

**New example systems:** Figma, Linear, Automerge-adjacent local-first tooling, Aurora DSQL — alongside the
1st ed's PostgreSQL/MySQL/Dynamo-style examples.

---

## 1st-Ed Chapter 6: Partitioning

**Where it lives in 2nd ed:** **Ch 7, renamed "Sharding".**

**Terminology shift (headline):** *partitioning → sharding* throughout — the chapter title itself changed
(O'Reilly ch07; early-release TOC). Presumably to match industry usage and avoid collision with network
partitions / partitioned tables.

**New concepts:** **[inferred from refs repo unless noted]**
- **Sharding for multitenancy** (a new section per the O'Reilly section list surfaced in search).
- **Shard management services**: Facebook's Shard Manager; ScyllaDB's Raft-based topology changes;
  DynamoDB adaptive capacity for hot partitions; S3's internal sharding story.
- Consistent hashing treated with newer algorithms (jump hash, random slicing).

**De-emphasized:** the *need* to shard, *as a matter of judgment*: Kleppmann notes bigger machines and managed
cloud services mean most teams no longer must shard early (Pragmatic Engineer podcast). The rebalancing /
request-routing / secondary-index structure survives (O'Reilly section list).

**New example systems:** S3, DynamoDB, ScyllaDB, Facebook Shard Manager — vs the 1st ed's
Cassandra/Riak/Voldemort-era examples.

---

## 1st-Ed Chapter 7: Transactions

**Where it lives in 2nd ed:** **Ch 8, same title.**

**New concepts:** **[inferred from refs repo unless noted]**
- **Distributed SQL / NewSQL in practice**: CockroachDB, TiDB, Spanner, FoundationDB now anchor the
  distributed-transactions discussion.
- Storage-layer honesty about durability: fsync-failure research ("Can Applications Recover from fsync
  Failures?", the PostgreSQL fsyncgate), crash-consistency studies, SSD power-fault behavior.
- Real-world stakes framing: opens with / includes the UK Post Office **Horizon scandal** reference;
  ACIDRain attacks on isolation bugs; Bitcoin-exchange race conditions.
- Newer isolation analysis: client-centric isolation specifications, Jepsen's Elle checker, MVCC internals
  of Postgres/MySQL.

**De-emphasized/dropped:** no explicit statement. XA/two-phase-commit skepticism carries over (same
cautionary refs retained). 1st-ed structure (weak isolation levels → serializability → distributed
transactions) appears preserved.

**Terminology/refinements:** sharper distinction between isolation levels and (distributed) consistency
levels — refs cite explainers on exactly that confusion **[inferred from refs repo]**.

**New example systems:** CockroachDB, TiDB, FoundationDB, Spanner (now production-proven) — vs the 1st ed's
reliance on classic RDBMS + early NoSQL examples.

---

## 1st-Ed Chapter 8: The Trouble with Distributed Systems

**Where it lives in 2nd ed:** **Ch 9, same title** — named by the publisher as one of the three
new/heavily-revised chapters (Amazon blurb).

**New concepts:** **[inferred from refs repo unless noted]**
- **Gray failure and partial/asymmetric network partitions** as first-class fault classes.
- Modern clock infrastructure: **Precision Time Protocol at Meta, microsecond-accurate clocks on AWS EC2**,
  clock synchronization in finance (MiFID II), GPS jamming — a big upgrade over the 1st ed's NTP-centric view.
- **Deterministic simulation testing** and randomized fault injection as a response to distributed-systems
  uncertainty (Polar Signals DST reference; the Medium review lists "formal methods, randomized testing"
  among new topics).
- Fresh outage case studies (Roblox 2021 return-to-service, Cloudflare leap-second DNS incident, undersea-cable
  sabotage) replacing/augmenting 2013-era war stories.

**De-emphasized/dropped:** nothing publicly reported dropped; the chapter's skeleton (unreliable networks,
unreliable clocks, process pauses, knowledge/truth) is recognizably intact from the refs structure.

**Terminology/refinements:** Byzantine-fault discussion updated with XFT and real-world Byzantine incident
reports **[inferred from refs repo]**.

---

## 1st-Ed Chapter 9: Consistency and Consensus

**Where it lives in 2nd ed:** **Ch 10, same title.** Publisher blurb singles this chapter out as
"significantly expanded" (O'Reilly/Amazon description, echoed by the Javarevisited review).

**New concepts:** **[inferred from refs repo unless noted]**
- **Raft covered properly** (the 1st ed centered ZooKeeper/Zab and treated Raft briefly): "In Search of an
  Understandable Consensus Algorithm", Ongaro's "Consensus: Bridging Theory and Practice", "Raft Refloated",
  and "Paxos vs Raft: Have We Reached Consensus on Distributed Consensus?" are all cited.
- **Shared-log architectures** (CORFU, Tango, Delos-lineage) and Calvin-style deterministic transactions in
  the total-order-broadcast discussion.
- Distributed **ID generation** (Snowflake IDs, ULID, UUID ordering) tied to logical clocks.
- Refined CAP treatment continues ("Please Stop Calling Databases CP or AP", "A Critique of the CAP Theorem")
  plus newer strict-serializability/external-consistency explainers (Spanner, CockroachDB consistency model).

**De-emphasized/dropped:** no public statement; expect ZooKeeper to share space with etcd as the
coordination-service example (etcd Jepsen analyses cited).

**Terminology/refinements:** clearer layering of linearizability vs serializability vs strict
serializability, and consistency vs isolation levels **[inferred from refs repo]**.

---

## 1st-Ed Chapter 10: Batch Processing

**Where it lives in 2nd ed:** **Ch 11, same title.**

**Biggest delta in the book (explicit):** **MapReduce coverage was cut** — Kleppmann says it survives only
"purely as a learning tool, for understanding partitioned batch systems," since practically nobody uses it
anymore; Spark/Flink are the replacements (Pragmatic Engineer podcast). The refs repo matches: it cites
"The Elephant Was a Trojan Horse: On the Death of Map-Reduce at Google" and Google's "R.I.P. MapReduce"
codebase-removal announcement.

**New concepts:** **[inferred from refs repo unless noted]**
- **Object storage (S3) instead of HDFS** as the substrate for batch data; erasure coding; spot instances
  and cloud cluster schedulers (Borg, YARN as history).
- **Lakehouse** architecture and **data mesh** / data-fabric organizational patterns.
- **ML training pipelines as a batch workload**: preparing training data, embeddings at LinkedIn, OpenAI's
  LLM scaling on Ray — matching the publisher's "batch processing systems for preparing training data" claim.
- Derived-data serving stores (LinkedIn Venice).

**De-emphasized/dropped:** Hadoop/HDFS ecosystem detail (Pig/Hive-era workflows) demoted along with
MapReduce; Unix-philosophy framing survives (sort/coreutils refs retained).

**New example systems:** Spark (now the default), Flink batch, BigQuery, S3, Ray, lakehouse platforms — vs
the 1st ed's Hadoop-centric examples.

---

## 1st-Ed Chapter 11: Stream Processing

**Where it lives in 2nd ed:** **Ch 12, same title.** (The digitalbiztalk "review" speculating about this
chapter is explicitly guesswork; ignored.)

**New concepts:** **[inferred from refs repo unless noted]**
- **Streaming maturity**: exactly-once/effectively-once semantics done properly — Kafka transactions
  (KIP-98), Flink's asynchronous snapshots; TLA+ verification of Kafka transactions is cited (a formal-methods
  touchpoint matching the Medium review's list).
- **Change data capture grown up**: Debezium, Netflix DBLog, the **outbox pattern**, "CDC is having a moment".
- **Incremental view maintenance / streaming databases**: DBSP, differential dataflow, Materialize,
  RisingWave — a category that barely existed in 2017.
- Watermarks/event-time from the **Dataflow Model** ("Streaming 102") now standard vocabulary.
- **GDPR-era deletion**: crypto-shredding and excision in immutable-log systems.
- Dead-letter queues, queues-vs-logs trade-offs (KIP-932 "Queues for Kafka"), Postgres-as-queue at scale.

**De-emphasized/dropped:** no explicit statement; AMQP/JMS message brokers remain as one lineage but the
log-based (Kafka) model clearly dominates. Lambda-architecture critique carries over ("Questioning the
Lambda Architecture").

**New example systems:** Debezium, Materialize, RisingWave, Flink (mature), Kafka Streams — vs 2017-era
Samza/Storm emphasis.

---

## 1st-Ed Chapter 12: The Future of Data Systems

**Where it lives in 2nd ed: split into Ch 13 and Ch 14.**

- **Ch 13, "A Philosophy of Streaming Systems"** (title: O'Reilly ch13 page; DDIA Companion) inherits the
  technical program: data integration via logs, lambda-architecture critique, **unbundling the database**
  reframed alongside 2020s "**composable data systems**" and polystores, "turning the database inside out,"
  microservices-as-event-driven-systems, end-to-end correctness without distributed transactions (OLEP,
  sagas, end-to-end argument), integrity checking/auditing (certificate transparency, Merkle trees)
  **[inferred from refs repo — Ch 13's citations are precisely this 1st-ed Ch 12 literature plus newer
  composable-data-systems work]**. The retitling drops the speculative "future" framing: what was a
  forward-looking essay in 2017 is now presented as a philosophy of systems that exist.
- **Ch 14, "Doing the Right Thing"** promotes the 1st ed's closing ethics section to a full chapter in its
  own part ("Data and Society"): predictive-analytics bias and discrimination, algorithmic accountability
  and feedback loops, surveillance as a business model, limits of consent, data minimization
  (Datensparsamkeit) as an engineering duty, **GDPR and regulation now as enacted law rather than
  prediction**, plus AI-ethics material (ACM code, ML-bias enforcement statements, FTC actions)
  (Pragmatic Engineer excerpt post excerpts this chapter; system-design.space confirms the new final
  chapter's scope; refs repo confirms topics).

**Dropped/de-emphasized:** the 2017 speculative predictions framing itself. No public inventory exists of
which specific "future" bets were cut vs converted; where a 1st-ed Ch 12 idea matters to you, check Ch 13
directly — **no more detailed public delta information found for this chapter beyond the above**.

---

## Gaps in the Public Record

- No official chapter-by-chapter "what changed" document exists from the authors; the per-chapter detail
  above is triangulated from the publisher blurb, two author interviews, and the official references repo.
- For 1st-ed Ch 4 (Encoding) and Ch 7 (Transactions) specifically, no public statement identifies anything
  *removed*; deltas listed are additions inferred from the refs repo.
- Exact section-level structure inside most 2nd-edition chapters is not publicly enumerated (O'Reilly's TOC
  requires a subscription); section names cited here surfaced via search snippets and should be treated as
  indicative.
