# linear-workflow.md

## Purpose

This document defines how Linear should be used as the team-visible layer of this product operating system.

The repository remains the **source of truth** for product intent, specifications, design rules, architecture, quality standards, and decision history.

Linear becomes the **shared map of the work**:

- where we are
- what is happening now
- what is blocked
- what still needs a decision
- what should be revisited
- how the project is moving from idea to release

---

# Core model

```txt
Repository = what we know
Linear = where that knowledge is in motion
```

Use the repository for durable knowledge:

- `/docs` = stable project rules and intent
- `/specs` = current product and feature decisions
- `/decisions` = remembered reasons
- `/skills` = repeatable methods

Use Linear for shared visibility:

- Initiatives = larger product or business goals
- Projects = coherent bodies of work with clear outcomes
- Milestones = lifecycle stages
- Issues = work someone must do next
- Updates = the current story of the project
- Labels and views = uncertainty, blockers, and attention

---

# Linear hierarchy

## 1. Initiative

Use an **Initiative** for the larger product effort or business objective.

Examples:

```txt
Launch first release of [Product Name]
Create AI-assisted product building system
```

Use the Initiative to answer:

- Why are we doing this?
- What larger goal does it serve?
- Which projects together move that goal forward?

## 2. Project

Use a **Project** for one coherent body of work with a clear outcome.

For a new product, the first useful project is usually:

```txt
[Product Name] — Foundation and MVP
```

Do not make one Linear project represent the whole product forever. Create a new project when the work becomes a new meaningful phase, such as:

- Foundation and MVP
- Public beta
- Collaboration
- Mobile launch
- Design system expansion

## 3. Milestones

Use **Milestones** to show where the product is in its lifecycle.

Default milestone set for a new product:

```txt
1. Product direction
2. Brand and experience
3. Technical foundation
4. First spec ready
5. MVP implementation
6. Review and release readiness
```

Milestones should answer:

- What stage are we in?
- What must be true before we move forward?
- Which part of product formation is currently active?

## 4. Issues

Use **Issues** for concrete work that can be owned, discussed, and completed.

Issues should generally describe:

- a meaningful unit of work
- an expected outcome
- the relevant file, spec, or decision
- any open questions or acceptance criteria

Avoid using issues as vague containers for “thinking about” work without a clear next result.

---

# Project setup template

Create a reusable Linear Project Template called:

```txt
AI Product Project
```

## Suggested default project name

```txt
[Product Name] — Foundation and MVP
```

## Suggested default milestones

```txt
1. Product direction
2. Brand and experience
3. Technical foundation
4. First spec ready
5. MVP implementation
6. Review and release readiness
```

## Suggested default project status

```txt
Idea shaping
```

## Suggested default project labels

Project labels are optional, but useful when several projects exist.

Examples:

```txt
new-product
mvp
internal-tool
client-work
design-system
```

---

# Default issues by milestone

## 1. Product direction

- Run project kickoff guide
- Draft `docs/product-north-star.md`
- Confirm primary user, problem, and value proposition
- Confirm first-version scope and non-goals
- Record open product questions

## 2. Brand and experience

- Draft `docs/brand.md`
- Adapt `docs/design.md` to the project
- Complete `docs/content.md`
- Identify initial screens and key user flow
- Review product character and anti-patterns

## 3. Technical foundation

- Choose stack and hosting approach
- Complete `docs/architecture.md`
- Set up repository and base folder structure
- Establish tokens and component foundation
- Review `docs/quality.md`
- Create first ADRs where needed

## 4. First spec ready

- Draft MVP or first-build spec in `/specs`
- Review user stories and main flow
- Review states, edge cases, and permissions
- Confirm acceptance criteria
- Break the first build into implementation phases

## 5. MVP implementation

- Build foundation work
- Build primary user flow
- Build relevant states and errors
- Add analytics or observability where needed
- Update docs when implementation changes decisions

## 6. Review and release readiness

