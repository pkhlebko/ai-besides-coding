# Daily Notes Folder - Guidelines for Claude Code

## Overview

This folder contains daily notes organized chronologically with YYYY-MM-DD naming format. It serves as a catch-all journal for work updates, personal tasks, meeting notes, and project-specific discussions.

## File Structure

**Format**: Each daily note file follows this standard structure:

```yaml
---
processed: false
tags: [DailyNote]
---

## ToDo

- [ ] Task item
- [x] Completed task

## Remarks

Meeting notes, technical discussions, and reference materials here.
```

## Content Types

### 1. Work & Project Management

* **Azure DevOps Work Items**: Task IDs and references (e.g., 438963, 452176)
* **Team Assignments**: Task assignments to specific team members
* **Technical Discussions**: Database schema questions, API design decisions
* **Sprint Planning**: Dictionary requirements, telemetry setup, master data updates
* **Configuration Notes**: Azure variables, JWT modules, OpenTelemetry settings

### 2. Technical Notes

* Database schema discussions (Contacts, Products tables)
* Backend/Frontend/BFF implementation details
* Service integrations (MS Graph, Search, Kafka, Redis)
* Unit testing rules and code coverage targets (99%)
* Monitoring and logging setup

### 3. Personal Content

* Real estate negotiation drafts
* Items for sale list
* Personal project ideas (Home Assistant, electrical projects)
* Language learning notes (mixed Russian/Lithuanian/English)

### 4. Reference Materials

* VPS provider links
* Azure configuration guidelines
* Contact role and product details architecture discussions
* Links configuration patterns

## Working with Daily Notes

### Adding New Entries

1. Create file with YYYY-MM-DD format
2. Include YAML frontmatter with `processed: false` and tags
3. Use consistent section headings (##)
4. Keep checklist items concise

### Important Flags

* **`processed: false`**: Indicates the note has not been archived or processed yet
  * Consider setting to `true` when archiving to Daily notes summary
* **`tags: [DailyNote]`**: Standard tag for all daily notes

### Multi-Language Support

Notes contain content in:

* English (primary)
* Russian (Cyrillic)
* Lithuanian (ongoing language learning)

Preserve all languages as-is; do not translate.

## Security Considerations

⚠️ **Sensitive Information Present**:

* API keys and tokens (avoid committing)
* Real estate pricing and negotiation details
* Work-related task IDs and internal discussions
* Contact information and email addresses

Review notes before pushing to shared repositories.

## Content Organization Patterns

### Work Section Examples

* Task decomposition and subtasks
* Decision points and open questions
* Implementation approaches and concerns
* Team coordination details

### Remarks Section Patterns

* Meeting notes with attendees
* Technical Q&A discussions
* Draft communications (emails, negotiations)
* Configuration checklists
* External links and references

## Maintenance

* **Archiving**: Old notes can be archived when fully processed
* **Consolidation**: Use the `notes-condense` skill to summarize and condense notes
* **Cross-referencing**: Link to other Obsidian notes using `[[Note Name]]` format when relevant

## Tools & Commands

When working with daily notes:

```bash
# View all daily notes
ls -la Daily\ notes/*.md

# Search for specific tasks or topics
grep -r "task-id\|keyword" Daily\ notes/

# Condense and summarize (using Claude Code skill)
/notes-condense
```

## Best Practices

1. **Keep entries detailed but scannable** - Use bullet points and clear hierarchies
2. **Close completed items** - Mark checkboxes as `[x]` when done
3. **Timestamp important discussions** - Include dates for time-sensitive decisions
4. **Cross-reference external systems** - Include Azure DevOps links, GitHub repos, etc.
5. **Separate concerns** - Keep work tasks and personal notes in their sections
6. **Review for sensitive data** - Before committing, ensure no secrets are exposed

## Note Properties

| Property | Value | Notes |
|----------|-------|-------|
| Date Format | YYYY-MM-DD | ISO 8601 standard |
| Frontmatter | `processed: false` | Toggle when archived |
| Tags | `[DailyNote]` | Standard categorization |
| Sections | ToDo, Remarks | Flexible within, keep headers consistent |
| Languages | EN, RU, LT | Mixed language support |
