# PixPouch image format support

[Home](README.md) · [中文首页](README.zh-CN.md) · [Measured examples](measured-examples.md)

Updated **2026-10-26**. Current itch.io downloads are Free 1.1.1 and Pro 1.1.1. The representative input-format evidence in the table below comes from **historical PixPouch Windows 1.0.2 native checks**. Current importer declarations and the 1.1.1 workflow checks do not turn those historical tests into a full 1.1.1 format-matrix retest.

File extensions alone do not guarantee compatibility: the individual encoding, profile and condition of the file matter.

## Input and output formats

| Declared input | Representative 1.0.2 checks | Output options |
| --- | --- | --- |
| JPG / JPEG | Ordinary JPEG and one EXIF orientation-6 example | JPG, PNG, WebP |
| PNG | Transparent PNG | JPG, PNG, WebP |
| WebP | Transparent WebP | JPG, PNG, WebP |
| HEIC / HEIF | One real HEVC HEIC image; a byte-identical `.heif` extension alias | JPG, PNG, WebP |
| GIF | Static GIF and a two-frame animated example | JPG, PNG, WebP still images |
| TIF / TIFF | Two-page TIFF; `.tif` and `.tiff` extension aliases | JPG, PNG, WebP still images |
| AVIF | One ordinary AVIF example | JPG, PNG, WebP |

Those historical native checks produced **33 decoded exports** across the three output formats. This demonstrates the tested files, not every codec profile, HEIF collection, HDR mode or color workflow. A HEIF extension alias is not a separate codec/profile test. The `.tif`/`.tiff` aliases likewise do not establish different TIFF encodings.

The current importer declares the same listed extensions. **BMP, SVG and PDF are not accepted inputs.** Outputs are **JPG, PNG and WebP only**; there is no HEIC/HEIF, AVIF, TIFF, GIF, BMP, SVG or PDF export option. No promise is made that all metadata, ICC/color behavior or HDR properties survive conversion.

## What 1.1.1 QA establishes

The recorded fixed Free/Pro 1.1.1 native run contains **93 passing checks** covering edition identity, 10/300 import boundaries, Free feature locks, preset reuse and restart persistence, multiple output specs, naming, real exports, source preservation and selected layouts. A subsequent **26-check** run verifies the synthetic-sample marketing/export workflow. Both recorded no renderer errors.

The current six-output example starts with **three synthetic PNG sources** and exports JPG/WebP variants. A transparent product sample retains transparency in its WebP output and receives a white background in JPG. These are bounded PNG-to-JPG/WebP observations. They do not newly validate HEIC/HEIF, GIF, TIFF, AVIF, every PNG profile or every color/metadata workflow in 1.1.1. Check your own files before relying on a batch.

## Transparency, frames and dimensions

- PNG and WebP output retain transparency. JPG fills transparent regions with white.
- Multi-frame or multi-page files use the first frame or primary image and export as still images. There is no frame/page selector or animation-preserving output.
- The optional longest edge accepts 0 or integers from 64 to 16000. Aspect ratio is preserved and smaller sources are not enlarged.
- Setting the longest edge to 0 removes the user-set cap; file-size targeting may still reduce dimensions.
- Encoding quality is automatic. PNG processing can use palette quantization to fit a target; unchanged pixels or lossless conversion are not guaranteed for every file.

Successful conversion need not produce a smaller file. For example, a historical transparent WebP-to-PNG conversion grew from 37,034 B to 100,000 B, including non-pixel padding. Conversion cannot restore absent image detail. Inspect actual bytes, dimensions and padding notices before export.

## Limits and editions

Each source is limited to **100,000,000 bytes (100 decimal MB)** and **60,000,000 decoded pixels (60 MP)**. Daily batch count is unlimited. itch.io Free 1.1.1 allows up to 10 originals per batch; Pro 1.1.1 allows 300 and adds up to 50 saved single-output presets, up to five independent output specs per original and custom naming. Legacy Free 1.0.2 remains free with up to 300 originals for the basic workflow. The current free Store listing describes 300 images per list; its version is platform-controlled and its listing does not establish itch.io Pro access.

A 200 KB target permits **195,001–200,000 B**, inclusive, using decimal units. Quality reduction, resizing and non-pixel padding may be used; there is no separate maximum-only mode. Meeting this interval does not guarantee acceptance by an upload website. Read [target rules and limitations](privacy-and-limitations.md) before processing important files.

## Related guides

- [Batch Compress Images to a 200 KB Limit on Windows — PixPouch](https://heykim.itch.io/pixpouch/devlog/1724495/batch-compress-images-to-a-200-kb-limit-on-windows-pixpouch)
- [WebP to PNG on Windows: Transparency and Larger Files — PixPouch](https://heykim.itch.io/pixpouch/devlog/1724529/webp-to-png-on-windows-transparency-and-larger-files-pixpouch)
- [Windows 批量压缩图片到 200KB 以内：图小匣 PixPouch 实测](https://heykim.itch.io/pixpouch/devlog/1724666/windows-200kb-pixpouch-)
- [Pro 1.1.1: batch export multiple image sizes with presets and file naming](https://heykim.itch.io/pixpouch/devlog/1730788/batch-export-multiple-image-sizes-on-windows-with-presets-and-file-naming)

The three format/size walkthroughs retain historical 1.0.2 screenshots and measurements. Use the [current edition table and download steps](README.md#choose-a-download) when selecting a package.

