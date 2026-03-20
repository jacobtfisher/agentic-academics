# Example Skill: Literature Note

This is a generalized template for a skill that creates structured notes from papers you've read. Adapt the questions and note structure to your own research workflow.

## How to Use

Save this as a `.md` file in `~/.claude/skills/` (or `.claude/skills/` in your project) and modify it to match your note-taking conventions.

---

```markdown
# Literature Note Skill

## Overview
Creates a structured research note from a paper the user has read or is reading.
Invoke when the user asks to process a paper, create a literature note, or
take notes on a reading.

## Process

### Step 1: Identify the Paper
Ask the user for the paper — they may provide a citation key, DOI, title, or
just describe it. If a Zotero MCP is available, search for the paper to retrieve
full metadata (authors, year, journal, abstract, DOI).

### Step 2: Ask the User About the Paper
Ask 3-4 questions to draw out the user's own thinking. Do NOT generate a
summary first — the user's interpretation comes before any AI synthesis.

Suggested questions (rotate and adapt based on context):
1. What is the paper's core argument or main finding?
2. How does this connect to your current work?
3. What surprised you, or what do you disagree with?
4. Are there methodological choices you'd question or do differently?
5. What's the most useful idea from this paper for your own research?

### Step 3: Generate the Note
Create a note using the template below. Fill in metadata from Zotero (if
available) and the user's answers from Step 2.

### Step 4: Ask About Connections
After generating the note, ask: "Are there specific projects, manuscripts,
or other notes this should be linked to?" Add any connections the user mentions.

## Note Template

# [Authors] ([Year]) — [Short Descriptive Title]

## Metadata
- **Full Title:** [full title]
- **Authors:** [author list]
- **Journal:** [journal name]
- **Year:** [year]
- **DOI:** [doi if available]

## Summary
[2-3 sentences synthesizing the paper's contribution, drawn primarily from
the user's description in Step 2, supplemented by abstract if needed]

## Key Arguments / Findings
[Bullet points from the user's answers — what they identified as core]

## Connections to My Work
[How this paper relates to the user's projects, drawn from Step 2 Q&A]

## Critical Notes
[Methodological concerns, disagreements, limitations — from the user's answers]

## Quotes / Key Passages
[Leave empty — the user fills this in as they read or re-read]

## Related
[Links to other notes, projects, or papers mentioned in Step 4]

## Important Rules
- Always get the user's interpretation BEFORE generating content
- Do not fabricate citations or invent paper details
- If Zotero metadata is unavailable, ask the user to provide basics
- The note should reflect the USER's reading, not a generic summary
```
