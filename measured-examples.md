# Measured PixPouch examples — historical 1.0.2 and current 1.1.1

[Home](README.md) · [中文首页](README.zh-CN.md) · [Format support](format-support.md)

Updated **2026-10-26**. The two sections below use different software versions and source sets. Historical 1.0.2 figures remain historical; current 1.1.1 results were extracted from existing native QA reports, not from a newly run benchmark. These are representative demonstrations, not customer results, general performance data, full format coverage or a guarantee for other inputs. No processing-time or speed comparison is inferred.

## Historical 1.0.2: original recorded table

These measurements were recorded on **2026-10-23** using the existing PixPouch **1.0.2 native application payload**. Output bytes and dimensions were checked against actual exports. This was not a complete Store-installed validation.

| Example | Source bytes | Output bytes | Source → output pixels | Target | Non-pixel padding |
| --- | ---: | ---: | --- | --- | ---: |
| JPEG photo | 789,473 | 199,207 | 1536 × 1024 → 1136 × 757 | 200 KB | 0 B |
| Different JPEG photo | 214,432 | 195,717 | 1536 × 1024 → 1536 × 1024 | 200 KB | 0 B |
| HEIC → JPG | 730,185 | 200,000 | 1536 × 1024 → 1536 × 1024 | 200 KB | 9,288 B |
| Transparent WebP → PNG | 37,034 | 100,000 | 1200 × 900 → 1200 × 900 | 100 KB | 22,964 B |
| JPEG with longest edge 900 | 789,473 | 198,081 | 1536 × 1024 → 900 × 600 | 200 KB | 0 B |

The first example met the 200 KB interval while losing resolution; it was not lossless compression. The second retained dimensions in that run, which does not establish identical image quality.

The HEIC example demonstrates one tested HEVC image. Its padding adds bytes, not detail; it does not establish every HEIC/HEIF profile or HDR workflow.

The transparent WebP-to-PNG example became **larger**. Transparency was retained, and the specific output's decoded RGBA pixels matched the source in the recorded check. This bounded result is not a universal pixel-preservation guarantee. PNG conversion and padding can both change file size, and conversion cannot restore detail absent from the input.

