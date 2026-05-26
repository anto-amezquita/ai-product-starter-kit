---
name: project-kickoff
description: Use when starting a new digital product or app from a rough idea and the user needs guided help shaping the product direction, brand, experience, technical approach, and first spec before implementation.
---

# Project kickoff

Guide the user through the beginning of a new digital product project.

This skill is for turning a loose idea into a clear project foundation. It should feel like a thoughtful product workshop, not a form.

## When to use

Use when:

- starting a brand-new product from a rough idea
- no project foundation docs exist yet and direction needs to be shaped before implementation
- the user needs guided help across product, brand, design, and technical decisions together

Skip when:

- the project already has established docs — use the relevant targeted skill instead (product-spec, design-system, quality-gate)
- the user just needs a spec for a specific feature — use `product-spec` instead

## Read first

Before beginning, read:

1. `guide/start-a-new-project.md`
2. any existing files in `docs/` — if some docs already exist, build on them rather than starting over
3. `AGENTS.md`, if present

If the project does not yet contain the starter docs, use `guide/start-a-new-project.md` as the process and create the missing files when the direction is clear enough.

## Core behaviour

- Ask one main question at a time.
- When the user is unsure, offer 2–4 plausible options with brief trade-offs rather than waiting for clarity.
- Make provisional assumptions rather than stopping; label them clearly and keep them visible.
- Track three things throughout: **Decisions**, **Assumptions**, **Open questions**.
- Summarise the emerging product at natural checkpoints.
- Challenge unnecessary scope gently — prefer the smallest strong first version over a broad weak one.
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

Not all docs need to reach final form in one session — create what the conversation has shaped clearly, and note what remains unresolved.

## Output format

End the kickoff with:

```md
## Product summary
[What the product is, who it's for, and what the first version does — two or three sentences.]

## Key decisions
- [Decision made]

## Assumptions
- [Assumption — note what would change if this turns out to be wrong]

## Open questions
- [Question — what unblocks it or who should answer it]

## Files created or updated
- [File path]

## Next step
[One clear action to take immediately.]

## Implementation prompt
[Ready-to-use prompt for starting implementation.]
```

## Quality bar

This skill succeeds when:

- the product becomes clearer through the conversation
- the user feels helped rather than processed
- useful options appear when the answer is not obvious
- important trade-offs become visible
- the first version becomes smaller and stronger
- the generated files feel like the natural output of the conversation
