# Try Luma 0.7.6 — website handoff

Update `/try` to **Try Luma 0.7.6**. Use these versioned GitHub links for the download buttons. The release remains a public preview; avoid `/releases/latest/download` because prereleases do not resolve there.

| Platform | Link | Bytes | SHA256 |
|---|---|---:|---|
| macos-arm64 | [Download](https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try.Luma-0.7.6-macos-arm64.dmg) | 66,600,391 | `8c86526464f74a7c6cbd29a1cd4f75773178965eadadc861f635eea6929b3c0d` |
| windows-x86_64 | [Download](https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try-Luma-0.7.6-windows-x86_64.zip) | 267,075,020 | `6710a1d0cbd317e41e1822218894aa055f65cfba9d3c8614a7ff3fc6660ca7c2` |
| linux-x86_64 | [Download](https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try-Luma-0.7.6-linux-x86_64.AppImage) | 295,631,352 | `54872a8672416002c9a867340621d1a79830aada36d42f304e32c5eaacc328c4` |

Release: https://github.com/SimplyLuma/try/releases/tag/v0.7.6

Name the app **Try Luma**. macOS is Apple silicon; Windows and Linux downloads are x86-64. The Mac app and disk image are Developer ID signed, notarized and stapled. Windows is unsigned. The Mac bundle declares macOS 27.0 as its minimum; keep the requirement accurate on the page.

Suggested short update: “Smoother Mac previews and reliable app launching. Try Desktop, Tablet and Mobile in a persistent local workspace.” Guest rendering on Mac remains software; do not advertise hardware GPU acceleration.

The app downloads a prepared VM disk and boots directly to Luma with automatic login. Keep these large disks inside the app flow; the website's Try buttons should download the small application, rather than installer ISOs. One ARM64 disk and one x86-64 disk serve all three experiences.

Preview credentials are shown in the app sidebar in Try and Developer: username `luma`, password `TryLuma`. SSH is key-only.

## Hub download center and automatic updates

Register the three app artifacts below in the Hub and publish the signed tester release index for 0.7.6. GitHub publication alone does not populate the app's update checker. Use `kind: tester_app`, the exact URLs/byte counts/SHA256 above, and preserve tester-vs-website download attribution. The app's release builds already send tester attribution.

```json
[
  {
    "artifact_id": "tester/0.7.6/macos-arm64",
    "kind": "tester_app",
    "platform": "macos-arm64",
    "url": "https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try.Luma-0.7.6-macos-arm64.dmg",
    "size_bytes": 66600391,
    "sha256": "8c86526464f74a7c6cbd29a1cd4f75773178965eadadc861f635eea6929b3c0d"
  },
  {
    "artifact_id": "tester/0.7.6/windows-x86_64",
    "kind": "tester_app",
    "platform": "windows-x86_64",
    "url": "https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try-Luma-0.7.6-windows-x86_64.zip",
    "size_bytes": 267075020,
    "sha256": "6710a1d0cbd317e41e1822218894aa055f65cfba9d3c8614a7ff3fc6660ca7c2"
  },
  {
    "artifact_id": "tester/0.7.6/linux-x86_64",
    "kind": "tester_app",
    "platform": "linux-x86_64",
    "url": "https://github.com/SimplyLuma/try/releases/download/v0.7.6/Try-Luma-0.7.6-linux-x86_64.AppImage",
    "size_bytes": 295631352,
    "sha256": "54872a8672416002c9a867340621d1a79830aada36d42f304e32c5eaacc328c4"
  }
]
```

Approved VM channel: https://raw.githubusercontent.com/SimplyLuma/try/main/channels/images.json — generation 7, exactly two current prepared disks. The new image paths are `tester/20261028-ready4/try-luma-aarch64.qcow2` and `tester/20261028-ready4/try-luma-x86_64.qcow2` on `https://media.simplyluma.com/`. The channel contains their exact sizes and digests.

Application source, pinned modified-QEMU source, patch, build recipe and checksums are attached to the release. Existing workspaces and previous releases are preserved.
