# Bootstrap the ddia repo

- **Type**: wayfinder:task (HITL — needs the user's GitHub auth and Downloads access)
- **Status**: open
- **Assignee**: yagyesh (session, 2026-08-13)
- **Blocked by**: —

## Question

Get `~/ddia` fully operational so chapter work can start:

1. **Book file** (user): the shell cannot read `~/Downloads` (macOS privacy). User runs:
   `cp "/Users/yagyesh.srivastava/Downloads/Designing Data-Intensive Applications The Big Ideas Behind Reliable, Scalable, and Maintainable Systems by Martin Kleppmann (z-lib.org).pdf" ~/ddia/reference/ddia-1st-edition.pdf`
2. **TOC extraction** (agent): Read the PDF's table of contents and per-chapter section headings; commit as `reference/toc.md`. This is the completeness checklist every chapter session walks.
3. **GitHub** (user + agent): create a **private** repo on the user's personal GitHub account and push. Check which account `gh auth status` is logged into first — work account is likely; may need the user to auth or provide a remote URL.
4. **Hosting decision** (user): GitHub Pages needs Pro on private repos. Pick: Pages (Pro), public repo + Pages, or plain `file://` browsing. Record the choice.

## Resolution

_(recorded on close: what was done, remote URL, hosting choice)_
