---
name: quality-gate
description: Use near the end of meaningful product work to review whether a feature, flow, page, or release is actually ready according to the project's spec, design, content, architecture, accessibility, testing, and release standards.
---

# Quality gate

Run a final, product-wide readiness review before meaningful work is considered complete.

This skill exists to prevent “it appears to work” from being mistaken for “it is ready.”

## Read first

Before reviewing, read:

1. `docs/product-north-star.md`
2. `docs/brand.md`
3. `docs/design.md`
4. `docs/content.md`
5. `docs/architecture.md`
6. `docs/quality.md`
7. the relevant spec in `/specs`
8. relevant ADRs in `/decisions`
9. the implementation being reviewed

## Core behaviour

- Review the work against the actual spec, not only against the visible UI.
- Distinguish between:
  - done
  - done with known follow-ups
  - not ready
- Prefer concrete evidence over optimistic language.
- Surface gaps clearly.
- Include product, design, content, technical, accessibility, testing, analytics, and release concerns.
- Do not silently waive requirements; if something is skipped, name the trade-off.
- Do not call work complete if critical acceptance criteria are unmet.

## Review areas

### 1. Product fit

Check:

- the work still supports the product direction
- the user problem is actually addressed
- scope matches the spec
- non-goals have not accidentally crept in
- no major behaviour has been invented outside the docs

### 2. Spec coverage

Check:

- goals
- functional requirements
- non-functional requirements
- user flows
- edge cases
- acceptance criteria
- assumptions and open questions

### 3. UX and visual quality

Check:

- hierarchy
- responsive behaviour
- all relevant states
- motion behaviour
- consistency with `brand.md` and `design.md`
- realistic content
- copy quality against `content.md`

### 4. Accessibility

Check:

- keyboard use
- focus
- semantics
- labels
- contrast
- motion preferences
- errors
- touch targets
- screen-reader implications

Use `accessibility-review` when a deeper accessibility pass is needed.

### 5. Technical quality

Check:

- architecture fit
- reuse of existing components and tokens
- absence of unnecessary duplication
- error handling
- type safety
- state/data correctness
- maintainability
- relevant ADR updates

### 6. Testing and validation

Check:

- relevant tests added or updated
- tests pass
- linting/type checks pass
- manual QA done where needed
- regressions considered
- browser/device behaviour checked where relevant

### 7. Analytics and observability

Check when relevant:

- key events implemented
- success/failure states observable
- error reporting
- monitoring needs
- no unnecessary sensitive data collected

### 8. Release readiness

Check:

- documentation updated
- migration or rollout steps considered
- feature flags considered if needed
- rollback or recovery considered
- known issues listed
- production checks identified

## Workflow

### 1. Establish scope

Identify:

- what is being reviewed
- which spec governs it
- what “done” should mean here

### 2. Review evidence

Inspect:

- implementation
- tests
- UI behaviour
- docs
- acceptance criteria
- known issues

### 3. Classify findings

Use:

#### Blockers
Must be fixed before the work is considered ready.

#### Important follow-ups
Should be fixed soon, but may not block release depending on context.

#### Nice-to-have improvements
Useful refinements that do not undermine readiness.

### 4. Give a release recommendation

Use one of:

- **Ready**
- **Ready after small fixes**
- **Not ready**

Explain the reason clearly.

## Output format

```md
# Quality gate review

## Scope

## Overall recommendation
Ready | Ready after small fixes | Not ready

## What is complete

## Blockers

## Important follow-ups

## Nice-to-have improvements

## Evidence reviewed

## Suggested next actions
```

## Final review checklist

- Does the work solve the intended user problem?
- Does it satisfy the spec?
- Are edge cases and states handled?
- Does it follow the product system?
- Is the copy good enough to ship?
- Is it accessible?
- Is it technically maintainable?
- Are tests and checks complete enough?
- Are analytics and observability handled where needed?
- Could this be released without someone quietly knowing it is unfinished?
