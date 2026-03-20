# CLAUDE.md — Agentic Academics

This repo is a collection of guides, examples, and resources for academics using agentic AI tools in their research.

## Writing Style

- Write for an academic audience that is smart but not necessarily technical.
- Tone: clear, direct, collegial. Not corporate, not breathless about AI.
- Use concrete examples over abstract descriptions. Show what a workflow looks like, don't just describe the concept.
- Avoid hype. Acknowledge limitations and trade-offs honestly.
- When referencing tools or features, link to official documentation.

## Repo Structure

- `guides/` — standalone essays, each covering one topic. Frontmatter includes `order`, `category`, and `prerequisites` for future curriculum assembly.
- `examples/` — generalized templates (CLAUDE.md files, skills, MCP configs). These should be adaptable, not tied to any specific vault or project.
- `resources/` — curated links and reading lists.

## Guide Frontmatter

Every guide should include:

```yaml
---
title: "Guide Title"
order: N
category: foundations | workflows | tools | advanced
prerequisites: []
---
```

## Content Principles

1. **"Teach me" over "do this for me"** — this is the core philosophy. Every guide should reinforce it.
2. **Desirable difficulties matter** — don't present AI as eliminating struggle. Present it as redirecting your effort toward higher-order thinking.
3. **Tool-agnostic where possible** — lead with the principle, then show the Claude Code implementation. The ideas should outlast any specific tool.
4. **Generalize examples** — no personal vault paths, project names, or identifiable details in shared examples.
