---
allowed-tools: Glob, Read, Write, Edit, AskUserQuestion
description: Analyse Remarks subsections across all daily notes, propose category folders, then extract each approved subsection into its own file
model: claude-sonnet-4-6
---

## Step 1 — Scan all daily notes

Use Glob to list all `.md` files in `Daily notes/`. Skip `CLAUDE.md`.

Read each file and extract every `##`-level subsection inside the `# Remarks` section.
For each subsection collect:
- **date** — from the filename (YYYY-MM-DD)
- **title** — the subsection heading (text after `## `)
- **content** — all lines belonging to that subsection (up to the next `##`, `#`, or end of file)

---

## Step 2 — Categorise

Map each subsection to one of the existing category folders found in the project root (use Glob `*/` to list them, exclude `Daily notes`, `KB`, `Work`, `Personal`, `Lithuanian`, `Diary`, `AI`, `Project`, `_templates`).

Assign the best-fit folder. If a subsection clearly fits two categories, pick the primary one.

---

## Step 3 — Present proposal table

Show the user a Markdown table with one row per subsection:

| # | Date | Subsection Title | Proposed Folder |
|---|------|-----------------|-----------------|

Then ask:
> "Approve all, or enter the row numbers to skip (comma-separated), or type 'cancel' to abort."

Use AskUserQuestion to collect the response.

---

## Step 4 — Execute (after approval)

For each approved row, in order:

1. **Build the target filename**
   Format: `YYYY-MM-DD <Meaningful Title>.md`
   - Use the note's date as the ISO prefix.
   - Derive a short, descriptive title from the subsection heading (≤ 6 words, title-case, no special characters).

2. **Write the file** to the proposed folder:
   ```
   <Proposed Folder>/<filename>
   ```
   File content:
   ```markdown
   ---
   date: YYYY-MM-DD
   source: Daily notes/YYYY-MM-DD.md
   tags: [DailyNote, Extracted]
   ---

   ## <Subsection Title>

   <subsection content>
   ```

3. **Remove the subsection** from the source daily note using Edit — delete the `## <Title>` heading line and all its content lines, leaving the rest of the Remarks section intact.

After all rows are processed, print a summary:
> "Extracted N subsections into their category folders."
