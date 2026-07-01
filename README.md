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

Scoop downloads and extracts `CryptoTools.zip` itself, which strips the
"mark of the web", so running the (unsigned) `CryptoTools-Setup.exe` never
triggers Windows SmartScreen — this works for standard, non-admin users too.
The app installs per-user to `%LOCALAPPDATA%`.

### Updates

`bucket/crypto-tools.json` is kept in sync automatically: nyg/crypto-tools'
release workflow sends a `repository_dispatch` (`update-crypto-tools`) event
with the new `version` and `zip_sha256`, and
[`.github/workflows/update-crypto-tools.yml`](.github/workflows/update-crypto-tools.yml)
bumps the manifest's `version`, download URL, and `hash`.
