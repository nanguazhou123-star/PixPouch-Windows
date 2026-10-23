# Measured PixPouch examples

[Home](README.md) · [中文首页](README.zh-CN.md)

These representative demonstration measurements were recorded on 2026-10-23 using the existing PixPouch 1.0.2 native application payload. They are not a newly run benchmark, a complete Store-installed validation, customer results or a guarantee for other inputs. Output byte counts and dimensions were checked against actual exported files.

## Actual files and results

| Example | Source bytes | Output bytes | Source → output pixels | Target | Non-pixel padding |
| --- | ---: | ---: | --- | --- | ---: |
| JPEG photo | 789,473 | 199,207 | 1536 × 1024 → 1136 × 757 | 200 KB | 0 B |
| Different JPEG photo | 214,432 | 195,717 | 1536 × 1024 → 1536 × 1024 | 200 KB | 0 B |
| HEIC → JPG | 730,185 | 200,000 | 1536 × 1024 → 1536 × 1024 | 200 KB | 9,288 B |
| Transparent WebP → PNG | 37,034 | 100,000 | 1200 × 900 → 1200 × 900 | 100 KB | 22,964 B |
| JPEG with longest edge 900 | 789,473 | 198,081 | 1536 × 1024 → 900 × 600 | 200 KB | 0 B |

The first example met the 200 KB interval, but its dimensions also decreased. It is not lossless compression. The second retained its dimensions in this particular run; it still does not establish identical image quality.

The HEIC example demonstrates one tested HEVC image. Its padding adds bytes, not detail. It does not establish support for every HEIC/HEIF profile or HDR workflow.

The transparent WebP-to-PNG example is **larger**, not a compression-saving example. Transparency was retained, and the specific output's decoded RGBA pixels matched the source in the recorded check. That bounded observation is not a universal pixel-preservation guarantee. PNG conversion and padding can both affect file size; converting to PNG cannot restore details already absent from the input.

## Target intervals behind the examples

File sizes use decimal units: 1 KB = 1,000 bytes.

| Setting | Allowed output interval, inclusive |
| --- | --- |
| 30 KB | 25,001–30,000 B |
| 100 KB | 95,001–100,000 B |
| 200 KB | 195,001–200,000 B |
| 500 KB | 495,001–500,000 B |

The current app targets these intervals and has no separate maximum-only mode. Exact equality with the cap is not guaranteed. Outputs below the interval may receive non-pixel padding; unsuitable results cannot be exported. For strict “less than” upload requirements, choose a lower setting and inspect the actual output.

## Walkthroughs with native screenshots

- [Preparing images for a 200 KB upload limit](https://heykim.itch.io/pixpouch/devlog/1724495/how-to-prepare-a-batch-of-images-for-a-200-kb-upload-limit-on-windows-with-pixpouch)
- [Why WebP to PNG can make a file larger](https://heykim.itch.io/pixpouch/devlog/1724529/why-webp-to-png-can-make-a-file-larger-transparency-and-file-size-targets-in-pixpouch)

![Existing native screenshot of the 789473-to-199207-byte JPEG example.](https://img.itch.zone/aW1nLzMxMjU0OTk2LnBuZw==/original/Goctic.png)

The screenshot is an existing native capture. Its preview is not a substitute for checking the exported file's bytes and dimensions.

