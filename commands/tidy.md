---
name: tidy
description: File Daitoshokan journal entries into shelves now, without waiting for 5 to pile up.
---

# File the journal into shelves

Run "4. Filing procedure" from `library/how-to-run.md`. **Keep the token cost minimal.**

1. Grep `library/journal/` for `^## `, restricted to **`20*.md` only** (`README.md` is excluded — it holds examples). Do not read bodies
2. Headings without `✅` are the work list. If there are none, report "nothing to file" in one line and **stop immediately**
3. Read just the few lines of each target entry and file it into the shelf named by `| shelf:`
   - The shelf table in `library/catalog.md` is authoritative. Do not invent new shelves
   - If `| shelf:` is missing, decide from the content and report "N entries missing a shelf tag"
   - Merge overlapping content with existing entries
4. While a shelf is open, fix or delete anything contradicting current facts (do not go looking in shelves you did not open)
5. Add `✅` in front of the date in each filed heading (`## ✅2026-08-05 ...`). Never delete the body
6. Report in one or two lines: "filed N, revised N, missing tags N"

## Do not
- Re-read everything or read a shelf end to end
- Delete or rewrite journal bodies
- Split a shelf unless it is past ~300 lines (if it is, split it and update the catalog)
