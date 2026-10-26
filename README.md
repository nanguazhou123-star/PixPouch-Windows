# PixPouch — local batch image compressor and converter for Windows

[简体中文](README.zh-CN.md)

PixPouch (图小匣) compresses, converts and proportionally resizes images on your Windows PC. Add images or a folder, choose JPG, PNG or WebP, set a 200 KB, 500 KB or custom file-size target, then check actual bytes and dimensions before exporting new files. No PixPouch account or image upload is required for processing.

Maintained by **HeyKim**. This repository contains product documentation, format notes and measured examples; it does not publish the application source. Current itch.io editions are **Free 1.1.1** and **Pro 1.1.1**. Historical 1.0.2 measurements are labeled separately below and in the linked guides.

## Choose a download

| Channel / edition | Version | Price and batch limit | Included workflow |
| --- | --- | --- | --- |
| [itch.io Free](https://heykim.itch.io/pixpouch) | 1.1.1 | Free; up to 10 originals per batch | Basic compression, conversion, proportional resizing, comparison and export |
| [itch.io Pro](https://heykim.itch.io/pixpouch) | 1.1.1 | One-time **USD 2.99** purchase; up to 300 originals per batch | Basic workflow, up to 50 saved presets, up to 5 output specs per original, custom filename templates |
| [itch.io Legacy Free](https://heykim.itch.io/pixpouch) | 1.0.2 | Free; up to 300 originals per batch | Historical basic workflow; no 1.1.1 Pro preset, multi-spec or naming features |
| [Microsoft Store](https://apps.microsoft.com/detail/9NWD0K7W4WP3?cid=pixpouch-geo-github) | Check the Store for its current version | Public listing is free and describes up to 300 images per list | Basic workflow described by the Store; this listing does not establish access to itch.io Pro features |

**Daily batch count is unlimited.** Per-batch limits still apply. A 300-image basic batch is also available in Legacy Free 1.0.2 and is described in the current free Store listing; it is not exclusively a paid feature. Store availability and system requirements depend on the platform. Its installed package was not revalidated in the 1.1.1 portable-edition checks.

Pro is a **separate Windows x64 portable ZIP** with its features already enabled. It has no subscription or activation key. itch.io manages purchase and download access; purchasing the Pro file does not upgrade the Free executable or grant a Microsoft Store entitlement. Optional support below the Pro file's purchase threshold does not grant that paid file. To use Pro, purchase access to the Pro file and download that edition.

## Download, extract and start

1. Open the [itch.io product page](https://heykim.itch.io/pixpouch), read the edition labels, and choose Free 1.1.1, Pro 1.1.1 or Legacy Free 1.0.2. For Pro, complete the platform purchase and download the Pro ZIP from your download page.
2. Extract the **entire ZIP** to a folder and keep all included files together.
3. Run **图小匣.exe** from the extracted folder. The English interface is named PixPouch. Check the edition shown in the app before starting a batch.
4. Add images, choose settings, process, inspect the results, choose an export folder and export new files.

Running inside the ZIP or copying only the EXE is not the supported portable workflow. These ZIPs are Windows x64 desktop downloads; they do not include browser, macOS, Linux or ARM-native editions. Portable means extract-and-run; preferences and Pro presets are stored in the Windows user profile. For the Store edition, use the [Microsoft Store page](https://apps.microsoft.com/detail/9NWD0K7W4WP3?cid=pixpouch-geo-github) and its installation flow.

## Basic workflow and Pro additions

- Import supported files, including representative tested HEIC/HEIF inputs, and export JPG, PNG or WebP still images. See [format support and its test scope](format-support.md).
- Choose a shared output format, size target and optional longest-edge limit for an ordinary batch. Resizing preserves aspect ratio and does not upscale smaller sources.
- Drag the comparison divider and inspect output bytes, dimensions, target status and padding notices.
- Export new files while preserving originals. Occupied output names receive a numbered suffix.
- In **Pro 1.1.1**, save and reuse up to **50 single-output presets**, each containing a format, KB target and longest-edge setting. Applying a preset returns to single-output mode; it does not restore a multi-spec setup or filename template.
- In **Pro 1.1.1**, make up to **5 output specs per original**. Each spec has its own name, format, KB target and longest-edge setting. Exported variants are organized into spec subfolders.
- In **Pro 1.1.1**, use filename tokens `{name}`, `{spec}`, `{index}` and `{format}`. For example, `{name}_{spec}_{index}` includes the original name, spec name and a sequence such as `001`; the file extension is added automatically.

PNG and WebP output retain transparency; JPG fills transparent regions with white. Multi-frame or multi-page inputs export a still image from the first frame or primary image. Animation retention and frame/page selection are absent.

## What a 200 KB target means

**The app targets an interval near the cap and has no separate maximum-only mode.** Units are decimal: 1 KB = 1,000 bytes. A 200 KB setting allows **195,001–200,000 bytes**, inclusive. A 30 KB setting allows **25,001–30,000 bytes**.

Processing may lower quality or reduce dimensions. If an encoded result is below the interval, non-pixel data may be added. Padding increases file bytes without adding clarity or detail, and conversion can make a small source larger. Exact byte equality, unchanged dimensions, pixel-identical output and unchanged quality are not guaranteed. For a strict “less than” upload requirement, choose a lower setting and inspect the actual output.

Only valid results matching the current settings and interval can be exported; changing processing settings requires processing again. Each source is limited to **100,000,000 bytes (100 MB)** and **60,000,000 decoded pixels (60 MP)**. Meeting a byte target does not guarantee acceptance by an upload website: check its format, dimensions, aspect ratio and content rules separately.

## Measured examples by version

In the **historical 1.0.2** demonstration recorded on 2026-10-23, one JPEG changed from **789,473 bytes at 1536 × 1024** to **199,207 bytes at 1136 × 757**, with **0 padding bytes**. It met the 200 KB interval and lost resolution; this was not lossless compression.

The **1.1.1 Pro** native checks recorded three synthetic source PNGs exported into two specs, producing six real files. For example, the 3,090,988-byte, 2200 × 1500 landscape sample became a **200,000-byte, 1600 × 1091 JPG** and a **500,000-byte, 2000 × 1364 WebP**. Padding was not recorded for these six outputs. Synthetic samples are demonstrations, not customer data or a general performance benchmark.

See the [complete historical table, current six-file table and verification boundaries](measured-examples.md). Existing 1.1.1 QA recorded 93 Free/Pro checks and a further 26 marketing-flow checks, both passing with no recorded renderer errors. These checks do not establish full format compatibility or Store-installed behavior.

## Frequently asked questions

### Is PixPouch free, and do I have to pay for a 300-image batch?

Free 1.1.1 on itch.io supports 10 originals per batch. Pro 1.1.1 is USD 2.99 once and supports 300, presets, multiple output specs and custom naming. Legacy Free 1.0.2 still offers 300-image basic batches, and the current free Store listing describes 300 images per list. Daily batch count is unlimited.

### Are my images uploaded? Can I process locally without an account?

Processing and export run on your PC without a PixPouch account or image upload. Download and payment platforms have their own network and account practices. Local processing is not a claim that installation needs no internet or that an OS-wide network audit was performed. See [local data and limitations](privacy-and-limitations.md).

### Does “200 KB” mean exactly 200,000 bytes or guaranteed upload acceptance?

No. It means an inclusive 195,001–200,000-byte interval. The app may change quality, dimensions or add non-pixel padding. Check the exported file and the destination's other requirements; choose a lower target for a strict “less than” rule.

### Can PixPouch convert HEIC to JPG or WebP to PNG?

Yes, supported HEIC/HEIF and WebP inputs can be exported as JPG, PNG or WebP. Compatibility depends on the file and encoding. The representative HEIC/HEIF and wider input tests are from 1.0.2; 1.1.1 QA is not a full repeat of that format matrix. WebP-to-PNG conversion can make a file larger.

### Can one original produce several sizes and names?

Pro 1.1.1 supports up to five named output specs per original, each with its own format, KB target and longest edge, plus `{name}`, `{spec}`, `{index}` and `{format}` filename tokens. It also saves up to 50 single-output presets. Applying one returns to single-output mode; presets do not save the multi-spec setup or filename template. Free 1.1.1 and Legacy Free use the basic shared-settings workflow.

### How do Pro purchase, optional support and the Store edition relate?

Pro is a separate paid ZIP on itch.io with features enabled, no subscription and no activation key. Support below the paid file's threshold does not grant that file. Purchase the Pro file and download it; paying does not switch an existing Free executable to Pro, and itch.io and Microsoft Store entitlements do not transfer between channels.

## Guides and support

- [Windows 批量压缩图片到 200KB 以内：图小匣 PixPouch 实测](https://heykim.itch.io/pixpouch/devlog/1724666/windows-200kb-pixpouch-)
- [Batch Compress Images to a 200 KB Limit on Windows — PixPouch](https://heykim.itch.io/pixpouch/devlog/1724495/batch-compress-images-to-a-200-kb-limit-on-windows-pixpouch)
- [WebP to PNG on Windows: Transparency and Larger Files — PixPouch](https://heykim.itch.io/pixpouch/devlog/1724529/webp-to-png-on-windows-transparency-and-larger-files-pixpouch)
- [Pro 1.1.1: batch export multiple image sizes with presets and file naming](https://heykim.itch.io/pixpouch/devlog/1730788/batch-export-multiple-image-sizes-on-windows-with-presets-and-file-naming)
- [Format support](format-support.md) · [Measured examples](measured-examples.md) · [Local processing and limitations](privacy-and-limitations.md)

The three linked format/size walkthroughs use historical 1.0.2 screenshots and measurements. Read their version notes and the edition table above when choosing today's download.

Report problems through [GitHub Issues](https://github.com/nanguazhou123-star/PixPouch-Windows/issues) or the [product page](https://heykim.itch.io/pixpouch). Include your Windows version, download channel, edition/version, input format, settings and error message. Avoid posting private photos publicly.

Documentation updated **2026-10-26**. This documentation update does not change application packages, prices, features or software licensing.

