# INSTALL — setup instructions for AI agents

> This file is written **for an AI agent to read and execute**.
> Human-facing docs live in [README.md](README.md).
> When the user says "install this repo", follow the steps below in order.

Setup takes about five minutes and is nothing but copying files and appending text. No build, no install.

---

## Step 0 — Confirm the working folder and the always-loaded file

1. Install into **the folder the user is currently in** (the working directory). Do not create it elsewhere
2. Pick the always-loaded instruction file for whichever tool you are running as

| Tool | File |
|---|---|
| Claude Code / Cowork | `CLAUDE.md` |
| Codex / GitHub Copilot CLI | `AGENTS.md` |
| Cursor | `.cursor/rules/library.mdc` |
| Anything else | Whatever that tool loads automatically. If there is none, use `AGENTS.md` |

This file is referred to below as **`<always-file>`**.

3. Check whether `library/` already exists. **If it does, do not overwrite it — ask the user whether to merge into it or use a different name, and stop.**

## Step 1 — Fetch the files

Either clone the repo into a temporary folder:

```
git clone https://github.com/fuyutosan/ai-context-library.git
```

or, if `git` is unavailable, fetch these files individually from raw (`main` branch):

```
library/catalog.md
library/how-to-run.md
library/journal/README.md
library/shelves/work.md
library/shelves/hobbies-creative.md
library/shelves/ai-tips.md
library/shelves/preferences.md
snippets/claude-md-snippet.md
commands/log.md
commands/tidy.md
```

Raw URLs follow the pattern `https://raw.githubusercontent.com/fuyutosan/ai-context-library/main/<path>`.

## Step 2 — Put `library/` in the working folder

Copy the `library/` folder as-is into the root of the working folder.

```
working-folder/
├── library/
│   ├── catalog.md
│   ├── how-to-run.md
│   ├── shelves/ (4 files)
│   └── journal/README.md
└── <always-file>
```

## Step 3 — Append the snippet to `<always-file>`

Append **only the contents of the ```markdown block** from `snippets/claude-md-snippet.md` to the end of `<always-file>`.
Create `<always-file>` if it does not exist. **Never delete existing content.**

The text to append (safe to paste verbatim):

```markdown
## 📚 Daitoshokan (working-context library)

**Read** — Only open `library/catalog.md` when the task needs past history or the reasoning behind a decision, continues an existing project, or involves a proposal or plan. Then open just 1–2 relevant shelves. Never read a shelf end to end: grep for headings or keywords and read only the matching section. Skip the library entirely for one-off questions and self-contained tasks.

**Write** — When a piece of work that created or changed files wraps up, append an entry of 5 lines or fewer to `library/journal/YYYY-MM.md`. The heading MUST be in this form:
`## 2026-08-05 What you did | shelf:work`
(without `| shelf:` the entry is never filed and will sit in the journal forever). Use a shelf name listed in `library/catalog.md`.

**File** — Before appending to the journal, grep this month's journal for heading lines only (`^## `; do not read the bodies). If **5 or more** headings lack a `✅`, follow "4. Filing procedure" in `library/how-to-run.md` to move them into shelves and mark each done heading with `✅`. **Do this on your own — the user should not have to ask.**
```

## Step 4 — Install the slash commands (Claude Code only, optional)

On Claude Code, copy `commands/log.md` and `commands/tidy.md` into `.claude/commands/`.
That gives the user `/log` (record the current work) and `/tidy` (file entries right now) as manual triggers.
The automation works without them, so skip this step on other tools.

## Step 5 — Rebuild the shelves around the user

**This is the most important step.** The four shipped shelves (work / hobbies-creative / ai-tips / preferences) are examples.

1. Ask the user **exactly three questions**
   - What kinds of work or projects do you mainly use AI for? (2–3 of them)
   - Do you also use AI for hobbies or personal creative work?
   - When would you want the AI to recall past history?
2. Rename, add, or remove files under `library/shelves/` to match (3–5 shelves is the sweet spot — too many and nobody can choose)
3. Make the shelf table in `library/catalog.md` **match the actual files exactly**
   (a mismatch means filing cannot pick a destination, and the automation stops)
4. Delete the sample block (everything below `⚠️ Everything below is SAMPLE text`) from shelves the user is keeping

## Step 6 — Verify, then report

Check all of the following before reporting.

- [ ] The shelf list in `library/catalog.md` matches the real files in `library/shelves/`
- [ ] `<always-file>` contains the snippet
- [ ] You created this month's journal file (`library/journal/YYYY-MM.md`) and wrote the install itself as the first entry
      (heading format `## 2026-08-05 Installed Daitoshokan | shelf:xxx` — it doubles as the worked example)

Then tell the user:

- What you created and where (a file list)
- How many shelves there are and what they are called
- **"From here on, just work normally. I'll write the journal when things wrap up, and file them into shelves once five entries pile up."**

---

## Notes for the agent, post-install

- Write a journal entry when work that created or changed files wraps up. Not for chit-chat or one-off questions
- Evaluate the filing trigger **right before** appending. It is just a grep over heading lines, so it is cheap
- If the user says "log this" or "record that", write the entry immediately without waiting for the trigger
- As shelves grow, keep the one-line descriptions in the catalog honest
