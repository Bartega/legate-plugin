---
name: drafting-for-legate
description: How to draft content and send it to the user's Legate board via the Legate MCP tools (create_draft, list_accounts, list_campaigns). Use when the user asks to draft a post, tweet, or thread and put it on their board, or mentions Legate.
---

# Drafting for Legate

Legate is the user's content board. It has **accounts** (each a distinct voice / board column) and **campaigns** (boards). When the Legate MCP server is connected, three tools are available:

- `list_accounts` — the accounts (voices) in the workspace; each has a `key` and an `@handle` and a voice label.
- `list_campaigns` — the campaigns (boards); each has a `name` and an `id`.
- `create_draft` — send a draft onto the board.
  - **Omit `account` and `campaign`** → the draft lands in the **scratch inbox**, a staging area the user promotes to a board column by hand. This is the safe default whenever you're unsure where it belongs.
  - **Provide both** (`account` = key or `@handle`, `campaign` = name or id) → the draft drops straight into that board column.
  - Use `body` for a single post, or `thread` (an array of posts) for a thread.

## How to draft well

1. If the user names an account, match that account's voice — call `list_accounts` to see the options and their voice labels when you're unsure which to use.
2. Default to the scratch inbox unless the user clearly wants the draft on a specific account + campaign. The user stays in the loop.
3. Never invent live figures, prices, product names, or URLs. Leave a placeholder (e.g. `<TBD>`, `<LINK>`) when a real value isn't known — the board renders these as fill-before-posting chips.
4. Nothing is ever posted publicly. Legate is a drafting board, not a publisher — your job ends when the draft is on the board.

After creating a draft, tell the user its id, whether it went to the inbox or a named column, and the board link the tool returns.
