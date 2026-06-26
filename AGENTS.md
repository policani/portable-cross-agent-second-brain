# Knowledge Base — operating guide for Codex and Cursor

This is your living memory: the owner's knowledge base. Read from it to do their
work in their voice and context, and help keep it current. The owner reads and
edits it too.

## Parity note (this is the whole point)

The same rules apply whether you are running in **Codex**, **Cursor**, or
**Claude**. Codex and Cursor both read this `AGENTS.md` (Cursor reads root
`AGENTS.md` natively); Claude reads `CLAUDE.md`. The two files are kept in parity
— same rules, phrased for each client. If you change an operating rule in one,
mirror it in the other. There is no separate `.cursor/rules` file to maintain.

## Find the knowledge base

The notes live in `knowledge-base/` next to this file:

- `snapshot` — who they are, one-paragraph orientation
- `key-people` — stakeholders, roles, who decides what
- `preferences-and-rules` — how they like things done, and the red lines
- `project-history` — what's happened, in order
- `decisions-and-rationale` — what was decided and why
- `open-loops` — commitments and follow-ups still in the air
- `source-links` — where each fact came from

Each note has frontmatter (`title`, `source`, `date`, `status`, `sensitivity`).
If the notes are not here, they may be in a connected project or a linked
Notion/Drive — ask where the vault lives rather than guessing.

## How to use it

- Before answering or drafting, read the relevant notes. Prefer vault facts over
  assumptions, and reflect `preferences-and-rules` (voice, red lines).
- Cite the source note for important claims. A claim with no source is an
  opinion, not memory.

## Keeping it current — propose, then approve

- New material flows `_inbox/` → ingest → `_proposed/`. You draft; the owner
  approves and promotes. **Never** write straight into `knowledge-base/` as
  trusted fact.
- Mark every fact's `status`: `extracted` (from a source) · `inferred` (needs
  confirmation) · `verified` (confirmed) · `deprecated` (history only).
- Label `sensitivity`: `public` · `internal` · `confidential` · `restricted`.
  Keep `restricted` material (credentials, personal/legal/medical) out unless
  the owner explicitly approves it.
- Two skills do the ongoing work: `skills/ingest` (capture new material) and
  `skills/curate` (periodic health check). See `INSTALL.md`.

## The invariant

AI only ever **proposes**. A human approves before anything becomes trusted
memory. The moment an unreviewed guess lands as fact, the system recreates the
exact problem it exists to solve.
