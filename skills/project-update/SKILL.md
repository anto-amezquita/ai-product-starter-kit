---
name: project-update
description: Use to draft a Linear project update (health + what changed) for this repo's project, written for non-coders such as project managers. Run weekly during active work or when scope, risk or direction changes.
---

# Project update

Write the project's current story from what actually moved in Linear, in words a project manager can read.

## Requires

- Linear MCP tools.
- `AGENTS.md` names the Linear team and project.

## Workflow

1. Find the last update date (`get_status_updates` for the project). If none, use the project's start date.
2. `list_issues` for the project updated since then. Sort them into: completed, started or moved phase, newly blocked, new `decision-needed`, created.
3. Read the plain-language comments `start-task` and `finish-task` left; they're the source for "what changed for the user". Don't paraphrase commit messages.
4. Pick a health and say why in one line:
   - **On track** — moving as planned
   - **At risk** — a blocker or open decision threatens the next step
   - **Off track** — the next step can't happen without a change of plan
5. Draft with the template in `docs/linear-workflow.md` ("Update template"). Link issue IDs instead of retelling them. No jargon; if a technical term is unavoidable, explain it in five words.
6. Show the draft. Post it with `save_status_update` only after the person approves or edits it.

## Don't

- Don't claim progress no issue shows.
- Don't post without approval; the update speaks for the person.
