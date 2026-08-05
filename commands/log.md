---
name: log
description: Record the current piece of work in the Daitoshokan journal in 5 lines or fewer.
---

# Write a journal entry

Follow "1. Writing a journal entry" in `library/how-to-run.md`.

1. Open this month's journal `library/journal/YYYY-MM.md` (create it with a `# Journal YYYY-MM` heading if missing)
2. **Check the filing trigger before appending**: grep this month's file for heading lines (`^## `). If 5 or more
   lack a `✅`, run "4. Filing procedure" in `library/how-to-run.md` first
3. Append the current work in 5 lines or fewer

```
## 2026-08-05 What you did | shelf:shelf-name
- Did: what happened, in one line
- Output: file path or URL
- Learned: something worth carrying forward
```

- `| shelf:` is required. Use a shelf name from the table in `library/catalog.md`
- No raw logs. Never exceed 5 lines
- If the work isn't worth recording, say so and write nothing

Report only the heading line you wrote.
