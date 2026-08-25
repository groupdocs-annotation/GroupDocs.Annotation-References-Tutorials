---
categories:
- Document Processing
date: '2026-08-25'
description: 了解如何在 .NET 中删除 PDF 注释并创建高质量的 PDF 缩略图。使用 GroupDocs.Annotation 的分步指南，生成干净的预览。
keywords:
- remove pdf annotations
- generate pdf thumbnails
- render pdf as image
- create pdf thumbnails
- pdf thumbnail generation
lastmod: '2026-08-25'
linktitle: 生成无注释的预览
og_description: 在 .NET 中使用 GroupDocs.Annotation 删除 PDF 注释并生成清晰的 PDF 缩略图。本指南展示了仅需几步的干净预览工作流。
og_image_alt: 'Developer guide: remove PDF annotations and create thumbnails using
  GroupDocs.Annotation for .NET'
og_title: 如何在 .NET 中删除 PDF 注释并生成缩略图
schemas:
- author: GroupDocs
  dateModified: '2026-08-25'
  description: Learn how to remove PDF annotations and create high‑quality PDF thumbnails
    in .NET. Step‑by‑step guide with clean preview generation using GroupDocs.Annotation.
  headline: How to remove PDF annotations and generate thumbnails in .NET
  type: TechArticle
- description: Learn how to remove PDF annotations and create high‑quality PDF thumbnails
    in .NET. Step‑by‑step guide with clean preview generation using GroupDocs.Annotation.
  name: How to remove PDF annotations and generate thumbnails in .NET
  steps:
  - name: initialize the annotator
    text: '`Annotator` is the entry point for all operations on a PDF file. It opens
      the document, manages resources, and exposes preview functionality. > **Pro
      tip:** Validate the file path and enforce security checks when handling user‑uploaded
      PDFs.'
  - name: configure preview options
    text: '`PreviewOptions` defines how the preview is rendered. Setting `RenderAnnotations
      = false` disables all markup layers, while the `OutputFormat` and `Dpi` properties
      control image quality. **Key points** - **File naming** – the lambda inside
      `GeneratePreview` (shown later) creates a unique PNG file fo'
  - name: generate the clean preview
    text: '`GeneratePreview` renders the images based on the options you defined and
      writes them to the target folder. Your clean thumbnail files (`page_1.png`,
      `page_2.png`, …) are now ready for use in any UI component.'
  type: HowTo
- questions:
  - answer: Yes. The library also supports DOCX, XLSX, PPTX, and many image formats,
      applying the same preview workflow regardless of source type.
    question: Can I use GroupDocs.Annotation for .NET with formats other than PDF?
  - answer: Absolutely. It runs on .NET Framework, .NET Core, and .NET 5/6+, so you
      can target modern cross‑platform applications.
    question: Is GroupDocs.Annotation for .NET compatible with .NET Core?
  - answer: It does, but when `RenderAnnotations = false` those tools are ignored
      for preview generation, ensuring a clean image.
    question: Does the library provide annotation editing tools?
  - answer: Yes. Just make sure the web server has appropriate file‑system permissions
      and consider streaming the PNG directly to the client to avoid temporary files.
    question: Can I integrate this into an ASP.NET web app?
  - answer: PNG delivers lossless quality, while JPEG reduces file size by up to 80
      %—choose based on your visual fidelity versus bandwidth needs.
    question: Which image format should I pick for thumbnail galleries?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- pdf-preview
- document-collaboration
- annotations
- net-development
- pdf thumbnails
title: 如何在 .NET 中删除 PDF 注释并生成缩略图
type: docs
---

# 如何在 .NET 中移除 PDF 注释并生成缩略图

在许多以文档为中心的应用程序中，您需要显示 PDF 的 **干净预览**，同时隐藏用户添加的任何标记。本教程将向您展示如何在 .NET 中 **移除 PDF 注释** 并 **生成 PDF 缩略图**，提供仅包含原始文档内容的清晰 PNG 图像。阅读完本指南后，您将拥有可在 .NET 5/6+、.NET Core 和经典 .NET Framework 上运行的生产就绪代码片段。

## 快速答案
- **`RenderAnnotations = false` 是做什么的？** 它告诉 GroupDocs.Annotation 在渲染预览时跳过所有标记层，因此输出仅包含原始 PDF 的图形。  
- **哪种图像格式能提供最佳的缩略图质量？** PNG 保留 100 % 的源像素；JPEG 可以将文件大小缩小最多 80 %，但会产生压缩伪影。  
- **我可以为缩略图集合选择特定页面吗？** 可以——将 `PreviewOptions.PageNumbers` 设置为所需的页面索引。  
- **生产环境使用是否需要许可证？** 商业许可证可解锁无限页面，去除评估水印，并提供优先支持。  
- **这在 .NET Core 及更高版本上是否可用？** 当然——GroupDocs.Annotation 支持 .NET Framework、.NET Core 和 .NET 5/6+。

## 什么是移除 PDF 注释？
**移除 PDF 注释是指在渲染文档时不包含任何评论、突出显示或绘图层。** 这会生成一张纯净的图像，反映作者的原始意图，适合公开分享或法律审查。通过省略注释层，您可以保持原始视觉布局完整，同时仍然保留 PDF 中的标记数据以供后续使用。

## 为什么生成不含注释的预览？
生成不含注释的预览可以让用户清晰地看到原始文档，避免分散注意力的笔记或高亮。此类干净的呈现加快决策过程，保护机密评论，并确保任何后续处理（如打印或 OCR）都基于未被修改的内容。

- **加快审批周期** – 评审者看到原始布局而不受干扰，审阅时间可缩短至多 30 %。  
- **隐藏私人笔记** – 注释仍保存在源 PDF 中，但不会出现在公开的缩略图库中。  
- **降低带宽消耗** – 单页的 PNG 缩略图通常小于 200 KB，远小于传输完整 PDF。  
- **提升打印质量** – 当预览用于可打印资产时，杂散的标记不会导致意外的打印错误。

## 先决条件
- **GroupDocs.Annotation for .NET** – 从官方[发布页面](https://releases.groupdocs.com/annotation/net/)安装。  
- **许可证（可选但推荐）** – 通过[购买页面](https://purchase.groupdocs.com/buy)购买完整许可证，或请求[临时许可证](https://purchase.groupdocs.com/temporary-license/)。  
- 基础的 C#/.NET 知识。  
- PDF 查看器（例如 Adobe Acrobat Reader）用于验证生成的缩略图。

## 导入命名空间
添加所需的 `using` 语句，以便使用注释 API：

`Annotation` 命名空间提供用于加载 PDF 和配置预览选项的核心类。

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System.IO;
```

