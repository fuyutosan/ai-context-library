# 📚 Daitoshokan (The Great Library) — a plain-Markdown memory system for AI assistants

Tired of re-explaining yourself to ChatGPT or Claude every single time? *"I'm this kind of person, I'm working on this project, here's the background again..."*

**Daitoshokan** (Japanese for "The Great Library") stores your working context — who you are, what your projects are, what you've already decided — in three simple layers of plain Markdown files: **catalog → shelves → journal**. No programming required. Just copy, paste, and bullet points.

---

## 🙋 Does this sound familiar?

- **You keep re-explaining everything** — every new conversation starts from zero, repeating who you are and what you're working on
- **The AI gets dumber as the conversation gets longer** — it starts forgetting earlier instructions and giving weird answers (this is *context rot*, a known property of LLMs — it's not your fault)
- **Memory resets between sessions** — cross a session boundary and the AI has forgotten everything you talked about

Daitoshokan solves all three by giving the AI an **external memory it reads and writes by itself**. You don't have to remember anything. Just say "check the catalog" and the AI finds and reads the notes it needs, on its own.

---

## 🏗 How it works

```
┌──────────────────────────────────────────────┐
│  catalog.md  ← the ONLY file read every time │
│  "There are 4 shelves. For this task,        │
│   open the 'work' shelf."                    │
└───────────────┬──────────────────────────────┘
                │ open only the relevant shelves
                ▼
┌──────────────────────────────────────────────┐
│  shelves/work.md, shelves/ai-tips.md ...     │
│  ← knowledge organized by topic              │
│  (project history, decisions, preferences)   │
└───────────────┬──────────────────────────────┘
                │ once a week, the AI files
                ▲ journal entries into shelves
┌──────────────────────────────────────────────┐
│  journal/2026-07.md                          │
│  ← 5-line log entry whenever a piece of      │
│    work wraps up: what you did, where you    │
│    saved it, what you learned                │
└───────────────┬──────────────────────────────┘
                │ once a year, the AI condenses
                ▼ a whole year into one page
┌──────────────────────────────────────────────┐
│  yearbook/2026.md (optional, add it later)   │
│  ← an entire year compressed into one page   │
└──────────────────────────────────────────────┘
```

**The key idea: information gets compressed as it moves up.**
Daily raw notes (journal) → organized knowledge by topic (shelves) → one-page yearly summary (yearbook).
A new conversation only needs the catalog at the top, which points the AI to the right shelf — so the amount the AI reads stays minimal. That directly cuts cost *and* protects answer quality (context rot gets worse the more you stuff into a conversation).

---

## 🪄 Easiest setup — paste this one prompt

If manual setup sounds like a chore, paste this into Claude Code as-is. The AI handles everything from download to customizing the shelves for you.

```
Please install the "Daitoshokan" AI memory system from
https://github.com/fuyutosan/ai-context-library

1. Fetch the repository into a temporary folder (git clone, or download the files individually)
2. Copy its library/ folder into the root of my current working folder
   (if a library/ folder already exists, do NOT overwrite it — ask me first)
3. Append the contents of snippets/claude-md-snippet.md to the CLAUDE.md
   in my working folder (create CLAUDE.md if it doesn't exist)
4. Read library/catalog.md and library/how-to-run.md to understand the system
5. Ask me up to 3 questions about what I mainly use AI for
   (work, projects, hobbies), then customize the shelf names and the
   catalog to fit me
6. Finally, report a list of everything you created and where
```

Using Codex or another AI agent instead of Claude Code? Just replace "CLAUDE.md" in the prompt with that tool's always-loaded instructions file (for Codex, that's `AGENTS.md`).

Prefer to set things up by hand, or want to understand the system before installing it? Read on.

## ⏱ 5-minute manual setup

### Step 1: Copy the folder
Copy the `library/` folder from this repository into the root of your working folder.

```
your-working-folder/
├── library/          ← copy it here
│   ├── catalog.md
│   ├── how-to-run.md
│   ├── shelves/
│   └── journal/
└── CLAUDE.md         (if you use Claude Code)
```

If you're using something other than Claude Code (ChatGPT, etc.), just upload this folder as reference files for your project.

### Step 2: Add two lines to CLAUDE.md (Claude Code users)
Copy the contents of `snippets/claude-md-snippet.md` into your project's `CLAUDE.md` (create it if it doesn't exist). This makes "always check the catalog before starting new work" a standing rule the AI follows automatically.

