---
title: "MCPs for Academics"
order: 4
category: tools
prerequisites: [getting-started]
---

# MCPs for Academics

Model Context Protocol (MCP) servers are what turn Claude Code from a smart text assistant into something that can actually interact with your research tools. They're the bridge between AI and the software you already use.

## What Is an MCP?

An MCP server is a small program that gives Claude Code the ability to use specific tools. Without MCPs, Claude Code can read files and run terminal commands. With MCPs, it can:

- Search your Zotero library and retrieve paper metadata
- Read and write notes in your Obsidian vault
- Query databases
- Interact with web APIs
- Connect to project management tools like Linear or Notion

Think of MCPs as plugins that extend what Claude Code can do. Each MCP exposes a set of *tools* — specific actions Claude Code can take. When you ask Claude Code something that requires one of these tools, it calls the MCP automatically.

## Why MCPs Matter for Research

Academic research involves a constellation of tools: reference managers, note-taking systems, data repositories, writing environments, collaboration platforms. These tools don't usually talk to each other. You manually copy citations from Zotero into your manuscript, manually cross-reference your notes with your reading list, manually check your project tracker against your calendar.

MCPs collapse that manual layer. They let Claude Code operate across your toolset in a single conversation.

## Deep Dive: Zotero MCP

Zotero is the reference manager of choice for many academics, and `zotero-mcp` is one of the most useful MCPs for research workflows.

### What It Enables

With Zotero connected, Claude Code can:

- **Search your library** by author, title, keyword, or tag
- **Retrieve full metadata** for any item (authors, abstract, journal, year, DOI)
- **Access annotations and notes** you've made on papers
- **Perform semantic search** — find papers related to a concept, not just matching a keyword
- **Browse collections** you've organized in Zotero

### Example Interactions

**Finding relevant literature:**
```
> I'm writing a section on how reward learning drives habitual media use.
> Search my Zotero library for papers that connect reward, habit, and
> media selection.
```

Claude Code searches your library, returns relevant hits, and can summarize the abstracts or your annotations to help you decide what to cite.

**Building a reference list:**
```
> Based on the papers we've been discussing, generate a bibliography
> in APA format for the ones I should cite in this section.
```

**Discovering connections:**
```
> I just read [Author 2024]. Are there papers in my library that
> make a similar argument from a different theoretical tradition?
```

This is where the "creating serendipity" angle comes in — see [Creating Serendipity](creating-serendipity.md).

### Setting Up Zotero MCP

1. Make sure Zotero is installed and your library is populated
2. Install the MCP server (check the [zotero-mcp repository](https://github.com/anthropics/zotero-mcp) for current instructions)
3. Add the server to your Claude Code MCP configuration (`~/.claude/mcp.json`)

A basic configuration looks like:

```json
{
  "mcpServers": {
    "zotero": {
      "command": "npx",
      "args": ["zotero-mcp"],
      "env": {
        "ZOTERO_API_KEY": "your-api-key",
        "ZOTERO_USER_ID": "your-user-id"
      }
    }
  }
}
```

Your API key and user ID are available in your Zotero account settings at [zotero.org/settings](https://www.zotero.org/settings).

## Other MCPs for Academic Work

### Obsidian MCP

If you use Obsidian for research notes, an Obsidian MCP lets Claude Code read, write, and search your vault. This is especially powerful for knowledge management workflows — Claude Code can find connections across hundreds of notes that you might not discover on your own.

### Notion MCP

For labs or research groups using Notion for project management, a Notion MCP lets Claude Code interact with your databases: query project statuses, update task lists, search meeting notes.

### Web Search / Fetch

MCPs that enable web access let Claude Code pull in information from the open web — useful for checking facts, finding recent preprints, or accessing documentation.

## Evaluating MCPs

Not all MCPs are equally mature or well-maintained. When considering an MCP:

1. **Check the source.** Is it maintained by a reputable organization or developer? Is the code open-source?
2. **Understand the permissions.** What data does the MCP access? Can it write/modify, or only read? Be cautious with MCPs that have write access to important systems.
3. **Test in a low-stakes context first.** Try the MCP on a test library or vault before pointing it at your real research data.
4. **Read the privacy policy.** Some MCPs may transmit data to external services. Understand where your data goes.

## Privacy Considerations

When you connect Claude Code to your research tools, you're giving it access to your work. A few things to keep in mind:

- **API keys are sensitive.** Store them securely. Don't commit them to version control.
- **Understand data flow.** When Claude Code queries your Zotero library, the query goes through the MCP server. Know what's local and what hits external APIs.
- **Unpublished work.** If your Zotero library contains unpublished manuscripts or confidential review materials, be mindful of what you ask Claude Code to access.
- **Institutional policies.** Your university may have policies about AI tools accessing research data. Check before connecting sensitive systems.

## Getting Started

1. Start with one MCP — Zotero is a natural first choice for most researchers.
2. Set it up, test it with simple queries, and get a feel for what it can do.
3. Add more MCPs as your workflow demands them. Don't try to connect everything at once.
