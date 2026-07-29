# ReceiptDrop for Codex

This plugin exposes a local ReceiptDrop MCP server to Codex.

## Account configuration

On first use, ask Codex to configure your ReceiptDrop user UUID. The plugin saves
it locally at:

```text
~/.config/receiptdrop/config.json
```

`RECEIPTDROP_USER_ID` is also supported as an optional environment override.

## Included tools

- `search_receipts`
- `get_receipt_attachment`
- `get_recent_uploads`
- `get_account_quota`
- `upload_receipts`
- `update_receipt`
- `generate_expense_package`
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

`get_account_quota` follows the v1.8.4 account screen and returns the configured
user's subscription status, virtual receipt inbox, bonus quota, monthly quota,
remaining/combined receipt allowance, and AI Voice quick-note and journey
allowances. AI Voice requires the user's Supabase access token in
`RECEIPTDROP_API_TOKEN`.

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
