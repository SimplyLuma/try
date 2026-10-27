# Approved installation media

`images.json` is the explicit image-selection policy used by Tester. It is
separate from the Hub's historical download catalog. Read it through the canonical
HTTPS URL in this repository; it contains no download URLs or executable commands.
The Hub remains responsible for artifact metadata and signed OS indexes.

Each approval has exactly `artifact_id` and `sha256`. The artifact ID has the
form `os/CHANNEL/BUILD_ID/ARCH`, using `nightly`, `beta` or `stable` and `x86_64`
or `aarch64`. SHA-256 is the complete ISO body's lowercase 64-character digest.
Both fields must match the Hub catalog before an ISO appears in Installation media.

Keep zero, one or two approvals, with at most one per architecture. Replace an
old approval when approving its successor. Do not append an archive of old builds.
Increase the positive integer `generation` for every policy change. Clients
ignore older generations and retain their last valid policy when offline.
An empty newer generation withdraws all offered installation media without
deleting anyone's installed workspaces or cached images.

Before approval, verify the exact source/component receipts, complete ISO digest
and native boot evidence. Publish the matching immutable artifact through the
authorized OS release infrastructure. Then commit the two actual IDs/digests and
increment the generation. Do not insert placeholder digests or infer approval
from dates, filenames, “latest” or catalog ordering.

Generation 3 approves the qualified October 27 x86-64 and ARM64 media after
complete public-byte and signed-listing verification. Existing local imports
and workspaces remain available in the app.
