---
title: "CLAUDE.md as Institutional Memory"
order: 6
category: workflows
prerequisites: [getting-started]
---

# CLAUDE.md as Institutional Memory

Every time you start a new conversation with Claude Code, it begins with no memory of your previous sessions. It does not know your project structure, your conventions, your collaborators, or your preferences. You are onboarding a new collaborator from scratch, every single time.

Unless you write a CLAUDE.md.

## What CLAUDE.md Does

A `CLAUDE.md` file in your project's root directory is automatically loaded at the start of every Claude Code session. It is the first thing Claude Code reads. Whatever you put in this file becomes persistent context: instructions, conventions, and knowledge that carry across every conversation.

For software projects, CLAUDE.md typically contains coding standards and build commands. For academic research, it can be considerably more: a living document that encodes how your research works, what state your projects are in, and what conventions Claude Code needs to respect in order to be genuinely useful.

## Why This Matters for Research

Academic projects are complex in ways that aren't always obvious from the file structure alone. They involve naming patterns for data files, manuscript drafts, and notes that only make sense if you know the conventions behind them. They involve relationships between projects, manuscripts, and people that aren't captured in any directory hierarchy. They involve methodological choices that inform how data should be handled, journal-specific formatting requirements that vary across submissions, and ongoing status information that changes week to week.

Without CLAUDE.md, you re-explain all of this every session. With it, Claude Code arrives already understanding your project. Not perfectly, but with enough context to be a useful collaborator rather than a blank slate. The difference in both the quality and the relevance of its responses is substantial.

## Structuring a CLAUDE.md for Research

Here's a template for a solo researcher's project:

```markdown
# CLAUDE.md

## Project Overview
This project is [brief description]. The principal investigator is [name].
We are currently in the [phase: data collection / analysis / writing] stage.

## File Structure
- `data/` — raw and processed data files. Do not modify raw data.
- `analysis/` — R/Python scripts for analysis
- `manuscript/` — LaTeX/Word manuscript drafts
- `notes/` — research notes, meeting minutes, decisions log

## Conventions
- Data files are named: `[study]_[wave]_[type]_[date].csv`
- Analysis scripts are numbered: `01_clean.R`, `02_descriptives.R`, etc.
- Manuscript drafts use the pattern: `manuscript_v[N].docx`

## Current Status
- Data collection complete (N = 450, collected via Prolific, March 2026)
- Preliminary analysis done — see `analysis/02_descriptives.R`
- Working on confirmatory factor analysis
- Target journal: [Journal Name] — see their author guidelines at [link]

## Collaborators
- [Name] — co-PI, handles [area]
- [Name] — graduate student, working on [specific task]

## Important Notes
- IRB approval #[number], expires [date]
- Pre-registration: [link]
- The DV "engagement" is measured with [scale name] — do not rename or recode
```

## CLAUDE.md for a Lab Group

If your lab or research group shares a repository, CLAUDE.md can encode collective conventions, the kind of tacit knowledge that usually lives in a lab handbook or, more often, in no written document at all:

```markdown
# CLAUDE.md — [Lab Name] Research Group

## Lab Conventions
- All analyses use R 4.3+ with tidyverse
- We follow APA 7th edition formatting for all manuscripts
- Data must never be committed to git — use .gitignore
- All study materials go in `materials/` with IRB documentation

## Active Projects
- **Project A** — [one-line status]. Lead: [Name]. Dir: `project-a/`
- **Project B** — [one-line status]. Lead: [Name]. Dir: `project-b/`

## Onboarding
New lab members should read:
1. `docs/lab-handbook.md`
2. `docs/data-management-policy.md`
3. The project-specific README in whichever project they're joining

## Style
- We write in active voice
- Methods sections follow [lab template] structure
- Statistical reporting: F(df1, df2) = X.XX, p = .XXX, η² = .XX
```

## Tips for Maintaining CLAUDE.md

1. **Start small.** You don't need a comprehensive document on day one. Add information as you notice yourself repeating it across sessions. Each repetition is a signal that something belongs in the file.

2. **Update regularly.** CLAUDE.md should reflect your current project status, not a snapshot from the day you created it. Updating the "Current Status" section weekly takes less than a minute and pays for itself in session quality.

3. **Be specific about what not to do.** If there are files Claude Code shouldn't modify, data it shouldn't access, or conventions it shouldn't break, say so explicitly. Negative instructions are often more informative than positive ones. They encode the mistakes you have already encountered or want to prevent.

4. **Include links.** If your project references external resources (a pre-registration, a journal's author guidelines, a shared drive), link to them. Claude Code can often access URLs to retrieve current information, which keeps your CLAUDE.md from needing to duplicate content that lives elsewhere.

5. **Version it.** Since CLAUDE.md lives in your project directory, it's naturally version-controlled if you use git. This means you have a history of how your project conventions have evolved, which is itself a useful form of documentation.

## CLAUDE.md as Documentation

Here's a secondary benefit worth noting: a well-maintained CLAUDE.md is also useful documentation for *humans*. When a new collaborator joins your project, they can read CLAUDE.md to understand the structure, conventions, and current status, the same way Claude Code does. The document serves both audiences because the information both audiences need is, in most cases, the same: what is this project, how is it organized, and what should I know before I start working in it.

This dual purpose makes CLAUDE.md worth maintaining even if you stopped using Claude Code tomorrow. It is a lightweight, low-ceremony way to keep project knowledge externalized and current, the kind of documentation that academic projects need but rarely have.

## Getting Started

1. Create a `CLAUDE.md` file in the root of one of your current projects.
2. Write three sections: Project Overview, File Structure, and Current Status.
3. Start your next Claude Code session in that directory and notice the difference.
4. Add to it every time you catch yourself explaining something Claude Code should already know.
