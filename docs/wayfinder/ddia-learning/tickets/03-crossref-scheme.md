# Cross-reference scheme (concept anchor registry)

- **Type**: wayfinder:grilling (HITL)
- **Status**: open
- **Assignee**:
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

_(recorded on close)_
