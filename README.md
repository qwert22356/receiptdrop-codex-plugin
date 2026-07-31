# ReceiptDrop for Codex

ReceiptDrop's Codex plugin uploads, searches, views, and updates receipts,
queries synced Footprint activities, cross-checks business-trip candidates,
lets the user confirm which expenses to reimburse, runs ReceiptDrop Generate,
and downloads the generated package.

## Install

Add this repository as a local Codex marketplace, then install the plugin:

```bash
codex plugin marketplace add https://github.com/qwert22356/receiptdrop-codex-plugin
codex plugin add receiptdrop@receiptdrop
```

Start a new Codex task after installation.

## First use

Connect the ReceiptDrop account with OAuth:

```text
Connect my ReceiptDrop account.
```

The OAuth session is stored only on the current computer at:

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
- `get_recent_uploads`
- `get_account_quota`
- `get_receipt_attachment`
- `list_footprints`
- `list_footprint_categories`
- `create_footprint`
- `update_footprint`
- `delete_footprint`
- `find_business_trip_receipts`
- `upload_receipts`
- `update_receipt`
- `generate_expense_package`

Generated packages are downloaded under:

```text
/private/tmp/receiptdrop-expense/
```

## Security

The bundled plugin contains no user IDs, access tokens, receipt data, Footprint
data, or generated files. OAuth tokens remain in the local ReceiptDrop config.
