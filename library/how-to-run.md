# How to run the library (written by the AI, read by the AI)

This library runs in three steps: **write to the journal → file entries into shelves once they pile up → read only what you need from the shelves.**
Two contracts hold the three steps together: **`| shelf:xxx` and `✅` in the heading line.** If either breaks, the automation silently stops.

---

## 1. Writing a journal entry (once per wrapped-up piece of work)

Append to the end of `journal/YYYY-MM.md`. **Always put the destination shelf in the heading. 5 lines maximum.**

```
## 2026-08-05 What you did | shelf:work
- Did: what happened, in one line
- Output: file path or URL
- Learned: something worth carrying forward
```

- An entry without `| shelf:` cannot be picked up by filing and will never reach a shelf
- Use the shelf's **filename without `.md`** as the name (the list lives in `catalog.md`)
- For two destinations: `| shelf:work,ai-tips`
- Never paste raw logs (full transcripts, full error dumps). Keep it to the point
- Chit-chat sessions and work not worth 5 lines: **don't write anything**

## 2. The filed marker (the contract with filing)

Once an entry has been filed into a shelf, put `✅` in front of the date in its heading.

```
## ✅2026-08-05 What you did | shelf:work
```

- Filing only processes headings **without** `✅`. The journal can grow for months without the reading cost going up
- No double-filing (it is idempotent). Skipping filing any number of times loses nothing
- Never delete the body of a filed entry — the journal stays as the raw chronological record

## 3. When filing is triggered (the user does nothing)

**Right before appending to the journal, grep this month's file for heading lines (`^## `). If 5 or more headings lack a `✅`, file them.**

Do not schedule filing by time ("once a week"). Time-based rules have no owner, so nobody starts them and the system quietly dies.
Riding on "writing to the journal" — something that always happens — means filing always gets its turn.

## 4. Filing procedure

1. Grep `journal/` for `^## `, restricted to **`20*.md` only** (`README.md` holds examples, so exclude it). Do not read bodies
2. Use the line numbers of the headings without `✅` to read just those few lines. Never read the whole journal
3. File each entry into the shelf named by `| shelf:`
   - The shelf table in `catalog.md` is authoritative. Do not invent new shelves
   - If `| shelf:` is missing, decide from the content and report "1 entry missing its shelf tag"
   - Merge with an existing entry when the content overlaps (never say the same thing twice)
   - If the authoritative source lives in another file, link to it in one line instead of copying
4. While a shelf is open, fix or delete anything that contradicts the current facts (do not go looking in shelves you did not open)
5. Add `✅` to every heading you filed. **Forget this and everything gets filed again next time**
6. Report in one or two lines: "filed N, revised N"

## 5. Reading a shelf

- **Never read a shelf top to bottom.** Grep for headings (`^#{2,3} `) or keywords first, then read only that section
- Do not open a shelf whose "open it when..." line in the catalog does not match the task
- One or two shelves per task, as a rule

## 6. Writing into a shelf

- One entry = a heading plus a few lines: when, what happened, where it lives, what was learned
- **If an authoritative source exists elsewhere, link to it instead of copying** ("see xxx.md for the full procedure")
- **Never put writing tips inside a shelf.** This file is the single source for how to write. Tips in a shelf get re-read every time it opens
- Lessons that graduate into rules (e.g. the same mistake twice) belong in the always-loaded file (CLAUDE.md / AGENTS.md), not a shelf
- Never mix examples with real content. Sample text left in a shelf is not a fact

## 7. Designed to last

- **Compression over time**: journal (daily, raw) → shelves (by topic, organized) → yearbook (yearly, one page). Old detail sinks down; reading the top layer still gives you the whole picture
- **Yearly yearbook** (adopt once the routine sticks): condense 12 months of journal entries into `yearbook/YYYY.md`. Once written, that year's journal graduates from your reading list (archive it, don't delete it)
- **The catalog stays one page**: when it outgrows that, nest the shelves and list only the parents
- **Split a shelf past ~300 lines** and update the catalog
- **Tool-independent and portable**: plain Markdown only, minimal dependence on paths or tool names

## 8. A library you can't search is a dead library

- Write filenames and headings in ordinary words you'd actually search for
- Give full names plus locations (file path or URL) on first mention. No "that thing" or "the usual"
- Always use absolute dates (2026-08-05). Never "last week" or "yesterday" — they stop meaning anything later
