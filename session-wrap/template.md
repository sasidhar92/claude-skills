# {{COMMAND_NAME}} — Save Session Summary

**Usage:** `{{COMMAND_NAME}}` at the end of a session to save a structured summary.

---

## Customization Guide

Before using this template, replace every `{{PLACEHOLDER}}` below.
Each option is explained in the README.

| Placeholder | Your value |
|-------------|------------|
| `{{COMMAND_NAME}}` | e.g. `/wrap`, `/save-session`, `/log-session` |
| `{{SAVE_LOCATION}}` | e.g. `research/sessions/`, `memory/sessions/` |
| `{{FILENAME_PATTERN}}` | See naming options below |
| `{{TOPIC_INFERENCE}}` | See inference options below |
| `{{SUMMARY_FORMAT}}` | See format options below |
| `{{POST_SAVE_ACTION}}` | See action options below |

---

## Instructions

When this skill is invoked, follow these steps exactly:

### Step 1: Determine the Topic

<!-- PICK ONE and delete the others -->

<!-- OPTION A: Auto from conversation (recommended) -->
{{TOPIC_INFERENCE}}
Read the full conversation and derive a concise 3-5 word topic slug that captures what this session was about.
- Use lowercase, hyphen-separated words (e.g. `mac-app-launch-prep`, `auth-refactor`, `sqlite-migration`)
- Be specific — avoid generic slugs like `coding-session` or `bug-fixes`
- Pick the dominant theme if multiple topics were covered

<!-- OPTION B: Propose + confirm -->
<!-- Read the conversation, propose a topic slug to the user, and wait for confirmation or override before continuing. -->

<!-- OPTION C: From git diff -->
<!-- Run `git diff --name-only HEAD` and derive the topic from the files that were changed this session. -->

<!-- OPTION D: Hybrid (git diff + conversation) -->
<!-- Run `git diff --name-only HEAD`, combine with conversation context, and pick the most accurate slug. -->

### Step 2: Build the Filename

<!-- PICK ONE and delete the others -->

<!-- OPTION A: Date + auto topic -->
Run: `date +%Y-%m-%d`
Filename: `YYYY-MM-DD-{topic-slug}.md`
Example: `2026-02-22-mac-app-launch-prep.md`

<!-- OPTION B: Date + user-provided title -->
<!-- Ask the user for a short title. Slugify it (lowercase, hyphens). -->
<!-- Filename: `YYYY-MM-DD-{user-title}.md` -->

<!-- OPTION C: Auto topic only (no date) -->
<!-- Filename: `{topic-slug}.md` -->

<!-- OPTION D: Full timestamp + auto topic -->
<!-- Run: `date +%Y%m%d-%H%M%S` -->
<!-- Filename: `YYYYMMDD-HHMMSS-{topic-slug}.md` -->

### Step 3: Write the Summary

Save to: `{{SAVE_LOCATION}}{filename}`

<!-- PICK ONE FORMAT and delete the others -->

<!-- FORMAT A: Concise bullets (recommended) -->
Use this exact structure with concise bullet points (no prose):

```markdown
# Session: {topic-slug}
**Date:** YYYY-MM-DD

## What Was Worked On
- bullet
- bullet

## Key Decisions
- bullet
- bullet

## Files Changed
- `path/to/file.ext` — one-line description
- `path/to/file.ext` — one-line description

## Next Steps / Open Items
- bullet
- bullet
```

Rules:
- Bullets only — no prose paragraphs
- List actual file paths that were read/edited/created
- If a section has nothing to report, write `- None`
- One line per bullet, no sub-bullets

<!-- FORMAT B: Prose paragraphs -->
<!-- Write narrative paragraphs under H2 headings for each section. -->

<!-- FORMAT C: Structured markdown (headers + mixed bullets/prose) -->
<!-- Use H2 headers per section with a mix of bullet lists and 1-2 sentence prose where useful. -->

<!-- FORMAT D: Ultra-minimal (one-liner per item) -->
<!-- No headers. Just a flat list of one-liners: "Built X", "Decided Y", "Changed Z", "TODO: W" -->

**Include only the sections relevant to you:**
- What Was Worked On
- Key Decisions
- Files Changed
- Next Steps / Open Items

<!-- Remove any sections you don't want -->

### Step 4: Post-Save Action

<!-- PICK ONE and delete the others -->

<!-- ACTION A: Git commit -->
```bash
git add {{SAVE_LOCATION}}{filename}
git commit -m "session: YYYY-MM-DD {topic-slug}"
```

<!-- ACTION B: Update WORKING.md -->
<!-- Append the "Next Steps / Open Items" bullets to `memory/WORKING.md` under a dated heading. -->

<!-- ACTION C: Send iMessage -->
<!-- Send a brief 2-3 line recap via iMessage. -->

<!-- ACTION D: Nothing — just save the file -->
<!-- Skip this step entirely. -->

### Step 5: Confirm

Print a single line:
`Saved → {{SAVE_LOCATION}}{filename}`
