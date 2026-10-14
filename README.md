# Ovrilo releases

Public downloads for the [Ovrilo](https://github.com/Ovrilo) desktop app. The source code lives in private repositories; this repository only hosts release assets and the download page.

**Download:** https://ovrilo.github.io/ovrilo-releases/ (or the [Releases](https://github.com/Ovrilo/ovrilo-releases/releases) tab).

## What a release contains

| File | Purpose |
| --- | --- |
| `Ovrilo_<version>_x64-setup.exe` | Windows installer (per-user, no admin rights). Not Authenticode-signed yet: Windows may warn about an unknown publisher. |
| `Ovrilo_<version>_x64-setup.exe.sig` | Tauri updater signature. The app refuses updates whose signature does not match its built-in public key. |
| `latest.json` | Updater manifest. Installed apps read `releases/latest/download/latest.json`, which always points at the newest **published, non-pre-release** release. |
| `SHA256SUMS.txt` | Checksum of the installer. It confirms an intact download, not the publisher's identity. |

## How releases are made

Releases are created as **drafts** by the `Release` workflow of the private `Ovrilo/ovrilo` repository when a `v*` tag is pushed. A maintainer installs and checks the draft, then publishes it; only then do installed apps see the update. Published assets are never replaced: fixes ship as a new version.

## Download page

`index.html` is served by GitHub Pages from the `main` branch. It reads published releases from the public GitHub API in the browser (no token, no backend).
