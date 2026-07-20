# 📚 Daitoshokan Catalog (read this one page to find the right shelf)

This library stores the context of all your work with AI.
**In every new conversation, read ONLY this catalog first.** Then open just the shelves relevant to the task at hand.

## How to use (3 lines)
1. When starting new work, check this catalog and pick the relevant shelf
2. Read that shelf (`shelves/xxx.md`) before diving into the work
3. When the work wraps up, leave a 5-line record in `journal/` (format: see `how-to-run.md`)

## Shelf guide (start with these 4 examples — rename or add shelves to fit yourself)

| Shelf | Open it when the task involves... |
|---|---|
| [work](shelves/work.md) | Your job, side projects, client work — history and decisions |
| [hobbies-creative](shelves/hobbies-creative.md) | Personal creative work, hobby projects, things made for fun |
| [ai-tips](shelves/ai-tips.md) | How you use AI well — cost control, past failures and fixes |
| [preferences](shelves/preferences.md) | Open before proposals, design choices, or prioritization. Your values and tastes, written so the AI can follow them |

## Adding shelves
- When a new theme comes up 2–3 times, give it its own shelf (create a new file under `shelves/`)
- Just add one row to the table above. Keep the catalog short enough to fit on one page
- If a shelf grows past ~300 lines, split it by topic (e.g. `work.md` → `work-project-a.md`) and update the catalog

## Yearbook (add later, once the library has grown)
- Once the routine is established, create a `yearbook/` folder and, once a year, condense 12 months of journal entries into a single page
- You don't need this at first (shelves + journal are enough)

## Journal (raw, chronological notes)
- `journal/YYYY-MM.md` ← this month's log. One file per month

## Division of labor with other stores (avoid duplication)
- **CLAUDE.md (or custom instructions)** = hard rules, loaded automatically every time. Only settled conclusions go here
- **This library (library/)** = the history and lived experience of "what we've done." Knowledge that isn't a rule yet, but pays off later