If you use ChatGPT or another tool, paste the same text at the start of your conversations, or put it in your Custom Instructions.

### Step 3: Paste the quick-start prompt
Once `library/` is in place, paste this into your AI chat:

```
I've installed the Daitoshokan memory system in the library/ folder.
Read catalog.md, how-to-run.md, and the files under shelves/ to
understand how it works. Then ask me 3 questions about my situation
(what work, projects, and hobbies I use AI for) and customize the
shelf names to fit me.
```

That's the whole setup. From here, just work as usual — when a task wraps up, say "log this in the journal" and the system starts running itself.

---

## 📋 The operating rules, in three lines

The full version is in `library/how-to-run.md`. The short version:

1. **When a piece of work wraps up, write 5 lines in the journal** (what you did, where the output lives, what you learned, which shelf it belongs on)
2. **Once a week, tell the AI: "file this week's journal entries into the shelves"** (should take ~10 minutes; no need to re-read everything)
3. **When a shelf accumulates stale information, tell the AI: "fix the entries that contradict current facts"** (a library stays alive by being *revised*, not just appended to)

---

## 📖 The story behind this

I'm not an engineer. I started vibe-coding with Claude in May 2026, as a complete beginner.

Within weeks I hit the wall everyone hits: my AI assistant kept forgetting everything. Every session started from zero. Long conversations degraded into confusion. I didn't know the term "context rot" yet — I just knew my AI was getting dumber and I was tired of repeating myself.

So I did what a non-engineer does: instead of building a clever tool, I organized *files*. A catalog that points to shelves. Shelves that hold organized knowledge. A journal for raw daily notes. The AI reads the catalog first, opens only what it needs, and files new entries once a week — like a librarian.

I've been running this exact system every day since. It's not a smart tool; it's a boring routine. But boring routines are what actually survive daily use — and this one has quietly become the backbone of everything I do with AI.

This repository is that system, stripped of my personal data and generalized so you can use it too.

---

## ❓ FAQ

**Q. Do I need programming knowledge?**
A. No. Everything is written in ordinary sentences using Markdown — a plain, lightly-formatted text format.

**Q. Does it work with tools other than Claude Code (ChatGPT, Gemini, etc.)?**
A. Yes. The system is just text files, so you can paste or upload the library folder at the start of a conversation. That said, the real magic — the AI *deciding on its own* to check the catalog and read only the relevant shelves — works best with tools that can read files autonomously (Claude Code, custom GPTs with file attachments, and similar).

**Q. Can I have more than 4 shelves?**
A. Absolutely. Add one row to the table in `library/catalog.md` and create a new file under `library/shelves/`. If the catalog gets too long, group related shelves into subfolders (see `how-to-run.md`).

**Q. What if I forget to write journal entries?**
A. Nothing bad happens. Write when you can — that level of looseness is fine. But if you notice you're asking the AI the same questions repeatedly, that's your signal to log more often.

**Q. Can I share this with family or coworkers?**
A. Yes, but the library tends to accumulate personal and confidential information. Always review the contents before sharing or publishing.

**Q. 日本語版はありますか？ / Is there a Japanese version?**
A. Yes — this project started in Japanese: https://github.com/fuyutosan/daitoshokan-ai-library

---

## 🤝 Work with me

If you'd like help setting this up or adapting it to your workflow, **support is currently free**. Open a GitHub Issue or start a Discussion on this repository — text only.

One honest note: I'm Japanese and my English isn't fluent — replies are drafted with my AI assistant. That's kind of the point of this project.

---

## 🗂 What's in this repository

```
├── README.md                  ← this file
├── library/
│   ├── catalog.md             ← start by copying this
│   ├── how-to-run.md
│   ├── shelves/
│   │   ├── work.md
│   │   ├── hobbies-creative.md
│   │   ├── ai-tips.md
│   │   └── preferences.md
│   └── journal/
│       └── README.md          ← how to write journal entries, with examples
└── snippets/
    └── claude-md-snippet.md   ← the two lines to add to CLAUDE.md
```

---

Daitoshokan is not a clever tool — it's a humble operating routine. Nothing flashy, but it compounds the longer you keep it running. Start with just one shelf and see how it feels.
