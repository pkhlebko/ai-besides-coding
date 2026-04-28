---
allowed-tools: Glob, Read, Write, Edit
description: Condense daily notes — collect unfinished todos and remarks into today's note, mark sources as processed
model: claude-sonnet-4-6
---

Go through all `.md` files in the `Daily notes` folder (skip `CLAUDE.md`).

For each file where `processed: false` (skip today's file):

- Extract all unfinished tasks (`- [ ] ...`) from the ToDo section. Skip lines containing only `ToDo goes here`.
- Extract all content from the Remarks section. Skip lines containing only `Meeting notes etc.`.
- Set `processed: true` in the frontmatter.

In the file with today's date:

- Add all extracted unfinished tasks to the ToDo section (no duplicates).
- Add all extracted remarks to the Remarks section, separating each source file's content with a `---` line (no duplicates).
