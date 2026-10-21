# Legate plugin for Claude Code

One-click(ish) integration that lets you draft content and send it straight to your [Legate](https://legate.social) board from Claude Code. Bundles:

- the **Legate MCP server** (the `create_draft`, `list_accounts`, `list_campaigns` tools),
- a **`/legate-draft`** slash command,
- a **drafting-for-legate** skill so Claude knows the board model and defaults.

## Install

1. Create an API key: **legate.social → Team → API keys → Create key** (copy it — shown once; looks like `legate_sk_…`).
2. Add the plugin's marketplace, then install:

```bash
/plugin marketplace add Bartega/legate-plugin     # or a local path to this folder
/plugin install legate@legate
```

You'll be prompted for your API key at install (stored by Claude Code, sent as the `Authorization` header to the hosted MCP server).

### Try it locally first (no marketplace)

```bash
claude --plugin-dir /path/to/legate-plugin/legate
```

This loads the plugin for one session so you can test `/legate-draft` and the tools. (Point `--plugin-dir` at the inner `legate/` folder — the one containing `.claude-plugin/plugin.json` — not the marketplace root.)

## Use

```
/legate-draft a teaser about Arcline 2.0, for @arcline on the launch-week campaign
```

or just talk to Claude — "draft this and put it in my Legate inbox" — and it will use the tools. Omit an account/campaign and the draft lands in your **scratch inbox**; name both and it goes straight into that board column.

## Alternative: no plugin

The same MCP server is hosted, so you can skip the plugin entirely:

```bash
claude mcp add --transport http legate https://legate.social/api/mcp \
  --header "Authorization: Bearer legate_sk_..."
```

## Notes

- Nothing is ever posted publicly — Legate is a drafting board. The tools only create cards.
- Keys are workspace-scoped and revocable in **Team → API keys**.
