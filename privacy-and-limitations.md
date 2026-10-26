# PixPouch local processing, target rules and limitations

[Home](README.md) · [中文首页](README.zh-CN.md) · [Format support](format-support.md)

Updated **2026-10-26**. This page describes the current itch.io **Free 1.1.1 / Pro 1.1.1** portable editions and identifies historical or channel-specific facts separately. Download platforms have their own account, payment, network, privacy and analytics practices. This documentation does not change software licensing.

## What local processing means

Images are processed and exported on the user's Windows PC from local files. The app requires neither a PixPouch account nor an image upload. Representative historical processing/export flows worked with the app browser context set offline, and the current application source blocks remote renderer requests. These observations are not an OS-wide packet audit or a promise that downloading, purchasing or installing the app requires no internet connection.

Previews and temporary processing outputs are stored in a session folder in the local temporary directory. The app attempts to remove its session folder on exit; interruptions or cleanup failures may leave temporary files. Exported files stay in the selected output folder.

The current portable editions store preferences locally under `%APPDATA%\Qingtu\preferences.json` for Free and `%APPDATA%\Qingtu-Pro\preferences.json` for Pro. Pro presets are stored in `presets.json` in the Pro user-data directory. Thus, extract-and-run distribution does not mean all user data stays beside the EXE. No cloud synchronization or automatic preference migration between editions is promised.

Processing preserves originals. Exporting to an occupied output name adds a numbered suffix rather than replacing that file. The 1.1.1 native checks confirmed unchanged hashes for the original fixtures after processing/export. This does not describe unrelated filesystem operations performed outside PixPouch.

## File-size targets include a lower bound

Units are decimal: 1 KB = 1,000 B and 1 MB = 1,000,000 B. For a selected cap of `N` bytes, the permitted interval is:

```text
max(1, N - 4999) through N bytes, inclusive
```

| Setting | Allowed output interval, inclusive |
| --- | --- |
| 30 KB | 25,001–30,000 B |
| 100 KB | 95,001–100,000 B |
| 200 KB | 195,001–200,000 B |
| 500 KB | 495,001–500,000 B |

The app has no separate maximum-only mode and does not promise exact equality with the cap. A 200,000-byte file can meet this app's 200 KB interval while failing a destination's strict “less than 200,000 bytes” rule. Choose a lower setting for a strict boundary and verify the actual export.

Encoding automatically adjusts quality and may reduce dimensions. The optional longest edge accepts 0 or integers from 64 to 16000, preserves aspect ratio and does not enlarge smaller sources. Setting it to 0 removes the user-set edge cap but does not prevent target-driven resizing. There is no manual quality slider or independent width/height entry.

If the encoded result falls below the interval, valid non-pixel container data may be added to bring the file into it. Padding adds bytes without improving clarity or restoring detail. A conversion may make a source larger. PNG output may use palette quantization to fit a target, so it is not a universal guarantee of unchanged pixels or lossless processing.

Only valid results matching the current settings and byte interval are exportable. Unattainable results cannot be exported, while other valid results can still be saved. Changing processing settings, including Pro output specs, requires processing again; previous cached results cannot stand in for the new settings.

## Editions and workflow boundaries

| Channel / edition | Version | Price and originals per batch | Workflow |
| --- | --- | --- | --- |
| [itch.io Free](https://heykim.itch.io/pixpouch) | 1.1.1 | Free; up to 10 | Basic shared-settings batch |
| [itch.io Pro](https://heykim.itch.io/pixpouch) | 1.1.1 | USD 2.99 once; up to 300 | Basic batch, up to 50 saved single-output presets, up to 5 specs per original, custom naming |
| [itch.io Legacy Free](https://heykim.itch.io/pixpouch) | 1.0.2 | Free; up to 300 | Historical basic batch |
| [Microsoft Store](https://apps.microsoft.com/detail/9NWD0K7W4WP3?cid=pixpouch-geo-github) | Check the platform | Public listing is free and describes up to 300 per list | Publicly described basic workflow; no itch.io Pro entitlement established |

Daily batch count is unlimited; the per-batch limit is not a daily allowance. Legacy Free 1.0.2 still provides a free 300-original basic workflow, and the Store's public listing describes 300. Do not infer that all 300-image processing requires Pro.

An ordinary batch shares one output format, KB target and longest edge. Selecting a preview row does not assign a separate per-image setting. Pro adds up to five named specs per original, each with its own format, KB target and longest edge; variants export into spec subfolders. Up to 50 saved presets retain single-output settings, not an entire multi-spec setup or filename template. Applying a preset disables multi-spec mode and returns to the single-output workflow. If using a preset as a starting point, apply it before configuring the multiple output specs.

Pro filename tokens are `{name}` (source stem), `{spec}` (spec name), `{index}` (sequence, such as `001`) and `{format}` (`jpg`, `png` or `webp`). Extensions are added automatically. Invalid or unsafe templates are rejected. The actual names should still be inspected before delivery to another system.

## Supported scope and declared limits

- Windows x64 desktop portable packages. No browser app, macOS, Linux or ARM-native edition is included.
- Each source file: at most **100,000,000 bytes (100 MB)** and **60,000,000 decoded pixels (60 MP)**.
- A processing worker has a 90-second timeout. Declared size, pixel and timeout boundaries were read from implementation; they were not all stress-tested by the recorded UI checks.
- Outputs: **JPG, PNG and WebP only**. PNG/WebP retain transparency; JPG fills transparent regions with white.
- Multi-frame/multi-page inputs use the first frame or primary image and export still images. There is no animation retention or frame/page selector.
- Longest edge: 0 or integers from 64 to 16000. No cropping, background replacement, upscaling or AI enhancement.
- Format support depends on each file and encoding. The historical 1.0.2 representative format tests do not establish every HDR, HEIF, color-management or metadata workflow. The 1.1.1 Free/Pro QA is not full format-matrix coverage.

Meeting a file-size interval does not guarantee acceptance by an upload destination. Check the destination's format, inclusive/strict byte boundary, dimensions, aspect ratio and image-content rules separately. See [format support](format-support.md) and [measured examples](measured-examples.md).

## Purchase and download

Use the [itch.io product page](https://heykim.itch.io/pixpouch) for Free 1.1.1, Pro 1.1.1 or Legacy Free 1.0.2. Extract the entire selected ZIP, keep all files together, and run **图小匣.exe** from the extracted folder. Copying only the EXE or running inside the ZIP is not the supported workflow.

Pro is a separate one-time USD 2.99 portable download with features enabled, no subscription and no activation key. itch.io manages access to the paid file. Optional support below that file's purchase threshold does not grant it; purchasing access to the Pro file does. You must download and run Pro rather than expect the Free executable to change editions. itch.io and Microsoft Store purchase/download entitlements do not transfer between channels. Check the Store for its current version, availability and requirements; its installed package was not revalidated in the 1.1.1 portable QA.

For a problem report, include Windows version, channel, edition/version, input format, settings and the error message. Avoid sharing private images in public issues or comments. Screenshots and measured examples describe observed cases, not universal quality, compatibility or upload guarantees.


[Pro 1.1.1 workflow tutorial](https://heykim.itch.io/pixpouch/devlog/1730788/batch-export-multiple-image-sizes-on-windows-with-presets-and-file-naming)

