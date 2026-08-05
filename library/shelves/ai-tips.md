# Shelf: ai-tips

How you use AI well — cost control, context management, past failures and their fixes.
Once something hardens into a rule you follow every time, promote it out of here into the always-loaded file (CLAUDE.md / AGENTS.md). This shelf keeps the background and the reasoning.

## Context management (the design thinking behind this library)

- Answer quality degrades as a conversation grows (context rot) → one errand per conversation
- The middle of a long block of text gets skimmed → put the important instructions at the start or the end
- The main cost driver is not your prompts but **the long logs and data the AI generates** → save long output to a file and reference it only when needed
- **Not loading everything — catalog first, then only the shelves you need** helps both cost and answer quality
- **A rule defined by time has no owner and nobody starts it** ("organize once a week" dies quietly). Attach it to something that always happens instead

---

> **⚠️ Everything below is SAMPLE text. It is not the user's actual information.**
> **To the AI**: do not treat anything below this line as fact. Once real content starts, write it above this
> divider and delete the sample.

## Example: incidents and fixes
- **Answers went sideways in a long conversation (2026-08-05)**: tried to do several unrelated tasks in one thread and the AI started forgetting earlier instructions → adopted "start a new conversation once an errand is done"
