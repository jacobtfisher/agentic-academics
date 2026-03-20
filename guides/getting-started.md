---
title: "Getting Started with Claude Code"
order: 2
category: foundations
prerequisites: []
---

# Getting Started with Claude Code

This guide walks you through installing Claude Code, having your first conversation, and building a mental model for what agentic AI tools can do in a research context. By the end, you'll have a working setup and enough orientation to start using it on real projects.

## What Is Claude Code?

Claude Code is a command-line AI assistant that can read and write files, run commands, search your project, and interact with external tools. Unlike a chatbot in a browser window, it operates directly in your working environment — your project folders, your terminal, your existing toolchain.

For researchers, this means it can:
- Read your manuscripts, data files, and notes
- Write and run analysis scripts
- Search your reference library (with the right integrations)
- Help you manage complex, multi-file projects
- Automate repetitive workflows

It's not a chatbot you visit. It's a collaborator that sits in your workspace.

## Installation

### Prerequisites
- A terminal (macOS Terminal, iTerm2, Windows Terminal, or any Linux terminal)
- Node.js 18+ installed ([download here](https://nodejs.org/))
- An Anthropic API key or a Claude Pro/Max subscription

### Install

```bash
npm install -g @anthropic-ai/claude-code
```

### First Launch

Navigate to any project directory and type:

```bash
claude
```

That's it. You're in a conversation with Claude Code, scoped to whatever directory you're in.

## Your First Conversation

Start simple. Navigate to a folder containing some of your work — a manuscript draft, a data analysis project, an R or Python script — and ask Claude Code about it.

```
> What's in this directory? Give me an overview of the project.
```

Claude Code will read your files and provide a summary. From there, you might try:

- "What does this R script do? Walk me through the analysis steps."
- "I'm working on a manuscript about [topic]. Read the draft and tell me where the argument is weakest."
- "Help me think through the design for a new study on [topic]."

Notice the phrasing. You're asking it to *help you think*, not to *produce something for you*. (See [Teach Me, Don't Do It For Me](teach-me-mindset.md) for why this distinction matters.)

## Key Concepts

### The Working Directory

Claude Code is always scoped to a directory. It can read files in that directory and its subdirectories, create new files, and run commands. When you start a session, think about where you want to be working.

```bash
cd ~/research/my-project
claude
```

### CLAUDE.md — Your Project's Memory

If you place a file called `CLAUDE.md` in your project root, Claude Code reads it at the start of every conversation. This is where you describe your project: what the files are, what conventions you follow, what to watch out for. Think of it as onboarding documentation for your AI collaborator — the kind of briefing you'd give a new research assistant on their first day.

See [CLAUDE.md as Institutional Memory](claude-md-as-memory.md) for a deep dive.

### Skills — Reusable Workflows

Skills are saved prompts that encode complex, multi-step workflows. Rather than re-explaining your literature note process or your data cleaning protocol every session, you write it once as a skill and invoke it with a slash command. The result is both a time-saver and a form of documentation — a shareable record of how your workflow actually operates.

See [Skills for Research](skills-for-research.md) for details.

### MCPs — Tool Connections

Model Context Protocol (MCP) servers let Claude Code interact with external tools: your Zotero library, your Obsidian vault, web APIs, databases. They transform Claude Code from a text assistant into something that can operate across your research ecosystem — searching your references, querying your notes, and pulling in information from the tools you already use.

See [MCPs for Academics](mcps-for-academics.md) for details.

## Tips for Your First Week

1. **Start in a real project.** Don't create a toy folder to experiment with. Open Claude Code in a manuscript directory or analysis project you're actively working on. The value becomes obvious faster when the stakes are real.

2. **Ask it to explain, not just do.** When Claude Code writes code or suggests an approach, ask *why*. "Why did you choose that statistical test?" "What are the alternatives here?" This builds your understanding and catches mistakes early.

3. **Create a CLAUDE.md early.** Even a few lines — "This is a manuscript about X. The data is in /data. I use R for analysis." — will dramatically improve the quality of Claude Code's responses. Context is everything.

4. **Don't fight the terminal.** If you're not accustomed to command-line tools, there's a small learning curve. With that said, Claude Code itself can help you navigate — ask it to explain commands, find files, or troubleshoot errors. The tool teaches you how to use the tool.

5. **Review everything.** AI makes mistakes. It will occasionally hallucinate a citation, introduce a bug in code, or misunderstand your intent. Treat its output the way you'd treat a draft from a new research assistant: promising but in need of verification.

## Learning Resources

- [Anthropic's Claude Code documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Anthropic courses on Skilljar](https://anthropic.skilljar.com/) — structured courses on prompting and tool use
- [Claude Code GitHub](https://github.com/anthropics/claude-code) — source, issues, community discussion

## Next Steps

Once you're comfortable with basic conversations, explore:
- [Skills for Research](skills-for-research.md) — automate your recurring workflows
- [MCPs for Academics](mcps-for-academics.md) — connect Claude Code to your tools
- [CLAUDE.md as Institutional Memory](claude-md-as-memory.md) — teach Claude Code how your project works
