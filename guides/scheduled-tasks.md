---
title: "Scheduled Tasks and Automation"
order: 7
category: advanced
prerequisites: [skills-for-research, claude-md-as-memory]
---

# Scheduled Tasks and Automation

One of the most powerful (and least discussed) capabilities of agentic AI tools is the ability to run tasks on a schedule, without your direct involvement. The AI works while you sleep, while you teach, while you're in a meeting, and has results waiting when you return. For researchers managing multiple projects with overlapping deadlines and competing demands on attention, this amounts to a structural advantage.

## The Case for Automation in Research

Academic research involves a substantial amount of recurring maintenance work that is essential but rarely urgent enough to do in the moment: checking the status of data collections, scanning for upcoming deadlines, reviewing whether projects have gone stale, updating documentation, surfacing new connections in your notes. Left to manual effort, these tasks tend to happen inconsistently. You do them when you remember, which often means you do not do them until something breaks or a deadline arrives unexpectedly.

Scheduled tasks address this by converting maintenance work from something you need to remember into something that happens automatically. The AI performs the scan, generates a report, and places it where you'll see it. Your job shifts from doing the maintenance to reviewing the results, a much lighter cognitive load that can be folded into a morning routine rather than carved out as a separate work session.

## What Scheduled Tasks Can Do

The range of tasks amenable to automation is broader than it might initially seem. A few patterns that work well in research contexts:

### Daily Status Scans

A task that runs each morning and sweeps across your active projects, looking for:
- **Deadlines approaching** within the next 7-14 days
- **Projects that have gone stale** — no logged activity in 10+ days
- **Completions detected** — tasks or milestones checked off since the last scan
- **Overdue items** — target dates that have passed without resolution

The output is a structured summary placed in your daily note or a dashboard file, organized by urgency. When you sit down to plan your day, the scan has already done the triage. You are reviewing and deciding, not hunting through project files to reconstruct the current state of things.

### Research Note Generation

A task that runs periodically (daily or weekly) and populates your knowledge base with new research notes. The pattern:
1. Scan for "seed" material: recent annotations in Zotero, flagged ideas in your notes, keywords from active manuscripts
2. Search your reference library for related papers, especially ones you tagged but haven't thought about recently
3. Generate structured research notes that map the seed ideas to relevant literature

This is the automation layer beneath the serendipity workflow described in [Creating Serendipity](creating-serendipity.md). The scheduled task handles the encounter; you handle the judgment about what's worth pursuing.

### Weekly Rollups

A task that runs at the end of each week and generates a summary of activity across your projects and manuscripts:
- What moved forward this week
- What's still pending
- What deadlines are coming in the next two weeks
- Which projects haven't had any logged activity

This provides the raw material for a weekly review. The data is already gathered and organized, so the review itself can focus on reflection and priority-setting rather than information retrieval.

### Manuscript Status Tracking

A task that monitors your manuscripts (both those in progress and those under review) and flags status changes or approaching deadlines:
- Submission deadlines for conference papers
- Expected response windows for papers under review
- Revision deadlines after an R&R
- Co-author deliverables that are pending

## Designing Effective Scheduled Tasks

Not every recurring task benefits from automation, and poorly designed automated tasks can create noise rather than signal. A few principles worth observing:

### Automate the Scan, Not the Decision

The most effective scheduled tasks gather and organize information; they do not take action on your behalf. A task that scans your projects and reports "Reward Proximity Study has had no activity in 22 days" is useful. A task that automatically creates follow-up tasks or sends reminders to collaborators removes you from the judgment loop at exactly the point where judgment is most needed.

As such, the output of a scheduled task should be a report, not an action. Present the information clearly, flag what seems urgent, and let the human decide what to do about it.

### Design for Skimmability

Scheduled task output needs to be scannable in under a minute. If the report takes as long to read as the underlying work would take to do manually, the automation hasn't saved you anything. Effective formats include:
- **Categorized summaries** (completions, due soon, overdue, stale) rather than chronological lists
- **Priority ordering** — the most time-sensitive items at the top
- **Brief, specific language** — "NCA deadline in 5 days; abstract drafted but not submitted" tells you everything you need to know

### Fail Gracefully

Scheduled tasks run unattended, which means they encounter errors unattended. A well-designed task should handle common failure modes (a file moved, an MCP connection timing out, a project note with unexpected formatting) without crashing or producing misleading output. When something goes wrong, the task should report what it couldn't do rather than silently skip it.

### Keep the Task Scope Narrow

A task that tries to do too many things becomes hard to debug and hard to trust. Better to have several focused tasks (one for deadline scanning, one for research note generation, one for manuscript tracking) than a single monolithic task that does everything. Each task should have a clear purpose that you can describe in one sentence.

## Implementation

### Setting Up a Scheduled Task

In Claude Code, scheduled tasks are created using the `/schedule` command or through the scheduled tasks interface. A task consists of:

1. **A prompt** — the instructions for what the task should do (essentially a skill that runs unattended)
2. **A schedule** — when and how often it runs (daily at 8 AM, weekly on Mondays, etc.)
3. **Allowed tools** — which tools the task has permission to use (file read/write, MCP access, git commands, etc.)

A basic daily status scan might be configured as:

```
Schedule: Daily at 08:00
Prompt: "Scan all active project notes in 03 Projects/Active/. For each project,
check the target_date and due_status frontmatter fields. Categorize projects as:
completions detected (tasks checked off since yesterday), due soon (within 14 days),
overdue (target date passed), or stale (no logged activity in 10+ days). Write a
structured summary to today's daily note under '### Status Check (Auto)'."
Allowed tools: Read, Write, Glob, Grep
```

### Permissions and Security

Scheduled tasks run with a defined set of tool permissions. This is by design: you want to be explicit about what an unattended task can and cannot do. For most research automation:
- **Read access** to project notes and data files: yes
- **Write access** to specific output locations (daily notes, dashboards): yes
- **MCP access** (Zotero, Obsidian): yes, if the task needs to search your library
- **Git commands**: only if you want the task to commit its output automatically; otherwise, let changes accumulate for your manual review
- **Shell execution**: be cautious; limit to specific, well-understood commands

### Iterating on Task Design

Scheduled tasks benefit from the same iterative refinement as skills. Run the task manually a few times, review the output, and adjust the prompt until the reports are genuinely useful. Common refinements include:
- Adjusting what counts as "stale" (10 days? 14 days? depends on your workflow tempo)
- Tuning the deadline window (7 days out? 14? 30?)
- Refining the output format based on what you actually read vs. what you skip
- Adding or removing categories based on what turns out to be signal vs. noise

## What Automation Does Not Replace

Scheduled tasks handle the mechanical aspects of research maintenance: the scanning, the aggregating, the flagging. They do not replace the reflective practice that makes that information useful. A daily status scan tells you what's due and what's stale; it does not tell you what matters most or how to allocate your limited time.

The scheduled task is the preparation; the daily review conversation (see [the daily review skill template](../examples/skills/daily-review.md)) is where the thinking happens. Both are necessary. Automation without reflection produces reports no one reads. Reflection without automation produces plans based on incomplete information. The combination of automated scanning feeding into a structured, human-driven review is where the real value lies.
