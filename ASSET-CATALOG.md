# Asset catalog

This catalog records the artwork tree at commit
[`ae3644fbe37fb935241f18f867efed9a5458fef0`](https://github.com/GutterFTW/GutterWorldImageRepo/tree/ae3644fbe37fb935241f18f867efed9a5458fef0),
also present unchanged in documentation PR #1's initial head `daacdc5`.
It was measured on **2026-10-31**. Update the affected rows when changing an
asset; this is a documented snapshot rather than a generated runtime manifest.

All 16 files have a PNG signature and an 8-bit PNG IHDR header. Dimensions and
encoding below were read from the headers, and each measured local file's Git
blob hash matched its tracked object. RGB means PNG color type 2; RGBA means
color type 6. RGBA provides an alpha channel, but that does not prove that any
pixel is transparent. Header checks do not prove that an entire file decodes or
looks correct.

## Tracked images

| Exact path | Width × height (pixels) | Bytes | Encoding |
|---|---:|---:|---|
| [Nest1/Official_Wyvern_Logo.png](Nest1/Official_Wyvern_Logo.png) | 2048 × 2048 | 1,504,438 | RGBA |
| [TSL-Images/2024_11.12_TSL_Tuesday_13.png](TSL-Images/2024_11.12_TSL_Tuesday_13.png) | 750 × 1000 | 936,715 | RGB |
| [TSL-Images/2024_11_Emission.png](TSL-Images/2024_11_Emission.png) | 750 × 1000 | 404,725 | RGB |
| [TSL-Images/2025_10.14.25_TSL.png](TSL-Images/2025_10.14.25_TSL.png) | 1250 × 1250 | 3,081,952 | RGB |
| [TSL-Images/2025_10.14_Emission.png](TSL-Images/2025_10.14_Emission.png) | 1250 × 1250 | 35,113 | RGB |
| [TSL-Images/2025_5.13_TSL.png](TSL-Images/2025_5.13_TSL.png) | 1250 × 1250 | 953,135 | RGB |
| [TSL-Images/2025_5_Emission.png](TSL-Images/2025_5_Emission.png) | 1250 × 1250 | 27,313 | RGB |
| [TSL-Images/2025_8.30_TSL_Resident_Saturday.png](TSL-Images/2025_8.30_TSL_Resident_Saturday.png) | 1250 × 1250 | 2,108,427 | RGB |
| [TSL-Images/2025_8_Emission.png](TSL-Images/2025_8_Emission.png) | 1250 × 1250 | 30,269 | RGB |
| [TSL-Images/780_Racer_logo.png](TSL-Images/780_Racer_logo.png) | 366 × 375 | 46,705 | RGBA |
| [TSL-Images/Frog_temp_logo.png](TSL-Images/Frog_temp_logo.png) | 960 × 540 | 225,138 | RGBA |
| [TSL-Images/GutterDJLogo.png](TSL-Images/GutterDJLogo.png) | 1500 × 1500 | 262,344 | RGBA |
| [TSL-Images/ItzSpookey_logo.png](TSL-Images/ItzSpookey_logo.png) | 2250 × 2250 | 895,354 | RGBA |
| [TSL-Images/Neon_logo.png](TSL-Images/Neon_logo.png) | 768 × 512 | 132,277 | RGBA |
| [TSL-Images/R0n1n_logo.png](TSL-Images/R0n1n_logo.png) | 1814 × 725 | 197,022 | RGBA |
| [TSL-Images/Serenity_Logo.png](TSL-Images/Serenity_Logo.png) | 1500 × 1150 | 296,881 | RGBA |

Total: **16 files, 11,137,808 bytes**. No directory other than `Nest1/` and
`TSL-Images/` contains tracked artwork in this snapshot. Empty directories or
files present only in a local checkout are not part of this inventory.

## Interpretation and maintenance

- The measurements describe existing files. They do not prescribe future image
  dimensions, compression, maximum file size, color space, or transparency.
- `Emission` is a filename label. No tracked code maps it to a Unity material,
  shader property, paired poster, or color-space setting. Confirm those details
  in the actual consumer before editing.
- The dates use several spellings. No tracked code parses them or establishes a
  chronological sort rule. Exact filenames remain the reliable lookup keys.
- Folder and logo names do not establish ownership, licensing, attribution, or
  approved use. Those decisions remain with the rights holders and owner.

Follow [MAINTENANCE.md](MAINTENANCE.md) for changes and validation. Use the
[README URL examples](README.md#get-an-image-url) for raw and pinned references.
