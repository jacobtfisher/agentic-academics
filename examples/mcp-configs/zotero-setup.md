# Setting Up Zotero MCP

This guide walks through connecting Claude Code to your Zotero reference library via the Zotero MCP server.

## Prerequisites

- [Zotero](https://www.zotero.org/) installed with a populated library
- A Zotero account (free at zotero.org)
- Claude Code installed and working
- Node.js 18+

## Step 1: Get Your Zotero API Credentials

1. Go to [zotero.org/settings/keys](https://www.zotero.org/settings/keys)
2. Click "Create new private key"
3. Give it a descriptive name (e.g., "Claude Code MCP")
4. Under "Personal Library," grant **read access** (write access is optional and should be granted cautiously)
5. Save the key — you'll need it in Step 3
6. Note your **User ID** from the [Feeds/API settings page](https://www.zotero.org/settings/keys)

## Step 2: Install the MCP Server

Check the [zotero-mcp repository](https://github.com/anthropics/zotero-mcp) for the most current installation instructions. Typically:

```bash
npm install -g zotero-mcp
```

Or you can run it via `npx` without global installation (shown in the config below).

## Step 3: Configure Claude Code

Add the Zotero MCP to your Claude Code configuration. Edit (or create) `~/.claude/mcp.json`:

```json
{
  "mcpServers": {
    "zotero": {
      "command": "npx",
      "args": ["zotero-mcp"],
      "env": {
        "ZOTERO_API_KEY": "your-api-key-here",
        "ZOTERO_USER_ID": "your-user-id-here"
      }
    }
  }
}
```

Replace the placeholder values with your actual API key and user ID.

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

## Privacy Notes

- Your Zotero API key grants access to your library's metadata and notes. Treat it like a password.
- Queries go through the Zotero API — your library data is transmitted to retrieve results.
- If your library contains sensitive materials (unpublished manuscripts, confidential reviews), be mindful of what you search for.
- Store your API key securely. Do not commit `mcp.json` to public repositories.

## Troubleshooting

- **"No results found"** — Check that your API key has read access to your personal library. Try searching for a paper you know exists by exact title.
- **Connection errors** — Verify your User ID is correct (it's a number, not your username). Check that `npx` can run the package.
- **Slow responses** — Large libraries may take a moment to search. Semantic search is slower than keyword search.
