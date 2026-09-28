---
categories:
- Document Processing
date: '2026-09-20'
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中删除 PDF 注释并生成干净的缩略图。本指南展示了如何隐藏注释、创建无评论预览以及生成专业的
  PDF 缩略图。
keywords:
- remove pdf comments
- hide pdf annotations
- file explorer pdf thumbnail
- render pdf pages images
- pdf to png thumbnail
lastmod: '2026-09-20'
linktitle: 生成无评论预览
og_description: 在 .NET 中使用 GroupDocs.Annotation 删除 PDF 注释并创建干净的缩略图。按照分步说明隐藏注释、选择 formats
  并 optimize performance。
og_image_alt: Guide showing clean PDF thumbnail generation in .NET using GroupDocs.Annotation
og_title: 如何在 .NET 中删除 PDF 注释并生成缩略图
schemas:
- author: GroupDocs
  dateModified: '2026-09-20'
  description: Learn how to remove PDF comments and generate clean thumbnails in .NET
    using GroupDocs.Annotation. This guide shows how to hide annotations, create comment‑free
    previews, and produce professional PDF thumbnails.
  headline: How to remove PDF comments and generate thumbnails in .NET
  type: TechArticle
- description: Learn how to remove PDF comments and generate clean thumbnails in .NET
    using GroupDocs.Annotation. This guide shows how to hide annotations, create comment‑free
    previews, and produce professional PDF thumbnails.
  name: How to remove PDF comments and generate thumbnails in .NET
  steps:
  - name: Initialize the annotator
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and processing documents. The `Annotator` object loads the source file. The
      `using` block guarantees that all unmanaged resources are released once we’re
      done.'
  - name: Configure preview options
    text: '`PreviewOptions` defines how each page is rendered, including format, DPI,
      and output stream. Here we tell the library where to store each page’s image.
      The lambda receives the page number and returns a writable `FileStream`.'
  - name: Choose format and pages
    text: PNG delivers crisp thumbnails, but you can switch to JPEG if file size is
      a bigger concern. Selecting a subset of pages reduces processing time—perfect
      for thumbnail galleries that only need the first few pages.
  - name: Disable rendering of comments
    text: '`RenderComments` is a boolean flag that tells the renderer whether to include
      annotation comment layers in the output. **This line is the key to “how to hide
      annotations.”** Setting `RenderComments` to `false` strips out all comment layers,
      giving you a clean PDF preview.'
  - name: Generate the preview images
    text: The library processes the document and writes the images to the locations
      you defined earlier.
  type: HowTo
