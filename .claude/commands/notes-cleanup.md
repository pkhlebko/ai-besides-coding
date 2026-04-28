---
allowed-tools: Bash, Glob
description: Delete all processed daily notes (processed: true), keeping today's note
model: claude-haiku-4-5-20251001
---

Delete all files in the `Daily notes` folder where the frontmatter contains `processed: true`, except for the file with today's date.

Use Glob to list all `.md` files in `Daily notes` (skip `CLAUDE.md`).
Then use a single Bash command to find and delete matching files:

```bash
grep -rl "^processed: true" "Daily notes/" --include="*.md" | grep -v "CLAUDE.md" | grep -v "$(date +%Y-%m-%d)"
```

Show the list of files that will be deleted, then delete them with `rm`.
Print a summary of how many files were deleted.
