# Snippet to add to CLAUDE.md (or your custom instructions)

Copy the contents of the ```markdown block below into the file your AI tool always loads.

| Tool | Paste it into |
|---|---|
| Claude Code / Cowork | `CLAUDE.md` |
| Codex / GitHub Copilot CLI | `AGENTS.md` |
| Cursor | `.cursor/rules/library.mdc` |
| ChatGPT, Gemini, etc. | Custom instructions field |

```markdown
## 📚 Daitoshokan (working-context library)

**Read** — Only open `library/catalog.md` when the task needs past history or the reasoning behind a decision, continues an existing project, or involves a proposal or plan. Then open just 1–2 relevant shelves. Never read a shelf end to end: grep for headings or keywords and read only the matching section. Skip the library entirely for one-off questions and self-contained tasks.

**Write** — When a piece of work that created or changed files wraps up, append an entry of 5 lines or fewer to `library/journal/YYYY-MM.md`. The heading MUST be in this form:
`## 2026-08-05 What you did | shelf:work`
(without `| shelf:` the entry is never filed and will sit in the journal forever). Use a shelf name listed in `library/catalog.md`.

**File** — Before appending to the journal, grep this month's journal for heading lines only (`^## `; do not read the bodies). If **5 or more** headings lack a `✅`, follow "4. Filing procedure" in `library/how-to-run.md` to move them into shelves and mark each done heading with `✅`. **Do this on your own — the user should not have to ask.**
```

## What this gives you

- The AI checks the catalog by itself at the start of each conversation and reads only the shelves it needs
- One journal entry appears every time a piece of work wraps up
- Once 5 entries pile up, **the AI files them into shelves on its own**. You never say "please organize this"

`✅` marks "already filed into a shelf." Because of it the AI never re-reads the whole journal and never files the same entry twice.
