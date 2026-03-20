---
title: "Skills for Research Workflows"
order: 3
category: workflows
prerequisites: [getting-started]
---

# Skills for Research Workflows

One of Claude Code's most useful features for academic work is the skill system — a mechanism for encoding complex, multi-step workflows as reusable prompts. Rather than re-explaining your process every session, you write it once and invoke it with a command. Think of skills as research protocols for your AI collaborator.

## What Is a Skill?

A skill is a markdown file stored in `~/.claude/skills/` (global) or `.claude/skills/` (per-project). Each skill contains:

1. **A description** — tells Claude Code when and how to trigger the skill
2. **Detailed instructions** — step-by-step process, formatting rules, conventions
3. **Reference materials** — optional files the skill can consult (style guides, templates, examples)

When you invoke a skill (e.g., by typing `/my-skill`), Claude Code loads the instructions and follows them.

## Why Skills Matter for Researchers

Academic work is full of recurring processes — taking structured notes on a paper you've read, running a standard set of checks on a dataset, generating documentation for an analysis pipeline, conducting a weekly review of your projects, preparing a manuscript for submission to a specific journal. Each of these involves judgment calls, formatting conventions, and domain knowledge that you'd otherwise need to re-explain every session.

Skills address both an efficiency problem and a reproducibility problem. On the efficiency side, encoding a workflow once means you don't waste conversation turns re-establishing context. On the reproducibility side, a well-written skill is a documented, shareable description of exactly how a workflow operates. Another researcher can read your skill file and understand your process — or adapt it for their own use. As such, skills serve a dual function: they make your AI interactions more productive *and* they make your methods more transparent.

## Anatomy of a Skill

Here's a simplified example of a literature note skill:

```markdown
# Literature Note Skill

## Overview
This skill creates a structured research note from a paper the user has read.
Use when the user asks to create a literature note or process a paper.

## Steps

1. Ask the user for the paper (citation key, DOI, or title).
2. Retrieve the paper's metadata (title, authors, year, journal).
3. Ask the user 3-4 targeted questions:
   - What is the paper's core argument or finding?
   - How does it connect to your current research?
   - What did you find surprising or worth pushing back on?
   - Are there methodological choices you'd do differently?
4. Create a note with this structure:

## Note Template

```
# [Authors] ([Year]) — [Short Title]

## Summary
[2-3 sentences based on metadata + user's description]

## Key Contributions
[Bullet points drawn from the user's answers]

## Connections
[Links to the user's existing projects/notes mentioned in the Q&A]

## Critical Notes
[Methodological concerns, limitations, open questions from the Q&A]

## Quotes / Key Passages
[Leave empty for the user to fill in]
```

## Important
- Always ask the user to provide their own interpretation first.
  Do not generate a summary they haven't contributed to.
- Link to related notes and projects when possible.
```

Notice the structure: the skill asks you to do the thinking (the Q&A step), then organizes and connects your input. It doesn't replace the intellectual work — it scaffolds it. This is the "teach me" principle operationalized as a workflow.

## Example Skills for Academic Work

### Daily Research Review

A skill that runs each morning:
- Scans your project notes for pending tasks and upcoming deadlines
- Asks you a few reflective questions about your priorities
- Generates a structured daily note with your intentions, carry-forward items, and a timeline

### Data Codebook Generator

A skill that documents a dataset:
- Reads a data file (CSV, SPSS, Stata, etc.)
- Extracts variable names, types, and basic descriptive statistics
- Asks you to describe each variable's meaning and any coding decisions
- Produces a formatted codebook with your descriptions and the computed statistics

### Manuscript Submission Checklist

A skill for pre-submission review:
- Reads your manuscript draft
- Checks against a journal's submission guidelines (word count, formatting, required sections)
- Flags potential issues (missing ethics statement, incomplete references, inconsistent terminology)
- Generates a checklist of items to address before submitting

### Literature Gap Finder

A skill that helps you map a literature:
- Takes a research question and a list of key papers you've already read
- Asks you to describe the main theoretical camps or methodological approaches in the area
- Identifies potential gaps based on your description: "You've described three theoretical accounts but haven't mentioned any papers that try to integrate them. Is that a gap, or have you seen integration attempts?"
- Helps you articulate the gap your work addresses

## Writing Your Own Skills

1. **Start with a workflow you repeat.** If you've explained the same process to Claude Code more than twice, it's a candidate for a skill.

2. **Write the instructions as if for a smart new collaborator.** Be specific about steps, conventions, and quality standards. Include examples of good output. The goal is to externalize the tacit knowledge that makes your workflow yours.

3. **Build in user interaction.** The best research skills ask you questions rather than generating output autonomously. This keeps you in the thinking loop — which, as we argue in [Teach Me, Don't Do It For Me](teach-me-mindset.md), is where the real value lies.

4. **Include reference files.** If your skill needs to follow a style guide, consult a template, or check against a rubric, put those files in a `references/` subfolder alongside the skill. The more context the skill has, the better its output.

5. **Iterate.** Run the skill, see what it gets wrong, and refine the instructions. Skills improve with use — each revision encodes something you've learned about both the workflow and the tool.

## Sharing Skills

Because skills are just markdown files, they're straightforward to share:
- Post them in a GitHub repo (like this one — see `examples/skills/`)
- Share them with collaborators who use Claude Code
- Adapt someone else's skill to your own conventions

This is one of the ways agentic AI tools can make research workflows more transparent and reproducible. Your "methods" include not just your statistical approach but the documented process by which you engaged with the literature, managed your data, and structured your writing. Taken together, a well-maintained set of skills constitutes a kind of methodological appendix — one that another researcher can not only read but actually run.
