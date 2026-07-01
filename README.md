# scoop-bucket

A [Scoop](https://scoop.sh) bucket for [nyg](https://github.com/nyg)'s Windows
apps.

## crypto-tools

Install [crypto-tools](https://github.com/nyg/crypto-tools) with no admin rights
and no SmartScreen prompt:

```powershell
scoop bucket add nyg https://github.com/nyg/scoop-bucket
scoop install crypto-tools
```

Don't have Scoop yet? Install it first (no admin required):

```powershell
irm get.scoop.sh | iex
```

Scoop downloads and extracts `CryptoTools-Scoop.zip`, a flat portable package
whose root contains `bin\launcher.exe` and the Electrobun runtime files.

### Updates

`bucket/crypto-tools.json` is kept in sync automatically by
`nyg/crypto-tools`' release workflow, which updates and pushes the manifest
directly after publishing each release asset.
