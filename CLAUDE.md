# YuchenWorkDoc

Markdown-based work summary for HR events (annual reviews, promotions, manager conversations).

## Structure

- `profile.md` — Role intro, team history
- `work/<year>/<slug>.md` — All entries (projects, research, presentations, events)
- `schema.md` — Frontmatter reference
- `_generated/` — Compiled outputs (gitignored, reproducible)

## Frontmatter

Minimal. Every file uses the same schema:

```yaml
---
title: Human-readable title
description: One-line summary (manager will scan these)
time: 2025 Q2        # or "2025 Q1-Q3", "2025 Q4 - 2026 Q2" for ranges
type: project | research | presentation | event
---
```

## Body

5 sections (Summary is required; others expand as the story matures):

1. **Summary** — 2-3 sentences, standalone, manager-readable
2. **Context & Problem** — Why this work was needed
3. **What I Did** — First person, YOUR decisions and contributions
4. **Impact & Results** — Quantified outcomes where possible
5. **Links** — References to design docs, wikis, weblabs, Quip docs, etc.

## Conventions

- File naming: kebab-case
- One project per file
- Year-based subdirectories in `work/`
- Write in first person
- This package is open to my manager — keep Summaries polished
- After creating or updating any work artifact (`work/**`, `profile.md`), run the `humanizer` skill on the changed prose to strip AI writing patterns (em dashes, copula avoidance, rule-of-three, promotional language). Keep the neutral, factual register — do not inject first-person opinion or personality into these technical docs. If the `humanizer` skill is not found, install it by following [github.com/blader/humanizer](https://github.com/blader/humanizer)

## Generation (On-Demand)

When asked to generate a narrative doc (annual review, promo doc, highlights), read ALL relevant source files and compile into a coherent document. Write output to `_generated/`.
