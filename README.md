# PixPouch — local batch image conversion for Windows

[简体中文](README.zh-CN.md)

PixPouch (图小匣) is a Windows desktop tool for local batch image compression, format conversion and proportional resizing. Choose a 200 KB, 500 KB or custom target, then inspect actual output sizes and dimensions before exporting new files.

Maintained by **HeyKim**. This repository publishes product guides, format notes and measured examples for PixPouch Windows 1.0.2.

## Download

- [Microsoft Store](https://apps.microsoft.com/detail/9NWD0K7W4WP3?cid=pixpouch-geo-github)
- [itch.io product page and Windows x64 ZIP](https://heykim.itch.io/pixpouch)

The itch.io download is free with optional support. A donation does not unlock additional processing features. The existing 1.0.2 portable ZIP is **423,942,316 bytes**; itch.io displays about **404 MB**. This download contains a Windows x64 desktop application.

Extract the entire ZIP, keep all included files together, and run **图小匣.exe**. The English interface is named PixPouch. Running only a copied EXE or launching it inside the ZIP is not the supported portable workflow. Browser, macOS, Linux and ARM-native editions are not included in this download. Check the Store page for its current system requirements and availability.

## What you can do

- Add images or a folder and process a batch using one shared output format and target.
- Convert supported inputs, including HEIC/HEIF, to JPG, PNG or WebP still images.
- Set an optional longest-edge limit while preserving the aspect ratio and avoiding upscaling.
- Drag the comparison divider and inspect actual output size, dimensions, target status and padding notices.
- Export new files while preserving sources; occupied output names receive a numbered suffix.
- Process images locally without a PixPouch account or image upload.

PNG and WebP output retain transparency. JPG uses white for transparent regions. Multi-frame or multi-page inputs export a still image from the first frame or primary image.

## How file-size targets work

**The current app targets a narrow interval near the cap; it has no separate maximum-only mode.** Units are decimal: 1 KB = 1,000 bytes. A 200 KB setting permits **195,001–200,000 bytes**, including both endpoints. A 30 KB setting permits **25,001–30,000 bytes**.

Processing may lower quality or reduce dimensions. If an encoded result is below the interval, non-pixel data may be added. Padding increases file bytes without adding clarity or detail, and conversion can make a small source larger. Exact byte equality, unchanged dimensions and unchanged image quality are not guaranteed. For a strict “less than” requirement, choose a lower setting and inspect the actual output.

Results outside the selected interval cannot be exported. Changing output settings requires processing again.

## A measured example

One recorded JPEG changed from **789,473 bytes at 1536 × 1024** to **199,207 bytes at 1136 × 757**, with **0 padding bytes**. It met the 200 KB target interval and also lost resolution; this was not lossless compression. These are representative demonstration measurements from 2026-10-23, not a guaranteed result for every file.

![PixPouch 1.0.2 showing a JPEG processed from 789473 to 199207 bytes, with output dimensions 1136 by 757 pixels.](https://img.itch.zone/aW1nLzMxMjU0OTk2LnBuZw==/original/Goctic.png)

## Documentation and walkthroughs

- [中文：Windows 如何批量把图片处理到 200KB 以内？用图小匣实测](https://heykim.itch.io/pixpouch/devlog/1724666/windows-200kb-)

- [Format support](format-support.md)
- [Measured examples](measured-examples.md)
- [Local processing, target rules and limitations](privacy-and-limitations.md)
- [Preparing a batch for a 200 KB upload limit](https://heykim.itch.io/pixpouch/devlog/1724495/how-to-prepare-a-batch-of-images-for-a-200-kb-upload-limit-on-windows-with-pixpouch)
- [Why WebP to PNG can make a file larger](https://heykim.itch.io/pixpouch/devlog/1724529/why-webp-to-png-can-make-a-file-larger-transparency-and-file-size-targets-in-pixpouch)

For bug reports and feature feedback, use [GitHub Issues](https://github.com/nanguazhou123-star/PixPouch-Windows/issues) or the [product page](https://heykim.itch.io/pixpouch). Include your Windows version, input format, target settings and error message. Avoid posting private photos in public comments or issues.

Documentation updated 2026-10-24. Measurements describe the existing 1.0.2 app, not a newly built release.

