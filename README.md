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

| App | Start menu name | Description |
| --- | --- | --- |
| [crypto-tools](https://github.com/nyg/crypto-tools) | Crypto Tools | A collection of cryptocurrency tools for Kraken and Binance exchanges. |
| [qoqa-compta](https://github.com/nyg/qoqa-compta) | QoQa Compta | Desktop spending dashboard for QoQa.ch — syncs your orders and PDF invoices to a local database and displays spending charts, stats, and a searchable orders table. |
| [wiktionary-to-kindle](https://github.com/nyg/wiktionary-to-kindle) | Wiktionary to Kindle | Converts Wiktionary data into Kindle-compatible MOBI dictionaries. |

```powershell
scoop install crypto-tools
scoop install qoqa-compta
scoop install wiktionary-to-kindle
```

Each manifest points at the flat portable
`<app>-<version>-windows-x64-scoop.zip` release asset, which Scoop downloads and
extracts — no installer runs. The `<app>-<version>-windows-x64-setup.zip` assets
published alongside them are the standalone installer builds and are not used by
this bucket.

The Electrobun apps (`crypto-tools`, `qoqa-compta`) launch through
`bin\launcher.exe` next to the runtime files; `wiktionary-to-kindle` ships
`Wiktionary to Kindle.exe` at the archive root. Every manifest aliases its `bin`
entry to the app's own name, so each one gets a `crypto-tools`, `qoqa-compta`,
or `wiktionary-to-kindle` shim on the Scoop path — the alias matters because the
Electrobun entry point is always called `launcher.exe`, and without it those two
apps would collide on a single `launcher` shim. All three also register a Start
menu shortcut under the names above.

macOS builds of the same apps are packaged in
[nyg/homebrew-tap](https://github.com/nyg/homebrew-tap).

## Updates

The manifests in `bucket/` are kept in sync automatically: each app's release
workflow updates the version and hash here and pushes the change directly after
publishing its release asset.
