---
name: backlog-sync
description: Use to regenerate docs/backlog.md from this repo's Linear project, so agents and readers see the same open work Linear holds. Run after finishing a task, or when asked to "sync the backlog".
---

# Backlog sync

`docs/backlog.md` is a read-only snapshot of the repo's Linear project. Linear is where open work is edited; this file is how an agent (or a person without Linear) reads it from the repo.

## Requires

- Linear MCP tools.
- `AGENTS.md` names the Linear team and project. If it doesn't, ask once.

## Workflow

1. `list_issues` for the project, excluding `Done`, `Canceled` and `Duplicate`. Fields: id, title, status, assignee, labels, priority, url. Fetch relations for anything labelled `blocked`.
2. Group by status, in workflow order: `In Review`, `In Progress`, `Design`, `Spec`, `Todo`, `Backlog`. Within a group, sort by priority (Urgent → Low, then none).
3. Rewrite only section 2 ("Open items") of `docs/backlog.md`, keeping the file's other sections. Each item is one line:

```md
- **[AME-12](url)** Title — owner · labels · blocked by AME-7
```

4. Update the generated-on line at the top of section 2: `Generated from Linear project <name> on <YYYY-MM-DD> by backlog-sync. Edit in Linear, not here.`
5. Show the diff. Commit only if the person agrees: `docs: sync backlog from Linear`.

## Don't

- Don't edit issues from here; this skill only reads Linear.
- Don't add history (closed items) to the file.
- Don't hand-edit items in the file; the next sync overwrites them. Change Linear instead.
