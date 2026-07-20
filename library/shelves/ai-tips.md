# Shelf: ai-tips

How you use AI well — workflow tricks, cost control, context management, and past failures with their fixes.

## Writing tips
- Treat this as a "never repeat the same failure" record (approaches that *didn't* work belong here too)
- Once a lesson hardens into a rule you should follow every time, promote it out of this shelf into the rules layer (CLAUDE.md or custom instructions). This shelf keeps the background and the story

---

## Incident log (example)
- **Answers degraded in a long conversation (e.g. 2026-07-05)**: tried to batch several tasks into one conversation; partway through, the AI started forgetting earlier instructions → made it a rule: "one errand per conversation — start fresh when a task is done"

## Context management principles (the design philosophy behind this library)
- Answer quality drops as conversations grow (known as *context rot*) → aim for one errand per conversation
- AI tends to skim the *middle* of long text (*lost in the middle*) → put critical instructions at the start or end, never buried in the middle
- The main driver of cost and slowdown isn't your instructions — it's the long logs and data the AI itself generates → save long output to files and reference them only when needed
- **Read the catalog first, then only the relevant shelves — the "library method"** helps both cost and answer quality
