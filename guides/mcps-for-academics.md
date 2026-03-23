---
title: "MCPs for Academics"
order: 4
category: tools
prerequisites: [getting-started]
---

# MCPs for Academics

Model Context Protocol (MCP) servers are what transform Claude Code from a text assistant that reads files and runs commands into something that can actually interact with your research tools. They serve as the bridge between AI and the software you already use, and for researchers, that bridge matters more than it might first appear.

## What Is an MCP?

An MCP server is a small program that gives Claude Code the ability to use specific external tools. Without MCPs, Claude Code can read files and run terminal commands. With MCPs, it can:

- Search your Zotero library and retrieve paper metadata
- Read and write notes in your Obsidian vault
- Query databases
- Interact with web APIs
- Connect to project management tools like Linear or Notion

Think of MCPs as plugins that extend what Claude Code can do. Each MCP exposes a set of *tools*, specific actions Claude Code can take. When you ask Claude Code something that requires one of these tools, it calls the MCP automatically.

## Why MCPs Matter for Research

Academic research involves a constellation of tools: reference managers, note-taking systems, data repositories, writing environments, collaboration platforms. These tools don't usually talk to each other. You manually copy citations from Zotero into your manuscript, manually cross-reference your notes with your reading list, manually check your project tracker against your calendar. The friction is low enough for any single task that it rarely feels worth solving, but it accumulates across the dozens of cross-tool operations that constitute a typical research day.

MCPs collapse that manual layer. They let Claude Code operate across your toolset in a single conversation, retrieving a citation from Zotero, checking it against a note in Obsidian, and incorporating both into a manuscript draft without you switching windows or copy-pasting between applications. In short, they turn a collection of isolated tools into something closer to an integrated research environment.

## Deep Dive: Zotero MCP

Zotero is the reference manager of choice for many academics, and the Zotero MCP is one of the most useful integrations for research workflows.

### What It Enables

With Zotero connected, Claude Code can:

- **Search your library** by author, title, keyword, or tag
- **Retrieve full metadata** for any item (authors, abstract, journal, year, DOI), with BibTeX export
- **Access annotations and notes** you have made on papers, including direct PDF annotation extraction
- **Perform semantic search** using AI-powered embeddings to find papers related to a concept, not just matching a keyword
- **Browse collections** you have organized in Zotero
- **Add papers by DOI or URL** with automatic metadata fetching and open-access PDF attachment
- **Manage your library**: create collections, update metadata, batch-update tags, find and merge duplicates

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

This last example is where the real value of tool integration becomes clear. See [Creating Serendipity](creating-serendipity.md) for a deeper treatment of how these cross-library searches can surface connections you wouldn't have found on your own.

### Setting Up Zotero MCP

