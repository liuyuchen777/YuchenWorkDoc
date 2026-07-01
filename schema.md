# Schema Reference

## Frontmatter

Every markdown file has the same minimal frontmatter:

```yaml
---
title: Human-readable title
description: One-line summary (your manager will scan these)
time: 2025 Q2        # or "2025 Q1-Q3", "2025 Q4 - 2026 Q2" for ranges
type: project        # project | research | presentation | event
---
```

### Type values

- `project` — sustained engineering work with deliverables
- `research` — investigation, exploration, analysis without shipping code
- `presentation` — knowledge shares, WTS sessions, deep-dives, talks
- `event` — hackathons, team process contributions, facilitation

## Body Structure

Every entry has up to 4 sections:

```markdown
## Summary
2-3 sentences. Manager-readable standalone paragraph.

## Context & Problem
Why this work was needed.

## What I Did
First-person narrative. YOUR decisions, contributions, challenges solved.

## Impact & Results
Quantified outcomes where possible.
```

For lightweight entries (presentations, events), Summary alone is sufficient. Expand other sections as the story matures.
