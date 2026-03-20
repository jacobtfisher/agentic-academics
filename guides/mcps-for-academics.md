---
title: "MCPs for Academics"
order: 4
category: tools
prerequisites: [getting-started]
---

# MCPs for Academics

Model Context Protocol (MCP) servers are what transform Claude Code from a text assistant that reads files and runs commands into something that can actually interact with your research tools. They're the bridge between AI and the software you already use — and for researchers, that bridge matters more than it might first appear.

## What Is an MCP?

An MCP server is a small program that gives Claude Code the ability to use specific external tools. Without MCPs, Claude Code can read files and run terminal commands. With MCPs, it can:

- Search your Zotero library and retrieve paper metadata
- Read and write notes in your Obsidian vault
- Query databases
- Interact with web APIs
- Connect to project management tools like Linear or Notion

Think of MCPs as plugins that extend what Claude Code can do. Each MCP exposes a set of *tools* — specific actions Claude Code can take. When you ask Claude Code something that requires one of these tools, it calls the MCP automatically.

## Why MCPs Matter for Research

Academic research involves a constellation of tools: reference managers, note-taking systems, data repositories, writing environments, collaboration platforms. These tools don't usually talk to each other. You manually copy citations from Zotero into your manuscript, manually cross-reference your notes with your reading list, manually check your project tracker against your calendar. The friction is low enough for any single task that it rarely feels worth solving, but it accumulates across the dozens of cross-tool operations that constitute a typical research day.

MCPs collapse that manual layer. They let Claude Code operate across your toolset in a single conversation — retrieving a citation from Zotero, checking it against a note in Obsidian, and incorporating both into a manuscript draft without you switching windows or copy-pasting between applications. In short, they turn a collection of isolated tools into something closer to an integrated research environment.

## Deep Dive: Zotero MCP

Zotero is the reference manager of choice for many academics, and the Zotero MCP is one of the most useful integrations for research workflows.

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

This last example is where the real value of tool integration becomes clear — see [Creating Serendipity](creating-serendipity.md) for a deeper treatment of how these cross-library searches can surface connections you wouldn't have found on your own.

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

If you use Obsidian for research notes, an Obsidian MCP lets Claude Code read, write, and search your vault. This integration is especially powerful for knowledge management workflows — Claude Code can find connections across hundreds of notes that you might not discover through manual browsing alone.

### Notion MCP

For labs or research groups that use Notion for project management, a Notion MCP lets Claude Code interact with your databases: query project statuses, update task lists, search meeting notes.

### Web Search / Fetch

MCPs that enable web access let Claude Code pull in information from the open web — useful for checking facts, finding recent preprints, or accessing documentation that isn't stored locally.

## Evaluating MCPs

Not all MCPs are equally mature or well-maintained. Before integrating one into your workflow, it's worth considering a few things:

1. **Check the source.** Is it maintained by a reputable organization or developer? Is the code open-source and auditable?
2. **Understand the permissions.** What data does the MCP access? Can it write and modify, or only read? Be cautious with MCPs that have write access to systems containing your research data.
3. **Test in a low-stakes context first.** Try the MCP on a test library or vault before pointing it at your actual research materials.
4. **Read the privacy policy.** Some MCPs may transmit data to external services. Understand where your data goes before connecting sensitive resources.

## Privacy Considerations

When you connect Claude Code to your research tools, you're giving it access to your work. A few things to keep in mind:

- **API keys are sensitive.** Store them securely. Don't commit them to version control.
- **Understand data flow.** When Claude Code queries your Zotero library, the query goes through the MCP server. Know what's processed locally and what hits external APIs.
- **Unpublished work.** If your Zotero library contains unpublished manuscripts or confidential review materials, be mindful of what you ask Claude Code to access and where that data travels.
- **Institutional policies.** Your university may have policies about AI tools accessing research data. Check before connecting sensitive systems — this is the kind of question your IRB or IT office can answer.

## Getting Started

1. Start with one MCP — Zotero is a natural first choice for most researchers.
2. Set it up, test it with simple queries, and get a feel for what it can do.
3. Add more MCPs as your workflow demands them. Don't try to connect everything at once — each integration is worth understanding on its own terms before layering on the next.
