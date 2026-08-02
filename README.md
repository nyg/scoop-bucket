# scoop-bucket

A [Scoop](https://scoop.sh) bucket for [nyg](https://github.com/nyg)'s Windows
apps. Everything installs with no admin rights and no SmartScreen prompt.

## Setup

```powershell
scoop bucket add nyg https://github.com/nyg/scoop-bucket
```

Don't have Scoop yet? Install it first (no admin required):

```powershell
irm get.scoop.sh | iex
```

## Apps

| App | Description |
| --- | --- |
| [crypto-tools](https://github.com/nyg/crypto-tools) | A collection of cryptocurrency tools for Kraken and Binance exchanges. |
| [qoqa-compta](https://github.com/nyg/qoqa-compta) | Desktop spending dashboard for QoQa.ch — syncs your orders and PDF invoices to a local database and displays spending charts, stats, and a searchable orders table. |
| [wiktionary-to-kindle](https://github.com/nyg/wiktionary-to-kindle) | Converts Wiktionary data into Kindle-compatible MOBI dictionaries. |

```powershell
scoop install crypto-tools
scoop install qoqa-compta
scoop install wiktionary-to-kindle
```

Each manifest points at a flat portable `*-Scoop.zip` release asset that Scoop
downloads and extracts. The Electrobun apps (`crypto-tools`, `qoqa-compta`)
expose `bin\launcher.exe` next to the runtime files;
`wiktionary-to-kindle` ships its executable at the archive root. All three
register a Start menu shortcut.

## Updates

The manifests in `bucket/` are kept in sync automatically: each app's release
workflow updates the version and hash here and pushes the change directly after
publishing its release asset.
