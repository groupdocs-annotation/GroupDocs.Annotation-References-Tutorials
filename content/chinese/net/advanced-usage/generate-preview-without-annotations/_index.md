---
categories:
- Document Processing
date: '2026-04-01'
description: 学习如何在 .NET 中创建 PDF 缩略图并生成不带批注的干净 PDF 预览。使用 GroupDocs.Annotation 的 PDF
  缩略图生成代码的逐步指南。
keywords:
- create pdf thumbnails
- generate pdf preview
- remove annotations preview
- render pdf without markup
- pdf thumbnail generation
lastmod: '2025-01-02'
linktitle: 生成无注释的预览
second_title: GroupDocs.Annotation .NET API
tags:
- pdf-preview
- document-collaboration
- annotations
- net-development
title: 在 .NET 中创建 PDF 缩略图——无注释的干净预览
type: docs
url: /zh/net/advanced-usage/generate-preview-without-annotations/
weight: 13
---

# 在 .NET 中创建 PDF 缩略图 – 无注释的干净预览

在为画廊、审批工作流或公开共享 **创建 pdf 缩略图** 时，生成干净的文档预览是常见需求。在本教程中，您将学习如何 **创建 pdf 缩略图**，省略所有注释，为用户提供原始 PDF 内容的纯净视图。

## 快速答案
- **RenderAnnotations = false 是什么作用？** 它告诉 GroupDocs.Annotation 在渲染预览时跳过所有标记。  
- **哪种图像格式适合高质量缩略图？** PNG 提供无损质量；JPEG 文件更小但有损。  
- **我可以为缩略图集合选择特定页面吗？** 是的 – 将 `PreviewOptions.PageNumbers` 设置为您需要的页面。  
- **生产环境使用是否需要许可证？** 建议使用许可证以获得无限功能和支持。  
- **此方法是否兼容 .NET Core？** 完全兼容 – GroupDocs.Annotation 可在 .NET Framework 和 .NET Core 上运行。

## 什么是 “create pdf thumbnails”？
创建 PDF 缩略图是指将 PDF 的每一页渲染为图像（PNG/JPEG），以便在 UI 中显示。缩略图对于快速预览、文档浏览器以及在不加载完整 PDF 的情况下生成预览网格非常有用。

## 为什么生成不带注释的预览？
从预览中移除注释可使焦点保持在原始文档内容上。这一点在以下场景中尤为重要：
- **文档审批工作流** – 将干净版本与带注释的版本进行比较。  
- **缩略图画廊** – 避免评论或高亮导致的视觉杂乱。  
- **公开共享** – 在仍显示文档的同时保护敏感标记。  
- **打印准备** – 生成干净的 PDF 供打印，同时保持数字笔记分离。

