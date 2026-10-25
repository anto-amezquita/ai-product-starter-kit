---
name: brand-direction
description: Use when a product needs its visual brand decided, after docs/brand.md has an essence, attributes, sliders and visual direction. Researches references, explores three directions, chooses one and hands it off as tokens.
---

# Brand direction

Turn the brief in `docs/brand.md` into one chosen visual direction (typeface, accent, neutrals, radius, spacing) and hand it to the design system as tokens.

Stage 3 of the kickoff settles the brand in words. This skill is the visual half. A product that goes to build without it ends up on its tools' defaults and looks like everything else built with them.

## Read first

1. `docs/brand.md`: §1, §4, §5 and §9 must be filled. If any is empty, fill it with the user first (`guide/stages/03-brand-character.md`).
2. `docs/product-north-star.md`
3. `docs/design.md`
4. The design system the product uses, if any: its tokens, its brands and how a brand is applied.

## The five steps

Run them in order. Each one ends with something written in the repo, so the next session doesn't depend on this chat. Keep the working notes in one spec, `specs/<date>-brand-direction.md`.

### 1. Teardown

Ask the user for three reference products whose feel is close to what they want. Add the product's current state, if one exists, as the baseline. Answer the same questions for each, with things you can measure or point to, not impressions. Use DevTools for numbers.

| Question | Answer |
|---|---|
| Content max width, and gutter | |
| Headline font, size and weight at desktop | |
| Body font and size | |
| Colours on the first screen (count them) | |
| Where the accent is used, and where it isn't | |
| What fills the first screen | |
| The one signature element you'd recognise it by | |
| How product UI or components are framed | |
| Active state in the nav | |
| Interaction states (hover, pressed) | |
| One thing to take | |
| One thing to leave | |

"One thing to take" and "one thing to leave" are the user's taste: ask, don't fill them in. Then write three to five lines on what all the references do that the baseline doesn't.

### 2. Brief

Check `docs/brand.md` against the teardown, then fill this prompt from it. Take every value from the docs; don't invent any.

> I'm designing the brand for [product], [what it is in one line] ([URL, if any]). Its job: [what the first screen must make people understand].
>
> Brand essence: "[§1 one-line essence]"
> Feel: [§1 feelings]. Attributes: [§4 attributes].
> Not: [§1 "not"s].
> Leans: [§5, one word per row].
>
> Give me three distinct directions. For each one:
> 1. A typeface for headings and one for body ([font source, e.g. Google Fonts only]), with a type scale.
> 2. One accent colour with a single job, and a neutral scale tinted toward the accent's hue (no flat grey).
> 3. A corner radius and a spacing feel, on a [4px] base.
> 4. [The key screen] rendered with it, at desktop (1440px) and mobile (375px): [what the screen contains, built from real components of the imported design system].
>
> Rules: one left edge for the whole page; spacing only from the scale; text on the accent reaches 4.5:1 in light and dark; [the accent's one job, and where it never goes]; no logo strips, no stock imagery, no gradients for their own sake. Show each direction in light and dark, desktop and mobile. Present one direction at a time; I will save each before asking for the next.

Put the filled prompt in the spec.

### 3. Explore

Run the prompt in a visual design tool. With Claude Design, import the design system first (`/design-sync` from the design-system repo), so the directions use real components. Import the published state, not work in progress.

- One direction at a time. Review it against the brief and give feedback in numbers ("the gap above the buttons to 24px"). Fix, then save before asking for the next.
- Saving means exporting into the repo (`design/direction-<n>/`) and committing, with a README: the direction in one sentence; a table of headings, body, accent (with contrast ratios), neutrals, radius and spacing; decisions made while iterating; known issues. Git is the version history.
- Stop at three. If none fits, mix the strongest parts, or vary only type and accent on one fixed screen, rather than asking for more directions.

Check every direction for these:

- The brand lives in the frame: nav, headline, surfaces, buttons. Components shown as demos can stay in the design system's base theme; don't expect them to carry the brand.
- The first screen shows the product doing its job. A row of loose component specimens reads as generated filler.
- Anything that looks interactive is interactive. A static "active" marker with nothing to mark misleads people.
- Left and right edges line up across nav, hero and every section.
- Text on the accent reaches 4.5:1 in both modes. Measure it.
- Borders and outlines are as quiet as the brief asks.

### 4. Decide

The user chooses. Before they do, compare each direction against §1, §5 and §9 and say which fits best and why, with evidence from the exports. Then write the decision into the spec:

| | Direction chosen | Typeface (heading / body) | Accent | Neutral tint | Radius | Spacing feel |
|---|---|---|---|---|---|---|
| Result | | | | | | |

Add two or three lines on why it beat the others.

Name the brand with the user. If the design system names brands for their job (`base`, `portfolio`), follow that pattern (`site`, `app`). Avoid colour names: the name breaks when the colour changes. The direction's own name can stay as the story for a case study.

Fill `docs/brand.md` §11 Typography, §12 Colour and §13 Shape and material from the chosen direction.

### 5. Hand off

The direction becomes tokens. Nothing is copied by hand.

- **A token-based design system with brands** (e.g. `@amezquita/design-system`): add `tokens/brands/<name>/` in the design-system repo, generate the outputs, and apply the brand in the product with the system's theme scope (`<ThemeScope brand="<name>">`). Release it under the design system's release rules.
- **Tokens in the product repo:** add them as primitive → semantic → component tokens, following `skills/design-system/SKILL.md`.
- **No tokens yet:** create them before building any screen.

Record the choice in `/decisions` as an ADR: what was chosen, the alternatives, and why.

## Done when

- The teardown, the filled prompt, the exports and the decision are in the repo.
- `docs/brand.md` §11–13 match the chosen direction.
- The brand exists as tokens, with a name, and an ADR records it.
