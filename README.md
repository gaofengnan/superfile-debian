![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/gaofengnan/superfile-debian/total)
![GitHub Downloads (all assets, latest release)](https://img.shields.io/github/downloads/gaofengnan/superfile-debian/latest/total)
![GitHub Release](https://img.shields.io/github/v/release/gaofengnan/superfile-debian)
![GitHub Release Date](https://img.shields.io/github/release-date/gaofengnan/superfile-debian)

<h1>
   <p align="center">
     <a href="https://superfile.dev/"><img src="https://github.com/gaofengnan/superfile-debian/blob/main/superfile.svg" alt="superfile Logo" width="220" style="margin-right: 20px"></a>
     <a href="https://www.debian.org/"><img src="https://github.com/gaofengnan/superfile-debian/blob/main/debian-logo.png" alt="Debian Logo" width="104" style="margin-left: 20px"></a>
     <br>superfile for Debian
   </p>
</h1>
<p align="center">
 superfile is a pretty fancy and modern terminal file manager, with multi-panel browsing, previews, and a built-in trash bin.
</p>

# superfile for Debian

> Fork of [dariogriffo/superfile-debian](https://github.com/dariogriffo/superfile-debian) (MIT); the original packaging is by Dario Griffo. Served at [deb.gaofn.xyz](https://deb.gaofn.xyz) for Debian 12 (bookworm) and 13 (trixie).

This repository contains build scripts to produce the _unofficial_ Debian packages
(.deb) for [superfile](https://github.com/yorukot/superfile/) hosted at [deb.gaofn.xyz](https://deb.gaofn.xyz)

Currently supported Debian distros are:
- Bookworm (v12)
- Trixie (v13)
- Forky (v14)
- Sid (testing)

Currently supported Ubuntu distros are:
- Jammy (22.04)
- Noble (24.04)
- Questing (25.10)
- Resolute (26.04)

Supported architectures:
- amd64 (x86_64) - All distributions
- arm64 (aarch64) - All distributions

Upstream publishes no i386, armel, armhf or riscv64 binaries, so those
architectures are not available.

> ℹ️ The package installs a single command called **`spf`**, not `superfile` —
> that is upstream's own naming. Upstream ships no man page or shell
> completions; run `spf --help` for the command reference and `spf path-list`
> to print the configuration and data directory paths.

superfile has no hard dependencies (it is a statically linked Go binary), but a
few optional tools unlock extra features: `xdg-utils` to open files with your
desktop's default application, `zoxide` for the jump panel, `ffmpeg` and
`poppler-utils` for video and PDF previews, `libimage-exiftool-perl` for
extended metadata, and `xclip` or `wl-clipboard` for clipboard integration.

This is an unofficial community project to provide a package that's easy to
install on Debian. If you're looking for the superfile source code, see
[superfile](https://github.com/yorukot/superfile/).

## Install/Update

### The Debian way

```sh
sudo install -d -m 0755 /etc/apt/keyrings
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.gpg -o /etc/apt/keyrings/deb.gaofn.xyz.gpg
sudo curl -fsSL https://deb.gaofn.xyz/deb.gaofn.xyz.sources -o /etc/apt/sources.list.d/deb.gaofn.xyz.sources
# Debian 12 (bookworm): fetch deb.gaofn.xyz-bookworm.sources instead
sudo apt update
sudo apt install -y superfile
```

### Manual Installation

1. Download the .deb package for your Debian version available on
   the [Releases](https://github.com/gaofengnan/superfile-debian/releases) page.
2. Install the downloaded .deb package.

```sh
sudo dpkg -i <filename>.deb
```
## Updating

To update to a new version, just follow any of the installation methods above. There's no need to uninstall the old version; it will be updated correctly.

## Building

### Build for single architecture
```sh
./build.sh <superfile_version> <build_version> <architecture>
# Example: ./build.sh 1.6.0 1 arm64
```

### Build for all architectures
```sh
./build.sh <superfile_version> <build_version> all
# Example: ./build.sh 1.6.0 1 all
```

## Roadmap

- [x] Produce a .deb package on GitHub Releases
- [x] Set up a debian mirror for easier updates
- [x] Multi-architecture support (amd64, arm64)

## Disclaimer

- This repo is not open for issues related to superfile. This repo is only for _unofficial_ Debian packaging.
