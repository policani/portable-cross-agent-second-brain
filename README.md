# Memventory — Team

Memventory is a structured, visual second brain: a portable plain-markdown wiki
that works the same in **Claude, Codex, and Cursor** through just two instruction
files. It routes to the note it needs instead of loading everything, limiting
unnecessary context loading; a propose-then-approve process means nothing
untrusted ever lands as fact.

No database. No vectors. No Obsidian. No lock-in. Clone it, fill in seven notes,
point any of three agents at it, and your AI stops forgetting who you are between
sessions.

![Memventory Team Management Console showing vault metrics, a searchable folder rail, the live constellation map, and an inspection panel](assets/memventory-team-console.png)

*The bundled Management Console renders the shared vault like this. Open
`index.html` through the included launcher to search files, browse folder
regions, switch views, and inspect the live constellation. Nothing reaches
trusted memory without approval.*

## What it solves

Memventory addresses the practical failures behind “AI amnesia”: context resets,
repeated re-explaining, scattered decisions, uncertain AI-generated facts, and
memory trapped in a single tool. It gives teams portable context continuity,
source-aware working memory, selective retrieval, and an approval boundary for
trusted shared knowledge.

See [PRODUCT_IDENTITY.md](PRODUCT_IDENTITY.md) for the customer problems,
personal and business value, claim discipline, and an honest measurement method
for token efficiency.

## Visual Console and Wiki

Your second brain now has a **console** — open
**`Open-Memventory-Console.bat`** to manage the whole vault in the browser.
It starts a local-only helper, so the **Refresh** button can rebuild the index
and reload the same page with an updated timestamp. No account is required and
your files never leave your machine.

The console renders the vault you choose to index, rather than shipping a
real-person example. The public map above is an anonymized schematic of the
same structure.

The console is one page with several lenses over the same vault:

- **Constellation** — the interactive map, now building in real time on load.
- **Types** — files grouped and colored by role or raw format, with counts and sizes.
- **Sizes** — a treemap that makes large files and folders obvious at a glance.
- **Table** — a sortable, **Excel-style filterable** list; filter to just AI-logic
  files, or just outputs, in two clicks.
- **Inventory scope** — switch plainly between Memory & work files, All files,
  and Cleanup candidates so a large physical inventory never makes the map
  unreadable by default.
- **Cleanup** — a read-only storage-triage report that flags known runtime
  caches, rebuildable dependencies, build output, large files, archives, and
  exact duplicates with its evidence. It never deletes files or claims that
  candidate bytes are reclaimable space.
- **Refresh** — rebuilds the local index and reloads the current console page.

Search, folder tree, per-type filters, and a detail inspector are always at hand.
In the constellation, use × to hide the search and display controls, then ☰ to
bring them back. Everything runs locally against your own notes — nothing is
uploaded.

> **This is the Team edition** — built for shared use, with a propose-then-approve
> gate so memory stays trustworthy when more than one person (and their agents)
> write to it. Working solo? The
> Personal edition drops the gate: the AI drafts straight into one person's notes.

## How it works

```mermaid
flowchart LR
    inbox["_inbox/<br/>drop raw material"] --> ingest{{"ingest skill<br/>AI drafts"}}
    ingest --> proposed["_proposed/<br/>drafts for review"]
    proposed --> approve(["human approves"])
    approve --> vault[("knowledge-base/<br/>7 trusted notes")]
    vault -.-> curate{{"curate skill<br/>weekly health check"}}
    curate -.-> proposed
    claude["Claude · CLAUDE.md"] --> router
    codex["Codex · AGENTS.md"] --> router
    cursor["Cursor · AGENTS.md"] --> router
    router{{"selective routing<br/>opens only the note needed — saves tokens"}} --> vault
```

New material is always **proposed**, never written straight to memory; a human
approves before anything in `knowledge-base/` becomes trusted. On the read side,
each of the three agents **routes to the one note it needs** instead of loading
the whole vault — that's the token-saving retrieval layer. The same vault is read
by all three agents through two files kept in parity: Claude reads `CLAUDE.md`;
Codex and Cursor both read `AGENTS.md` (Cursor reads it natively).

The routing is enforced by code, not just convention. The bundled **`brain.py`**
(one file, Python stdlib, zero dependencies) indexes every heading-level section
of the vault and answers "where is X?" deterministically — keyword scoring,
`path:line` targets, best section printed straight to the terminal — before a
single model token is spent. The same generated index feeds the **web Management
Console** (`index.html`) and the standalone **Constellation map** (`vault-map.html`).
The map opens directly from the filesystem; use `Open-Memventory-Console.bat`
when you want Refresh to rebuild and reload the console in the same browser page.

