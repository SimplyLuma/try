# Approved preview images

`images.json` is Try Luma’s curated download policy. Generation 4 offers one
prepared x86-64 VM disk and one prepared ARM64 VM disk. Each supports Desktop,
Tablet and Mobile through the OS experience flag. Both files have been booted
natively and their complete public download bodies verified against SHA-256.

`workspaces` contains at most one `tester_image` per architecture, with its
immutable HTTPS URL, complete size and SHA-256, and a validated `tester_profile`.
Profiles select the restricted `luma-unified-v1` boot protocol; they contain no
executable setup commands. New clients offer these prepared disks instead of
installation media, including when the Hub catalog is unavailable.

The legacy `images` approvals retain one installer ISO per architecture for
older-client compatibility. IDs and digests must match the Hub catalog.
Manually imported images and saved local workspaces remain available.

Increase `generation` for each policy change. Clients reject stale generations
and retain their last valid policy offline. Approve new artifacts only after
source checks, native boot qualification and complete public-byte verification.
Never derive approval from filenames, dates or catalog ordering. Keep generated
VM disks and application packages out of Git.
