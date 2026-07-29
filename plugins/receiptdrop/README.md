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
