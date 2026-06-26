---
name: curate
description: Weekly health check for the knowledge base. Use when the owner says "curate", "health check", "review the vault", "what's stale", or on a weekly schedule. Reads the notes and sources read-only, writes a short health report plus proposed fixes to _proposed/ — never changes knowledge-base/ directly.
---

# Skill: Curate (run weekly)

Keep the vault healthy. **Read-only** on `knowledge-base/` and the sources; write
findings and proposed fixes to `_proposed/`.

## Report and propose fixes for

- Recent source activity (new emails, meetings, docs, `_inbox/` drops) that was
  never ingested.
- Stale notes (past their review date, or outdated by newer notes).
- Contradictions (two notes that disagree).
- Open loops with no recent activity.
- Facts with no source, or still marked `inferred`.
- Gaps the owner clearly cares about but the vault doesn't cover.

## Output

A short health report (what's healthy, what needs attention) plus proposed edits
as draft notes in `_proposed/`. Recommend; never auto-change. The owner approves
and promotes.

## Schedule it

- **Claude Cowork / Code:** run on a weekly scheduled task, or just ask "curate"
  weekly.
- **Codex / Cursor:** invoke the skill weekly, or wire it into your own cron/task
  runner pointed at this folder.
