# Cross-reference scheme (concept anchor registry)

- **Type**: wayfinder:grilling (HITL)
- **Status**: closed (2026-08-26)
- **Assignee**: yagyesh (session, 2026-08-25)
- **Blocked by**: [01-bootstrap-repo](01-bootstrap-repo.md)

## Question

How do chapters reference each other's concepts — including **forward** references to chapters that don't exist yet?

To decide:

1. **Anchor naming**: a stable scheme like `ch05.html#leader-follower` — kebab-case concept slugs, one per concept section. Who owns the slug list?
2. **Registry**: a committed `concepts.json` (or `concepts.md`) mapping every concept slug → chapter, title, one-line definition — generated from the TOC (ticket 01) up front so forward links can be written *before* the target chapter is built.
3. **Dangling-link behavior**: what a forward link to an unbuilt chapter does — dead link, or link to a stub page/index entry that says "not yet written"?
4. **Link presentation**: how a cross-reference looks in the page (inline link, hover tooltip with the one-line definition, a "see also" box per concept?).
5. **2nd-edition notes**: whether the registry also records "in 2nd ed this is chapter X" per concept (feeds from ticket 02).

Output: the scheme recorded here + the initial registry file committed, feeding the pilot.

## Resolution

Scheme decided (user picked all recommended options) and artifacts committed:

1. **Anchors**: `<chapter file>#<concept-slug>` — kebab-case section titles, globally unique (collisions suffixed `-chNN`). Chapter files: `chapters/chNN-<slug>.html`.
2. **Registry**: `concepts.json` at repo root, pre-seeded from the PDF outline — 12 chapters + 169 concepts, each with title, chapter, parent section, 0-based `pdf_page`, 2nd-edition location per chapter, and an empty `definition`. **Definitions are filled by each chapter's build session** (its own concepts); until then tooltips fall back to title + "not yet written". Chapter builds may add finer-grained slugs — additive only, never rename existing slugs.
3. **Dangling links**: every chapter has a stub HTML page at its final filename from day one (committed) — links never 404; builds replace stubs in place. Stubs link to `index.html`, which lands with ticket 16.
4. **Presentation**: inline links at point of mention, styled distinctly (dotted underline, →chN marker), hover tooltip showing the registry definition; backward vs forward refs visually distinguished. Exact styling locks in the pilot.
5. **2nd-ed notes**: carried per chapter in `concepts.json` (`chapters.*.second_ed`) from the deltas research.
