# Example Skill: Daily Research Review

This is a generalized template for a skill that runs a daily check-in on your research projects and helps you plan your day. Adapt the questions and structure to your own workflow.

---

```markdown
# Daily Research Review Skill

## Overview
Runs a morning check-in that scans project status, surfaces pending items,
and helps the user set intentions for the day. Invoke when the user asks for
a daily review, morning check-in, or daily planning session.

## Process

### Step 1: Scan Context
Read the user's recent notes (last 3-5 days) and active project files.
Look for:
- Unfinished tasks or follow-ups mentioned
- Upcoming deadlines (next 7-14 days)
- People the user said they needed to contact
- Research projects with pending next steps
- Items that have been carrying forward without resolution

### Step 2: Ask the User
Present what you found, then ask 3-5 questions drawn from this pool
(rotate daily — don't ask the same questions every day):

**Research & Projects**
- You have [N] active projects. Which one do you want to focus on today?
- What's the single most important research task you could do today?
- [If deadline is near]: [Project] is due in [N] days — where do things stand?

**Communications**
- Who do you owe a response to?
- Any meetings today you need to prepare for?

**Teaching** (if applicable)
- Any teaching tasks on your plate today?

**Energy & Intentions**
- How are you feeling today? What kind of work day do you want to have?
- What would make today feel like a success?

### Step 3: Generate the Daily Note
Create a structured daily note with:

## Template

# [Date]

## Today's Focus
[2-3 bullet points summarizing the user's main intentions from the Q&A]

## Tasks
[3-5 actionable items derived from the conversation, with relevant
project/person references]

## Carry-Forward
[Items from recent notes that haven't been resolved yet]

## Notes
[Any additional context from the conversation]

## Important Rules
- Keep tasks at a high level — one task per distinct action, not a
  granular checklist
- Always ask the user about their priorities — don't just generate
  a task list from scanning notes
- Reference specific projects and people by name
- If the user mentions something they explicitly do NOT want to work
  on today, respect that
```
