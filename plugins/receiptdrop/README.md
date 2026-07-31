# ReceiptDrop for Codex

This plugin exposes a local ReceiptDrop MCP server to Codex.

## Account connection

On first use, ask Codex to connect ReceiptDrop. Codex returns a secure
ReceiptDrop authorization link. Sign in in the browser and choose **Allow
access**. The ReceiptDrop completion page provides a single-use callback URL;
copy it back to Codex to finish the PKCE exchange. The local MCP then identifies
the account automatically and saves the OAuth access and refresh tokens at:

```text
/private/tmp/receiptdrop/config.json
```

Codex permits its sandboxed local MCP to write this location. The file is
created with mode `0600`, and tokens are refreshed automatically. If macOS
cleans the temporary directory, reconnect ReceiptDrop.
`RECEIPTDROP_USER_ID` and `RECEIPTDROP_API_TOKEN` remain supported as optional
environment overrides for advanced or legacy setups.

## Included tools

- `search_receipts`
- `find_business_trip_receipts`
- `get_receipt_attachment`
- `get_recent_uploads`
- `get_account_quota`
- `upload_receipts`
- `update_receipt`
- `generate_expense_package`
- `connect_receiptdrop`
- `complete_receiptdrop_connection`
- `configure_receiptdrop_user`

`update_receipt` supports the editable v2.3.8 receipt fields: buyer, seller,
invoice date, category, total, currency, invoice number, address, original
information, OCR text, hash ID, and creation time. Its `note` convenience
parameter is prepended to the existing `address` with a ` | ` separator. This
keeps the original address intact while making the note searchable through
`search_receipts`.

`search_receipts` returns the receipt attachment URL when present.
`get_receipt_attachment` verifies a selected receipt, downloads it once to the
local temporary cache, and returns a fast local Markdown image/link instead of
hot-linking a long signed storage URL. `upload_receipts` accepts absolute local
image/PDF paths and uploads them through the v2.3.8 multipart API with a 10 MB
per-file limit.

`get_recent_uploads` uses the v2.3.8 create-time endpoint, so it filters by the
date a receipt was uploaded to ReceiptDrop rather than the date recognized from
the invoice.

`find_business_trip_receipts` analyzes one explicit year/month. It uses
transport receipts as provisional trip boundaries, returns location and route
evidence from receipt metadata/OCR, and includes meal and transport candidates
inside the inferred window. Codex must show the candidates and obtain
confirmation of exact receipt IDs before calling `generate_expense_package`.

`get_account_quota` follows the v1.8.4 account screen and returns the configured
user's subscription status, virtual receipt inbox, bonus quota, monthly quota,
remaining/combined receipt allowance, and AI Voice quick-note and journey
allowances. With OAuth, the AI Voice query uses the connected user's access
token automatically.

Generated packages are downloaded under:

```text
/private/tmp/receiptdrop-expense/
```

## Capability boundary

When a user asks for an operation that the exposed MCP tools or fields cannot
perform, the server instructs Codex to identify the unsupported capability,
summarize the relevant available capabilities, and suggest updating the plugin
or using another appropriate method. Codex must not claim that an unsupported
action was completed.

Users who want to contribute a missing capability can open an issue or submit
a pull request at
[qwert22356/receiptdrop-codex-plugin](https://github.com/qwert22356/receiptdrop-codex-plugin)
using their own GitHub account. The plugin must not submit external changes
without the user's authorization.
