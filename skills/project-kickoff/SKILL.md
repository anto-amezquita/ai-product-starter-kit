---
name: project-kickoff
description: Use when starting a new digital product or app from a rough idea and the user needs guided help shaping the product direction, brand, experience, technical approach, and first spec before implementation.
---

# Project kickoff

Guide the user through the beginning of a new digital product project.

This skill is for turning a loose idea into a clear project foundation. It should feel like a thoughtful product workshop, not a form.

## Read first

Before beginning, read:

1. `guide/start-a-new-project.md`
2. any existing files in `docs/`
3. `AGENTS.md`, if present

If the project does not yet contain the starter docs, use `guide/start-a-new-project.md` as the process and create the missing files when the direction is clear enough.

## Core behaviour

- Ask one main question at a time.
- Keep the user moving forward.
- When the user is unsure, offer 2–4 plausible options with brief trade-offs.
- Make provisional assumptions rather than stopping too often; label them clearly.
- Keep track of:
  - **Decisions**
  - **Assumptions**
  - **Open questions**
- Summarise the emerging product at natural checkpoints.
- Challenge unnecessary scope gently.
- Prefer the smallest strong first version over a broad weak one.
- Do not generate final documents before the idea has enough shape.

## Stages

Follow the process in `guide/start-a-new-project.md`:

1. Idea
2. Product direction
3. Brand character
4. Experience direction
5. Technical direction
6. First build
7. Project setup and next step

Show a compact progress indicator at natural checkpoints.

## Required outputs

By the end, create or update:

- `docs/product-north-star.md`
- `docs/brand.md`
- `docs/design.md`
- `docs/content.md`
- `docs/architecture.md`
- `docs/quality.md`
- the first relevant spec in `/specs`
- `AGENTS.md`

If major technical choices are made, create an ADR in `/decisions`.

## Final response

End with:

1. a concise product summary
2. key decisions made
3. assumptions still in play
4. open questions worth revisiting
5. files created or updated
6. the best next step
7. a ready-to-use implementation prompt

## Quality bar

This skill succeeds when:

- the product becomes clearer through the conversation
- the user feels helped rather than processed
- useful options appear when the answer is not obvious
- important trade-offs become visible
- the first version becomes smaller and stronger
- the generated files feel like the natural output of the conversation
