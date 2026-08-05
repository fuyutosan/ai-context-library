# How to write the journal

The journal holds the raw record of what happened this month. One file per month (`journal/YYYY-MM.md`), appended to whenever a piece of work wraps up.
The authoritative rules are sections 1 and 2 of `../how-to-run.md`. This page just restates the format.

## Format (5 lines maximum)

```
## 2026-08-05 What you did | shelf:work
- Did: what happened, in one line
- Output: file path or URL
- Learned: something worth carrying forward
```

- **`| shelf:` is required.** Without it the entry is never picked up and never reaches a shelf
- Use a shelf name from the table in `../catalog.md` (the filename without `.md`)
- Once filed, the AI adds `✅` to the heading → `## ✅2026-08-05 ...`
- Never paste raw logs (full transcripts, full error dumps). Keep it to the point
- Chit-chat sessions and work not worth 5 lines: don't write anything
- Never delete old monthly files

## Examples

> This file is not named `20*.md`, so filing ignores it — the samples below will never be mistaken for unfiled entries.

```
## ✅2026-08-05 Locked the color scheme for site A | shelf:work
- Did: agreed the final design direction with the client
- Output: `projects/site-a/design-final.pdf`
- Learned: asking for preferred colors up front avoids rework

## 2026-08-06 Outlined chapter 2 of the short story | shelf:hobbies-creative
- Did: drafted 3 outlines and picked one
- Output: `creative/short-story/ch2-outline.md`
- Learned: picking from 3 options kills the "what if" second-guessing later
```

The first is filed (`✅`), the second is not. Filing only touches the second one.
