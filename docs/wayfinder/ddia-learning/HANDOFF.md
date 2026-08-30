# Handoff — DDIA interactive study notes (wayfinder map)

_Written 2026-08-27, updated after the Chapter 9 session (2026-08-30). Continue by opening a session in `~/ddia`
(or anywhere) and saying `Use ~/ddia/docs/wayfinder/ddia-learning/HANDOFF.md`, then what to do
(e.g. "close ch4 and ch5, do chapter 6"). If a `wayfinder` skill is available, `/wayfinder MAP.md`
also works; otherwise read `MAP.md` + `tickets/` directly._

## What this effort is

Building one self-contained interactive HTML page per chapter of *Designing Data-Intensive
Applications* (Kleppmann, 1st ed.) with 2nd-edition updates folded in, for the user's personal
study. Everything canonical lives in the repo — read these rather than this doc:

- **Map (destination, notes, decisions, fog):** `~/ddia/docs/wayfinder/ddia-learning/MAP.md`
- **Tickets:** `~/ddia/docs/wayfinder/ddia-learning/tickets/` (local-markdown tracker:
  `Status:`, `Assignee:` = claim, `Blocked by:`; frontier = open + unblocked + unassigned)
- **Locked chapter template:** `~/ddia/docs/template.md` — page anatomy, ember=write/cyan=read
  color language, stepper mechanics (`data-on`/`data-hot` + `<ol class="cap">`), quiz format
- **Concept registry:** `~/ddia/concepts.json` — 169 slugs; anchors are
  `chNN-<slug>.html#<concept-slug>`; each chapter build fills its own `definition` fields
- **2nd-edition deltas per chapter:** `~/ddia/docs/wayfinder/ddia-learning/research/02-second-edition-deltas.md`
- **Book TOC with 0-based PDF page indexes:** `~/ddia/reference/toc.md`
- **Book PDF (gitignored):** `~/ddia/reference/ddia-1st-edition.pdf`; pypdf venv at `~/ddia/.venv/`
- **Remote:** https://github.com/NeoTheElder/ddia (private, user's personal account; `gh` is authed)

## State right now

Built chapters: **3 (pilot), 1, 2, 4, 5, 6, 7, 8** closed on the map. **Chapter 9 is built and pushed,
awaiting user review** — ticket 12 is claimed (`Assignee: claude`), not closed. On "close it": set
`Status: closed`, write `## Resolution` in ticket 12, add a Decisions-so-far line to `MAP.md`,
commit, push. User's pattern so far: "close it, do the next chapter."

Remaining frontier after that: chapters 10–12 (tickets 13–15, in book order; user may name
a different one) and the **index page** (ticket 16 — `index.html` doesn't exist yet; stubs and
chapter footers already link to it).

Every unbuilt chapter has a stub HTML at its final filename, so cross-references never 404.

## How a chapter session runs (the recipe that has worked 4 times)

1. Claim the ticket (set `Assignee:`), commit.
2. Extract chapter text: `.venv/bin/python` + pypdf over the page range from `reference/toc.md`
   (write to the scratchpad, then Read it in two halves — ~80K chars).
3. `awk` the chapter's section out of the deltas research file.
4. Check slugs: the chapter's own (for `id=`s) and any cross-reference targets in `concepts.json`.
5. Write the body only (nav + `<main>` … `</main></div>`) to a scratch file.
6. Assemble by splicing ch03's head/CSS (title swapped) and its `<script>` tail verbatim —
   this guarantees template fidelity. Validate: HTML tag balance, each stepper's caption count
   ≥ max `data-on` step, every `href="chNN…#slug"` resolves to an existing file + registry slug.
7. Fill the chapter's `definition`s in `concepts.json`; commit; push; `open` the file.
8. User reviews → on "close it": set `Status: closed`, write the `## Resolution`, add a
   Decisions-so-far line to `MAP.md`, commit, push.

The assembly/validation Python is in the last few Bash calls of the previous session's
transcript and is short; re-derive from the description above if needed. Chapter pages weigh
100–135KB; the pilot and ch 2/ch 4 have 6 steppers, ch 1 has 2 — calibrate by mechanism density.

