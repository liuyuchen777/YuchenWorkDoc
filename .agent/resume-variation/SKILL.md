---
name: resume-variation
description: Create polished JD-tailored LaTeX resume variants and rendered PDFs from this repo's jd, work, profile, and resume folders.
---

# Resume Variation

Use this skill when the user asks to create, tailor, or review a LaTeX resume variation for a job description in this repo.

## Inputs

- JD: `jd/<slug>.txt` or `jd/<slug>.md`
- Base resume: `resume/base.latex`
- Career context: `profile.md`
- Evidence: relevant files in `work/**`
- Output source: `resume/<slug>.latex`
- Rendered PDF: `resume_rendered/<slug>.pdf`

## Workflow

1. Identify the JD slug and read the JD completely.
2. Read `resume/base.latex`, `profile.md`, and enough `work/**` files to support the JD's target skills.
3. Extract the JD priorities: role type, must-have skills, preferred skills, domain signals, seniority, and keywords.
4. Select evidence-backed projects from `work/**`; do not invent facts.
5. Create `resume/<slug>.latex` from `resume/base.latex`.
6. Tailor summary, skill ordering, and experience bullets to the JD.
7. Run the `humanizer` skill on the tailored resume source, preserving facts, LaTeX commands, and the existing resume style.
8. Render the resume locally when LaTeX is available. Use ignored build output for auxiliary files and keep the final PDF in `resume_rendered/`:
   - `PATH="/Library/TeX/texbin:$PATH" latexmk -pdf -interaction=nonstopmode -halt-on-error -output-directory=_generated/latex resume/<slug>.latex`
   - `mkdir -p resume_rendered`
   - `cp _generated/latex/<slug>.pdf resume_rendered/<slug>.pdf`
9. Review the rendered PDF when possible, especially page count, spacing, line wraps, and whether it fits the intended page count.
10. Show the user the main positioning choices and the rendered PDF path. Ask for review when wording choices are subjective.

## Tailoring Rules

- Keep facts consistent with `profile.md`, `work/**`, and existing resume dates.
- Make JD-specific changes in the variant file, not `resume/base.latex`, unless the user asks to update the base.
- Keep claims specific and metric-backed where evidence exists.
- Use the JD's terminology when it truthfully maps to existing experience.
- Avoid adding technologies that appear only in the JD and not in repo evidence or the base resume.
- Preserve the existing LaTeX commands and structure unless layout changes are required.
- Remove em dashes, en dashes, generic promotional phrasing, rule-of-three cadence, and vague AI-style claims during the humanizer pass.
- Use the local LaTeX engine when available. If `latexmk` or `pdflatex` is missing, tell the user what to install and still provide the polished `.latex` source.
- Keep auxiliary build files under `_generated/`, which is ignored. Keep rendered PDFs under `resume_rendered/` so they are part of the repo.

## Review Checklist

- The resume tells a coherent story for the target role.
- Every strong claim has support in `work/**`, `profile.md`, or `resume/base.latex`.
- Skills are ordered by JD relevance.
- Bullets emphasize impact, scope, and technical depth.
- The LaTeX source compiles locally when LaTeX is available.
- The rendered PDF exists at `resume_rendered/<slug>.pdf` when local rendering succeeds.
