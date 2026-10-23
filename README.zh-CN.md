# 图小匣 PixPouch — Windows 本地批量图片处理

[English](README.md)

图小匣（PixPouch）是一款 Windows 桌面图片压缩、格式转换与等比例缩图工具。添加图片或文件夹，选择 200 KB、500 KB 或自定义目标，在导出前查看实际文件大小、尺寸和目标状态。

由 **HeyKim 维护**。本仓库用于发布 PixPouch Windows 1.0.2 的使用指南、格式说明与实际测量示例。

## 下载与启动

- [Microsoft Store](https://apps.microsoft.com/detail/9NWD0K7W4WP3?cid=pixpouch-geo-github)
- [itch.io 产品页与 Windows x64 便携 ZIP](https://heykim.itch.io/pixpouch)

itch 当前免费，可自愿支持；支持金额不解锁额外处理功能。现有 1.0.2 便携 ZIP 为 **423,942,316 字节**，itch 页面显示约 **404 MB**。

请完整解压 ZIP，保留所有文件，再运行 **图小匣.exe**。英文界面名为 PixPouch；只复制一个 EXE 或直接在 ZIP 内运行不属于便携包的正确启动方式。该下载为 Windows x64 桌面软件，不含浏览器版、macOS、Linux 或 ARM 原生版本。商店的当前系统要求和可用地区以商店页面为准。

## 主要功能

- 添加多张图片或文件夹，整批使用相同输出格式和大小目标。
- 将支持的输入（含 HEIC/HEIF）转换为 JPG、PNG、WebP 静态图片。
- 设置最长边，保持比例，不放大小图。
- 拖动分隔线比较原图与结果，核对实际字节、尺寸、目标状态及填充提示。
- 导出新文件并保留原图；遇到已有同名文件时加数字后缀。
- 在本机处理，无需 PixPouch 账户或上传图片。

PNG/WebP 输出保留透明，JPG 将透明区域变为白色。动画、多帧或多页输入仅导出首帧或主图，不保留动画。

## “200 KB”实际代表什么

**当前采用接近上限的目标区间，没有独立的“仅最大值”模式。** 1 KB = 1000 字节。200 KB 对应 **195001–200000 字节**，包含上下界；30 KB 对应 **25001–30000 字节**。

为达到目标，程序可能降低画质或缩小尺寸。编码结果低于区间时，可能加入非像素数据补足文件体积；填充不增加清晰度或细节，转换后的文件也可能更大。不保证每张恰好等于目标、保留原尺寸或画质不变。若上传要求严格小于某个字节数，请调低设置并核对实际输出。

不符合目标区间的结果无法导出；改变处理设置后需要重新处理。文件大小达标不代表上传网站会通过审核，还应检查格式、像素尺寸、比例与内容要求。

## 真实测量示例

一张 JPG 从 **789473 字节、1536×1024**，处理为 **199207 字节、1136×757**，填充为 **0 字节**。它符合 200 KB 目标区间，同时降低了分辨率，不能称为无损压缩。数据来自 2026-10-23 的代表性演示样本，不保证其他图片得到相同结果。

![PixPouch 1.0.2 真实界面：JPG 从 789473 字节处理为 199207 字节，输出 1136×757 像素。](https://img.itch.zone/aW1nLzMxMjU0OTk2LnBuZw==/original/Goctic.png)

## 使用资料

- [Windows 如何批量把图片处理到 200KB 以内？用图小匣实测](https://heykim.itch.io/pixpouch/devlog/1724666/windows-200kb-)

- [格式支持与透明处理（英文）](format-support.md)
- [实际测量数据（英文）](measured-examples.md)
- [本地处理、目标规则与限制（英文）](privacy-and-limitations.md)
- [200 KB 上传目标教程（英文）](https://heykim.itch.io/pixpouch/devlog/1724495/how-to-prepare-a-batch-of-images-for-a-200-kb-upload-limit-on-windows-with-pixpouch)
- [WebP 转 PNG 为什么会变大（英文）](https://heykim.itch.io/pixpouch/devlog/1724529/why-webp-to-png-can-make-a-file-larger-transparency-and-file-size-targets-in-pixpouch)

问题与建议可提交至 [GitHub Issues](https://github.com/nanguazhou123-star/PixPouch-Windows/issues) 或[产品页](https://heykim.itch.io/pixpouch)，请提供 Windows 版本、输入格式、处理设置和错误提示；请勿在公开评论或 Issue 中直接发布私人照片。

文档更新于 2026-10-24，描述既有 1.0.2 版本，不代表发布了新软件包。

