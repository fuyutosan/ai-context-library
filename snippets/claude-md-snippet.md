# Snippet to add to CLAUDE.md (or your custom instructions)

Paste the following near the top of your `CLAUDE.md`, or into your AI tool's custom instructions field.

```markdown
## 📚 Daitoshokan (working-context library)
When starting new work, read `library/catalog.md` and load ONLY the relevant shelves. Never load the whole library (it wastes context and degrades answer quality).
When a piece of work wraps up, leave a record of 5 lines or fewer in `library/journal/YYYY-MM.md` (format: `library/how-to-run.md`). Once a week, file journal entries into shelves and revise stale statements.
```

That's all it takes — the AI will now check the catalog on its own at the start of each new conversation and read only the shelves it needs.
