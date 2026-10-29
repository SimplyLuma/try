# Try Luma 0.7.7 — Linux website and Hub handoff

Update the **Linux** Try Luma download to 0.7.7. macOS and Windows keep their existing 0.7.6 packages and links. The prepared OS image channel remains generation 7, with one ARM64 and one x86-64 disk serving Desktop, Tablet and Mobile.

Keep the website's tracked `/get/app/try/linux` route and change its registered artifact destination to the Linux URL below. Preserve attribution. A GitHub release does not update the website route or the signed Hub update index automatically. These releases are previews; do not use `/releases/latest/download`.

| Platform | Version | Download | Bytes | SHA256 |
|---|---|---|---:|---|
| Linux x86-64 | 0.7.7 | [AppImage](https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-linux-x86_64.AppImage) | 298,301,944 | `7ef43171375d5e628f03abebbcbf42411b81e16820ffab63587f5c559c66222b` |
| macOS Apple silicon | 0.7.6 | [DMG](https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try.Luma-0.7.6-macos-arm64.dmg) | 66,600,391 | `8c86526464f74a7c6cbd29a1cd4f75773178965eadadc861f635eea6929b3c0d` |
| Windows x86-64 | 0.7.6 | [ZIP](https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try-Luma-0.7.6-windows-x86_64.zip) | 267,075,020 | `6710a1d0cbd317e41e1822218894aa055f65cfba9d3c8614a7ff3fc6660ca7c2` |

Release: [Try Luma 0.7.7](https://github.com/SimplyLuma/try/releases/tag/v0.7.7).

Suggested Linux release text: “Fix graphics-library compatibility in the Linux AppImage. Add downloaded-image deletion and fix launcher display initialization.” Avoid claims of universal GPU performance improvements: the package was checked for private graphics-library resolution, older Ubuntu userspace, startup and fallback; full hardware performance depends on the host.

Register this artifact in the Hub download center and include it in the signed Tester release index for Linux. Keep the Mac and Windows entries at their existing versions. Preserve website/tester source attribution. Production packages send `tester` attribution; QA previews use `test`.

```json
{
  "artifact_id": "tester/0.7.7/linux-x86_64",
  "kind": "tester_app",
  "platform": "linux-x86_64",
  "url": "https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-linux-x86_64.AppImage",
  "size_bytes": 298301944,
  "sha256": "7ef43171375d5e628f03abebbcbf42411b81e16820ffab63587f5c559c66222b"
}
```

Name the app **Try Luma**. Keep existing platform requirements and signing descriptions: Mac 0.7.6 is Developer ID signed and notarized; Windows is unsigned. The Linux release does not introduce hardware GPU acceleration on Mac.

The app downloads a prepared VM disk and boots directly into Luma with automatic login. Existing workspaces and snapshots persist. The preview sidebar shows username `luma` and password `TryLuma` in Try and Developer modes. VM disks stay inside the app download flow; `/try` buttons download applications.

Approved images: [channels/images.json](https://raw.githubusercontent.com/SimplyLuma/try/main/channels/images.json). No new OS image registration is required for this release.
