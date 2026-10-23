# PixPouch format support

[Home](README.md) · [中文首页](README.zh-CN.md)

This page describes PixPouch Windows 1.0.2. File extensions alone do not guarantee compatibility: the individual encoding, profile and file condition matter.

## Input and output formats

| Input | Representative checks | Output options |
| --- | --- | --- |
| JPG / JPEG | Ordinary JPEG and one EXIF orientation-6 example | JPG, PNG, WebP |
| PNG | Transparent PNG | JPG, PNG, WebP |
| WebP | Transparent WebP | JPG, PNG, WebP |
| HEIC / HEIF | One real HEVC HEIC image; a byte-identical `.heif` extension alias | JPG, PNG, WebP |
| GIF | Static GIF and a two-frame animated example | JPG, PNG, WebP still images |
| TIF / TIFF | Two-page TIFF; `.tif` and `.tiff` extension aliases | JPG, PNG, WebP still images |
| AVIF | One ordinary AVIF example | JPG, PNG, WebP |

The representative native checks produced 33 decoded exports across the three output formats. This demonstrates those tested files, not every codec profile, HEIF collection, HDR mode or color workflow. The HEIF alias check is not a separate HEIF codec/profile test.

BMP is not accepted by the current importer. SVG and PDF are not supported inputs. There is no HEIC/HEIF, AVIF, TIFF, GIF, BMP, SVG or PDF export option.

## Transparency, frames and dimensions

- PNG and WebP output retain transparency. JPG fills transparent regions with white.
- Multi-frame or multi-page files use the first frame or primary image and export as still images. There is no frame/page selector or animation-preserving output.
- The optional longest-edge setting accepts 0 or integers from 64 to 16000. The aspect ratio is preserved and smaller sources are not enlarged.
- Setting the longest edge to 0 removes the user-set edge cap. File-size targeting may still reduce dimensions.
- Quality selection is automatic. PNG processing can use palette quantization when fitting a size target; the app does not guarantee lossless or pixel-identical output for every conversion.

Successful conversion does not imply a smaller file. Inspect the actual byte count, dimensions and padding notice before export. See [measured examples](measured-examples.md) and [target rules and limitations](privacy-and-limitations.md).

