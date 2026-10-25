---
name: start-task
description: Use when starting work on a Linear issue (e.g. "/start-task AME-12"). Creates the issue's own git worktree on Linear's branch name, moves the issue to the right phase, and records who is responsible.
---

# Start a task from Linear

Turn one Linear issue into a ready-to-work branch, with the issue showing who is doing what and why.

## Core principle

```txt
Linear = what's open, who owns it, where it stands
Repo   = what we know (docs, specs, decisions)
Branch = one issue, one worktree, one PR
```

## Requires

- Linear MCP tools (the claude.ai Linear connector, or `claude mcp add --transport http linear https://mcp.linear.app/mcp`). If they aren't available, stop and say so.
- `AGENTS.md` names this repo's Linear team and project (`Linear: team AME, project Ajar`). If it doesn't, ask once and offer to add the line.
- The repo is connected to Linear's GitHub integration (so branches and PRs move the issue).

## Workflow

### 1. Read the issue

`get_issue` with relations. Collect: title, description, status, assignee, labels, project, `gitBranchName`, attachments, blocking relations.

Stop and ask before going further if:
- the issue belongs to a different project than this repo's (wrong repo)
- it's Done or Canceled
- it's blocked (a `blocked by` relation that isn't Done, or the `blocked` label)
- it has `decision-needed` and the decision isn't recorded yet — the first job is the decision, not code

### 2. Read the context

Read `AGENTS.md`, `docs/backlog.md`, and every spec, decision or plan the issue links or names. Don't start from the issue text alone.

### 3. Pick the phase

The status is the phase. Choose where the work starts:

| Status | When |
|---|---|
| `Spec` | No spec covers it yet, or the spec has open questions |
| `Design` | Spec is settled; layout or visual direction isn't |
| `In Progress` | Spec and design are settled; building |

Say which one you picked and why in one line. If the person disagrees, use theirs.

### 4. Create the worktree

Use Linear's branch name exactly (`gitBranchName`). One worktree per issue, beside the repo, so tasks can run in parallel without touching each other:

```sh
git fetch origin
# new branch from the latest main
git worktree add "../<repo>.worktrees/<ISSUE-ID>" -b "<gitBranchName>" origin/main
# or, if the branch already exists on origin
git worktree add "../<repo>.worktrees/<ISSUE-ID>" "<gitBranchName>"
```

Install dependencies inside the worktree if the project needs it. Work only in that folder from here on.

### 5. Update Linear

- `state`: the phase from step 3
- `assignee`: the human who asked (`me`), unless the issue already has a human owner who agreed. The human stays responsible; Claude is the tool.
- `addLabels`: `agent:claude`
- Comment, in plain language a non-coder can read:

```md
**Started** — [phase] · owner: @[person] · built with Claude Code
**Branch:** `[gitBranchName]`
**Plan:** [2–4 short lines: what will change, in user terms, and how it will be checked]
**Reads:** [specs/decisions this follows]
```

### 6. Open a draft PR early (when building)

Once there's a first commit in the `In Progress` phase, push and open a draft PR so the issue and the code are linked from the start:

```sh
git push -u origin HEAD
gh pr create --draft --title "<ISSUE-ID>: <title>" --body "Part of <ISSUE-ID>"
```

Linear's automation keeps the issue in `In Progress`. If `gh` isn't installed, say so and give the person the compare URL instead.

### 7. Hand-offs between phases

When a phase ends (spec written, design chosen) and someone else owns the next one, change `state` and `assignee` together and comment one line: what was done, what the next owner needs. Linear's history then shows each hand-off.

## Don't

- Don't invent a branch name or reuse another issue's worktree.
- Don't move the issue to `In Review` or `Done` by hand; the PR does that.
- Don't change scope silently. If the work grows, comment and create a follow-up issue.
