# claude-skills

A collection of slash commands for [Claude Code](https://claude.ai/claude-code).

Each command is a markdown file that lives in `~/.claude/commands/` and teaches Claude a reusable workflow you can trigger with a short slash command.

---

## Commands

| Command | What it does |
|---------|--------------|
| [session-wrap](./session-wrap/) `/wrap` | Saves a structured session summary and optionally commits it |

---

## session-wrap

Save a structured markdown summary of your Claude Code session — what was built, decisions made, files changed, and what's next.

### Quickstart (automated)

Paste the contents of [`session-wrap/bootstrap-prompt.md`](./session-wrap/bootstrap-prompt.md) into any Claude Code session.

Claude will ask you a series of multiple-choice questions and write the command file for you automatically. No manual editing required.

### Manual setup

1. Copy [`session-wrap/template.md`](./session-wrap/template.md) to `~/.claude/commands/wrap.md` (or your preferred name)
2. Open it and replace each `{{PLACEHOLDER}}` with your choice
3. Delete the comment blocks for options you didn't choose
4. Done — use your command at the end of any session

### What you can customize

**Command name**
How you invoke it. Popular choices:

| Option | Best for |
|--------|----------|
| `/wrap` | Fast typists, end-of-session habit |
| `/save-session` | Explicitness over brevity |
| `/log-session` | Archival mindset |
| `/session-summary` | Maximum clarity |

**Save location**
Where the `.md` files land in your repo:

| Option | Notes |
|--------|-------|
| `research/sessions/` | Good if you have a research/ folder already |
| `memory/sessions/` | Near daily logs and decisions |
| `notes/sessions/` | Lightweight, low-ceremony |
| Custom path | Anything you like |

**File naming**
How the filename is constructed:

| Option | Example |
|--------|---------|
| Date + auto topic | `2026-02-22-mac-app-launch-prep.md` |
| Date + you provide title | `2026-02-22-my-custom-title.md` |
| Auto topic only | `mac-app-launch-prep.md` |
| Full timestamp + auto topic | `20260222-143022-mac-app-launch.md` |

**Topic inference**
How Claude picks the session name:

| Option | Notes |
|--------|-------|
| Auto from conversation | Fully hands-off, reads the full chat |
| Propose + confirm | Claude suggests, you approve or override |
| From git diff | Derives topic from changed files |
| Hybrid | Git diff + conversation — most accurate |

**Summary sections** (pick any combination)
- What was worked on
- Key decisions made
- Files changed
- Next steps / open items

**Format**

| Option | Example |
|--------|---------|
| Concise bullets | `- Added OAuth flow to login screen` |
| Prose paragraphs | Full sentences under each heading |
| Structured markdown | H2 headers + mixed bullets and prose |
| Ultra-minimal | Flat one-liners, no headers |

**Post-save action** (pick any combination)
- Git commit the summary file
- Append next steps to `WORKING.md`
- Send an iMessage recap
- Nothing — just save the file

---

## How slash commands work

A slash command is a markdown file in `~/.claude/commands/`. When you run `/command-name` in Claude Code, Claude reads the file and follows the instructions inside it.

Claude Code auto-discovers all `.md` files in `~/.claude/commands/` — no registration step required. Drop a file there and the command is immediately available.

---

## Contributing

Got a command you use regularly? PRs welcome. Keep each command in its own folder with:
- `template.md` — the parameterized command file
- `bootstrap-prompt.md` — a paste-into-Claude setup prompt
- An entry in this README