![Historical PixPouch 1.0.2 native screenshot: JPEG from 789473 to 199207 bytes and from 1536 by 1024 to 1136 by 757 pixels.](https://img.itch.zone/aW1nLzMxMjU0OTk2LnBuZw==/original/Goctic.png)

This is an existing **1.0.2** native screenshot. Its preview does not substitute for checking an exported file's bytes and dimensions and does not depict the 1.1.1 Pro workflow.

## Current 1.1.1 Pro: three synthetic sources, two specs, six real exports

The existing **2026-10-25** native QA records use the fixed standalone **Pro 1.1.1 Windows x64** package, driven through its Electron UI. A 93-check Free/Pro run includes this demonstration, and a later 26-check run repeats its marketing/export flow. Both report `passed` with no recorded renderer errors. These counts describe the recorded check lists, not a certification, a full format-matrix test or Store-installed validation.

The source set consists of three locally created **synthetic PNG demonstration images**. They are not customer photographs or evidence of typical processing speed, quality or compression ratios.

| Source file | Source bytes | Source pixels |
| --- | ---: | --- |
| `测试_山湖风景.png` — landscape sample | 3,090,988 | 2200 × 1500 |
| `测试_竖版海报.png` — portrait poster sample | 3,259,851 | 1600 × 2200 |
| `测试_透明商品.png` — transparent product sample | 1,147,808 | 2000 × 1600 |

The two specs were **Web JPG 200KB** (JPG, 200 KB target, longest edge 1600) and **WebP 500KB** (WebP, 500 KB target, longest edge 2000). The filename template was `{name}_{spec}_{index}`; the extension was added automatically. Outputs were written into `01-Web JPG 200KB` and `02-WebP 500KB` subfolders.

| Source | Spec | Output bytes | Source → output pixels | Decoded output alpha | Non-pixel padding |
| --- | --- | ---: | --- | --- | --- |
| Landscape | Web JPG 200KB | 200,000 | 2200 × 1500 → 1600 × 1091 | No | Not recorded |
| Portrait poster | Web JPG 200KB | 195,719 | 1600 × 2200 → 1164 × 1600 | No | Not recorded |
| Transparent product | Web JPG 200KB | 198,062 | 2000 × 1600 → 1600 × 1280 | No; white background | Not recorded |
| Landscape | WebP 500KB | 500,000 | 2200 × 1500 → 2000 × 1364 | No | Not recorded |
| Portrait poster | WebP 500KB | 500,000 | 1600 × 2200 → 1455 × 2000 | No | Not recorded |
| Transparent product | WebP 500KB | 500,000 | 2000 × 1600 → 2000 × 1600 | Yes | Not recorded |

The recorded byte counts, names and decoded dimensions agree with the exported files. The JPG product variant fills transparency with white, while the WebP product variant retains it. Alpha flags do not establish color accuracy or pixel identity. An output at exactly 200,000 or 500,000 bytes does not reveal how much padding it contains. **Padding bytes were not recorded for these six files; “not recorded” must not be read as zero.**

### File identity check on 2026-10-26

The three source files were rehashed locally and matched their SHA-256 values in both reports. The six exports in each recorded run were present, matched their reported byte counts, and had matching SHA-256 hashes across the two runs. This verifies the existing local artifacts and their identity; image processing was not rerun for this documentation update. Historical 1.0.2 file hashes were not rechecked here.

| Source file | SHA-256 |
| --- | --- |
| `测试_山湖风景.png` | `8ade8cb310d635e8fe5b8f35f5f2dc001a12da6b39bcd2b0819fce9081cea4d0` |
| `测试_竖版海报.png` | `05037bdf388ad64dffc43f0ae95b6041d6a6eb72778b81d31693eb19420364b6` |
| `测试_透明商品.png` | `c61b0c5f9b26e03cae99c76f16b089db1d2523f311842a8c92ff792cee702eb0` |

| Export file | SHA-256, identical in both recorded runs |
| --- | --- |
| `测试_山湖风景_Web JPG 200KB_001.jpg` | `e6bcefdb1e6078545ab192504bea51843322fc2e7683733709cb184ee0d817df` |
| `测试_竖版海报_Web JPG 200KB_002.jpg` | `c1137373658b7789dd1f1721c8b397ed5a35d4a1289588b678d01c13c72dd720` |
| `测试_透明商品_Web JPG 200KB_003.jpg` | `c0d8f9cd55152f2db17083f3e3e5f19bb17590a23712dffe638e0c2d236e9b0e` |
| `测试_山湖风景_WebP 500KB_001.webp` | `cedc8078af45f48b5ef0312cb2ad48f445980c1a9e69570e7e94e45a7e491c3b` |
| `测试_竖版海报_WebP 500KB_002.webp` | `4bed41faf8f5c027da89e6db4da6fc5e64966ae43a63e4e1c56900ca0318680b` |
| `测试_透明商品_WebP 500KB_003.webp` | `ba5561445e4a213c9dfa8261c03e07c93ef43dd2464879728675270523aefa0f` |

The local evidence records are `offstore-1792938954025-17f85922/report.json` (93 checks) and `offstore-1792939311810-ddc0c935/report.json` (26 checks). The application source, QA source tree and local image artifacts are not published by this documentation repository; those report identifiers describe provenance, not public download links.

## Target intervals behind both sets of examples

File sizes use decimal units: 1 KB = 1,000 bytes.

| Setting | Allowed output interval, inclusive |
| --- | --- |
| 30 KB | 25,001–30,000 B |
| 100 KB | 95,001–100,000 B |
| 200 KB | 195,001–200,000 B |
| 500 KB | 495,001–500,000 B |

The app targets these intervals and has no separate maximum-only mode. It may lower quality, reduce dimensions or add non-pixel padding. Exact cap equality, unchanged pixels and a smaller file are not guaranteed. Results that cannot meet the settings and interval cannot be exported; changing settings requires reprocessing. For strict “less than” upload requirements, choose a lower setting and check the actual file. Size compliance does not guarantee upload acceptance.

Each source is limited to 100,000,000 bytes and 60,000,000 decoded pixels. Outputs are JPG, PNG or WebP only. See [format support](format-support.md) and [local processing, editions and limitations](privacy-and-limitations.md).

## Guides and current downloads

- [Batch Compress Images to a 200 KB Limit on Windows — PixPouch](https://heykim.itch.io/pixpouch/devlog/1724495/batch-compress-images-to-a-200-kb-limit-on-windows-pixpouch)
- [WebP to PNG on Windows: Transparency and Larger Files — PixPouch](https://heykim.itch.io/pixpouch/devlog/1724529/webp-to-png-on-windows-transparency-and-larger-files-pixpouch)
- [Windows 批量压缩图片到 200KB 以内：图小匣 PixPouch 实测](https://heykim.itch.io/pixpouch/devlog/1724666/windows-200kb-pixpouch-)
- [Pro 1.1.1: batch export multiple image sizes with presets and file naming](https://heykim.itch.io/pixpouch/devlog/1730788/batch-export-multiple-image-sizes-on-windows-with-presets-and-file-naming)

The three format/size walkthroughs use historical 1.0.2 examples. Current itch.io Free 1.1.1 permits 10 originals per batch; Pro 1.1.1 is a separate one-time USD 2.99 ZIP with a 300-original limit, up to 50 saved single-output presets, up to five output specs and custom naming. Legacy Free 1.0.2 remains free with 300-image basic batches. The current free Store listing also describes 300 images per list; its version is platform-controlled and its listing does not establish Pro access. Daily batch count is unlimited. Read the [four-channel comparison and installation steps](README.md#choose-a-download) before downloading.

