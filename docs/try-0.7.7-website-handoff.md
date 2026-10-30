# Try Luma 0.7.7 — website and Hub handoff

Update **macOS, Windows and Linux** Try Luma downloads to 0.7.7. All three packages include downloaded-image deletion. The Mac app and DMG are Developer ID signed, Apple notarized and stapled. The prepared OS image channel remains generation 7, with one ARM64 and one x86-64 disk serving Desktop, Tablet and Mobile.

Keep the website's tracked `/get/app/try/mac`, `/get/app/try/windows` and `/get/app/try/linux` routes and change their registered artifact destinations to the URLs below. Preserve attribution. A GitHub release does not update the website route or the signed Hub update index automatically. These releases are previews; do not use `/releases/latest/download`.

| Platform | Version | Download | Bytes | SHA256 |
|---|---|---|---:|---|
| Linux x86-64 | 0.7.7 | [AppImage](https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-linux-x86_64.AppImage) | 298,301,944 | `7ef43171375d5e628f03abebbcbf42411b81e16820ffab63587f5c559c66222b` |
| macOS Apple silicon | 0.7.7 | [DMG](https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try.Luma-0.7.7-macos-arm64.dmg) | 66,562,917 | `63eba52f129693cc99ee89bf4007795bc90c7d7178771cbd72450fc9533e90e6` |
| Windows x86-64 | 0.7.7 | [ZIP](https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try-Luma-0.7.7-windows-x86_64.zip) | 267,078,718 | `120337eb4eeccb7cccf13a1597e6b932205e2a2fd6d7a998850637d7932140c9` |

Release: [Try Luma 0.7.7](https://github.com/SimplyLuma/try/releases/tag/v0.7.7).

Suggested Linux release text: “Fix graphics-library compatibility in the Linux AppImage. Add downloaded-image deletion and fix launcher display initialization.” Avoid claims of universal GPU performance improvements: the package was checked for private graphics-library resolution, older Ubuntu userspace, startup and fallback; full hardware performance depends on the host.

Register all three 0.7.7 artifacts in the Hub download center and include them in the signed Tester release index for their respective platforms. Preserve website/tester source attribution. Production packages send `tester` attribution; QA previews use `test`.

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

Mac 0.7.7 passed the native image-picker deletion/cancel/confirmation checks, all 11 storage tests, the Desktop default and one-click UI checks, password sidebar checks and hardened QEMU accelerator control checks. The final downloaded DMG and installed app passed Gatekeeper with quarantine applied. This update preserves the existing Mac graphics implementation.

```json
{
  "artifact_id": "tester/0.7.7/macos-arm64",
  "kind": "tester_app",
  "platform": "macos-arm64",
  "url": "https://github.com/SimplyLuma/try/releases/download/v0.7.7/Try.Luma-0.7.7-macos-arm64.dmg",
  "size_bytes": 66562917,
  "sha256": "63eba52f129693cc99ee89bf4007795bc90c7d7178771cbd72450fc9533e90e6"
}
```

Name the app **Try Luma**. Keep existing platform requirements and signing descriptions: Mac 0.7.7 is Developer ID signed and notarized; Windows is unsigned. The Linux release does not introduce hardware GPU acceleration on Mac.

The app downloads a prepared VM disk and boots directly into Luma with automatic login. Existing workspaces and snapshots persist. The preview sidebar shows username `luma` and password `TryLuma` in Try and Developer modes. VM disks stay inside the app download flow; `/try` buttons download applications.

Approved images: [channels/images.json](https://raw.githubusercontent.com/SimplyLuma/try/main/channels/images.json). No new OS image registration is required for this release.
