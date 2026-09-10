---
categories:
- Document Processing
date: '2026-07-30'
description: 了解如何使用 GroupDocs.Annotation for .NET 从文档 Versions 中检索 Annotations。逐步指南，包含
  code snippets、performance tips 和 troubleshooting。
keywords:
- retrieve annotations from document
- GroupDocs annotation version loading
- .NET document annotation tutorial
- annotated PDF version handling
- load annotated document versions
lastmod: '2026-07-30'
linktitle: 加载 Annotated Document Version
og_description: 使用 GroupDocs.Annotation for .NET 检索文档 Versions 中的 Annotations。本指南展示如何高效加载、比较和保存特定的
  Annotation Versions。
og_image_alt: Guide to loading annotated document versions in .NET using GroupDocs.Annotation
og_title: 检索文档中的 Annotations – 在 .NET 中加载 Versions
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to retrieve annotations from document versions using GroupDocs.Annotation
    for .NET. Step-by-step guide with code snippets, performance tips, and troubleshooting.
  headline: Retrieve Annotations from Document – Load Versions in .NET
  type: TechArticle
- description: Learn how to retrieve annotations from document versions using GroupDocs.Annotation
    for .NET. Step-by-step guide with code snippets, performance tips, and troubleshooting.
  name: Retrieve Annotations from Document – Load Versions in .NET
  steps:
  - name: Define Output Path
    text: We use `Path.Combine` to build a cross‑platform file path and preserve the
      original extension with `Path.GetExtension`.
  - name: Specify Load Options
    text: 'The `LoadOptions` object configures how the document and its annotations
      are loaded, including version selection. The `Version` property selects which
      annotation set to load. Acceptable values are: - `"FIRST"` – the earliest annotation
      version. - `"LAST"` – the most recent annotation version. - Any '
  - name: Initialize Annotator
    text: The `using` statement guarantees that the `Annotator` instance is disposed,
      freeing file handles and unmanaged resources.
  - name: Retrieve Annotations
    text: '`Get()` returns the collection of annotation objects for the loaded version.
      You can iterate, modify, or export them as needed.'
  - name: Save Document with Annotations
    text: '`Save()` writes the current annotations back to a file, optionally preserving
      the original format.'
  - name: Display Confirmation Message
    text: Providing user feedback (e.g., console output, UI toast) improves the overall
      experience.
  type: HowTo
