# Try Luma 0.7.7 — website and Hub handoff

Update the **Linux and Windows** Try Luma downloads to 0.7.7. macOS keeps its existing signed, notarized 0.7.6 package until the 0.7.7 notarization finishes. The prepared OS image channel remains generation 7, with one ARM64 and one x86-64 disk serving Desktop, Tablet and Mobile.

Keep the website's tracked `/get/app/try/linux` and `/get/app/try/windows` routes and change their registered artifact destinations to the URLs below. Preserve attribution. A GitHub release does not update the website route or the signed Hub update index automatically. These releases are previews; do not use `/releases/latest/download`.

| Platform | Version | Download | Bytes | SHA256 |
|---|---|---|---:|---|
| Linux x86-64 | 0.7.7 | [AppImage](https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-linux-x86_64.AppImage) | 298,301,944 | `7ef43171375d5e628f03abebbcbf42411b81e16820ffab63587f5c559c66222b` |
| macOS Apple silicon | 0.7.6 | [DMG](https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try.Luma-0.7.6-macos-arm64.dmg) | 66,600,391 | `8c86526464f74a7c6cbd29a1cd4f75773178965eadadc861f635eea6929b3c0d` |
| Windows x86-64 | 0.7.7 | [ZIP](https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-windows-x86_64.zip) | 267,078,718 | `120337eb4eeccb7cccf13a1597e6b932205e2a2fd6d7a998850637d7932140c9` |

Release: [Try Luma 0.7.7](https://github.com/SimplyLuma/try/releases/tag/v0.7.7).

Suggested Linux release text: “Fix graphics-library compatibility in the Linux AppImage. Add downloaded-image deletion and fix launcher display initialization.” Avoid claims of universal GPU performance improvements: the package was checked for private graphics-library resolution, older Ubuntu userspace, startup and fallback; full hardware performance depends on the host.

Register both new artifacts in the Hub download center and include them in the signed Tester release index for their respective platforms. Keep the Mac entry at its existing version. Preserve website/tester source attribution. Production packages send `tester` attribution; QA previews use `test`.

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

Windows 0.7.7 adds the downloaded-image trash action, confirmation and cancellation. The actual native Windows picker and all 11 storage tests passed, including workspace locks and real qcow2 snapshots. Its published ZIP was downloaded in full and its SHA-256 verified. Windows runtime binaries are unchanged from the previously qualified runtime.

```json
{
  "artifact_id": "tester/0.7.7/windows-x86_64",
  "kind": "tester_app",
  "platform": "windows-x86_64",
  "url": "https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-windows-x86_64.zip",
  "size_bytes": 267078718,
  "sha256": "120337eb4eeccb7cccf13a1597e6b932205e2a2fd6d7a998850637d7932140c9"
}
```

Name the app **Try Luma**. Keep existing platform requirements and signing descriptions: Mac 0.7.6 is Developer ID signed and notarized; Windows is unsigned. The Linux release does not introduce hardware GPU acceleration on Mac.

The app downloads a prepared VM disk and boots directly into Luma with automatic login. Existing workspaces and snapshots persist. The preview sidebar shows username `luma` and password `TryLuma` in Try and Developer modes. VM disks stay inside the app download flow; `/try` buttons download applications.

Approved images: [channels/images.json](https://raw.githubusercontent.com/SimplyLuma/try/main/channels/images.json). No new OS image registration is required for this release.
