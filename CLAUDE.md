# YuchenWorkDoc

Markdown-based work summary for HR events (annual reviews, promotions, manager conversations).

## Structure

- `profile.md` — Role intro, team history
- `work/<year>/<slug>.md` — All entries (projects, research, presentations, events)
- `schema.md` — Frontmatter reference
- `jd/` — Job descriptions used to tailor resume variants
- `resume/` — LaTeX resume sources, including `base.latex` and JD-specific variants
- `resume_rendered/` — Rendered resume PDFs that are committed with the source
- `.agent/resume-variation/SKILL.md` — Repo-local skill draft for resume tailoring
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

## Resume Workflow

When asked to create a resume variation, read the JD from `jd/`, the base resume from `resume/base.latex`, career context from `profile.md`, and relevant evidence from `work/**`. Create the tailored LaTeX source as `resume/<jd-slug>.latex`, run the `humanizer` skill on the final resume source, render it locally with `latexmk`, and copy the final PDF to `resume_rendered/<jd-slug>.pdf`. Keep auxiliary build files under `_generated/latex/`, which is ignored by git.

Keep `resume/base.latex` general-purpose unless the user explicitly asks to update it. Do not invent projects, metrics, technologies, roles, dates, or employers; tailor by selecting, ordering, and rewriting evidence-backed material.
