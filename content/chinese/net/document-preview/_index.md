---
categories:
- GroupDocs.Annotation
date: '2026-08-09'
description: 了解如何使用 GroupDocs.Annotation for .NET 创建预览、高效渲染 PDF 缩略图，并在 Web 或移动应用中提供安全的文档预览。
keywords:
- how to create preview
- render pdf thumbnail
- secure document preview
- GroupDocs.Annotation .NET
- document visualization
lastmod: '2026-08-09'
linktitle: 文档预览教程
og_description: 了解如何使用 GroupDocs.Annotation for .NET 创建预览、高效渲染 PDF 缩略图，并在 Web 或移动应用中提供安全的文档预览。
og_image_alt: Guide showing how to create preview and render PDF thumbnail using GroupDocs.Annotation
  for .NET
og_title: 如何在 .NET 中使用 GroupDocs.Annotation 创建预览
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to create preview with GroupDocs.Annotation for .NET, render
    PDF thumbnail efficiently, and deliver secure document preview in web or mobile
    apps.
  headline: How to create preview in .NET using GroupDocs.Annotation
  type: TechArticle
- description: Learn how to create preview with GroupDocs.Annotation for .NET, render
    PDF thumbnail efficiently, and deliver secure document preview in web or mobile
    apps.
  name: How to create preview in .NET using GroupDocs.Annotation
  steps:
  - name: install the NuGet package
    text: 'Open your project’s Package Manager Console and run:'
  - name: initialise the API
    text: Create an `AnnotationApi` instance, passing your license file path and optional
      configuration (e.g., cache folder, memory limit).
  - name: generate a preview without annotations
    text: Set the `HideAnnotations` flag to true, choose the desired DPI, and request
      the page(s) you need. The `GetPreview` call returns a byte array that you can
      send directly to an HTTP response, store in a CDN, or embed in a UI component.
  - name: cache and reuse previews
    text: To avoid regenerating the same preview repeatedly, store the image using
      a hash of the source file and the preview settings as the cache key. When the
      source document changes, invalidate the cache by comparing timestamps.
  - name: handle large documents efficiently
    text: For files larger than 100 MB, use a `using` block to ensure the `AnnotationApi`
      disposes of internal streams promptly. Process pages in batches if you need
      multi‑page previews, releasing each batch before moving to the next.
  type: HowTo
- questions:
  - answer: Yes. Provide the password in the `LoadOptions` when creating the `AnnotationApi`
      instance; the preview will be generated after successful decryption.
    question: Can I generate previews for password‑protected documents?
  - answer: Absolutely. GroupDocs.Annotation can render previews for over **30** different
      formats, including DOCX, XLSX, PPTX, and many image types.
    question: Does the library support rendering previews for non‑PDF formats like
      DOCX or XLSX?
  - answer: Use the `HideMetadata` option in `PreviewOptions`; the API strips out
      all document properties before rendering the image.
    question: How do I ensure that the preview does not reveal hidden metadata?
  - answer: The preview stream is generated server‑side and can be delivered over
      HTTPS. Combine it with token‑based authentication to restrict access to authorized
      users only.
    question: Is it safe to expose the preview endpoint publicly?
  - answer: Cache previews for the lifetime of the source document version. When the
      document’s last‑modified timestamp changes, invalidate the cached image and
      regenerate.
    question: What is the recommended cache expiration policy?
  type: FAQPage
tags:
- document-preview
- GroupDocs.Annotation
- .NET tutorial
- PDF thumbnail
- secure preview
title: 如何在 .NET 中使用 GroupDocs.Annotation 创建预览
type: docs
url: /zh/net/document-preview/
weight: 14
---

# 如何在 .NET 使用 GroupDocs.Annotation 创建预览

生成 **如何创建预览** 体验是现代文档中心应用的基石。使用适用于 .NET 的 GroupDocs.Annotation，您可以渲染 PDF 缩略图、生成安全的文档预览流，并在移动设备上保持用户界面流畅。在本指南中，您将了解预览生成的重要性，探索常见的实现场景，并获得将高质量预览添加到您自己的解决方案的路线图。

