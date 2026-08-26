# Chapter template (LOCKED 2026-08-26 — structural changes go through a map decision)

**Enrichment passes are a standing workflow**: studying a chapter in detail will surface
sections that need extra figures or steppers (first flagged candidate: ch 3 "B-tree
optimizations"). Enrichments are *additive* — new figures/steppers/Feynman boxes inside the
locked structure — and any chapter accepts them at any time on request. They never change
the template itself; if one seems to require a structural change, that's a map decision.

Every chapter is one self-contained HTML file at `chapters/chNN-<slug>.html`. No external
requests of any kind: all CSS/JS inline, figures are hand-authored inline SVG, fonts are
system stacks. Pages must work from `file://`, in light and dark themes, down to mobile
widths, and with reduced motion.

## Page anatomy (in order)

1. **Header** — eyebrow row (`← index` link · `1st ed · chapter NN` · `2nd ed · chapter MM`
   · theme toggle button `#themebtn`), chapter title, the chapter's epigraph if it has one.
2. **Framing intro** — a few paragraphs orienting the chapter, ending in a chapter-level
   Feynman box ("the whole chapter in one idea") that also introduces the color language.
3. **Concept sections** — one `<section class="concept">` per top-level book section (h2),
   book subsections as h3, finer material as h4. Every h2/h3 carries `id=` its registry slug
   from `concepts.json` and a `key: <slug>` chip. Walk the section list in `reference/toc.md`
   — every section under the chapter must appear.
4. **Core takeaways** — `<section class="takeaways">`, one `<ul>`, ~8–12 bullets, last bullet
   summarizes the 2nd-edition arc.
5. **Quiz** — `<section id="quiz">`, 12–16 MCQs (4 options each), a Check-answers button with
   score, then a `<details class="anskey">` answer key: per-question explanation of the right
   answer AND why the tempting distractors are wrong. Checking auto-opens the key.
6. **Footer** — prev/next chapter links + index link + the not-affiliated note.

## Design tokens (copy from ch03 and keep identical across chapters)

- Cool paper background, serif body (Charter/Iowan/Palatino/Georgia), ui-monospace for all
  structural labels (nav, key chips, eyebrows, SVG labels, quiz letters).
- **Semantic color language, book-wide: ember `--write` = write path / mutation;
  cyan `--read` = read path / lookup.** Neutral ink for everything else. Never repurpose
  these two hues.
- Theme: tokens on `:root`; dark via `@media (prefers-color-scheme: dark)` guarded with
  `:root:not([data-theme="light"])`, plus `:root[data-theme="dark"]`; toggle persists to
  localStorage key `ddia-theme`.
- Signature: the sticky left "SPARSE INDEX" nav (mono slugs, `.l1` for h2 entries) — the page
  presents itself as a sorted, indexed log.

## Components

- **Feynman box** `.feynman` — plain-language analogy per major concept. Tag line
  `FEYNMAN · <topic>`. At least one per h2 section.
- **2nd-edition aside** `.ed2` — tag `2ND EDITION · <topic>`; content sourced from
  `research/02-second-edition-deltas.md`; respect its [inferred from refs repo] flags.
- **Cross-reference** `.xref` — inline `<a>` with `data-tip` tooltip text and a `<sup>`
  marker: backward `class="xref back"` + `<sup>←N</sup>`, forward `class="xref fwd"` +
  `<sup>→N</sup>`. Href = `chNN-<slug>.html#<concept-slug>` from `concepts.json`. Tooltip
  text: `Ch N · Title — one-line definition` (append `· not yet written` for unbuilt
  chapters). Every chapter should link both directions where the book does.
- **Stepper** `.anim` — the click-through animation. One `<svg>` where elements carry
  `data-on="1-3,5"` (steps visible, 1-based ranges) and optional `data-hot="2"` (highlight);
  a `.ctl` row (prev/next/restart + `.count`); an `<ol class="cap">` with exactly one `<li>`
  per step — caption format `<strong>LABEL</strong> sentence(s)`. Steps must read as a story:
  setup → mechanism → payoff/takeaway. Arrow keys work when the figure is focused.
- **Static figure** — `<figure><svg role="img" aria-label=…>…<figcaption>` for mechanisms
  that don't move. Label the arrows; captions carry the argument, not the drawing.
- **Tables** — wrap in `.tablewrap` for horizontal scroll.

## Content rules

- Ground every section in the book text: extract the chapter's pages from
  `reference/ddia-1st-edition.pdf` (pypdf venv at `.venv/`) before writing; page ranges in
  `reference/toc.md`. Explanations are original prose — never reproduce book text beyond
  short attributed phrases.
- Feynman-first: each concept gets the mechanism (what/why), a concrete example, and — for
  anything with moving parts — a stepper. Prefer one great stepper per big idea over many
  small ones (ch03 has 6 steppers + ~7 static figures; use as calibration).
- Real system names stay (Bitcask, RocksDB, Vertica…); 2nd-edition system updates go in
  `.ed2` asides, not mixed silently into 1st-edition claims.
- After building: fill the chapter's `definition` fields in `concepts.json` (one line each,
  usable as tooltip text elsewhere), replace the chapter's stub file, update `index.html`
  status, run an HTML tag-balance check and `node --check` on the extracted script.

## Process per chapter ticket

1. Claim ticket → extract chapter text → read the deltas file's section for this chapter.
2. Build the page per this template. 3. Fill `concepts.json` definitions. 4. Validate
(tags + JS). 5. Commit, push. 6. User reviews in browser; iterate. 7. Close ticket with
resolution notes; update the map.
