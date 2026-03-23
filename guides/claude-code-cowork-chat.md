---
title: "Claude Code, Cowork, and Chat"
order: 2.5
category: foundations
prerequisites: []
---

# Claude Code, Cowork, and Chat

Claude is available through several interfaces, and the distinctions among them matter more than they might first appear. Each mode has a different relationship to your files, your tools, and the kind of work it can do. Choosing the right one for a given task is itself a skill worth developing.

## Chat (claude.ai / Desktop App)

This is what most people mean when they say "I used Claude." You open a browser or the desktop app, type a message, and get a response. Chat is conversational: you provide context in the message, Claude responds, and the exchange lives entirely within that conversation window.

**What it can do:**
- Answer questions, explain concepts, brainstorm ideas
- Analyze text, images, or documents you paste or upload into the conversation
- Write and edit prose, generate code snippets, summarize papers
- Engage in extended back-and-forth dialogue

**What it cannot do:**
- Read or write files on your computer
- Run code or terminal commands
- Interact with external tools (Zotero, Obsidian, databases)
- Maintain persistent context across sessions (beyond what the conversation window holds)

**When to use it:** Chat is the right tool for quick, self-contained interactions. If you want to brainstorm a study design, get feedback on a paragraph, talk through an analytical approach, or ask a factual question, chat is fast and requires no setup. It is the intellectual equivalent of a hallway conversation: low overhead, no commitments.

**Limitations for research:** The constraint is that chat has no access to your working environment. Every piece of context — your data, your notes, your manuscript draft — must be manually pasted or uploaded into the conversation. For short interactions this is fine. For sustained project work, it becomes a bottleneck.

## Claude Code (Terminal / Desktop App)

Claude Code operates directly in your file system. It can read your project files, write new ones, run scripts, execute terminal commands, and interact with external tools through MCPs. It's scoped to a working directory, and it reads your CLAUDE.md file at the start of every session.

**What it can do (beyond chat):**
- Read and write files in your project directory
- Run code, install packages, execute shell commands
- Connect to external tools via MCPs (Zotero, Obsidian, databases, web APIs)
- Use skills — reusable multi-step workflows invoked with slash commands
- Schedule automated tasks
- Maintain project-level memory through CLAUDE.md

**When to use it:** Claude Code is the right tool for sustained project work, anything that involves your actual files, your actual data, and your actual tools. Manuscript revision, data analysis, literature management, project tracking, workflow automation. If you find yourself copying and pasting content between your files and a chat window, that's a signal you should be working in Claude Code instead.

**Access:** Available both through the terminal (for those comfortable with command-line tools) and through the Claude desktop app (for a more graphical experience). See [Getting Started](getting-started.md) for installation details.

## Cowork (Desktop App)

Cowork is a collaborative mode available in the Claude desktop app that allows Claude to work alongside you on extended tasks. Where a standard chat is turn-by-turn (you say something, Claude responds, you say something else), Cowork gives Claude the ability to work more autonomously on a task (researching, drafting, iterating) while you continue with other work or check in periodically.

**What it adds beyond standard Claude Code:**
- Claude can work on longer tasks with greater autonomy
- You can check in on progress, redirect, or provide feedback as it works
- Multiple workstreams can run in parallel
- The interface is designed for collaboration rather than sequential conversation

**When to use it:** Cowork is well suited to tasks that require sustained effort but do not require your continuous input: a first pass at a literature search, drafting boilerplate sections of a grant application, reorganizing a set of notes, running a series of analyses with iterative refinement. The key distinction is autonomy: Cowork is for tasks where you trust Claude to make reasonable intermediate decisions and want to review the output rather than supervise every step.

**A caveat aligned with the "teach me" mindset:** Cowork's autonomy is a feature that warrants careful use. For mechanical tasks (formatting, data wrangling, file organization), extended autonomy is appropriate and efficient. For intellectual tasks (argumentation, interpretation, research design), you'll want to stay closer to the conversation — checking in frequently, redirecting when needed, and ensuring that the thinking remains yours. The [Teach Me, Don't Do It For Me](teach-me-mindset.md) principles apply with particular force when a tool is capable of working without you.

## Choosing the Right Mode

| Task | Best Mode | Why |
|------|-----------|-----|
| Quick question about a concept | Chat | No file access needed, low overhead |
| Feedback on a paragraph you're drafting | Chat | Paste the text, get a response, move on |
| Analyzing a dataset in your project | Claude Code | Needs file access and the ability to run scripts |
| Building a literature note from a Zotero paper | Claude Code | Requires MCP integration |
| Running your daily review skill | Claude Code | Uses skills, reads project notes, writes output |
| First-pass draft of a grant budget justification | Cowork | Sustained task, mostly mechanical, review output after |
| Reorganizing 50 research notes | Cowork | File-heavy, benefits from autonomy with periodic check-ins |
| Designing a new study | Chat or Claude Code | Start in chat for brainstorming, move to Claude Code when you need to reference your existing data and notes |

The modes are not mutually exclusive, and you'll likely find yourself moving between them as a task evolves. The general trajectory for research work tends to be: start in chat for early-stage thinking, move to Claude Code once the work involves your actual files and tools, and use Cowork for well-defined tasks that benefit from sustained, semi-autonomous effort.

## A Note on Subscriptions

As of this writing, Claude Code is available through Claude Pro and Max subscriptions, as well as through direct API access. Chat is available at all tiers, including the free tier (with usage limits). Cowork is available through the desktop app for Pro and Max subscribers. Check [Anthropic's pricing page](https://www.anthropic.com/pricing) for current details, as these tiers evolve.
