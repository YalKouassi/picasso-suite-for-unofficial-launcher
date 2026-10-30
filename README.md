# Picasso Suite for Craft Unofficial Launcher

**An unofficial mirror** of [Picasso Suite](https://github.com/fabox-os/Picasso-Suite) releases, maintained by
[YalKouassi](https://github.com/YalKouassi), so that
[Craft Unofficial Launcher](https://github.com/YalKouassi/craft-unofficial-launcher) can install
and update Picasso Suite.

This repo is **not affiliated with, endorsed by or supported by fabox-os** (the authors of Picasso Suite),
**or by ArtCraft**. Report problems with Picasso Suite itself upstream at
<https://github.com/fabox-os/Picasso-Suite>; report problems with this mirror here.

## What this repo publishes

The packages in this repo's releases are **Picasso Suite's own builds**, as published on
[fabox-os/Picasso-Suite's releases](https://github.com/fabox-os/Picasso-Suite/releases). Nothing is rebuilt and no program file is
changed. Each release here:

- downloads upstream's packages and verifies each one before using it;
- renames them to the launcher's `<id>-<version>-<os>-<arch>` naming and, only where the launcher
  couldn't install an archive's layout, repacks that archive (the same files with the same bytes,
  in different folders);
- adds `craft-app.json`, the icon, `SHA256SUMS.txt`, and upstream's licence files from the same tag.

The notes of each release list every file, the upstream asset it came from, its SHA-256, and
whether it was repacked, so you can compare it with upstream's release.

### For Picasso Suite

Upstream's packages are **renamed** to the launcher's naming contract and otherwise mirrored
**byte for byte**:

| Upstream | Here |
|---|---|
| `picasso-suite-<v>-windows.zip` | `picasso-suite-<v>-windows-x64-portable.zip` |
| `picasso-suite-<v>-<arch>.AppImage` / `.rpm` / `.flatpak` | `picasso-suite-<v>-linux-<arch>.AppImage` / `.rpm` / `.flatpak` |
| `picasso-suite-<v>.flatpak` | `picasso-suite-<v>-linux-x86_64.flatpak` |
| `picasso-suite-<v>-amd64.deb` / `-arm64.deb` | `picasso-suite-<v>-linux-x86_64.deb` / `-linux-aarch64.deb` |

Upstream publishes no checksum file, so downloads are checked against GitHub's own asset digests.

Not mirrored: the macOS zips (the launcher installs macOS apps from a `.dmg` only).

## How it runs

[`.github/workflows/bridge.yml`](.github/workflows/bridge.yml) runs every 30 minutes. It uses
[craft-bridge](https://github.com/YalKouassi/craft-bridge) with [`bridge.toml`](bridge.toml) to
check upstream's latest release and mirror it if this repo doesn't have it yet. If upstream starts
publishing its own `craft-app.json`, the bridge stops publishing, and the launcher should point at
upstream directly.

Using this mirror means trusting its maintainer as well as upstream; see
[craft-bridge's Trust section](https://github.com/YalKouassi/craft-bridge#trust).

## Licences

Picasso Suite is licensed by its authors under GPL-3.0 (FFmpeg under its own licence); each release attaches upstream's licence files.
This repo's own files (the config, workflow and this README) are available under MIT OR
Apache-2.0 ([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)).
