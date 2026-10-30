# Photo Prep updates

Release files for **Photo Prep**, X-treme Photo Services' green-screen photo app
(developed by Ozark Mountain AI LLC, licensed to X-treme Photo Services).

Every Photo Prep PC (version 2.3.9 and later) checks the **latest release** here when it opens and
every 4 hours. A newer version downloads in the background, is checked against the SHA-256 in
`latest.json`, and installs when Photo Prep is closed. Nobody signs in; the app only reads this page.

## What each release holds

| File | What it is |
| --- | --- |
| `latest.json` | Version, file name, SHA-256 and size of the update. The app reads this first. |
| `PhotoPrep-<version>-update.exe` | The small update the PCs download (the app only; Python and AI models stay). |
| `PhotoPrep-<version>-Setup.exe` | Full installer for a new PC (when attached). |
| `Photo-Prep-User-Guide.pdf` | The staff user guide for that version. |

## Rules

- Only release files go here. No source code, photos, templates or customer data.
- Publishing a release here updates **every** Photo Prep PC. Keep two-factor sign-in on this account.
- Releases are published with `tools/publish_release.py` from the Photo Prep source, which writes
  `latest.json` with the right fingerprint. A release without a matching `latest.json` is ignored.
- To hold back a bad release: delete it (or mark it as a pre-release). PCs go back to treating the
  previous release as the latest; a PC that already installed it rolls back by itself if it won't start.
