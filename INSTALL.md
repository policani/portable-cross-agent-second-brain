# Install — set up the vault, skills, and your agent

Setup is once per environment. The knowledge base itself is just the markdown in
`knowledge-base/`; "installing" means pointing your agent at it and (optionally)
connecting sources.

## What's in the box

```
portable-knowledge-base/
  CLAUDE.md            # Claude entry point (rules + where the vault is)
  AGENTS.md            # Codex + Cursor entry point (same rules, in parity)
  knowledge-base/      # the 7 notes — your actual memory
  _inbox/              # drop raw material here
  _proposed/           # drafts await your approval here
  skills/ingest/       # capture new material -> _proposed/
  skills/curate/       # weekly health check -> _proposed/
  index.html           # open in a browser to read the vault
  INSTALL.md           # this file
  README.md
```

## 1. Fill the vault

Either edit the seven notes in `knowledge-base/` by hand, or let the AI do it:
drop source material in `_inbox/`, run the **ingest** skill, then approve the
drafts it writes to `_proposed/`.

## 2. Point your agent at it

**Claude (Cowork):** select this folder, and paste `CLAUDE.md` into the folder's
instructions. Connect sources (email, calendar, Drive) from the `+` → Connectors
if you want automatic ingest. Upload `skills/ingest` and `skills/curate` as
skills.

**Claude Code:** just open this folder. Claude Code reads `CLAUDE.md` and the
`skills/` folder from disk automatically.

**Codex:** open this folder. Codex reads `AGENTS.md` from the root.

**Cursor:** open this folder. Cursor reads root `AGENTS.md` natively — no
`.cursor/rules` file needed. (You can still add one later if you want
Cursor-specific behavior.)

Because Claude reads `CLAUDE.md` and Codex + Cursor read `AGENTS.md`, the same
vault behaves identically in all three. Keep the two files in parity if you edit
the rules.

## 3. Keep it current

- Run **ingest** whenever new material shows up.
- Run **curate** weekly (schedule it in Cowork, or invoke it on a cadence in
  Codex/Cursor).
- Approve drafts from `_proposed/` into `knowledge-base/`. Nothing becomes
  trusted memory until you say so.

## 4. Prove it works

Ask your agent for one real task — a follow-up email, a meeting prep, a brief —
using only the vault. Then ask the same thing in a blank AI with no vault. The
difference is the whole point.