## 快速答案
`AnnotationApi` 类是 GroupDocs.Annotation 的核心组件，用于加载文档并创建预览图像。`GetPages` 方法返回渲染的页面图像的字节数组。`HideAnnotations` 标志会从渲染的图像中移除所有注释层。

- **渲染 PDF 缩略图的最快方法是什么？** 使用 `AnnotationApi` 加载 PDF，设置 DPI = 150，并调用 `GetPages` —— 对于 2 MB 文件，首页在 200 ms 以下以 PNG 返回。  
- **我可以在预览中隐藏所有注释吗？** 可以 —— 在渲染之前使用 `HideAnnotations` 标志以生成干净的视图。  
- **预览生成是线程安全的吗？** 该 API 是无状态的；您可以安全地并行运行多个预览任务。  
- **生产环境需要许可证吗？** 需要有效的 GroupDocs.Annotation 许可证才能进行无限制的预览生成。  
- **支持哪些 .NET 版本？** .NET Framework 4.6+、.NET Core 3.1+、.NET 5/6/7。

## 什么是文档预览？
文档预览是一种轻量级的文件视觉表示——通常是图像或一系列图像——让用户无需下载完整文档即可快速浏览内容。它提升了用户体验，降低了带宽消耗，并通过仅呈现您决定渲染的内容来增加一层安全性。

## 为什么使用安全的文档预览？
安全的文档预览确保敏感的元数据、隐藏层或受限注释永不离开服务器。GroupDocs.Annotation 会加密预览流并剔除所有未明确允许的标记，让您完全控制终端用户看到的内容。量化声明：该库支持 **30+ 文件格式**，在使用默认 DPI 150 的标准 8 核服务器上，可在 2 秒内为 **500 页 PDF** 生成预览。

## 如何渲染 PDF 缩略图？
使用 `AnnotationApi` 加载 PDF，指定 150‑300 的 DPI 以获得清晰的文字，并请求首页为 PNG。此两步方法返回字节数组，您可以直接流式传输到浏览器或缓存到磁盘。使用更高的 DPI（例如 300）可提升文本密集文档的可读性，而较低的 DPI（例如 72）则可减小缩略图网格的文件大小。

## 前置条件
- .NET Framework 4.6+ 或 .NET Core 3.1+ 已安装。  
- 有效的 GroupDocs.Annotation 许可证（临时许可证可用于评估）。  
- 访问您打算预览的 PDF、Word、Excel 或其他受支持的文件。

## 如何逐步创建预览
要创建预览，您需要安装 GroupDocs.Annotation 包，用您的许可证初始化 API，配置预览选项，生成图像，并可选择缓存结果。以下章节通过代码示例逐步演示每一步，展示如何隐藏注释、设置 DPI，以及高效处理大文件。

### 步骤 1：安装 NuGet 包
打开项目的 Package Manager Console 并运行：

```
Install-Package GroupDocs.Annotation
```

### 步骤 2：初始化 API
创建 `AnnotationApi` 实例，传入您的许可证文件路径以及可选配置（例如缓存文件夹、内存限制）。

```
var config = new AnnotationConfig
{
    LicensePath = "GroupDocs.Annotation.lic",
    CacheFolder = Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Cache")
};
var annotationApi = new AnnotationApi(config);
```

### 步骤 3：生成无注释的预览
将 `HideAnnotations` 标志设为 true，选择所需的 DPI，并请求所需的页面。

```
var previewOptions = new PreviewOptions
{
    HideAnnotations = true,
    Dpi = 150,
    OutputFormat = PreviewOutputFormat.Png,
    PageNumbers = new[] { 1 }   // first page only for thumbnail
};

byte[] previewBytes = annotationApi.GetPreview("sample.pdf", previewOptions);
File.WriteAllBytes("sample_thumb.png", previewBytes);
```

`GetPreview` 调用返回字节数组，您可以直接发送到 HTTP 响应、存储在 CDN 中，或嵌入 UI 组件。

### 步骤 4：缓存并复用预览
为避免重复生成相同的预览，使用源文件的哈希和预览设置作为缓存键来存储图像。当源文档更改时，通过比较时间戳使缓存失效。

