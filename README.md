# 📚 Daitoshokan (The Great Library) — a plain-Markdown memory system for AI assistants

> 🤖 **AI agents**: if the user asks you to install this, read [INSTALL.md](INSTALL.md) and follow it top to bottom.
>
> 🇯🇵 **日本語版**: [daitoshokan-ai-library](https://github.com/fuyutosan/daitoshokan-ai-library)

Tired of re-explaining yourself to ChatGPT or Claude every single time? *"I'm this kind of person, I'm working on this project, here's the background again..."*

**Daitoshokan** (Japanese for "The Great Library") stores your working context — who you are, what your projects are, what you've already decided — in three simple layers of plain Markdown: **catalog → shelves → journal**. No programming required. **And the AI does both the recording and the filing itself.**

---

## 🪄 Installing takes one sentence

Say this to Claude Code, Codex, or any file-capable AI agent:

```
Read INSTALL.md at https://github.com/fuyutosan/ai-context-library and install Daitoshokan for me
```

The agent fetches the files, drops in `library/`, appends the config to your always-loaded instruction file
(CLAUDE.md / AGENTS.md), **asks you three questions to rebuild the shelves around your actual life**, and reports back.

Prefer doing it by hand, or want to understand it first? See "5-minute setup" below.

---

## 🙋 Does this sound familiar?

- **You keep re-explaining everything** — every new conversation starts from zero
- **The AI gets dumber as the conversation gets longer** — it forgets earlier instructions and gives weird answers (this is *context rot*, a known property of LLMs — not your fault)
- **Memory resets between sessions** — cross a session boundary and it's all gone

Daitoshokan solves all three by giving the AI an **external memory it reads and writes by itself**.

---

## 🏗 How it works

```
┌──────────────────────────────────────────────┐
│  catalog.md  ← checked only when needed      │
│  "There are 4 shelves. For this task,        │
│   open the 'work' shelf."                    │
└───────────────┬──────────────────────────────┘
                │ open only relevant shelves, grep for the section
                ▼
┌──────────────────────────────────────────────┐
│  shelves/work.md, shelves/ai-tips.md ...     │
│  ← knowledge organized by topic              │
│  (project history, decisions, preferences)   │
└───────────────┬──────────────────────────────┘
                │ once 5 unfiled entries pile up,
                ▲ the AI files them by itself
┌──────────────────────────────────────────────┐
│  journal/2026-08.md                          │
│  ← a 5-line entry each time work wraps up    │
│    filed headings carry a ✅                 │
└───────────────┬──────────────────────────────┘
                │ once a year, condensed (optional)
                ▼
┌──────────────────────────────────────────────┐
│  yearbook/2026.md                            │
└──────────────────────────────────────────────┘
```

**Information gets compressed as it moves up.** Daily notes (journal) → knowledge by topic (shelves) → a one-page year (yearbook).
A new conversation only needs the catalog, which points to the right shelf — so the amount read stays minimal. That cuts cost *and* protects answer quality.

---

## ⚙️ What makes it run by itself

The whole thing turns on **two contracts**.

| Contract | Meaning |
|---|---|
| `\| shelf:xxx` | Written in a journal heading: which shelf this entry belongs to |
| `✅` | Added to the heading: already filed into a shelf |

```
## ✅2026-08-05 Locked the color scheme for site A | shelf:work      ← filed
## 2026-08-06 Outlined chapter 2 of the short story | shelf:hobbies-creative   ← not yet
```

Right before adding to the journal, the AI **greps the heading lines only**. If five or more lack a `✅`, it files them on the spot.

Consequences of this design:

- **You never say "please organize this"** — filing rides on the act of writing
- **The journal can grow for months without the reading cost going up** — only heading lines are scanned
- **Nothing gets filed twice** — that's what `✅` is for
- **Skipping it for months loses nothing** — the trigger is a marker, not a date

> 💡 The first version of this template said "once a week, ask the AI to organize the journal." That **does not work**.
> Nobody owns "once a week", so it never starts and the journal just piles up.
> Time-based rules die quietly. **Attach the rule to something that always happens** — that was the fix.

---

## ⏱ 5-minute setup (manual)

### Step 1 — Copy `library/`

Copy this repo's `library/` folder into the root of your working folder.

```
your-working-folder/
├── library/
│   ├── catalog.md
│   ├── how-to-run.md
│   ├── shelves/
│   └── journal/
└── CLAUDE.md (or AGENTS.md)
```

### Step 2 — Paste the snippet into your always-loaded file

Copy the contents of the ```markdown block in `snippets/claude-md-snippet.md` into `CLAUDE.md` (or `AGENTS.md` for Codex, `.cursor/rules/` for Cursor, the custom-instructions box for ChatGPT).

That snippet is **the only thing loaded every session**. It carries the read conditions, the write format, and the filing trigger.

### Step 3 — Make the shelves yours

The four shipped shelves are examples. Tell the AI:

```
Read library/catalog.md and library/how-to-run.md and learn how this works.
Then ask me three questions and rebuild the shelves around my actual work.
Make the catalog table and the real shelf files match exactly.
```

**If the catalog table and the real files drift apart, filing has no destination and the automation stops.** That's the one thing to watch.

### Step 4 (optional) — Install the slash commands

On Claude Code, copy `commands/log.md` and `commands/tidy.md` into `.claude/commands/` for `/log` and `/tidy`. Not required — the automation runs without them.

---

## 📋 The rules in three lines

Full version in `library/how-to-run.md`.

1. **The AI writes 5 lines to the journal when work wraps up** (with `| shelf:xxx` in the heading)
2. **Once 5 unfiled entries pile up, the AI files them into shelves** (you say nothing)
3. **Shelves are never read end to end** — grep, then read only the matching section

---

## ❓ FAQ

**Q. Do I need to know how to code?**
A. No. It's all plain Markdown text files.

**Q. Does it work outside Claude Code?**
A. Yes. Codex, Cursor, GitHub Copilot CLI — any agent that reads and writes files works as-is. In plain ChatGPT or Gemini you can attach the library contents, but the "AI checks the catalog and opens only what it needs" automation really needs a file-capable tool.

**Q. Will the AI ever forget to write a journal entry?**
A. Yes. Deciding that "a piece of work wrapped up" is a judgement call, so it isn't 100%. If you notice it hasn't, just say "log this" (or run `/log` if you installed the commands). Once something is written, filing happens automatically.

**Q. Can I have more than four shelves?**
A. Yes — add a row to the table in `library/catalog.md` and a file under `library/shelves/`. **Just keep the table and the files in sync**, since filing uses the table to choose a destination. Three to five shelves is easiest to navigate.

**Q. What about the sample text in each shelf?**
A. Everything below the `⚠️ Everything below is SAMPLE text` divider is an illustration. The AI is instructed not to treat it as fact, and you can delete it once you start writing your own.

**Q. Can I share this with my team or family?**
A. Yes, but the library tends to accumulate personal and confidential details — review the contents before sharing or publishing.

---

## 🗂 What's in this repo

```
ai-context-library/
├── README.md                  ← this file (for humans)
├── INSTALL.md                 ← setup instructions for AI agents
├── library/
│   ├── catalog.md             ← the index, with open/don't-open conditions
│   ├── how-to-run.md          ← the source of truth: format, markers, filing procedure
│   ├── shelves/
│   │   ├── work.md
│   │   ├── hobbies-creative.md
│   │   ├── ai-tips.md
│   │   └── preferences.md
│   └── journal/
│       └── README.md          ← journal format and examples
├── commands/                  ← Claude Code slash commands (optional)
│   ├── log.md                 ← /log  record the current work
│   └── tidy.md                ← /tidy file entries right now
└── snippets/
    └── claude-md-snippet.md   ← the config you paste into your always-loaded file
```

---

Daitoshokan isn't a clever tool — it's a boring operating habit. Nothing flashy, but it compounds.
Start with a single shelf.