- Run accessibility review
- Run design-system review where reusable patterns emerged
- Run quality gate
- Resolve blockers
- Prepare release notes, handoff, or launch checklist

---

# Status model

Use project status as a deliberate team signal, not an automatic calculation.

Suggested statuses:

```txt
Idea shaping
Foundation
Spec ready
Building
Reviewing
Ready to ship
Shipped
Paused
```

## Suggested meanings

### Idea shaping
The product is being clarified. The team is still deciding what should exist.

### Foundation
The product direction is clear enough to establish brand, design, architecture, and quality rules.

### Spec ready
The first meaningful build is specified well enough to begin implementation.

### Building
Implementation is actively underway.

### Reviewing
The product exists in working form and is being tightened through review, testing, and revision.

### Ready to ship
Known blockers are resolved. Release preparation remains.

### Shipped
The project outcome has been delivered.

### Paused
Work is intentionally stopped or waiting on an external dependency.

---

# Labels

Use issue labels to make uncertainty and maintenance visible.

## Recommended labels

```txt
decision-needed
assumption
revisit
blocked
docs-update
adr-needed
```

## Definitions

### `decision-needed`
A meaningful product, design, or technical choice is required before work can proceed confidently.

### `assumption`
Work is proceeding on something treated as true for now but not yet fully verified.

### `revisit`
A decision or design should be checked again after new information, feedback, or implementation learning.

### `blocked`
Progress cannot continue until a dependency or decision is resolved.

### `docs-update`
The repository docs need to be updated because implementation, product direction, or process has changed.

### `adr-needed`
A meaningful technical or system decision should be recorded in `/decisions`.

---

# Saved views

Create views that answer the most useful team questions.

## Recommended saved views

### Open assumptions

Filter:

```txt
label = assumption
status != done
```

### Needs decision

Filter:

```txt
label = decision-needed
status != done
```

### Needs revisit

Filter:

```txt
label = revisit
status != done
```

### Docs out of date

Filter:

```txt
label = docs-update
status != done
```

### Blocked work

Filter:

```txt
label = blocked
status != done
```

### ADRs needed

Filter:

```txt
label = adr-needed
status != done
```

These views should make the project easier to understand, not merely more measurable.

---

# Issue workflow: phases, owners and branches

Projects carry a lifecycle status (above). Issues carry the work, and their status is the phase the work is in.

## Issue statuses

```txt
Backlog → Todo → Spec → Design → In Progress → In Review → Done
                                                          (Canceled)
```

| Status | Meaning | Moves by |
|---|---|---|
| Backlog | Known, not ready or not sequenced | hand |
| Todo | Ready to start | hand |
| Spec | Writing or fixing the spec in `/specs` | `start-task`, hand |
| Design | Layout or visual direction being decided | `start-task`, hand |
| In Progress | Building, on the issue's own branch | `start-task`, draft PR |
| In Review | PR ready, waiting for review | PR opened or review requested |
| Done | Merged into `main` | PR merge |

Spec and Design are custom "Started" statuses; add them in Linear under the team's workflow settings, before In Progress. Not every issue passes through every phase: a small fix can go Todo → In Progress.

## Who is responsible

- **The assignee owns the issue in its current phase.** When a phase ends and someone else owns the next one, change status and assignee together and leave a one-line hand-off comment. Linear's activity log then shows every hand-off with a date.
- **A person always owns the issue.** When Claude Code builds it, the person who started it stays the assignee and the issue gets the `agent:claude` label.
- Blockers are `blocked by` relations, not just labels, so the chain is visible.

## One issue, one branch

- Each issue has a branch name in Linear (copy with ⌘⇧. or read `gitBranchName`). Use it as-is; the issue ID in it links the branch, PRs and commits to the issue.
- `start-task` creates a separate git worktree per issue, so several issues can be in progress without touching each other.
- Pull request automations (team settings → Workflows & automations), with the GitHub integration connected:
  - draft PR opened → In Progress
  - PR opened, or review requested → In Review
  - PR merged → Done
