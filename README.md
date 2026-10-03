# qSIGHT releases

Signed qSIGHT releases for Linux amd64 and arm64. The source lives in a private repository. This repository holds only what an install downloads: each release's tarballs, its signed manifest and the installer.

## Install

On a Linux host with systemd, as root:

```sh
curl -fsSL https://github.com/interroseclabs/qsight-releases/releases/latest/download/install.sh | sudo sh
```

To install a specific version:

```sh
curl -fsSL https://github.com/interroseclabs/qsight-releases/releases/latest/download/install.sh | sudo sh -s -- --version 1.2.3
```

The installer checks the release's Ed25519 signature, and each tarball's SHA-256, before it unpacks anything. It installs to `/opt/qsight/versions/<version>`, with `/opt/qsight/current` pointing at the live version. A running install updates with `qsight update`.

Docker, Windows and macOS are not supported. qSIGHT needs Postgres 18. `qsight db compose` prints a Compose file that runs one, if the host has none.

## Each release

| File | What it is |
|---|---|
| `qsight-<version>-linux-amd64.tar.gz`, `qsight-<version>-linux-arm64.tar.gz` | The `qsight` binary and its bundled Python |
| `qsight-release.txt` | The manifest: the version, and each tarball's SHA-256, size and name |
| `qsight-release.txt.sig` | The manifest's Ed25519 signature |
| `install.sh` | The installer |

Using qSIGHT needs a licence for each Assessment. Releases are published here by a workflow in the source repository. Nothing else is committed here.