Nested `AGENTS.md` and `CLAUDE.md` files stay discoverable without becoming
global policy. Run `python brain.py --instructions "project/folder"` to inspect
the root-to-local chain for Codex/Cursor and Claude, or
`python brain.py --instruction-gaps` to review missing counterparts. The
registry reports scope and provenance; it does not resolve contradictions or
claim that client files are semantically identical.

## Why it's valuable

The business value is continuity with control: teams can recover decisions,
commitments, and operating context without rebuilding the story in every
session; managers can inspect sources, fact status, and approval history rather
than accepting an AI’s guess as memory. Selective routing focuses the context an
agent needs, which can reduce avoidable model-input loading when broad vault
reads would otherwise recur.

Memventory deliberately does not advertise a universal token multiplier, cost
payback, or productivity promise. Those outcomes depend on the workflow and
must be measured against a real baseline. The included product identity sets out
the claims the product can make now and how to earn stronger ones.

## Status

Working starter kit. Copy the folder, fill the vault, point your agent at it. The
structure and rules are stable; the seven notes ship as templates with one small
fictional example.

## Why this exists

Most "AI second brain" setups are either too complicated (vector stores,
plugins, a tool to learn) or locked to one vendor. This is the opposite:

- **Uncomplicated.** Seven markdown files and two instruction files. You can read
  the whole thing in ten minutes. The knowledge is yours, in a format any AI can
  read, forever.
- **Interchangeable across agents.** Claude reads `CLAUDE.md`; Codex and Cursor
  read `AGENTS.md` (Cursor reads it natively as of 2026). Two files in parity =
  one vault that behaves consistently in all three. Switch tools, or use all
  three on the same brain, with zero migration.
- **Token-efficient by design.** Selective routing means the agent reads a small
  map and opens only the relevant note — retrieval without a vector database.
  It's what keeps the no-database approach cheap as the vault grows.
- **Trustworthy.** New material flows `_inbox/` → ingest → `_proposed/` → you
  approve. AI only ever proposes; a human approves before anything becomes
  memory. That invariant is what makes it safe to rely on.

## What's inside

```
CLAUDE.md / AGENTS.md   two instruction files, kept in parity (the parity is the product)
knowledge-base/         the 7 notes: snapshot, key-people, preferences-and-rules,
                        project-history, decisions-and-rationale, open-loops, source-links
_inbox/  _proposed/     capture staging and the approval queue
skills/ingest/          capture new material into proposed notes
skills/curate/          weekly health check
brain.py                deterministic retrieval + scoped instruction registry + relationship ledger
index.html              web Management Console — Constellation, Types, Sizes, Table
vault-map.html          the Constellation map on its own, opens from the filesystem
serve-second-brain.py   localhost-only helper for live console refreshes
Open-Memventory-Console.bat   one-click launcher for the live console
INSTALL.md              setup for Claude, Codex, and Cursor
```

## The 7 notes

A working memory is seven kinds of note — that's the whole schema:

1. **Snapshot** — who they are, one paragraph
2. **Key people** — stakeholders, roles, who decides
3. **Preferences & rules** — how they like things done, and the red lines
4. **Project history** — what happened, in order
5. **Decisions & rationale** — what was decided and why
6. **Open loops** — commitments still in the air
7. **Source links** — where each fact came from

Each note carries frontmatter with a `status` (extracted / inferred / verified /
deprecated) and `sensitivity` (public / internal / confidential / restricted), so
a guess is never mistaken for a fact.

## How the routing works (the token-saver)

The instruction files carry a small routing map — "for this kind of question,
open this note" — and the rule *don't load the whole vault by default*. The agent
reads the map, opens only what's relevant, and skips the rest. With seven notes
the map is tiny; the point is that it keeps working as the vault grows to seventy.
That's retrieval-by-routing instead of retrieval-by-embedding: no vector store
or index server. It can reduce unnecessary context loading, but any savings
claim should be measured in the buyer’s own workflow.

## How to evaluate this in 5 minutes

1. Read `CLAUDE.md` and `AGENTS.md` side by side — note they're the same rules,
   phrased per client, including the routing map. That's the portability and the
   token-saving, made concrete.
2. Skim `knowledge-base/snapshot.md` to see the note shape and the example.
3. Read `skills/ingest/SKILL.md` to see how capture stays propose-then-approve.
4. Then the real test: open the folder in Claude (or Codex, or Cursor), fill the
   snapshot, and ask for one real task using only the vault. Run the same ask in
   a blank chat with no vault. The difference is the point.

## Quick start

See `INSTALL.md`. Short version: fill `knowledge-base/`, point your agent at the
folder, run **ingest** when new material shows up, run **curate** weekly, approve
drafts from `_proposed/`.

## Scope boundaries

This is a starter kit, deliberately small. It does **not** include: a hosted
server or database, automated connectors (you wire those per environment), or
migration of historical documents. Those are the natural next step up, not the
first delivery.

---

MIT licensed — plain markdown, no dependencies, yours to run and adapt.