- questions:
  - answer: Yes, the library supports over 30 formats, including PDF, DOCX, PPTX,
      XLSX, and many image types.
    question: Can I annotate documents of various formats with GroupDocs.Annotation
      for .NET?
  - answer: Yes, you can download a fully‑featured trial from [here](https://releases.groupdocs.com/).
    question: Is there a free trial available for GroupDocs.Annotation for .NET?
  - answer: The complete docs are available [here](https://tutorials.groupdocs.com/annotation/net/).
    question: Where can I find official documentation for GroupDocs.Annotation for
      .NET?
  - answer: Request a temporary key from [this link](https://purchase.groupdocs.com/temporary-license/).
    question: How do I obtain a temporary license for development?
  - answer: The community forum is the best place—visit it [here](https://forum.groupdocs.com/c/annotation/10).
    question: Where can I ask technical questions or get support?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- retrieve annotations
- GroupDocs.Annotation
- .NET document processing
- annotation versioning
- C# PDF annotations
title: 检索文档中的 Annotations – 在 .NET 中加载 Versions
type: docs
---

# 从文档检索注释 – 在 .NET 中加载版本

## 介绍

如果您需要快速且可靠地**从文档检索注释**版本，您来对地方了。无论您是在构建法律审查门户、协作设计系统，还是审计跟踪仪表板，处理多个注释修订都是核心需求。GroupDocs.Annotation for .NET 为您提供简洁的 API 来加载任何版本的注释——无论是初稿、最新审阅，还是任何中间检查点。

## 快速答案
- **“从文档检索注释”是什么意思？** 它指的是仅加载附加在文件特定修订上的注释数据。  
- **哪个库支持此功能？** GroupDocs.Annotation for .NET，支持 30 多种文件格式。  
- **我需要许可证吗？** 免费试用可用于测试；生产环境需要商业许可证。  
- **我只能加载第一版或最后一版吗？** 可以——使用 `Version` 选项，值为 `"FIRST"` 或 `"LAST"`。  
- **对大 PDF 安全么？** 是的——在加载单个版本时，500 页的 PDF 内存使用保持在 200 MB 以下。  

## 何时使用此功能

在深入代码之前，请考虑加载特定注释版本至关重要的场景：

- **文档审阅工作流** – 比较不同审阅周期的反馈。  
- **合规与审计** – 为监管机构保留每个注释集的不可变记录。  
- **协作编辑** – 让用户在“草稿”和“最终”注释层之间切换。  
- **回滚场景** – 如果后续编辑导致错误，可恢复到已知良好的注释状态。  

## 先决条件

1. **安装 GroupDocs.Annotation for .NET**  
   从[发布页面](https://releases.groupdocs.com/annotation/net/)下载包。您也可以访问主发布站点[此处](https://releases.groupdocs.com/)。按照 IDE 的安装指南进行操作。  

   **专业提示**：如果您更喜欢 NuGet，请在包管理器控制台中运行以下命令：  
   ```
Install-Package GroupDocs.Annotation
```

2. **获取带有注释的文档**  
   使用已经包含多个注释版本的 PDF、DOCX 或任何 30 多种受支持格式之一。如果是首次测试，请手动创建几个版本。  

## 导入命名空间

`GroupDocs.Annotation` 命名空间为您提供核心对象和加载选项的访问。  
`Annotator` 类是加载和操作文档注释的主要入口点。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

*定义锚点*：`Annotator` 是打开文件、应用加载选项并公开用于检索或保存注释的方法的主要类。  

## 逐步实现

以下是加载特定注释版本的完整步骤顺序。

### 步骤 1：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

我们使用 `Path.Combine` 构建跨平台文件路径，并使用 `Path.GetExtension` 保留原始扩展名。

### 步骤 2：指定加载选项
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```

`LoadOptions` 对象配置文档及其注释的加载方式，包括版本选择。`Version` 属性决定加载哪个注释集。可接受的值有：

- `"FIRST"` – 最早的注释版本。  
- `"LAST"` – 最近的注释版本。  
- 任何您在文档元数据中存储的自定义版本标识符。  

### 步骤 3：初始化 Annotator
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```

`using` 语句确保 `Annotator` 实例被释放，释放文件句柄和非托管资源。

### 步骤 4：检索注释
```csharp
var annotations = annotator.Get();
```

`Get()` 返回已加载版本的注释对象集合。您可以根据需要遍历、修改或导出它们。

### 步骤 5：保存带注释的文档
```csharp
annotator.Save(outputPath);
```

`Save()` 将当前注释写回文件，可选择保留原始格式。

### 步骤 6：显示确认信息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

提供用户反馈（例如控制台输出、UI 提示）可提升整体体验。

## 如何加载特定的注释版本？

使用 `new Annotator(filePath, loadOptions)` 加载文档，其中 `loadOptions.Version` 设置为所需标识符，然后调用 `annotator.Get()` 获取该版本的注释。此单行方法在不触及其他修订的情况下隔离所需版本。您也可以使用常量如 `Version.First` 或 `Version.Last` 指定版本，以确保准确检索目标注释集。

## Annotator 类是什么？

`Annotator` 是 GroupDocs.Annotation 的网关类，负责打开文件、应用 `LoadOptions`，并公开如 `Get()`、`Save()` 和 `GetVersionsList()` 等方法。所有注释操作都通过此对象进行。它管理文档的生命周期，处理资源清理，并提供线程安全的注释数据访问，适用于桌面和 Web 应用程序。

## 常见问题与故障排除

### 未找到版本错误
**问题**：请求的版本标识符不存在时抛出异常。  
**解决方案**：先调用 `annotator.GetVersionsList()` 列出可用版本，然后选择有效的标识符。

### 注释集合为空
**问题**：`Get()` 返回空列表。  
**解决方案**：确认所选版本确实包含注释，并且源文件在之前的保存过程中未被剥离注释元数据。

### 大文档的性能问题
**问题**：对于包含数千个注释的 500 页 PDF，加载需要数秒。  
**解决方案**：  
- 按注释类型过滤（`LoadOptions.AnnotationTypes`）。  
- 使用 `annotator.Get(pageIndex, pageSize)` 实现分页。  
- 如果工作流允许，可在内存中缓存频繁访问的版本。

### 文件路径问题
**问题**：“未找到文件”或访问被拒绝错误。  
**解决方案**：  
- 开发期间使用绝对路径。  
- 确保应用的服务账户对源文件夹和目标文件夹具有读写权限。  
- 如有必要，提前创建输出目录。

## 性能考虑

- **内存占用**：加载单个版本时，典型的 500 页 PDF 内存使用保持在 200 MB 以下。  
- **I/O 优化**：使用共享的 `Annotator` 池批量处理文档，以减少文件打开开销。  
- **网络延迟**：当文件位于云存储时，将调用包装在重试逻辑中，并考虑先将文件流式传输到本地临时文件夹再加载。

## 最佳实践

### 版本命名约定
采用清晰的命名方案，如 `v1.0`、`v1.1-review` 或 ISO 日期戳（`2025-01-02`），使终端用户能够直观地选择版本。

### 错误处理
将所有注释代码包装在 try‑catch 块中，并记录详细的错误信息。

```csharp
try 
{
    using (Annotator annotator = new Annotator(documentPath, loadOptions))
    {
        var annotations = annotator.Get();
        // Process annotations
    }
}
catch (Exception ex)
{
    // Log error and provide user-friendly message
    Console.WriteLine($"Error loading annotations: {ex.Message}");
}
```

### 资源管理
由于 `Annotator` 实现了 `IDisposable`，请始终使用 `using` 语句或显式调用 `Dispose()` 及时释放文件句柄。

## 与现有工作流的集成

- **文档管理系统** – 提供接受版本 ID 并返回相应带注释文件的 API 端点。  
- **RESTful 服务** – 将注释集合以 JSON 形式返回，以供前端渲染。  
- **后台任务** – 安排夜间作业，提取每个版本的注释用于合规报告。  
- **用户界面** – 使用 `annotator.GetVersionsList()` 填充下拉列表，让用户选择想要查看的版本。  

## 结论

您现在拥有使用 GroupDocs.Annotation for .NET **从文档检索注释**版本的完整、可投入生产的模式。请记住：

1. 在 `LoadOptions` 中设置正确的 `Version`。  
2. 正确释放 `Annotator`。  
3. 使用过滤或分页处理大文件。  

通过这些步骤，您可以构建强大、具备版本感知的注释功能，提升协作、审计能力以及无缝回滚。

**最后更新：** 2026-07-30  
**测试环境：** GroupDocs.Annotation 2.3.0 for .NET  
**作者：** GroupDocs  

## 常见问题

**Q: 我可以使用 GroupDocs.Annotation for .NET 对各种格式的文档进行注释吗？**  
A: 是的，库支持超过 30 种格式，包括 PDF、DOCX、PPTX、XLSX 以及多种图像类型。

**Q: GroupDocs.Annotation for .NET 是否提供免费试用？**  
A: 是的，您可以从[此处](https://releases.groupdocs.com/)下载功能完整的试用版。

**Q: 在哪里可以找到 GroupDocs.Annotation for .NET 的官方文档？**  
A: 完整文档可在[此处](https://tutorials.groupdocs.com/annotation/net/)获取。

**Q: 如何获取用于开发的临时许可证？**  
A: 请通过[此链接](https://purchase.groupdocs.com/temporary-license/)请求临时密钥。

**Q: 我可以在哪里提技术问题或获取支持？**  
A: 社区论坛是最佳地点——请访问[此处](https://forum.groupdocs.com/c/annotation/10)。

**Q: 如何列出文档中所有的注释版本？**  
A: 使用 `annotator.GetVersionsList()`；它返回文件中存储的所有版本标识符。

**Q: 加载特定版本会影响其他版本吗？**  
A: 不会——加载是只读的。除非您显式修改并保存，否则其他版本保持不变。

## 相关教程

- [GroupDocs.Annotation .NET 获取注释 - 完整版本键指南](/annotation/net/advanced-usage/get-list-annotations-version-key/)
- [文档版本控制 .NET - 完整 GroupDocs.Annotation 指南](/annotation/net/version-control/load-specific-versions-groupdocs-annotation-net/)
- [文档版本管理 .NET - 跟踪文档版本的完整指南](/annotation/net/advanced-usage/get-all-version-keys-document/)