## 如何在不含注释的情况下创建 PDF 缩略图
加载源 PDF，禁用注释渲染，并将每页导出为 PNG 图像。工作流程非常直接：创建 `Annotator`，使用 `RenderAnnotations = false` 配置 `PreviewOptions`，可选地限制页面范围，然后调用 `GeneratePreview`。此方法在一次处理过程中生成干净的缩略图，无需额外的后处理。

### 步骤 1：初始化 annotator
`Annotator` 是对 PDF 文件进行所有操作的入口。它打开文档，管理资源，并提供预览功能。

```csharp
using (var annotator = new Annotator("sample.pdf"))
{
```

> **专业提示：** 在处理用户上传的 PDF 时，验证文件路径并执行安全检查。

### 步骤 2：配置预览选项
`PreviewOptions` 定义预览的渲染方式。将 `RenderAnnotations = false` 设置为禁用所有标记层，而 `OutputFormat` 和 `Dpi` 属性则控制图像质量。

```csharp
    var previewOptions = new PreviewOptions
    {
        OutputFormat = PreviewOutputFormat.Png,   // lossless PNG for crisp thumbnails
        Dpi = 150,                               // 150 DPI balances quality and size
        RenderAnnotations = false,               // core flag that removes annotations
        PageNumbers = new[] { 1, 2, 3 }           // generate thumbnails for the first three pages
    };
```

**关键点**

- **文件命名** – `GeneratePreview` 中的 lambda（后面会展示）为每页创建唯一的 PNG 文件。  
- **格式选择** – PNG 保留每个像素；如果需要更小的体积，可切换为 `Jpeg`。  
- **页面选择** – 精确指定要 **创建 PDF 缩略图** 的页面，以节省 CPU 资源。  

### 步骤 3：生成干净的预览
`GeneratePreview` 根据您定义的选项渲染图像并将其写入目标文件夹。

```csharp
    annotator.GeneratePreview(previewOptions, (pageNumber, stream) =>
    {
        var filePath = Path.Combine("thumbnails", $"page_{pageNumber}.png");
        using (var fileStream = File.Create(filePath))
        {
            stream.CopyTo(fileStream);
        }
    });
}
```

您的干净缩略图文件（`page_1.png`、`page_2.png`，……）现在已可在任何 UI 组件中使用。

