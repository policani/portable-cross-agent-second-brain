---
name: ingest
description: Turn new material into proposed knowledge-base notes. Use when the owner drops files in _inbox/, pastes new material, or says "ingest", "capture this", "add to the knowledge base", or connects a new source (email, calendar, Drive, Notion). Reads sources and existing notes, drafts notes into _proposed/ for approval — never writes to knowledge-base/ directly.
---

# Skill: Ingest new material

Turn new material — from any connected source, not just `_inbox/` — into proposed
notes the owner can approve. You draft; the owner promotes.

## Steps

1. **Gather.** Read everything new the owner has connected: `_inbox/` files,
   pasted text, and (if connected) recent email threads, calendar meetings,
   shared Drive/Docs/Notion. Also read the existing `knowledge-base/` notes so
   you know what's already captured.
2. **Extract durable facts only.** Decisions, preferences, commitments, people,
   changed facts. Skip small talk and anything already in the vault.
3. **Map each fact to a note type:** snapshot, key-people, preferences-and-rules,
   project-history, decisions-and-rationale, open-loops, source-links.
4. **Draft into `_proposed/`** — one file per proposed note, with frontmatter:
   `title`, `source` (always record where it came from), `date`,
   `status: extracted` (or `inferred` if you reasoned it out),
   `sensitivity` (public/internal/confidential/restricted).
5. **Flag conflicts.** If a draft contradicts an existing note, say so explicitly
   in the draft rather than silently overwriting.
6. **Stop.** Do not write to `knowledge-base/`. Tell the owner what you proposed
   and let them approve.

## Rules

- Never promote `restricted` material into the vault without explicit approval.
- A fact with no traceable source is `status: inferred`, not `verified`.
- Recommend; never auto-change trusted memory.