1. Make sure Zotero 7+ is installed and your library is populated
2. Install the MCP server (see the [zotero-mcp repository](https://github.com/54yyyu/zotero-mcp) for full documentation):

```bash
uv tool install zotero-mcp-server
```

3. Run the setup command, which auto-detects your Zotero installation and configures your MCP client:

```bash
zotero-mcp setup
```

The setup wizard will walk you through choosing between local mode (reads directly from your Zotero database, no API key needed) and web API mode (accesses your library through the Zotero API). Local mode is the simplest option for most researchers and provides full-text access.

If you prefer to configure manually, add the following to your Claude Code MCP configuration (`~/.claude/mcp.json`):

```json
{
  "mcpServers": {
    "zotero": {
      "command": "zotero-mcp",
      "env": {
        "ZOTERO_LOCAL": "true"
      }
    }
  }
}
```

For web API access instead, replace the env block with your API key and library ID from [zotero.org/settings](https://www.zotero.org/settings).

Semantic search is available as an optional extra (`uv tool install "zotero-mcp-server[semantic]"`) and supports local embeddings as well as OpenAI and Gemini models. See the [project documentation](https://stevenyuyy.us/zotero-mcp/) for details.

## Deep Dive: Scholar Gateway

If Zotero MCP gives Claude Code access to your personal library, Scholar Gateway gives it access to the publisher's. Developed by Wiley, Scholar Gateway is an MCP connector that provides semantic search across more than three million peer-reviewed articles spanning over 1,300 journals, from the sciences and healthcare to business, law, and the humanities.

The distinction from Zotero matters. Zotero searches what you've already collected. Scholar Gateway searches what's out there. The two are complementary in practice: you might use Scholar Gateway to discover literature you haven't encountered yet, then use Zotero to check whether it connects to work you've already read and annotated. That pairing of discovery and integration is where the real value lies.

### What It Enables

With Scholar Gateway connected, Claude Code can:

- **Semantic search across Wiley's corpus**: find passages based on meaning, not just keyword matching
- **Surface relevant literature you have not encountered**, especially when working across disciplinary boundaries
- **Retrieve citation metadata and DOI links** for anything it finds
- **Access full article text** (text-only; images, graphs, and charts are excluded)

### Example Interactions

**Exploring unfamiliar territory:**
```
> I'm writing a section on attentional capture in advertising contexts.
> Search Scholar Gateway for recent work on how reward-associated stimuli
> affect visual attention — especially outside the cognitive psychology
> literature.
```

**Cross-disciplinary discovery:**
```
> I found a useful framework in [Author 2023] about information foraging.
> Are there papers in Wiley's catalog that apply similar ideas to social
> media news consumption?
```

**Pairing with Zotero:**
```
> Search Scholar Gateway for recent work on doomscrolling and habit formation.
> Then check my Zotero library — do I already have any of these, and what
> annotations did I make?
```

### Setting Up Scholar Gateway

Scholar Gateway connects via MCP using OAuth authentication:

1. You will need a Wiley CONNECT account. You can create one with your institutional or personal email at [connect.wiley.com](https://connect.wiley.com)
2. Add the MCP server to your Claude Code configuration:

```json
{
  "mcpServers": {
    "scholar-gateway": {
      "type": "url",
      "url": "https://connector.scholargateway.ai/mcp"
    }
  }
}
```

3. When Claude Code first attempts to use Scholar Gateway, it will prompt you to authenticate through your browser
4. Institutional subscribers get full access; a free trial with limited access is also available for researchers with valid institutional affiliations

### Limitations Worth Noting

Scholar Gateway covers Wiley's catalog, which is substantial but not exhaustive. It won't surface work published by Elsevier, Springer, or in open-access repositories. As such, it's best understood as one search surface among several rather than a replacement for a comprehensive literature review. The text-only processing also means you won't see figures or tables from papers — useful for finding and reading arguments, less so for evaluating empirical results that depend on visual presentation.

With that said, for researchers working in areas where Wiley journals are prominent (and there are many such areas), it meaningfully lowers the barrier between having a research question and finding relevant published work to engage with.

## Open-Source Literature Search MCPs

Scholar Gateway is useful but limited to Wiley's catalog. A growing ecosystem of open-source MCP servers connects Claude Code to broader academic databases: CrossRef, OpenAlex, Semantic Scholar, arXiv, PubMed, and others. These are community-built, free to use, and in many cases surprisingly capable.

Three stand out as of early 2026.

### paper-search-mcp

The most comprehensive single server. It provides unified search across more than twenty sources: arXiv, PubMed, Semantic Scholar, CrossRef, OpenAlex, SSRN, bioRxiv, CORE, Europe PMC, DOAJ, and others. Rather than installing separate servers for each database, paper-search-mcp aggregates them behind a single interface.

The practical value here is coverage. CrossRef and OpenAlex index broadly across disciplines, which means social science, humanities, and interdisciplinary work is well-represented, not just STEM. For researchers whose literature spans multiple fields (or who simply want to cast a wide net), this is the strongest option available.

```bash
uv tool install paper-search-mcp
```

Then add to your MCP configuration:

```json
{
  "mcpServers": {
    "paper-search": {
      "command": "paper-search-mcp"
    }
  }
}
```

- **GitHub:** [openags/paper-search-mcp](https://github.com/openags/paper-search-mcp)
- **Stars:** 870+ | Actively maintained

### arxiv-mcp-server

The most popular single-source academic MCP server, with over 2,400 stars. It does one thing well: search, download, and store arXiv preprints. It includes built-in research prompts and local paper storage, so Claude Code can retrieve a paper once and reference it across conversations.

If your work intersects with computational social science, natural language processing, or any field where arXiv preprints circulate before (or instead of) journal publication, this is worth having. For fields that don't use arXiv heavily, it's less essential.

```bash
uv tool install arxiv-mcp-server
```

- **GitHub:** [blazickjp/arxiv-mcp-server](https://github.com/blazickjp/arxiv-mcp-server)

### Semantic Scholar MCP

Semantic Scholar (maintained by the Allen Institute for AI) is one of the better free academic search APIs, and several MCP servers provide access to it. The most fully-featured implementation offers paper search, author lookup, citation network traversal, and paper recommendations based on a seed paper.

Citation network traversal is the distinctive feature here. You can give Claude Code a paper and ask it to map what cites it, what it cites, and where the clusters of influence are. This is the kind of bibliometric exploration that's tedious to do manually but genuinely useful when scoping a new area or checking whether you've missed something.

A free API key is required (available at [semanticscholar.org](https://www.semanticscholar.org/product/api)).

- **GitHub:** [zongmin-yu/semantic-scholar-fastmcp-mcp-server](https://github.com/zongmin-yu/semantic-scholar-fastmcp-mcp-server)

### The Publisher Landscape

It is worth noting that Wiley is currently the only major publisher offering an MCP connector. As of early 2026, no MCP server exists from Elsevier, Springer Nature, Taylor & Francis, SAGE, Oxford UP, Cambridge UP, IEEE, ACM, or Clarivate (Web of Science). Scopus and JSTOR have unofficial community-built access through smaller projects, but nothing robust. This will almost certainly change, but for now, open databases like CrossRef, OpenAlex, and Semantic Scholar provide the broadest coverage for researchers working outside Wiley's catalog.

## Other MCPs for Academic Work

### Obsidian MCP

If you use Obsidian for research notes, an Obsidian MCP lets Claude Code read, write, and search your vault. This integration is especially powerful for knowledge management workflows. Claude Code can find connections across hundreds of notes that you might not discover through manual browsing alone.

### Notion MCP

For labs or research groups that use Notion for project management, a Notion MCP lets Claude Code interact with your databases: query project statuses, update task lists, search meeting notes.

### Web Search / Fetch

MCPs that enable web access let Claude Code pull in information from the open web, useful for checking facts, finding recent preprints, or accessing documentation that isn't stored locally.

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
- **Institutional policies.** Your university may have policies about AI tools accessing research data. Check before connecting sensitive systems. This is the kind of question your IRB or IT office can answer.

## Getting Started

1. Start with one MCP. Zotero is a natural first choice for most researchers.
2. Set it up, test it with simple queries, and get a feel for what it can do.
3. Add more MCPs as your workflow demands them. Do not try to connect everything at once. Each integration is worth understanding on its own terms before layering on the next.
