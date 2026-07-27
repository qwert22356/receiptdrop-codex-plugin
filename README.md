# ReceiptDrop for Codex

ReceiptDrop's Codex plugin searches receipts, lets the user confirm which
expenses to reimburse, runs ReceiptDrop Generate, and downloads the generated
package for browser upload.

## Install

Add this repository as a local Codex marketplace, then install the plugin:

```bash
codex plugin marketplace add https://github.com/qwert22356/receiptdrop-codex-plugin
codex plugin add receiptdrop@receiptdrop
```

Start a new Codex task after installation.

## First use

Configure the ReceiptDrop user UUID once:

```text
Configure my ReceiptDrop user UUID: <your-uuid>
```

The UUID is stored only on the current computer at:

```text
~/.config/receiptdrop/config.json
```

Then ask Codex to search:

```text
Find my receipts from July 1, 2026.
```

## Included tools

- `configure_receiptdrop_user`
- `search_receipts`
- `generate_expense_package`

Generated packages are downloaded under:

```text
/private/tmp/receiptdrop-expense/
```

## Security

This preview uses a locally configured ReceiptDrop user UUID. It does not
contain user IDs, API keys, access tokens, receipt data, or generated files.
