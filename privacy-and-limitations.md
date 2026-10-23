# Local processing, target rules and limitations

[Home](README.md) · [中文首页](README.zh-CN.md)

This page describes the current PixPouch Windows 1.0.2 application. Download platforms have their own account, network, privacy and analytics practices.

## What local processing means

Image processing and export run on the user's Windows PC using local files. The app does not require a PixPouch account or an image upload. Representative processing/export flows worked with the app's browser context set offline, and the application source blocks remote renderer requests. This is not an OS-wide packet audit or a claim that downloading the app needs no internet connection.

Previews and temporary processing outputs are stored in a session folder in the local temporary directory. The app attempts to remove that session folder when it exits; interrupted sessions or cleanup failures may leave temporary files. Exported files remain in the selected output folder. Language and export-folder preferences are stored locally under `%APPDATA%\Qingtu\preferences.json`.

The processing pipeline preserves source files. Exporting to an occupied output name adds a numbered suffix instead of replacing the existing file. Representative source and collision checks confirmed this behavior; no claim is made about unrelated filesystem operations.

## File-size targets include a lower bound

Units are decimal: 1 KB = 1,000 B and 1 MB = 1,000,000 B. For a selected cap of `N` bytes, the allowed interval is:

```text
max(1, N - 4999) through N bytes, inclusive
```

For example, 200 KB allows 195,001–200,000 B. The current app does not offer a separate maximum-only mode or guarantee exact equality with the cap.

Processing automatically adjusts encoding settings and may reduce quality or dimensions. The longest-edge setting preserves the aspect ratio and does not upscale a smaller source; 0 removes the user-set edge cap but does not prevent target-driven resizing. There is no manual quality slider or independent width/height entry.

If the encoded file falls below the interval, valid non-pixel container data may be added to enter the interval. This padding does not improve clarity or restore detail. Conversion may make a source larger. PNG output may use palette quantization to fit a target, so “PNG output” is not a guarantee of unchanged pixels in every case.

Only results that match the current settings and byte interval are exportable. An unattainable target prevents that result from being exported; other valid results can still be saved. Changing settings requires processing again.

## Supported scope and declared limits

- Windows x64 desktop application. The portable download does not include a browser app or macOS, Linux or ARM-native editions.
- JPG, PNG and WebP output only. PNG/WebP keep transparency; JPG uses a white background for transparent regions.
- Multi-frame or multi-page inputs export the first frame or primary image as a still image. Animation retention and frame/page selection are absent.
- Up to 300 images per list; 100,000,000 bytes per source file; 60,000,000 decoded pixels. A worker has a 90-second timeout. These declared boundaries were read from implementation and were not all stress-tested.
- One output format and target are shared by the batch. Selecting a preview row does not create a separate per-image setting.
- Longest edge: 0 or integers from 64 to 16000. No cropping, background replacement, upscaling or AI enhancement.
- Format support depends on the actual file and encoding. Representative checks do not cover all HDR, HEIF, color-management or metadata-preservation workflows.

Fitting a file-size interval does not establish that an upload destination will accept the image. Check its format, strict/inclusive byte boundary, pixel dimensions, aspect ratio and image-content requirements separately.

## Download and support

Use the [itch.io product page](https://heykim.itch.io/pixpouch) or [Microsoft Store](https://apps.microsoft.com/detail/9NWD0K7W4WP3?cid=pixpouch-geo-github). The existing portable ZIP is 423,942,316 bytes; extract it completely and keep all included files together before running 图小匣.exe. The itch.io download is free with optional support, which does not unlock additional processing features.

For a problem report, include Windows version, input format, selected settings and the error message. Avoid sharing private images in public comments. Documentation and screenshots describe representative observed behavior, not a universal quality or compatibility guarantee.

