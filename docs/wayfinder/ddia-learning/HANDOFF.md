# Handoff — DDIA interactive study notes (wayfinder map)

_Written 2026-08-27, updated after the Chapter 12 session (2026-08-31). Continue by opening a session in `~/ddia`
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

Built chapters: **3 (pilot), 1, 2, 4, 5, 6, 7, 8, 9** closed on the map. **All 12 chapters are now
built and pushed. Chapters 10, 11, and 12 await user review** — tickets 13, 14, 15 are claimed
(`Assignee: claude`), not closed (the user keeps saying "do the next chapter" without "close it").
On "close it" for each: set `Status: closed`, write `## Resolution` in the ticket, add a
Decisions-so-far line to `MAP.md`, commit, push. User's pattern so far: "close it, do the next chapter."

Remaining frontier after that: the **index page** (ticket 16 — `index.html` doesn't exist yet;
every stub and chapter footer already links to it).

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

## Notes for the index page (ticket 16, the last one)

- `index.html` doesn't exist; every chapter footer and stub links to it (`href="index.html"`), and
  ch 1's header eyebrow links `← index` too. It must live at repo root? No — links are relative
  from `chapters/`, so the file goes at `chapters/index.html`. Verify with a link check before push.
- Content per the map's Destination: an index of the 12 chapter artifacts. Natural shape: the locked
  template's design language (sparse-index nav aesthetic, ember/cyan), one card/row per chapter with
  title, 1st/2nd-ed mapping, stepper/figure/quiz counts, and links. Registry `concepts.json` has
  per-chapter `file`, `title`, `second_ed`, `pdf_page` — generate the rows from it.
- All 169 registry definitions are now filled (ch 12's were the last). The "Not yet specified"
  items on the map (shared animation library, revision workflow) remain open — index build may
  surface them but shouldn't decide them unilaterally.
- Ch 12 build notes for calibration: 186KB, 6 steppers (unfriend/message causality race, CREATE
  INDEX ≡ follower ≡ CDC bootstrap, write/read-path boundary shifting, end-to-end duplicate
  suppression, uniqueness via log, multi-partition transfer without 2PC) + 7 static figures
  (derive-vs-dual-writes, lambda vs unified, federation vs unbundling, RPC vs dataflow,
  end-to-end stream, Merkle tree, feedback loop) + 1 table + 6 `.ed2` asides, 16-question quiz;
  43 screenshots caught 5 collisions in 2 fix rounds. Assembly: `assemble12`-style inline python
  (same sed-parameterization of assemble11.py; parts p12-1…p12-4).
- Ch 11 build notes: 206KB (the chapter is dense; earlier pages
  ran 100–170KB), 6 steppers (AMQP redelivery reordering Fig 11-2, partitioned log with offsets /
  failover / replay Fig 11-3, dual-write race Fig 11-4, CDC log compaction + bootstrap, processing-
  vs event-time under a redeploy Fig 11-7, stream-stream join) + 7 static figures (load balancing
  vs fan-out, CDC fan-out, state⇄stream integral/derivative, three timestamps, window types, three
  join types, checkpoint barriers) + 2 tables + 5 `.ed2` asides, 16-question quiz. 43 screenshots
  caught 6 collisions in one fix round (labels on arrows, text past box edges, two-column captions
  colliding at the x=360 midline).
- Assembly script: `assemble11.py` (sed-parameterized from `assemble10.py`; the parameters are the
  scratchpad path, title, `p11-` prefix, output filename, `chapter==11`, `ch11.js`). Its overflow
  heuristic assigns `text-anchor="middle"` to any `<text>` within 900 chars after a middle-anchored
  `<g>` — so left-anchored labels that follow an axis-label group escape detection; check those by
  hand. Caption budget ≤ ~118
  chars at x=20 for 9px, and text INSIDE a box must fit the box width (≈ (box width − 20) / 5.4
  chars). Chapters 9 and 10 each needed a trim pass of 20–35 captions — draft captions at ≤ 100
  chars and you'll skip that round.
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
  ~12; ch 9: 41 shots caught ~11; ch 10: 33 shots caught 5 (labels on a curve's path, an arrow routed through a box, text spilling past a box edge,
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
