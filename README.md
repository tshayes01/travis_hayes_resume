# Travis Hayes Resume Repository

This repository is structured for **both humans and AI agents**.

## Goals
- Make key career information easy to read in GitHub.
- Keep one canonical source of truth for resume data.
- Provide machine-readable formats for AI ingestion.
- Make updates traceable and automation-friendly.

## Recommended Structure

```text
.
├── README.md
├── resume/
│   ├── resume.md
│   ├── resume.json
│   └── changelog.md
├── assets/
│   └── resume.pdf
├── context/
│   ├── summary.md
│   ├── role_targets.md
│   └── keywords.txt
└── .github/
    └── workflows/
        └── validate-resume.yml
```

## Why this works for AI ingestion

### 1) Canonical, structured data (`resume/resume.json`)
Use this as the source for tooling and agents. Keep fields explicit and stable:
- `basics` (name, title, location, links)
- `experience` (company, role, dates, highlights, tech)
- `projects`
- `skills`
- `education`
- `certifications`

### 2) Human-friendly version (`resume/resume.md`)
Keep this narrative and concise. Most recruiters and humans read this first.

### 3) Retrieval context (`context/*`)
These files help agents tailor outputs:
- `summary.md`: short professional narrative and positioning.
- `role_targets.md`: target roles, industries, geographies.
- `keywords.txt`: explicit keywords for matching systems and LLM prompts.

### 4) Versioned changes (`resume/changelog.md`)
When major updates happen, log what changed and why. This helps agents reason about freshness.

## Content conventions for AI-readability
- Use ISO date format (`YYYY-MM`) for roles and projects.
- Prefer arrays of short bullet statements over long paragraphs.
- Keep technology names normalized (`PostgreSQL`, `TypeScript`, `AWS`).
- Use consistent section and key names over time.
- Avoid embedding critical details only in PDFs.

## Update Workflow
1. Update `resume/resume.json` first.
2. Regenerate or align `resume/resume.md` from JSON.
3. Export/update `assets/resume.pdf`.
4. Add a short entry to `resume/changelog.md`.
5. Run validation checks.

## Validation Checklist
- JSON is valid and parseable.
- Links are current.
- Dates are consistent across formats.
- Markdown has clear headings and no empty sections.

## Optional Next Steps
- Add a GitHub Action to validate JSON on each commit.
- Publish a GitHub Pages site from `resume/resume.md`.
- Add `versions/` snapshots for role-specific resume variants.