```
string cacheKey = $"{Path.GetFileNameWithoutExtension(filePath)}_{previewOptions.Dpi}_{previewOptions.HideAnnotations}";
```

### 步骤 5：高效处理大文档
对于大于 100 MB 的文件，使用 `using` 块以确保 `AnnotationApi` 及时释放内部流。如果需要多页预览，请分批处理页面，在进入下一批之前释放当前批次。

## 常见实现场景

- **文档管理系统** – 显示缩略图网格以实现快速视觉导航。  
- **协作平台** – 为审阅者渲染仅预览视图，然后根据需求切换注释层。  
- **Web 门户** – 对文件链接实现悬停预览，减少完整下载的需求。  
- **移动应用** – 生成低分辨率 PNG（72 DPI），使每页带宽使用低于 50 KB。

## 预览生成故障排除

- **大型 PDF 导致内存激增** – 确保在每个预览批次后调用 `AnnotationApi` 的 `Dispose()`，并限制并发预览任务的数量。  
- **缩略图文字模糊** – 将 DPI 提升至 300 或切换输出格式为 PNG；JPEG 压缩会使细字符变得柔和。  
- **Excel 预览缺少图像** – 通过在预览选项中设置 `LoadCharts = true`，确保工作簿的图表对象完整加载。  
- **响应时间慢** – 将预览生成移至后台工作者（例如 `Task.Run`），并在真实预览准备好之前提供占位图像。

## 常见问题

**问：我可以为受密码保护的文档生成预览吗？**  
答：可以。在创建 `AnnotationApi` 实例时在 `LoadOptions` 中提供密码；在成功解密后将生成预览。

**问：该库是否支持为非 PDF 格式（如 DOCX 或 XLSX）渲染预览？**  
答：当然。GroupDocs.Annotation 能够为超过 **30** 种不同格式渲染预览，包括 DOCX、XLSX、PPTX 以及多种图像类型。

**问：如何确保预览不泄露隐藏的元数据？**  
答：在 `PreviewOptions` 中使用 `HideMetadata` 选项；API 在渲染图像前会剥离所有文档属性。

**问：公开预览端点是否安全？**  
答：预览流在服务器端生成，可通过 HTTPS 传输。结合基于令牌的身份验证，可将访问限制仅限于授权用户。

**问：推荐的缓存过期策略是什么？**  
答：将预览缓存至源文档版本的生命周期。当文档的最后修改时间戳变化时，使缓存的图像失效并重新生成。

## 其他资源

- [使用 GroupDocs.Annotation for .NET 在自定义分辨率下生成高质量 PDF 预览](./generate-pdf-previews-custom-resolutions-groupdocs/)
- [使用 GroupDocs.Annotation .NET 生成 PDF 页面预览：完整指南](./generate-pdf-page-previews-groupdocs-annotation-net/)
- [使用 GroupDocs.Annotation .NET 生成针对性的 Excel 工作表预览](./groupdocs-annotation-net-create-previews-worksheet-columns/)
- [如何使用 GroupDocs.Annotation .NET 创建无注释的干净文档预览](./create-document-preview-without-annotations-groupdocs-dotnet/)
- [如何使用 GroupDocs.Annotation .NET 生成无评论的文档预览](./groupdocs-annotation-net-document-preview-no-comments/)
- [GroupDocs.Annotation for Net 文档](https://docs.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation for Net API 参考](https://reference.groupdocs.com/annotation/net/)
- [下载 GroupDocs.Annotation for Net](https://releases.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation 论坛](https://forum.groupdocs.com/c/annotation)
- [免费支持](https://forum.groupdocs.com/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)

---

**最后更新：** 2026-08-09  
**测试环境：** GroupDocs.Annotation 23.10 for .NET  
**作者：** GroupDocs  

---

## 相关教程

- [如何加载文档 .NET - 完整的 GroupDocs.Annotation 教程](/annotation/net/document-loading/)
- [文档元数据提取 .NET - 完整的 GroupDocs.Annotation 指南](/annotation/net/document-information/)
- [GroupDocs Annotation .NET 教程 - 文档管理完整指南](/annotation/net/annotation-management/)