- questions:
  - answer: Yes. It supports PDF, DOCX, PPTX, XLSX, common image types, and many OpenDocument
      formats.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Absolutely. You can change `PreviewFormat`, set image dimensions, DPI,
      and choose specific pages to render.
    question: Can I customize the look of the generated previews?
  - answer: GroupDocs.Annotation offers collaborative annotation features. The preview
      generation can be used to create clean views that hide all user comments.
    question: Does the library support multi‑user collaboration?
  - answer: The community and support team are active on the **[support forum](https://forum.groupdocs.com/c/annotation/10)**
      where you can ask questions and share experiences.
    question: Where can I get help if I run into issues?
  - answer: Yes, you can download a full‑function trial **[full‑function trial download](https://releases.groupdocs.com/)**
      to test the preview generation capabilities before purchasing.
    question: Is there a free trial available?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- remove pdf comments
- pdf thumbnail
- groupdocs annotation
- dotnet preview
title: 如何在 .NET 中删除 PDF 注释并生成缩略图
type: docs
url: /zh/net/advanced-usage/generate-preview-without-comments/
weight: 14
---

# 如何在 .NET 中删除 PDF 注释并生成缩略图

## 介绍

如果您需要在为文档查看器、文件资源管理器或内容管理系统生成缩略图的同时**删除 PDF 注释**，那么您来对地方了。许多 .NET 开发者在生成隐藏用户笔记和批注的干净预览时遇到困难。在本教程中，我们将逐步演示如何使用 **GroupDocs.Annotation for .NET** 创建无注释的 PDF 缩略图。您将学习如何隐藏批注、配置输出格式，并生成专业外观的图像，完美适用于画廊、仪表盘或任何需要无杂乱快照的 UI。

## 快速答案
- **哪个库可以创建无注释的缩略图？** GroupDocs.Annotation for .NET  
- **哪个属性可以禁用批注？** `RenderComments = false`  
- **我可以选择图像格式吗？** 是 – PNG、JPEG、BMP 等，通过 `PreviewFormat`  
- **生产环境需要许可证吗？** 需要商业许可证；临时许可证可用于测试。  
- **它仅限 .NET 吗？** 支持 .NET Framework、.NET Core 和 .NET 5/6+。

## 什么是无注释的缩略图生成？

无注释的缩略图生成是指渲染每页的视觉快照，**不包含**可能已添加到原始文件的任何标记、注释或协作批注。其结果是一张干净的静态图像，真实地呈现文档内容——非常适合面向公众的门户、法律档案或任何需要隐藏内部备注的场景。

## 为什么在创建预览时隐藏批注？

隐藏批注可以让预览保持专业、安全且快速。渲染更少的层级可减少处理时间，保护敏感备注，并确保缩略图与最终打印或导出的版本一致，后者同样不包含批注。

- **专业外观：** 最终用户仅看到文档内容，而不是审阅讨论。  
- **安全与隐私：** 敏感批注保持内部。  
- **性能：** 渲染更少的层级加快图像生成。  
- **一致性：** 缩略图与同样省略批注的打印或导出版本保持一致。

## 前置条件

### 1. 安装 GroupDocs.Annotation for .NET
从官方分发页面 **[官方分发页面](https://releases.groupdocs.com/annotation/net/)** 获取包，或通过 NuGet 安装。确保您的项目针对受支持的 .NET 版本。

### 2. 获取许可证
生产使用需要商业许可证。购买请访问 **[购买页面](https://purchase.groupdocs.com/buy)**，或申请临时评估许可证 **[临时评估许可证页面](https://purchase.groupdocs.com/temporary-license/)**。

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

## 步骤指南：生成干净的文档预览

### 步骤 1：初始化 Annotator

`Annotator` 是 GroupDocs.Annotation 的主要入口，用于加载和处理文档。  
`Annotator` 对象加载源文件。`using` 块确保在完成后释放所有非托管资源。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```

### 步骤 2：配置预览选项

`PreviewOptions` 定义每页的渲染方式，包括格式、DPI 和输出流。  
这里我们告诉库每页图像的存储位置。lambda 接收页码并返回可写的 `FileStream`。

```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```

### 步骤 3：选择格式和页面

PNG 可生成清晰的缩略图，但如果更关注文件大小，也可以切换为 JPEG。选择页面子集可减少处理时间——非常适合仅需前几页的缩略图画廊。

```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```

### 步骤 4：禁用批注渲染

`RenderComments` 是一个布尔标志，指示渲染器是否在输出中包含批注评论层。  
**此行是“如何隐藏批注”的关键。** 将 `RenderComments` 设置为 `false` 可去除所有评论层，生成干净的 PDF 预览。

```csharp
    previewOptions.RenderComments = false;
```

### 步骤 5：生成预览图像

库会处理文档并将图像写入之前定义的位置。

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

## 文档预览生成的最佳实践

- **缩略图尺寸调整：** 生成 PNG 后，考虑将其调整至约 200 × 300 px，以加快 UI 加载。  
- **批量处理大文件：** 初始仅生成前几页，然后按需生成其余页面。  
- **始终使用 `using` 包裹：** 确保正确的内存清理，尤其在处理大量文档时。  
- **添加错误处理：** 捕获 `FileNotFoundException`、`InvalidOperationException` 和许可证错误，以保持应用的健壮性。

## 常见问题与故障排除

- **未生成图像：** 检查输出文件夹是否存在且应用具有写入权限。  
- **缩略图模糊：** 尝试通过设置 `previewOptions.Dpi = 150;` 提高 DPI（代码中未显示，以保持原始块完整）。  
- **大 PDF 内存不足错误：** 一次处理单页，或在后台工作者中使用异步 API。  
- **未找到许可证：** 确保在创建 `Annotator` 前已加载 `License` 对象。

## 性能优化技巧

- **批量处理文档：** 循环遍历集合，尽可能复用单个 `Annotator` 实例。  
- **异步生成：** 将预览创建转移到后台服务，以保持 UI 响应。  
- **缓存结果：** 将生成的缩略图存储在 CDN 或本地缓存中，避免对同一文件重复处理。  
- **选择合适的格式：** PNG 提供无损质量，文档包含大量图像时使用 JPEG 可减小文件体积。

## 支持的文档格式

GroupDocs.Annotation for .NET 支持 **30+** 种输入和输出格式，可为 PDF、Office 文件、图像以及 OpenDocument 标准生成预览。

- **PDF** – 最常见的使用场景。  
- **Microsoft Office** – DOCX、XLSX、PPTX 及其旧版对应格式。  
- **Images** – TIFF、JPEG、PNG、BMP（适用于扫描文档）。  
- **OpenDocument** – ODT、ODS、ODP 等开放标准。

## 何时使用无批注预览生成

无批注预览生成非常适合内部审阅备注需隐藏的公共门户、展示干净缩略图网格的档案浏览器、需要在打印前展示最终外观的打印就绪工作流，以及需要比较有无批注版本的质量控制检查。

## 结论

现在您已经了解了在 .NET 中**删除 PDF 注释并生成缩略图**的完整方法，同时彻底去除批注。通过将 `RenderComments = false`，即可获得干净、专业的 PDF 预览，完美融入任何 UI。请根据具体场景调整预览格式、页面选择和图像尺寸，并始终妥善处理许可证和错误情况。遵循这些步骤，您的应用将提供快速、无杂乱的文档缩略图，提升用户体验。

## 常见问题

**Q: GroupDocs.Annotation for .NET 是否兼容所有文档格式？**  
A: 是的。它支持 PDF、DOCX、PPTX、XLSX、常见图像类型以及许多 OpenDocument 格式。

**Q: 我可以自定义生成预览的外观吗？**  
A: 完全可以。您可以更改 `PreviewFormat`，设置图像尺寸、DPI，并选择特定页面进行渲染。

**Q: 该库支持多用户协作吗？**  
A: GroupDocs.Annotation 提供协作批注功能。预览生成可用于创建隐藏所有用户评论的干净视图。

**Q: 如果遇到问题，我可以在哪里获得帮助？**  
A: 社区和支持团队活跃在 **[支持论坛](https://forum.groupdocs.com/c/annotation/10)**，您可以在此提问并分享经验。

**Q: 是否提供免费试用？**  
A: 是的，您可以下载完整功能的试用版 **[完整功能试用下载](https://releases.groupdocs.com/)**，在购买前测试预览生成功能。

**最后更新:** 2026-09-20  
**测试环境:** GroupDocs.Annotation for .NET (latest release)  
**作者:** GroupDocs

## 相关教程

- [在 .NET 中生成无批注的文档预览](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [使用 GroupDocs.Annotation for .NET 创建 PDF 缩略图](/annotation/net/advanced-usage/generate-document-pages-preview/)
- [如何删除 PDF 批注（C#）– GroupDocs.Annotation 指南](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)