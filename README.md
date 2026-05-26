# AI Product Starter Kit

This repository uses a small set of shared documents to keep product, design, architecture, and AI-assisted development aligned.

## Start here

1. Read `docs/product-north-star.md`
2. Read `docs/brand.md`
3. Read `docs/design.md`
4. Read `docs/content.md`
5. Read `docs/architecture.md`
6. Read `docs/quality.md`
7. For feature work, read the relevant file in `/specs`

## Working model

- Stable product rules live in `/docs`
- Feature definitions live in `/specs`
- Important technical decisions live in `/decisions`
- AI agents should begin with `AGENTS.md`

## Default workflow

1. Clarify the product intent
2. Create or update a spec
3. Design the flow and components
4. Implement within the architecture rules
5. Validate against the quality bar
6. Record important decisions

## Suggested setup order for a new project

1. Fill in `docs/product-north-star.md`
2. Adapt `docs/brand.md`
3. Adapt `docs/design.md`
4. Complete `docs/content.md`
5. Complete `docs/architecture.md`
6. Review `docs/quality.md`
7. Create the first product spec in `/specs`
8. Start building from that spec

## Optional cross-LLM adapter files

This starter kit includes `AGENTS.md` as the default agent entry file.

If you also use other coding agents, create small adapter files that point to the same shared docs:

- `CLAUDE.md`
- `GEMINI.md`
- `.github/copilot-instructions.md`

Keep the shared truth in `/docs`, not inside each adapter file.


## Starting a new project with the guide

Read `START-HERE.md`, then ask your AI assistant to use:

`guide/start-a-new-project.md`

The guide will lead you through the product idea, direction, brand, experience, technical setup, first spec, and next build step one question at a time.


## Reusable skills

This starter kit includes six skills in `/skills`:

- `project-kickoff`
- `product-spec`
- `frontend-design`
- `accessibility-review`
- `design-system`
- `quality-gate`

The docs hold the project's truth. The skills hold repeatable ways of working with that truth.

A useful default workflow is:

```txt
rough idea
→ project-kickoff
→ product-spec
→ frontend-design
→ design-system, when shared patterns emerge
→ accessibility-review
→ quality-gate
```


## Linear as the team-visible layer

Use `docs/linear-workflow.md` to represent the product operating system in Linear without moving the source of truth out of the repo.

```txt
Repository = what we know
Linear = where that knowledge is in motion
```

The starter workflow uses:

- Initiatives for larger goals
- Projects for coherent bodies of work
- Milestones for lifecycle stages
- Issues for concrete next work
- Labels and saved views for blockers, assumptions, and revisits
- Project updates for the current story of the work

Use `skills/project-setup-linear/SKILL.md` when creating the Linear structure for a new product project.
