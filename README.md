# Photo Prep updates

Release files for **Photo Prep**, X-treme Photo Services' green-screen photo app
(developed by Ozark Mountain AI LLC, licensed to X-treme Photo Services).

Every Photo Prep PC (version 2.3.9 and later) reads `latest.json` from this repository when it opens
and every 4 hours. A newer version downloads in the background, is checked against the SHA-256 in
`latest.json`, and installs when Photo Prep is closed. Nobody signs in; the app only reads the files.

## Layout

| Path | What it is |
| --- | --- |
| `latest.json` | The version every PC should run: version, address of the update, SHA-256, size. |
| `updates/<version>/PhotoPrep-<version>-update.exe` | The small update (the app only; Python and AI models stay). |
| `updates/<version>/Photo-Prep-User-Guide.pdf` | The staff user guide for that version. |

The full installer (about 400 MB) is too big for a repository; new PCs still get it from Dropbox.

## Rules

- Only update files go here. No source code, photos, templates or customer data.
- Publishing here updates **every** Photo Prep PC. Keep two-factor sign-in on this account.
- Updates are published with `tools/publish_release.py` from the Photo Prep source. It pushes the
  files and `latest.json` together in one commit, with the right fingerprint.
- `latest.json` may only point at files in this repository; the app refuses anything else.
- To hold back a bad update: point `latest.json` back at the previous version (or restore the
  previous commit of it). A PC that already installed a bad version rolls back by itself if it
  won't start.