- Put `Fixes <ISSUE-ID>` in the PR description so the merge closes the issue. Use `Part of <ISSUE-ID>` when a PR is only a slice.
- Leave "Auto-close stale issues" off. It moves untouched issues to Canceled on its own, which reads in the history as a decision nobody made.

## The record non-coders read

The history of an issue is its status changes, its hand-offs and the plain-language comments `start-task` and `finish-task` leave ("what changed for the user", "how we know it works"). The history of a project is its updates (`project-update`). Neither needs anyone to read code.

## The backlog file

When a project uses Linear, `docs/backlog.md` in the repo is a read-only snapshot of the Linear project, regenerated by `backlog-sync`. Agents read it first, as before; people edit Linear.

---

# Project documents and links

Use the Linear project overview to gather the most important project materials in one visible place.

## Add links to canonical repo files

Suggested resources:

```txt
Product North Star
Brand
Design
Content
Architecture
Quality
Current spec
Decision log
```

Prefer linking to the canonical repository files rather than copying them into multiple places.

## Use Linear documents for

- short project summaries
- meeting notes
- weekly updates
- temporary working notes
- optional human-friendly summaries of longer repo docs

Do not allow Linear documents to become a second hidden source of truth that contradicts the repo.

---

# Project updates

Use project updates to tell the current story of the work.

## Recommended cadence

- weekly during active work
- at milestone transitions
- whenever a material change affects scope, risk, or direction

## Update template

```md
# Current state

[One short paragraph on where the project stands.]

## Completed since last update

- [Completed item]
- [Completed item]

## In progress

- [Current work]
- [Current work]

## Open questions

- [Question]
- [Question]

## Risks or changes

- [Risk, change, or none]

## Next

- [Next step]
- [Next step]
```

## Update quality bar

A good update should make it easy to answer:

- What changed?
- What is happening now?
- What is uncertain?
- What should happen next?

---

# Relationship between Linear and the repo

## Keep in the repo

- product intent
- brand direction
- design rules
- content rules
- architecture
- quality standards
- specs
- ADRs
- skills

## Keep in Linear

- lifecycle status
- visible work queue (open issues; `docs/backlog.md` is a snapshot of it)
- owners, per phase
- branch and PR links
- blockers
- questions needing attention
- milestone progress
- weekly narrative updates

## Rule of thumb

If the question is:

> “What do we know or believe?”

look in the repo.

If the question is:

> “Where are we and what needs attention now?”

look in Linear.

---

# Recommended workflow for a new project

```txt
1. Run `project-kickoff`
2. Create the core docs in the repo
3. Create a Linear project from the `AI Product Project` template
4. Add links to the repo docs in the project overview
5. Create or attach the first spec
6. Start work inside the milestone structure
7. Use labels and saved views to keep uncertainty visible
8. Start each issue with `start-task`, finish it with `finish-task`
9. Send project updates throughout active work (`project-update`)
```

---

# Example project

## Initiative

```txt
AI-assisted product building system
```

## Project

```txt
AI Product Starter Kit v1
```

## Milestones

```txt
1. Product operating system defined
2. Kickoff guide created
3. Core skills created
4. Documentation article written
5. Linear workflow added
6. First real-world trial
```

## Example revisit issues

```txt
- Should specs live only in the repo, or sometimes in Linear documents?
- Do we need a content-review skill?
- Should user research become its own milestone in some projects?
```

---

# Final review checklist

Before considering the Linear setup complete, check:

- Is the repo still the single source of truth?
- Does the Initiative explain the larger goal?
- Does the Project have a clear outcome?
- Do the Milestones show the lifecycle clearly?
- Are Issues actionable?
- Are important docs linked from the project overview?
- Are uncertainty labels in use?
- Do saved views make blockers and revisits visible?
- Are project updates telling the story of the work?
- Could someone joining the project understand where we are within a few minutes?
