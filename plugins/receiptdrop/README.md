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
- `update_receipt`
- `generate_expense_package`
- `configure_receiptdrop_user`

`update_receipt` supports the editable v2.3.8 receipt fields: buyer, seller,
invoice date, category, total, currency, invoice number, address, original
information, OCR text, hash ID, and creation time. Its `note` convenience
parameter is prepended to the existing `address` with a ` | ` separator. This
keeps the original address intact while making the note searchable through
`search_receipts`.

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
