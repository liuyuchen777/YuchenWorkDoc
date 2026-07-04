# Resume Workflow

This repo keeps the source of truth for work evidence and resume variants.

## Folders

- `work/` stores project evidence, impact, and technical details by year.
- `profile.md` stores stable career context and role history.
- `jd/` stores job descriptions as plain text or Markdown.
- `resume/base.latex` is the general-purpose resume.
- `resume/<company>-<role>.latex` stores tailored resume variants.
- `resume_rendered/<company>-<role>.pdf` stores rendered PDFs that are committed with the resume source.
- `_generated/latex/` stores temporary LaTeX build files and is ignored by git.
- `.agent/resume-variation/SKILL.md` is the repo-local skill draft for future resume tailoring sessions.

## Naming

Use one slug across the JD and resume source:

```text
jd/<company>-<role>.txt
resume/<company>-<role>.latex
resume_rendered/<company>-<role>.pdf
```

Example:

```text
jd/openai-ml-infra.txt
resume/openai-ml-infra.latex
resume_rendered/openai-ml-infra.pdf
```

## Tailoring Loop

1. Add the JD to `jd/<slug>.txt`.
2. Ask Codex to create a resume variation for that JD.
3. Codex reads the JD, `resume/base.latex`, `profile.md`, and relevant `work/**` files.
4. Codex creates `resume/<slug>.latex` by copying and adapting the base resume.
5. Review the diff together, especially summary, skills ordering, experience bullets, and truthfulness.
6. Run the humanizer skill on the final resume source to remove AI writing patterns while preserving the facts and LaTeX structure.
7. Render the resume locally with `latexmk`, keeping auxiliary files under `_generated/latex/`.
8. Copy the rendered PDF to `resume_rendered/<slug>.pdf` so the PDF is part of the repo.
9. Review the PDF locally for page count, spacing, line wraps, and content balance.
10. If the local render or Overleaf reports LaTeX errors or layout issues, revise the `.latex` source and render again.

## Resume Editing Rules

- Keep `resume/base.latex` broadly useful; put JD-specific wording in separate variants.
- Do not invent projects, metrics, employers, dates, titles, or tools.
- Prefer evidence from `work/**` over generic claims.
- Optimize for the target JD by reordering and rewriting, not by exaggerating.
- Keep the resume concise enough to fit the intended page count.
- Preserve the existing LaTeX style unless there is a clear reason to change the template.
- Before rendering, run the `humanizer` skill on the resume text and remove em dashes, en dashes, generic promotional phrasing, and other AI-writing patterns.

## Local render

Prefer local rendering so the PDF can be reviewed and committed with the source. BasicTeX or MacTeX must provide `latexmk` and `pdflatex`. In non-interactive shells, TeX may need an explicit PATH:

```bash
PATH="/Library/TeX/texbin:$PATH" latexmk -pdf -interaction=nonstopmode -halt-on-error -output-directory=_generated/latex resume/<slug>.latex
mkdir -p resume_rendered
cp _generated/latex/<slug>.pdf resume_rendered/<slug>.pdf
```

The `_generated/latex/` directory is ignored and can be deleted or regenerated at any time. The `resume_rendered/<slug>.pdf` file is the rendered artifact that should stay in the repo.

Use Overleaf as a secondary check when needed, especially if local fonts or package versions differ from the target export environment.
