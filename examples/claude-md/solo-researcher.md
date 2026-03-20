# Example CLAUDE.md — Solo Researcher

This is a template for an individual researcher managing a single study or manuscript project. Adapt the sections to your own setup.

---

```markdown
# CLAUDE.md

## Project Overview
This project investigates [research question]. It involves [brief method description:
e.g., a 2x3 between-subjects experiment, a longitudinal survey, a systematic review].
Currently in the [data collection / analysis / writing] phase.

## File Structure
- `data/raw/` — original data files. Never modify these directly.
- `data/processed/` — cleaned and transformed datasets
- `analysis/` — analysis scripts, numbered sequentially (01_, 02_, etc.)
- `manuscript/` — manuscript drafts and submission materials
- `materials/` — study materials (surveys, stimuli, IRB documents)
- `notes/` — research notes, meeting logs, decision records

## Data Conventions
- Raw data filenames: `[study-name]_[source]_[date-collected].csv`
- Processed data filenames: `[study-name]_clean_[version].csv`
- Variable naming: snake_case, descriptive (e.g., `media_use_hours`, not `Q14`)
- Missing data coded as NA, not blank or -99

## Analysis Conventions
- Language: [R / Python / Stata]
- Package versions pinned in [renv.lock / requirements.txt / environment.yml]
- Every script starts with a comment block describing its purpose and inputs/outputs
- Figures saved to `output/figures/` as both PDF and PNG

## Manuscript
- Target journal: [Journal Name]
- Author guidelines: [URL]
- Citation style: [APA 7th / Chicago / journal-specific]
- Word limit: [N words]
- Current draft: `manuscript/draft_v[N].docx`

## Current Status
[Update this section regularly — it's the most valuable part of CLAUDE.md]

- Data collection: [complete / in progress / planned]
- Sample: N = [X], collected via [platform/method]
- Analysis status: [what's done, what's next]
- Manuscript status: [outline / drafting section X / revising / ready to submit]
- Key blocker: [if any]

## Collaborators
- [Name] — [role, what they're responsible for]
- [Name] — [role, what they're responsible for]

## Important
- Pre-registration: [URL]
- IRB: [approval number, expiration date]
- Do NOT modify files in `data/raw/` under any circumstances
- Do NOT fabricate or hallucinate citations — flag if unsure about a reference
```
