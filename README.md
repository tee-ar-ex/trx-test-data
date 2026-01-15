# TRX Test Data

Versioned test datasets for `trx-python`, hosted on the GitHub release `tee-ar-ex/trx-test-data` tag `v0.1.0`. Files mirror the original Figshare-hosted artifacts and include checksums for integrity.

## Access
- Release page: https://github.com/tee-ar-ex/trx-test-data/releases/tag/v0.1.0  
- Direct download base: `https://github.com/tee-ar-ex/trx-test-data/releases/download/v0.1.0/`
- Programmatic: use `trx.fetcher.fetch_data(get_testing_files_dict())` (downloads to `~/.tee_ar_ex` or `$TRX_HOME`).

## Contents

| File | Size (MB) | Description | MD5 | SHA256 |
| --- | --- | --- | --- | --- |
| `DSI.zip` | 1.33 | DSI Studio/TrackVis sample tractogram for I/O validation. | `b847f053fc694d55d935c0be0e5268f7` | `1b09ce8b4b47b2600336c558fdba7051218296e8440e737364f2c4b8ebae666c` |
| `memmap_test_data.zip` | 0.74 | Minimal memmap fixture datasets for allocation/resize tests. | `03f7651a0f9e3eeabee9aed0ad5f69e1` | `98ba89d7a9a7baa2d37956a0a591dce9bb4581bd01296ad5a596706ee90a52ef` |
| `trx_from_scratch.zip` | 24.7 | Full TRX examples generated from scratch; exercises conversion and dtype handling. | `d9f220a095ce7f027772fcd9451a2ee5` | `f98ab6da6a6065527fde4b0b6aa40f07583e925d952182e9bbd0febd55c0f6b2` |
| `gold_standard.zip` | 0.01 | Golden tractograms for regression comparisons. | `57e3f9951fe77245684ede8688af3ae8` | `35a0b633560cc2b0d8ecda885aa72d06385499e0cd1ca11a956b0904c3358f01` |

## Usage
```bash
# Download everything (cached under ~/.tee_ar_ex or $TRX_HOME)
python - <<'PY'
from trx.fetcher import get_testing_files_dict, fetch_data
fetch_data(get_testing_files_dict())
PY

# Or fetch a single archive
python - <<'PY'
from trx.fetcher import get_testing_files_dict, fetch_data
fetch_data(get_testing_files_dict(), keys="memmap_test_data.zip")
PY
```

### Manual download/verification
```bash
curl -LO https://github.com/tee-ar-ex/trx-test-data/releases/download/v0.1.0/DSI.zip
md5 DSI.zip       # or md5sum
shasum -a 256 DSI.zip
```

## Notes
- Checksums are stored alongside URLs in `trx/fetcher.py` (MD5 + SHA256) and enforced at download time.
- Datasets originate from the original Figshare-hosted TRX test bundles; hosting moved to GitHub for availability and versioning.
- Data is intended for testing only and should not be used as production tractography reference material.
