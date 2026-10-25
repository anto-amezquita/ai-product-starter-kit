---
name: finish-task
description: Use when the work on a Linear issue is ready for review (e.g. "/finish-task AME-12"). Runs the quality gate, opens or readies the PR, and leaves a plain-language record on the issue for non-coders.
---

# Finish a task

Close the loop on one issue: checked work, a PR that moves the issue, and a record a project manager can read without opening the code.

## Requires

The same as `start-task`. Run it from the issue's worktree.

## Workflow

### 1. Check the work

Run `skills/quality-gate/SKILL.md` against the issue and its spec, plus the repo's own commands (`package.json` scripts or `AGENTS.md`). Don't continue on a red check. If something can't be fixed now, say so and either fix it or record it (step 4).

### 2. Update the repo's knowledge

- A real decision was made → write it in `/decisions` (and remove `adr-needed` from the issue).
- The spec turned out wrong or incomplete → update it.
- A doc no longer matches reality → update it, or create a `docs-update` issue.

### 3. Push and open the PR

```sh
git push
gh pr create --title "<ISSUE-ID>: <title>" --body-file <body>   # or `gh pr ready` for an existing draft
```

PR body:

```md
Fixes <ISSUE-ID>

## What changed
[User-facing summary, then the technical one]

## How it was checked
[Commands run, results, manual checks]

## Decisions and docs
[Links to new or updated decisions/specs, or "none"]
```

`Fixes <ISSUE-ID>` makes the merge close the issue. Linear's automation moves it to `In Review` when the PR is ready and to `Done` on merge — don't set those by hand.

### 4. Record follow-ups

Anything punted, discovered or left rough becomes its own Linear issue in the same project, with a label (`revisit`, `docs-update`, `decision-needed`, `blocked`) and a `related to` link. Nothing stays only in the chat.

### 5. Leave the record

Comment on the issue in plain language. This is the history a non-coder reads:

```md
**Ready for review** · owner: @[person] · built with Claude Code
**What changed for the user:** [1–3 lines, no jargon]
**How we know it works:** [checks in plain words]
**Decisions:** [links, or "none"]
**Follow-ups:** [issue IDs, or "none"]
**PR:** [link]
```

### 6. After merge

When the person confirms the PR is merged:

```sh
git worktree remove "../<repo>.worktrees/<ISSUE-ID>"
git branch -d "<gitBranchName>"
```

Then run `backlog-sync` so `docs/backlog.md` matches Linear again.
