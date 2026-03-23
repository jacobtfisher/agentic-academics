# Setting Up Zotero MCP

This guide walks through connecting Claude Code to your Zotero reference library via the [Zotero MCP server](https://github.com/54yyyu/zotero-mcp).

## Prerequisites

- [Zotero 7+](https://www.zotero.org/) installed with a populated library
- Claude Code installed and working
- Python 3.10+ (for the MCP server)

## Step 1: Install the MCP Server

```bash
uv tool install zotero-mcp-server
```

Or via pip:

```bash
pip install zotero-mcp-server
```

For semantic search and PDF annotation extraction, install optional extras:

```bash
uv tool install "zotero-mcp-server[all]"
```

## Step 2: Run Setup

The built-in setup wizard auto-detects your Zotero installation and configures your MCP client:

```bash
zotero-mcp setup
```

The wizard will walk you through two choices:

1. **Local mode** (recommended for most researchers): reads directly from your Zotero database. No API key needed. Requires Zotero 7+ running on the same machine.
2. **Web API mode**: accesses your library through the Zotero API. Useful for remote setups or if you need cloud access. Requires an API key and library ID from [zotero.org/settings/keys](https://www.zotero.org/settings/keys).

If you choose local mode, make sure "Allow other applications on this computer to communicate with Zotero" is enabled in Zotero's preferences.

## Step 3: Manual Configuration (if needed)

If you prefer to configure manually rather than using the setup wizard, add the following to `~/.claude/mcp.json`:

**Local mode:**

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

**Web API mode:**

```json
{
  "mcpServers": {
    "zotero": {
      "command": "zotero-mcp",
      "env": {
        "ZOTERO_API_KEY": "your-api-key-here",
        "ZOTERO_LIBRARY_ID": "your-library-id-here"
      }
    }
  }
}
```

## Step 4: Test the Connection

Start a new Claude Code session and try:

```
> Search my Zotero library for papers about [topic you know is in your library]
```

If the connection is working, Claude Code will return matching items with metadata.

## What You Can Do

With Zotero connected, try:

- **Search by keyword:** "Find papers in my library about attention and social media"
- **Search by author:** "Do I have anything by Bjork in my library?"
- **Get metadata:** "What's the full citation for [paper title]?"
- **Browse collections:** "What's in my 'Dissertation' collection?"
- **Semantic search:** "Find papers related to the concept of desirable difficulties in learning"
- **Access annotations:** "What did I highlight in [paper title]?"
- **Add a paper:** "Add this paper to my library by DOI: 10.1234/example"
- **Manage collections:** "Create a new collection called 'Literature Review' and add these papers to it"

## Optional: Semantic Search Setup

If you installed with the `[semantic]` or `[all]` extra, configure semantic search during setup or separately:

```bash
zotero-mcp setup --semantic-config-only
```

Then build the search database:

```bash
zotero-mcp update-db            # Fast, metadata-only
zotero-mcp update-db --fulltext  # Comprehensive, includes full text
```

Embedding model options include a free local model (default), OpenAI, or Gemini.

## Privacy Notes

- In local mode, your library data stays on your machine. No API key is transmitted.
- In web API mode, queries go through the Zotero API. Treat your API key like a password.
- If your library contains sensitive materials (unpublished manuscripts, confidential reviews), be mindful of what you search for.
- Store API keys securely. Do not commit `mcp.json` to public repositories.

## Troubleshooting

- **"No results found"**: In local mode, make sure Zotero is running and local API access is enabled in preferences. In web API mode, check that your API key has read access to your personal library.
- **Connection errors**: For local mode, verify Zotero 7+ is running. For web API mode, verify your Library ID is correct (it is a number, not your username).
- **Slow responses**: Large libraries may take a moment to search. Semantic search is slower than keyword search.
- **Semantic search issues**: Run `zotero-mcp db-status` to check your database. If needed, rebuild with `zotero-mcp update-db --force-rebuild`.

See the [full documentation](https://stevenyuyy.us/zotero-mcp/) for additional configuration options and troubleshooting.
