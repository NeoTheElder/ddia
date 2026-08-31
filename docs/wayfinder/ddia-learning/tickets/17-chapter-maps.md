# Chapter maps (advance organizers) + book-level overview map

- **Type**: wayfinder:decision + task (template amendment; pilot, then rollout)
- **Status**: open
- **Assignee**: claude
- **Blocked by**:

## Question

Should every chapter open with a "map" — main parts + 5–7 big ideas, with details bucketed under
parts and a return-to-map affordance — per the advance-organizer principle (outline before
details)? And should there be an overarching map of all 12 chapters?

## Decision (grilled 2026-08-31)

Yes to both. Existing partial coverage acknowledged (sticky sparse nav = linear outline; framing
intro = prose map; chapter Feynman box = one-idea thesis; takeaways = ideas at the END); the gap
is the up-front parts+ideas preview, visible bucketing, and cross-chapter relationships.

- **Mechanism**: template amendment, pilot-first — ch 3 pilots the component, user reviews, then
  rollout to all 12. `docs/template.md` is amended when the pilot locks.
- **Per-chapter form**: a new `.map` box (same panel/tag anatomy as `.feynman`/`.ed2`, but a
  neutral ink left border — ember/cyan stay strictly semantic), tag
  `THE MAP · <n> parts, <m> big ideas`, `id="chapter-map"`, and `map` as the first sparse-nav
  entry (the sticky nav is the "return when lost" mechanism; no floating chrome). Inside: one
  bucket per h2 part — linked part name + big-idea one-liners — closing with the through-line.
  No per-chapter SVG map (QA cost); an SVG can be added later as a normal enrichment where a
  chapter's shape is non-linear.
- **Big ideas are fresh previews** that pose each part's tension; end-of-chapter takeaways stay
  unchanged (preview → learn → confirm loop). 5–7 ideas is a guideline that flexes per chapter.
- **Placement**: intro prose → chapter Feynman (one idea) → MAP (parts + ideas) → sections;
  trim intro sentences the map makes redundant.
- **Overarching map**: on `chapters/index.html` after the how-to-read box. One SVG dependency
  graph: 12 chapter nodes grouped by the three parts, edges drawn from the real cross-reference
  counts (96 directional pairs measured; heaviest: ch12→ch11 18, ch12→ch05 12, ch09→ch05 10,
  ch11→ch05 10; most-referenced: ch5 ×48, ch3 ×39, ch9 ×34), pruned to the top ~15 edges, the
  spine ch3→ch5→ch9→ch11→ch12 visually emphasized, nodes clickable.
- **Pilot session builds both** the ch 3 map box and the index overview map; on approval the
  remaining 11 chapter maps roll out in one pass.

## Resolution

_(recorded on close: pilot approved, template.md amended, all 12 chapters carry maps, index map live)_
