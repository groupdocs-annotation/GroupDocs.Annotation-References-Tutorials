---
categories:
- Document Processing
date: '2026-04-01'
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中生成不带评论的缩略图。本指南涵盖如何隐藏批注、移除评论预览以及创建干净的
  PDF 预览。
keywords:
- how to generate thumbnails
- how to hide annotations
- remove comments preview
- document preview without comments
- clean pdf preview
lastmod: '2026-04-01'
linktitle: 生成无评论预览
second_title: GroupDocs.Annotation .NET API
tags:
- document-preview
- pdf-thumbnails
- groupdocs
- dotnet
title: 如何在 .NET 中生成缩略图——简洁的 PDF 预览
type: docs
url: /zh/net/advanced-usage/generate-preview-without-comments/
weight: 14
---

# 如何在 .NET 中生成缩略图 – 干净的 PDF 预览

## 介绍

是否曾经需要为文档查看器、文件资源管理器或内容管理系统生成**缩略图**，并且保持图像不包含任何用户备注？你并不孤单。许多 .NET 开发者在尝试创建隐藏批注和评论的文档预览时会遇到障碍。  

在本教程中，我们将逐步演示如何使用 **GroupDocs.Annotation for .NET** 生成干净的 PDF 预览。您将看到如何隐藏批注、去除评论预览，并生成专业外观的缩略图，这些缩略图可以完美适配画廊、仪表板或任何需要无杂乱快照的用户界面。

## 快速答案
- **哪个库可以创建无评论的缩略图？** GroupDocs.Annotation for .NET  
- **哪个属性可以禁用批注？** `RenderComments = false`  
- **我可以选择图像格式吗？** 是的 – 通过 `PreviewFormat` 可使用 PNG、JPEG、BMP 等。  
- **生产环境是否需要许可证？** 需要商业许可证；临时许可证可用于测试。  
- **它仅限 .NET 吗？** 可在 .NET Framework、.NET Core 和 .NET 5/6+ 上使用。

## 什么是无评论的缩略图生成？

无评论的缩略图生成是指渲染每页的视觉快照，**不包含**任何可能已添加到原始文件的标记、注释或协作批注。其结果是一张干净的静态图像，准确呈现文档的真实内容——非常适合面向公众的门户、法律档案或任何需要隐藏内部备注的场景。

## 为什么在创建预览时隐藏批注？

- **专业外观：** 最终用户仅看到文档内容，而非审阅讨论。  
- **安全与隐私：** 敏感评论保持内部。  
- **性能：** 渲染更少的层可加快图像生成。  
- **一致性：** 缩略图与打印或导出的版本保持一致，后者同样省略了评论。

## 前置条件

