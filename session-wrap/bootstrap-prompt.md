# Bootstrap Prompt — Session Wrap Skill

Copy the text below and paste it into any Claude Code session.
Claude will ask you the setup questions and write the skill file automatically.

---

```
I want to create a slash command that saves a session summary at the end of conversations. Please help me set it up by asking me the following questions one group at a time, then generate and save the skill file.

---

QUESTION GROUP 1 — Ask these 2 questions together using AskUserQuestion with multiple choice options:

Q1: "What should the command be called?"
Options:
- /wrap — short, implies wrapping up
- /save-session — explicit and clear
- /log-session — emphasizes archiving
- /session-summary — most descriptive

Q2: "Where should session summaries be saved?"
Options:
- research/sessions/ — grouped with research artifacts
- memory/sessions/ — alongside daily logs and decisions
- notes/sessions/ — lightweight notes folder
- Custom path — I'll type it in

---

QUESTION GROUP 2 — Ask these 2 questions together:

Q3: "How should the session file be named?"
Options:
- Date + auto topic (e.g. 2026-02-22-mac-app-launch-prep.md) — fully hands-off
- Date + I provide the title — Claude suggests, I confirm or override
- Auto topic only, no date (e.g. mac-app-launch-prep.md)
- Full timestamp + auto topic (e.g. 20260222-143022-mac-app-launch.md)

Q4: "How should Claude infer the session topic?"
Options:
- From the conversation automatically — fully hands-off
- Propose + confirm — Claude suggests a name, I approve or override
- From git diff — derive topic from files changed
- Hybrid: git diff + conversation — most accurate

---

QUESTION GROUP 3 — Ask these 2 questions together:

Q5: "What should the summary include?" (multi-select)
Options:
- What was worked on
- Key decisions made
- Files changed
- Next steps / open items

Q6: "What format should the summary use?"
Options:
- Concise bullets — short bullet lists under each section
- Prose paragraphs — narrative style, more readable
- Structured markdown — H2 sections, mix of bullets and prose
- Ultra-minimal — one-liner per item, no headers

---

QUESTION GROUP 4 — Ask this question:

Q7: "Should the command do anything beyond saving the file?" (multi-select)
Options:
- Git commit the summary file
- Update WORKING.md with next steps
- Send an iMessage summary
- Nothing else — just save the file

---

After collecting all answers:

1. Generate a customized skill file based on my choices
2. Save it to ~/.claude/skills/{command-name-without-slash}.md
3. Add an entry for it in ~/.claude/CLAUDE.md under "Custom Skills → Available Skills" if that section exists
4. Confirm with: "Skill saved → ~/.claude/skills/{command-name}.md — use it with {command-name}"

Do not show me the file contents unless I ask. Just run the questions, generate, save, and confirm.
```