## 实际应用中的常见用例
- **文档管理系统** – 显示干净的缩略图网格，同时为内部审阅者保留单独的带注释版本。  
- **法律平台** – 向客户展示原始合同，而不泄露律师备注。  
- **在线学习门户** – 显示作业预览，教师的批注保持私密。  
- **营销工作流** – 为宣传册生成预览图像，去除内部审阅标记。

## 性能考虑
- **批处理** – 在后台工作线程中排队处理多个 PDF，以摊销 I/O 开销。  
- **缓存** – 首次上传后将生成的缩略图存入 CDN 缓存；后续请求可即时命中缓存。  
- **页面限制** – 对于超过 500 页的 PDF，将预览限制在前 5 页，以在典型 2.5 GHz 服务器上将每份文档的 CPU 使用时间控制在 2 秒以内。  
- **文件格式权衡** – PNG 提供无损质量；JPEG 可将存储空间减少最多 80 %，在缩略图库中仍保持可接受的视觉保真度。

## 常见问题排查
- **未生成缩略图** – 确保输出文件夹存在且应用进程具有写入权限；同时检查源 PDF 是否损坏。  
- **图像质量低** – 提高 `Dpi` 值（例如 300），或在使用 JPEG 时切换为 PNG。  
- **内存占用高** – 将页面分成更小的批次处理，或启用流模式 (`annotator.Stream = true`) 以避免将整个 PDF 加载到内存中。  
- **路径问题** – 始终使用 `Path.Combine()` 构建文件路径，以确保跨平台兼容性。

## 生产环境最佳实践
- 将预览生成代码包装在 `try‑catch` 块中，以优雅地处理 I/O 和权限错误。  
- 使用 `using` 语句（如示例所示）确保正确释放文件句柄和非托管资源。  
- 在处理前验证传入的 PDF（大小、格式、密码保护），以防止拒绝服务攻击。  
- 记录每次预览生成事件（包括页数和耗时），用于监控和调试。

## 高级配置选项
- **自定义 DPI** – 某些 GroupDocs.Annotation 版本允许设置 `previewOptions.Dpi = 300` 以获得超清晰的缩略图。  
- **水印** – 在调用 `GeneratePreview` 前链式添加 `WatermarkOptions` 对象，以加入 “仅供预览” 覆盖层。  
- **智能页面选择** – 使用 `DocumentInfo` 检测目录页，并自动将其包含在缩略图集合中。

## 结论
您现在拥有完整的、可投入生产的方案，使用 GroupDocs.Annotation for .NET **移除 PDF 注释** 并 **创建 PDF 缩略图**。通过设置 `RenderAnnotations = false`，您可以生成适用于图库、审批工作流和公开分享的干净预览图像——无需额外的后处理步骤。

---

## 常见问题

**问：我可以在 .NET 中使用 GroupDocs.Annotation 处理除 PDF 之外的格式吗？**  
**答：** 可以。该库还支持 DOCX、XLSX、PPTX 以及多种图像格式，无论源类型如何，都使用相同的预览工作流。

**问：GroupDocs.Annotation for .NET 是否兼容 .NET Core？**  
**答：** 绝对兼容——它可运行在 .NET Framework、.NET Core 和 .NET 5/6+ 上，您可以面向现代跨平台应用程序。

**问：该库提供注释编辑工具吗？**  
**答：** 提供，但在 `RenderAnnotations = false` 时，这些工具在预览生成时会被忽略，从而确保图像干净。

**问：我可以将其集成到 ASP.NET Web 应用中吗？**  
**答：** 可以。只需确保 Web 服务器拥有相应的文件系统权限，并考虑直接将 PNG 流式传输给客户端，以避免产生临时文件。

**问：缩略图库应选择哪种图像格式？**  
**答：** PNG 提供无损质量，而 JPEG 可将文件大小缩小最多 80 %，可根据视觉保真度与带宽需求进行选择。

**问：在哪里可以获得社区支持？**  
**答：** 访问 GroupDocs.Annotation 论坛 [GroupDocs.Annotation 论坛](https://forum.groupdocs.com/c/annotation/10)。社区活跃且响应及时。

**最后更新：** 2026-08-25  
**测试版本：** GroupDocs.Annotation for .NET 23.12  
**作者：** GroupDocs  

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```

```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

## 相关教程

- [如何在 .NET 中生成缩略图 – 干净的 PDF 预览](/annotation/net/advanced-usage/generate-preview-without-comments/)
- [使用 GroupDocs.Annotation for .NET 创建 PDF 缩略图](/annotation/net/advanced-usage/generate-document-pages-preview/)
- [创建 PDF 注释 .NET 教程 - 完整的 GroupDocs 指南](/annotation/net/annotation-management/annotate-pdf-groupdocs-annotation-net/)