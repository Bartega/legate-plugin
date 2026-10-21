---
description: Draft content and send it to your Legate board (scratch inbox by default)
argument-hint: [what to draft; optionally "for @account on <campaign>"]
---

The user wants to draft content and send it to their Legate board using the Legate MCP tools (`create_draft`, `list_accounts`, `list_campaigns`).

Request: $ARGUMENTS

Do this:

1. Write the draft. If the user named an account, match that account's voice — call `list_accounts` if you need to see the accounts and their voice labels. For a multi-post thread, prepare an array of posts.
2. Send it with `create_draft`:
   - If the user named BOTH an account and a campaign, pass them (call `list_campaigns` for the exact name/id) so the draft lands in that board column.
   - Otherwise omit `account` and `campaign` so it lands in the **scratch inbox** for the user to place themselves.
   - Use `thread` for a multi-post thread, `body` for a single post.
3. Report the draft id, whether it landed in the inbox or a specific column, and the board link the tool returns.

Rules: never post anything publicly — Legate is a drafting board, not a publisher. Never invent live numbers, prices, or URLs; leave a placeholder like `<TBD>` when a real value isn't known.
