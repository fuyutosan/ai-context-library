# How to run the library (written by the AI, read by the AI)

## 1. Writing journal entries (once per finished chunk of work)
When a piece of work wraps up, append an entry to `journal/YYYY-MM.md` in this format. **Hard limit: 5 lines.**

```
## 2026-07-10 | Task name
- Did: what happened, in one line
- Output: file path or URL
- Learned: an insight worth reusing
- Shelf: work
```

- Filling in "Shelf:" makes the weekly filing much faster
- No raw logs (full conversations, full tool output). Just the essentials, short
- Chat-only sessions and work not worth 5 lines don't need an entry

## 2. Writing shelf entries
- One entry = a heading + a few lines: when, what, where it lives, what was learned
- **If a canonical source exists, link to it instead of copying** (e.g. one line: "full procedure: see CLAUDE.md")
- Lessons that deserve promotion to a hard rule (same mistake made twice, etc.) move OUT of the shelf and INTO the rules layer (CLAUDE.md or custom instructions)

## 3. The weekly filing routine (~10 minutes)
Once a week, do only this. **Never re-read the whole library** (that approach collapses as the library grows).
1. Read this week's journal entries
2. File each entry into its shelf (merge with existing entries when they overlap)
3. While reading a shelf, **if you spot an old statement that contradicts current facts, fix or delete it** (revision)
4. If a shelf exceeds ~300 lines, split it into volumes → update the catalog

## 4. Designing for long-term growth (a library that lives for years)
This library is built to be tended for the long haul.

- **Compression layers over time**: journal (daily, raw) → shelves (by topic, organized) → yearbook (yearly, one page per year). Old detail sinks to the lower layers; reading only the upper layers gives you the whole picture
- **The yearly yearbook routine** (adopt once you're comfortable): condense the previous year's 12 months of journal entries and shelf changes into `yearbook/YYYY.md`, one page. Suggested items: the year's big events / projects that grew / top 3 lessons / numbers (things shipped, etc.). Once a year is condensed, its journals graduate from re-reading (keep them archived, don't delete)
- **The catalog stays one page**: if shelves multiply until the catalog overflows one screen, nest the shelves into subfolders and list only the parent items in the catalog
- **Tool-agnostic**: plain Markdown only. Never write in a way that depends on a specific app, AI model, or format (so any future AI or tool can read it)
- **Portable**: minimize path- and tool-specific references; the structure should survive moving the whole folder somewhere else

## 5. A library you can't search is a dead library
- Use everyday words in filenames and headings (so you can find things later by searching)
- Write proper nouns in full on first mention, with a location (file path or URL). Never "that thing" or "the usual issue"
- Dates are always absolute (2026-07-10). Never "last week" or "yesterday" (meaningless when read later)