### 1. 安装 GroupDocs.Annotation for .NET
从官方发行页面 **[此处](https://releases.groupdocs.com/annotation/net/)** 获取包，或通过 NuGet 安装。确保您的项目针对受支持的 .NET 版本。

### 2. 获取许可证
生产使用需要商业许可证。请在 **[此处](https://purchase.groupdocs.com/buy)** 购买，或在 **[此处](https://purchase.groupdocs.com/temporary-license/)** 请求临时评估许可证。

### 3. .NET 知识
您应熟悉 C# 基础、文件 I/O，以及使用 `using` 语句进行资源管理。

## 导入命名空间

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## 分步指南：生成干净的文档预览

### 步骤 1：初始化 Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
`Annotator` 对象加载源文件。`using` 块确保在完成后释放所有非托管资源。

### 步骤 2：配置预览选项
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
这里我们告诉库每页图像的存储位置。lambda 接收页码并返回可写的 `FileStream`。

### 步骤 3：选择格式和页面
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
PNG 可提供清晰的缩略图，但如果文件大小更重要，可切换为 JPEG。选择页面子集可减少处理时间——非常适合仅需前几页的缩略图画廊。

### 步骤 4：禁用评论渲染
```csharp
    previewOptions.RenderComments = false;
```
**此行是“如何隐藏批注”的关键。** 将 `RenderComments` 设置为 `false` 可去除所有评论层，生成干净的 PDF 预览。

### 步骤 5：生成预览图像
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
库会处理文档并将图像写入您先前定义的位置。

## 文档预览生成的最佳实践

- **缩放以适配缩略图：** 生成 PNG 后，考虑将其调整至约 200 × 300 px，以加快 UI 加载。  
- **批量处理大文件：** 初始仅生成前几页，然后按需生成其余页面。  
- **始终使用 `using` 包裹：** 确保正确的内存清理，尤其在处理大量文档时。  
- **添加错误处理：** 捕获 `FileNotFoundException`、`InvalidOperationException` 和许可证错误，以保持应用的健壮性。

## 常见问题与故障排除

- **未生成图像：** 检查输出文件夹是否存在且应用具有写入权限。  
- **缩略图模糊：** 尝试通过设置 `previewOptions.Dpi = 150;` 提高 DPI（代码中未显示，以保持原始块完整）。  
- **大 PDF 导致内存不足错误：** 每次处理单页，或在后台工作者中使用异步 API。  
- **未找到许可证：** 确保在创建 `Annotator` 之前已加载 `License` 对象。

## 性能优化技巧

- **批量处理多个文档：** 遍历集合时尽可能复用单个 `Annotator` 实例。  
- **异步生成：** 将预览创建转移到后台服务，以保持 UI 响应。  
- **缓存结果：** 将生成的缩略图存储在 CDN 或本地缓存中，避免对同一文件重复处理。  
- **选择合适的格式：** 文档包含大量图像时使用 PNG 以获得无损质量，或使用 JPEG 以获得更小文件。

## 支持的文档格式

GroupDocs.Annotation for .NET 可以生成以下格式的预览：

- **PDF** – 最常见的使用场景。  
- **Microsoft Office** – 包括 DOCX、XLSX、PPTX 及其旧版格式。  
- **图像** – TIFF、JPEG、PNG、BMP（适用于扫描文档）。  
- **OpenDocument** – ODT、ODS、ODP 等开放标准。

## 何时使用无评论的预览生成

- **公共门户**，内部审阅备注必须保持隐藏。  
- **档案浏览器**，显示干净的缩略图网格。  
- **可打印工作流**，在发送至打印机前需要展示最终外观。  
- **质量控制检查**，比较“带评论”和“无评论”版本。

## 结论

现在您已经了解如何在 .NET 中**生成缩略图**，并完全去除批注和评论。通过将 `RenderComments = false`，即可获得干净、专业的 PDF 预览，完美适配任何 UI。请记得根据具体场景定制预览格式、页面选择和图像尺寸，并始终妥善处理许可证和错误情况。通过这些步骤，您的应用将提供快速、无杂乱的文档缩略图，提升用户体验。

## 常见问题

**Q: GroupDocs.Annotation for .NET 是否兼容所有文档格式？**  
A: 是的。它支持 PDF、DOCX、PPTX、XLSX、常见图像类型以及许多 OpenDocument 格式。

**Q: 我可以自定义生成的预览外观吗？**  
A: 当然。您可以更改 `PreviewFormat`、设置图像尺寸、 DPI，并选择特定页面进行渲染。

**Q: 该库支持多用户协作吗？**  
A: GroupDocs.Annotation 提供协作批注功能。预览生成可用于创建隐藏所有用户评论的干净视图。

**Q: 如果遇到问题，我可以在哪里获得帮助？**  
A: 社区和支持团队活跃在 **[支持论坛](https://forum.groupdocs.com/c/annotation/10)**，您可以在此提问并分享经验。

**Q: 是否提供免费试用？**  
A: 是的，您可以在 **[此处](https://releases.groupdocs.com/)** 下载完整功能的试用版，以在购买前测试预览生成功能。

---

**最后更新:** 2026-04-01  
**测试环境:** GroupDocs.Annotation for .NET (latest release)  
**作者:** GroupDocs