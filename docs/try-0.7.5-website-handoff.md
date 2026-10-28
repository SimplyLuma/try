# Try Luma 0.7.5 website handoff

Use **Try Luma** as the product name. Update `/try` to these downloads:

| Host | Download |
| --- | --- |
| macOS Apple silicon | https://github.com/SimplyLuma/try/releases/download/v0.7.5/Try.Luma-0.7.5-macos-arm64.dmg |
| Windows x86-64 | https://github.com/SimplyLuma/try/releases/download/v0.7.5/Try-Luma-0.7.5-windows-x86_64.zip |
| Linux x86-64 | https://github.com/SimplyLuma/try/releases/download/v0.7.5/Try-Luma-0.7.5-linux-x86_64.AppImage |

Release: https://github.com/SimplyLuma/try/releases/tag/v0.7.5

Checksums: https://github.com/SimplyLuma/try/releases/download/v0.7.5/SHA256SUMS

The Mac download is Developer ID signed, notarized and stapled. Windows is unsigned.
These are host application packages; each obtains the approved ARM64 or x86-64 VM
image automatically. One image per guest architecture serves Desktop, Tablet and
Mobile. Keep the existing generation-5 image channel; no installer ISO is needed.

This release repairs app launching in affected preview workspaces and polishes the
sidebar. Preview credentials appear in both modes: `luma` / `TryLuma`. Existing
workspaces receive the repair when reopened. Mac graphics use the stable software
renderer; do not advertise Mac GPU acceleration yet.

For in-app update discovery, enter the published files, sizes and SHA-256 values
into the Hub's signed Tester release index as `kind=tester_app`, version `0.7.5`:
`tester/0.7.5/macos-arm64`, `tester/0.7.5/windows-x86_64`, and
`tester/0.7.5/linux-x86_64`. GitHub publication alone does not update that index.
Website download tracking should use the Hub's corresponding download-ticket links.
