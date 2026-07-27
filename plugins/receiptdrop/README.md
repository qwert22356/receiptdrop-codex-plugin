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
- `generate_expense_package`
- `configure_receiptdrop_user`

Generated packages are downloaded under:

```text
/private/tmp/receiptdrop-expense/
```