## 前置条件
- **GroupDocs.Annotation for .NET** – 从官方的 [releases page](https://releases.groupdocs.com/annotation/net/) 安装。  
- **License (optional but recommended)** – 通过 [purchase page](https://purchase.groupdocs.com/buy) 购买完整许可证，或请求 [temporary license](https://purchase.groupdocs.com/temporary-license/)。  
- 基本的 C#/.NET 知识。  
- 用于验证生成的缩略图的 PDF 查看器（例如 Adobe Acrobat Reader）。

## 导入命名空间
添加所需的 `using` 语句，以便使用注释 API：

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

## 如何在不带注释的情况下创建 PDF 缩略图

下面是一步步的演示，向您展示如何 **生成 pdf 预览** 图像，同时从输出中 **移除注释预览**。

### 步骤 1：初始化 Annotator
创建指向源 PDF 的 `Annotator` 实例。`using` 块可自动释放资源。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```

> **专业提示：** 在处理用户上传的 PDF 时，验证文件路径并执行适当的安全检查。

### 步骤 2：配置预览选项
设置 `PreviewOptions` 以定义输出格式、页面范围，并关键性地禁用注释渲染。

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

**关键点**
- **文件命名** – lambda 为每页创建唯一的 PNG 文件。  
- **格式选择** – PNG 用于高质量缩略图；切换到 JPEG 可获得更小的文件。  
- **页面选择** – 明确指定要进行 **pdf thumbnail generation** 的页面。  
- **`RenderAnnotations = false`** – 这会禁用所有标记，是 **disable annotations preview** 的核心。

### 步骤 3：生成干净的预览
调用 `GeneratePreview` 方法，根据您定义的选项渲染图像。

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

您的干净缩略图文件（`result1.png`、`result2.png`，…）现在已可使用。

## 实际应用中的常见用例
- **文档管理系统** – 为文件浏览器提供干净的缩略图，同时保留单独的带注释版本。  
- **法律审查平台** – 向客户展示没有内部评论的原始合同。  
- **在线学习门户** – 显示原始作业，教师将评分笔记保持私密。  
- **出版工作流** – 为营销材料创建预览图像，而不包含编辑标记。

## 性能考虑因素
- **批处理** – 在单个后台任务中处理多个 PDF，以降低开销。  
- **缓存** – 在首次上传后存储生成的缩略图，避免每次请求都重新渲染。  
- **页面限制** – 对于非常大的 PDF，限制预览仅前几页，以保持处理时间低。  
- **文件格式权衡** – PNG 提供清晰的缩略图；在带宽受限时 JPEG 可减少存储。

## 常见问题排查
- **未创建缩略图** – 验证输出文件夹的写入权限，并确保源 PDF 未损坏。  
- **图像质量低** – 切换到 PNG，或在 GroupDocs.Annotation 支持的情况下调整 DPI 设置。  
- **内存使用高** – 将页面分成更小的批次处理，或流式读取 PDF 而不是一次性加载到内存。  
- **路径问题** – 始终使用 `Path.Combine()` 构建文件路径，以确保跨平台安全。

## 生产环境最佳实践
- 将预览生成包装在 `try‑catch` 块中，以优雅地处理 I/O 错误。  
- 使用 `using` 语句（如示例所示）确保正确释放文件句柄。  
- 在处理之前验证传入的 PDF（大小、格式、密码保护）。  
- 记录每次预览生成事件，以便监控和调试。

## 高级配置选项
- **自定义 DPI** – 某些版本允许设置更高分辨率，以获得更清晰的缩略图。  
- **水印** – 添加 “Preview Only” 水印，以表明图像不是最终文档。  
- **智能页面选择** – 根据文档元数据自动挑选最相关的页面（例如首页、目录）。

## 结论
您现在拥有完整的、可投入生产的方案，可 **create pdf thumbnails** 并 **generate pdf preview** 图像而不带任何标记。通过设置 `RenderAnnotations = false`，您 **remove annotations preview**，并提供干净、专业的缩略图，能够无缝集成到任何以文档为中心的应用中。

---

## 常见问题

**Q: 我可以在 .NET 中使用 GroupDocs.Annotation 处理除 PDF 之外的格式吗？**  
A: 可以。该库支持 DOCX、XLSX、PPTX 等多种格式。无论源格式如何，预览工作流相同。

**Q: GroupDocs.Annotation for .NET 是否兼容 .NET Core？**  
A: 完全兼容。它可在 .NET Framework、 .NET Core 以及 .NET 5/6+ 上运行，您可以面向现代跨平台应用程序。

**Q: 该库是否提供可自定义的注释工具？**  
A: 提供，但当您设置 `RenderAnnotations = false` 时，这些工具在预览生成时会被忽略。

**Q: 我可以将其集成到 Web 应用程序中吗？**  
A: 可以。只需确保 Web 服务器具有适当的文件 I/O 权限，并考虑将输出直接流式传输给客户端，以避免临时文件。

**Q: 缩略图画廊应选择哪种图像格式？**  
A: PNG 提供最佳质量，而 JPEG 可减小文件大小。根据所需的视觉保真度与带宽限制进行选择。

**Q: 我可以在哪里获得社区支持？**  
A: 您可以在 GroupDocs.Annotation 论坛 [here](https://forum.groupdocs.com/c/annotation/10) 获得帮助。社区活跃且响应及时。

**最后更新：** 2026-04-01  
**测试环境：** GroupDocs.Annotation for .NET 23.12  
**作者：** GroupDocs  

---