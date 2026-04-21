# Meehl Solutions Powder Trickler — Firmware Releases

Public firmware binaries for the **Meehl Solutions Powder Trickler** (ESP32-S3).

Binaries are served directly from this repo by the Squarespace firmware updater
via the [jsDelivr](https://www.jsdelivr.com/) CDN.

## Layout

```
manifest.json      Index of all releases (consumed by the updater)
releases/
  FW130.bin        Firmware binary, named FW<version-no-dots>.bin
  ...
```

## Served URLs

```
https://cdn.jsdelivr.net/gh/HappyMeehl/trickler-firmware-releases@main/manifest.json
https://cdn.jsdelivr.net/gh/HappyMeehl/trickler-firmware-releases@main/releases/FW130.bin
```

> jsDelivr caches up to 12 h on `@main`. For an instant-refresh URL, tag a
> release (`git tag v1.4.0 && git push --tags`) and change `MSPT_FW_REPO_REF`
> in the updater HTML to `v1.4.0`.

## Publishing a new firmware

From the firmware source repo:

```powershell
./tools/publish-firmware.ps1 -Version 1.4.0 -Notes "Adds audio alert"
```

The script builds / copies the binary, prepends a new entry to `manifest.json`
in this repo's local clone, then commits + pushes.

## manifest.json schema

```json
{
  "name": "Meehl Solutions Powder Trickler",
  "chipFamily": "ESP32-S3",
  "offset": 65536,
  "releases": [
    {
      "version": "1.4.0",
      "file": "releases/FW140.bin",
      "notes": "Adds audio alert",
      "published": "2026-05-01"
    },
    {
      "version": "1.3.0",
      "file": "releases/FW130.bin",
      "notes": "Initial public release",
      "published": "2026-04-15"
    }
  ]
}
```

Newest release at the top. `file` is relative to the repo root.