## Notes for Chapter 10 (next in order)

- PDF pages 410–459 (0-based; ch 11 starts at 460). Part III (Derived Data) opens at 406 — the
  Part intro (406–409) is short and worth reading for framing (systems of record vs derived data).
  Sections in `reference/toc.md`; 2nd ed = its Chapter 11 per the deltas file; read that section.
- Existing forward links into ch 10 that must resolve: `#mapreduce-and-distributed-filesystems`
  (×2), `#comparing-hadoop-to-distributed-databases`, `#graphs-and-iterative-processing`. All slugs
  exist in the registry.
- Ch 9 build notes for calibration: 162KB, 6 steppers (linearizable register timeline Figs 9-2/9-3,
  non-linearizable strict quorum Fig 9-6, Lamport timestamps Fig 9-8, linearizable CAS via a
  total-order log, 2PC + coordinator crash Figs 9-9/9-10, epochs + overlapping quorums) + 4 static
  figures (football Fig 9-1, multi-DC CAP Fig 9-7, total vs partial order, consensus equivalence web)
  + 2 tables (consensus properties, ZooKeeper features), 16-question quiz.
- Assembly script: `assemble9.py` (sed-parameterized copy of `assemble.py`; the ch 9 copy also
  honours `text-anchor="end"` and inherits `text-anchor="middle"` from a parent `<g>`). Caption
  budget: ≤ ~120 chars at x=20 for 9px, ≤ ~105 for bold. Writing captions long and trimming after
  cost a full extra round in ch 9 — write them short.
- **Visual QA is worth doing before the first push** — the ch 6 screenshots caught ~10 SVG
  text overflows/overlaps (captions running past x=680, step-N text still visible under step-N+1
  banners, filled highlight rects covering text). Rules of thumb: 9px mono ≈ 5.4px/char, so a
  caption starting at x=20 must be ≤ ~115 chars; give every per-step caption its own
  `data-on="N"` group rather than a range; use `fill="none"` + stroke for highlight boxes over
  text; never put `<em>`/`<strong>` inside SVG `<text>` (use `<tspan>`).
- Headless Chrome recipe: write a temp copy of the page with a `<script>` appended before
  `</body>` that grabs the target figure (`getElementById` for `.anim`, or
  `querySelectorAll("figure:not(.anim)")[i]` for statics), clicks `.next` N−1 times, then
  `document.body.innerHTML=""; body.appendChild(f)`; screenshot with
  `--headless=new --hide-scrollbars --window-size=760,620 --screenshot=… file://tmp` (fragment
  URLs and scrolling do NOT work). Ch 7: 43 shots caught 9 label/arrow overlaps; ch 8: 35 shots caught
  ~12; ch 9: 41 shots caught ~11 (labels on a curve's path, an arrow routed through a box, text spilling past a box edge,
  a `data-on` range that left a stale label visible). Budget ~2 fix rounds per chapter.
- `concepts.json` is serialized with `indent=1` — dump it that way to keep diffs small.

## Standing user preferences (also in the map's Notes)

- Enrichment passes are a standing, additive workflow: when the user's study flags a section
  needing more figures/steppers (first candidate: ch 3 "B-tree optimizations"), add them on
  request without reopening tickets or the template.
- No Jira, no Co-Authored-By trailers, plain commit messages. Commit + push after each step.
- Hosting is local `file://`; do not set up GitHub Pages unless asked.
- Wayfinder's one-ticket-per-session rule has been explicitly overridden by the user's
  repeated "keep going" — proceed chapter after chapter when told to.

## Suggested skills (call via the Skill tool)

- `wayfinder` — invoke with the map path to pick up / claim the next ticket properly.
- `frontend-design:frontend-design` and `artifact-diagramming` — the map's Notes name these for
  building chapter pages (design stance is already locked; load mainly for diagram discipline).
- `grilling` — only if the user raises a template-level question (structural changes go
  through a map decision, not ad-hoc drift).
