# Product Improvement Plan

Last updated: 2026-07-01

## Customer-language correction

Do not position this only as a markdown knowledge base. Customer language points
to cross-tool AI memory, context continuity, decisions we made and why, shared
team state, and avoiding context resets without creating an unreviewed fact
dump.

Use language such as:

- portable AI memory;
- context continuity across assistants;
- source-grounded decisions and workflows;
- team-safe propose-then-approve memory;
- selective routing without a vector database;
- stale-memory cleanup.

## Product gap

The Team edition has a strong operating idea but needs clearer examples that
show the approval gate, project namespaces, stale-memory handling, source
lineage, and cross-agent handoff in action.

## Capability backlog

1. Add examples showing `_inbox/` to `_proposed/` to `knowledge-base/` with
   synthetic team notes.
2. Add a namespace example for multiple projects or clients.
3. Add stale-memory detection and cleanup guidance to `INSTALL.md` or examples.
4. Add import/export and restore/backfill notes for Git, Obsidian, or plain
   folder use.
5. Add a walkthrough showing Claude, Codex, and Cursor reading the same note map
   without loading the whole vault.

## Acceptance criteria

- A new evaluator can see how the Team approval gate protects trusted memory.
- Examples make source, status, sensitivity, and decision rationale visible.
- The product remains plain-markdown and vendor-independent.
- The Team edition stays clearly distinct from the Personal edition.
