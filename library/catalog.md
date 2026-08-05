# 📚 Daitoshokan Catalog (read this one page to find the right shelf)

This library stores the context of all your work with AI. **Open it only when you actually need it.**

## Open / don't open

| Open it | Skip it |
|---|---|
| The task needs past history or why something was decided | One-off questions answered on the spot |
| Continuing an existing project | Anything general knowledge covers |
| Proposals, planning, prioritization (preferences shelf) | Routine work with a settled procedure |

When in doubt, don't open it. You can always open it the moment you need it.

## How to use (3 lines)

1. Check this catalog and pick just 1–2 relevant shelves
2. Never read a shelf end to end — grep for headings or keywords and read only that section
3. When the work wraps up, leave a record of 5 lines or fewer in `journal/YYYY-MM.md`
   → the heading must carry `| shelf:xxx` (without it, nothing reaches a shelf; format in `how-to-run.md`)

## Shelf guide (these 4 are examples — rename, add, or drop them to fit yourself)

| Shelf | Open it when the task involves... |
|---|---|
| [work](shelves/work.md) | Your job, side projects, client work — history and decisions |
| [hobbies-creative](shelves/hobbies-creative.md) | Personal creative work, hobby projects, things made for fun |
| [ai-tips](shelves/ai-tips.md) | How you use AI well — cost control, past failures and fixes |
| [preferences](shelves/preferences.md) | Proposals, design choices, prioritization — your values and tastes |

> **Note right after install (for the AI)**: while a shelf still holds the shipped sample text, do not treat it
> as fact about the user. Everything below a sample divider is an illustration, not their information.

## Filing runs itself

Right before appending to the journal, grep this month's file for heading lines. If **5 or more** headings lack a `✅`,
file them into shelves following "4. Filing procedure" in `how-to-run.md`. **The user never has to ask.**

## Division of labor with other stores (avoid duplication)

| Where | What goes there | When it's read |
|---|---|---|
| **CLAUDE.md / AGENTS.md** | Hard rules — only things that change a decision | Automatically, every time |
| **library/shelves** | Know-how, reasoning, history. Not a rule yet, but it pays off later | Only when needed |
| **library/journal** | Raw chronological notes (the waiting room before a shelf) | Only during filing |

Never write the same thing in two places. Put it where the authoritative copy lives and link from the other.

## Adding shelves

- When a new theme comes up 2–3 times, give it its own shelf (a new file under `shelves/`)
- **Add one row to the table above.** Filing reads this table to pick a destination — skip this and entries never get filed
- If a shelf grows past ~300 lines, split it by topic and update this catalog

## Journal and yearbook

- `journal/YYYY-MM.md` ← this month's log, one file per month. Filed headings carry `✅`
- `yearbook/YYYY.md` ← once the routine sticks, condense 12 months into one page each year (not needed at first)
