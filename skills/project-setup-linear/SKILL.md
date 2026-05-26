---
name: project-setup-linear
description: Use when a new digital product project should be represented in Linear so the team can see lifecycle stage, current work, blockers, assumptions, revisit items, and links to the project's source-of-truth documents.
---

# Project setup in Linear

Create or define the Linear structure for a new product project so the team can understand where the project is, what is happening now, and what needs attention.

## Read first

Before proposing or creating the Linear setup, read:

1. `docs/product-north-star.md`
2. `docs/brand.md`
3. `docs/design.md`
4. `docs/content.md`
5. `docs/architecture.md`
6. `docs/quality.md`
7. `docs/linear-workflow.md`
8. the relevant first spec in `/specs`, if one exists
9. relevant ADRs in `/decisions`

## Core principle

```txt
Repository = source of truth
Linear = shared map of the work
```

Do not move canonical product knowledge out of the repository merely to fit Linear. Use Linear to make project progress, blockers, uncertainty, and revisits visible.

## When to use

Use this skill when:

- starting a new product project
- creating a team-visible project structure after kickoff
- translating the product operating system into Linear
- reviewing whether a Linear project reflects the current lifecycle of the work

## Required setup

Recommend or create:

### 1. Initiative

Use an Initiative when there is a broader product or company objective above the project.

### 2. Project

Default first project name:

```txt
[Product Name] — Foundation and MVP
```

### 3. Milestones

Default milestone set:

```txt
1. Product direction
2. Brand and experience
3. Technical foundation
4. First spec ready
5. MVP implementation
6. Review and release readiness
```

### 4. Project status

Use the status model from `docs/linear-workflow.md`:

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

### 5. Links or documents

Add visible links to:

- Product North Star
- Brand
- Design
- Content
- Architecture
- Quality
- Current spec
- Decision log

Use canonical repository docs as the source of truth.

### 6. Issues

Create a starter issue set under each milestone using `docs/linear-workflow.md`.

### 7. Labels

Use:

```txt
decision-needed
assumption
revisit
blocked
docs-update
adr-needed
```

### 8. Saved views

Recommend:

- Open assumptions
- Needs decision
- Needs revisit
- Docs out of date
- Blocked work
- ADRs needed

### 9. Project updates

Recommend a weekly update rhythm during active work and provide the standard update template from `docs/linear-workflow.md`.

## Behaviour

- Keep the Linear structure lightweight enough to help rather than burden the team.
- Use the product phase to decide whether all default milestones are useful.
- If the product is very small, recommend a reduced version rather than blindly creating everything.
- Make uncertainty visible; do not hide open questions in private notes.
- Explain the purpose of each part of the Linear setup so the user understands the model.
- If Linear automation or API access is unavailable, produce a copy-ready setup plan instead of pretending the project has been created.

## Output format

Use this structure:

```md
# Linear project setup

## Initiative

## Project

## Milestones

## Initial issues

## Labels

## Saved views

## Linked docs

## Update rhythm

## Why this structure fits the project

## Items to revisit later
```

## Review checklist

- Is the project outcome clear?
- Do the milestones reflect the real lifecycle?
- Are issues actionable rather than vague?
- Are important repo docs visible from Linear?
- Are blockers, assumptions, and revisits easy to find?
- Could a teammate understand the project state quickly?
- Is the Linear structure helping the work rather than duplicating the repo?
