# Try Luma

The release home for **Try Luma** on macOS, Windows and Linux. Try Luma
Desktop, Tablet and Mobile locally, with persistent workspaces and snapshots.

![Try Luma in Try mode, running Luma Desktop with Photos open](assets/luma-tester-try.webp)

The app downloads OS images when needed. One x86-64 ISO and one ARM64 ISO serve
all three experiences. OS downloads stay in Luma's download channel; application
packages belong in this repository's GitHub Releases.

## Download

[Try Luma 0.7.3 preview](https://github.com/SimplyLuma/try/releases/tag/v0.7.3)

- [macOS Apple silicon](https://github.com/SimplyLuma/try/releases/download/v0.7.3/Try.Luma-0.7.3-macos-arm64-notarized.dmg)
- [Windows x86-64](https://github.com/SimplyLuma/try/releases/download/v0.7.3/Try-Luma-0.7.3-windows-x86_64.zip)
- [Linux x86-64](https://github.com/SimplyLuma/try/releases/download/v0.7.3/Try-Luma-0.7.3-linux-x86_64.AppImage)

The macOS download is Developer ID signed and Apple notarized, with approval
tickets stapled to the app and disk image. Windows packages are unsigned.
Checksums and corresponding source are attached to the release.

## Source and builds

The application and shared LumaUI implementation are maintained together in
[SimplyLuma/luma](https://github.com/SimplyLuma/luma):

- Application: `src/luma-tester`
- Linux, macOS and Windows packagers: `scripts/tester`
- Build guidance: `docs/developer-platform/tester.md`

This repository holds the cross-platform release home and the curated image
channel. It does not fork the OS or shared UI platform. Generated applications
and multi-gigabyte OS images must not be committed to Git.

## Image channel

[`channels/images.json`](channels/images.json) explicitly approves the ISO
artifact IDs and checksums offered under **Installation media**. It contains
at most one image per CPU architecture. Older downloads and unapproved future
nightlies are not offered automatically. Existing local workspaces remain usable.

The channel approves the validated October 27 x86-64 and ARM64 installation
images. Each image supports Desktop, Tablet and Mobile.
See [the channel contract](channels/README.md).

## Application updates

Tester checks the Hub's authenticated catalog, which reads the signed Tester
release index. A newer package is selected for the host OS and CPU, independently
of the guest being emulated. Downloaded packages are verified and revealed for
installation; Tester does not replace a running app or restart an active VM.

Release packages require native validation and the authorized signing/publication
workflow. Their immutable URLs, sizes and checksums then enter the signed release
index. Publishing an OS image does not require publishing an app update.
