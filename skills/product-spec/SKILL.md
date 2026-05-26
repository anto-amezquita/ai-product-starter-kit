---
name: product-spec
description: Use when turning a product or feature idea into a buildable technical specification that aligns with the existing product, brand, design, content, architecture, and quality rules.
---

# Product spec

Create or update a product technical specification for a meaningful feature, workflow, redesign, or new product slice.

## Read first

Before writing a spec, read:

1. `docs/product-north-star.md`
2. `docs/brand.md`
3. `docs/design.md`
4. `docs/content.md`
5. `docs/architecture.md`
6. `docs/quality.md`
7. `docs/spec.md`
8. any relevant existing files in `/specs`
9. any relevant ADRs in `/decisions`

## When to use

Use this skill for:

- a new product
- a major feature
- a meaningful redesign
- a workflow affecting multiple parts of the product
- any work where behaviour, technical structure, or scope could otherwise become unclear

Do not use a full spec for:

- tiny copy changes
- isolated visual adjustments
- trivial bug fixes
- tasks already fully defined elsewhere

## Core behaviour

- Start from the user problem and desired outcome.
- Preserve the link between product intent, UX behaviour, and implementation.
- Ask only the questions needed to remove important ambiguity.
- When information is missing but not blocking, make a reasonable assumption and label it.
- Surface trade-offs, dependencies, risks, and open questions explicitly.
- Keep the spec compact, but not vague.
- Make requirements testable.
- Do not hide unresolved product decisions inside technical language.
- Do not invent product behaviour that conflicts with the core docs.

## Required structure

Follow `docs/spec.md`.

Every spec must cover:

1. Overview
2. Goals and non-goals
3. User experience
4. Functional requirements
5. Non-functional requirements
6. Information architecture and data
7. Technical approach
8. Interface and component breakdown
9. Risks, trade-offs, assumptions, and open questions
10. Acceptance criteria
11. Implementation plan

## File naming

Save specs as:

`/specs/YYYY-MM-DD-feature-name.md`

Use lowercase, hyphenated, specific names.

## Review before finalising

Check:

- Is the user problem clear?
- Is the desired outcome clear?
- Are goals distinct from tasks?
- Is the scope explicit?
- Are non-goals included?
- Are major flows covered?
- Are loading, empty, success, error, and permission states considered where relevant?
- Are requirements specific and testable?
- Are accessibility and responsive behaviour covered where relevant?
- Are data, dependencies, and permissions visible?
- Are assumptions and decisions separated?
- Could a competent contributor begin work without inventing the product?

## Final response

Return:

1. the spec file created or updated
2. a short summary of the feature
3. key decisions
4. assumptions
5. open questions
6. the recommended next step
