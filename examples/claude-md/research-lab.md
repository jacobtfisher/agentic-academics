# Example CLAUDE.md — Research Lab

This is a template for a shared lab repository where multiple people and projects coexist. Adapt to your lab's conventions.

---

```markdown
# CLAUDE.md — [Lab Name]

## Lab Overview
[Lab Name] studies [research area] in the Department of [X] at [University].
PI: [Name]. This repository contains shared resources, templates, and active projects.

## Repository Structure
- `projects/` — one subdirectory per active project (each has its own README)
- `templates/` — manuscript templates, analysis script templates, IRB templates
- `docs/` — lab handbook, onboarding guide, data management policy
- `shared/` — shared resources (stimuli libraries, common scales, reference lists)

## Lab Conventions

### Code
- Primary language: [R / Python]
- Style guide: [tidyverse style guide / PEP 8 / lab-specific guide in docs/]
- All analysis scripts must be reproducible from raw data with a single command
- Use [renv / conda / venv] for dependency management
- Never commit data files to git — data lives on [secure server / shared drive]

### Writing
- APA 7th edition unless a specific journal requires otherwise
- Active voice preferred
- Statistical reporting format: F(df1, df2) = X.XX, p = .XXX, effect size = .XX
- All manuscripts go through at least one internal lab review before submission

### Data Management
- Raw data is immutable — never modify original files
- All data processing steps must be scripted (no manual Excel edits)
- De-identified data only in shared repositories
- Sensitive data (identifiable, IRB-restricted) stays on [secure system]

## Active Projects

| Project | Lead | Status | Directory |
|---------|------|--------|-----------|
| [Project A] | [Name] | Data collection | `projects/project-a/` |
| [Project B] | [Name] | Analysis | `projects/project-b/` |
| [Project C] | [Name] | Writing | `projects/project-c/` |

## People

| Name | Role | Focus |
|------|------|-------|
| [PI Name] | Principal Investigator | [area] |
| [Name] | Postdoc | [area] |
| [Name] | PhD Student (Year N) | [project] |
| [Name] | RA | [tasks] |

## Onboarding
New lab members should:
1. Read `docs/lab-handbook.md`
2. Read `docs/data-management-policy.md`
3. Set up their development environment per `docs/setup-guide.md`
4. Read the README in their assigned project directory

## Important Policies
- All studies require IRB approval before any data collection
- Pre-registration is expected for confirmatory studies
- Code review is required before results are reported in manuscripts
- Do NOT commit API keys, credentials, or participant data to this repository
```
