# backend/data (runtime assets)

These files are required at import time and were MISSING from both V4.2.6 ZIPs; without them the backend cannot start.

| file | content |
|---|---|
| rules_test_only.json | TEST_ONLY rule registry; every standard_ref clause number is a placeholder. Not usable for formal cost output. |
| demo_basis_pack.json | TEST_ONLY demo basis pack (status DRAFT). |

Both are TEST_ONLY and contain no real project data, no unit prices and no personal information. Provenance: recovered from the V4.2.6 development workspace (backend/data) because the release archives omitted the folder.
