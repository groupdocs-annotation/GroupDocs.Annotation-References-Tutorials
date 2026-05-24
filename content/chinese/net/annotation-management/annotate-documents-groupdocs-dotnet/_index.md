---
categories:
- Document Processing
date: '2026-05-21'
description: 了解如何在 C# 中使用 GroupDocs Annotation .NET 对 PDF 文件进行批注。本分步指南涵盖设置、添加、更新以及管理
  PDF 批注，适用于法律、教育和企业场景。
keywords:
- how to annotate pdf
- legal document annotation
- collaborative pdf markup
- create document review system
lastmod: '2026-05-21'
linktitle: GroupDocs Annotation .NET 指南
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to annotate PDF files with GroupDocs Annotation .NET in C#.
    This step‑by‑step guide covers setup, adding, updating, and managing PDF annotations
    for legal, education, and enterprise use cases.
  headline: How to Annotate PDF using GroupDocs Annotation .NET (C#) Guide
  type: TechArticle
- questions:
  - answer: Yes, the free trial provides full functionality for 30 days but adds evaluation
      watermarks to every output file. For any production deployment you must apply
      a temporary or full license to remove those watermarks.
    question: Can I use GroupDocs.Annotation .NET without a license?
  - answer: The library works with .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5,
      .NET 6, and .NET 7, making it suitable for both legacy Windows services and
      modern cross‑platform containers.
    question: Which .NET versions are supported by GroupDocs.Annotation?
  - answer: Pricing starts around $1,999 for a developer license and scales with the
      number of deployed applications. Check the [GroupDocs pricing page](https://purchase.groupdocs.com/buy)
      for the latest rates and volume discounts.
    question: How much does GroupDocs.Annotation .NET cost?
  - answer: Over **50 formats** are supported, including PDF, DOC/DOCX, PPT/PPTX,
      XLS/XLSX, JPEG, PNG, TIFF, and many more. PDF receives the most comprehensive
      feature set, including vector‑based shapes and OCR‑ready redaction.
    question: What document formats can I annotate with GroupDocs.Annotation?
  - answer: 'Yes. Provide the password when constructing the `Annotator`:'
    question: Can I annotate password‑protected PDFs?
  type: FAQPage
tags:
- GroupDocs
- Annotation
- C#
- PDF
- Document Management
title: 使用 GroupDocs Annotation .NET (C#) 对 PDF 进行批注的指南
type: docs
url: /zh/net/annotation-management/annotate-documents-groupdocs-dotnet/
weight: 1
---

# 如何使用 GroupDocs Annotation .NET (C#) 对 PDF 进行注释

是否曾经需要以编程方式 **how to annotate pdf** 文件，并想知道哪个库既强大又简洁？无论您是在构建法律审查平台、电子学习系统，还是协作文档工作流，GroupDocs.Annotation .NET 都提供了可直接在 C# 代码中添加、编辑和删除 PDF 注释的生产就绪 API。在本指南中，您将学习实现完整注释引擎所需的一切，从初始设置到大规模文档库的性能调优。

## 快速答案
- **什么是向 PDF 添加文本注释的最快方法？** 使用 `Annotator` 加载文档，创建 `TextAnnotation`，设置其 `Box` 和 `Message`，然后调用 `Add()` —— 对于常规页面，整个过程不到一秒。  
- **支持哪些 .NET 版本？** .NET Framework 4.6.1+、.NET Core 2.0+、.NET 5、.NET 6 和 .NET 7。  
- **生产环境是否需要许可证？** 是的——完整或临时许可证可去除水印并解锁全部功能。  
- **我可以在 4 GB 服务器上处理 200 页的 PDF 吗？** 可以，通过使用批处理和后文展示的正确释放模式实现。  
- **GroupDocs.Annotation 适合法律文档注释吗？** 绝对适合——它支持超过 50 种格式，提供细粒度权限控制，并具备审计就绪的元数据。

## 什么是 “how to annotate pdf”？

**“How to annotate pdf”** 指的是以编程方式向 PDF 文件添加标记——例如评论、高亮、形状或马赛克的过程。使用 GroupDocs.Annotation .NET，您可以自动化此工作流，将注释数据存储在数据库中，并在网页或桌面查看器中即时渲染结果。

## 为什么使用 GroupDocs.Annotation 进行 PDF 标记？

GroupDocs.Annotation 支持 **50+ 种输入和输出格式**，能够在不将整个文件加载到内存的情况下处理高达 **500 MB** 的 PDF，并在每个请求创建独立 `Annotator` 实例时提供 **线程安全** 操作。与仅支持 PDF 的轻量库相比，它还允许使用相同的 API 对 Word、PowerPoint 和图像文件进行注释，从而显著降低多格式平台的开发工作量。

## 实际应用场景：文档注释的价值所在

了解业务背景有助于您选择合适的注释类型。

- **法律文档审查** – 律师添加评论、高亮条款并附加修订历史。GroupDocs.Annotation 使用用户 ID、时间戳以及可选的数字签名来跟踪每一次更改，以满足审计合规要求。  
- **教育平台** – 教师可以通过绘制形状、添加便签或直接在学生 PDF 上嵌入音频反馈来批改作业。  
- **医疗文档** – 临床医生在注释放射报告或患者病历时，仍能保留符合 HIPAA 的元数据。  
- **软件文档** – 技术作者在 API 规范上协作，插入标注框和修订说明，而无需离开源 PDF。  
- **金融服务** – 合规官员对贷款协议、风险评估和审计轨迹进行标注，然后导出注释版以进行归档。

## 前置条件和设置：准备您的环境

### 系统要求

- **IDE**：Visual Studio 2019 或更高版本（Community 版亦可）。  
- **运行时**：.NET Framework 4.6.1+ **或** .NET Core 2.0+（大型 PDF 推荐 8 GB RAM）。  
- **权限**：对保存注释 PDF 的文件夹具有写入权限。

### 知识前提

- 基本的 C# 语法和面向对象概念。  
- 熟悉 NuGet 包管理。  
- 了解文件 I/O（读取/写入流）。

### 安装 GroupDocs.Annotation .NET

您可以通过 NuGet 添加该库。请选择符合您工作流的方法。

**使用 NuGet 包管理器控制台**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**使用 .NET CLI**（CI/CD 流水线首选）  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

> **专业提示：** 始终固定版本号（例如 `Install-Package GroupDocs.Annotation -Version 23.12`）。这可防止在包自动更新时意外出现破坏性更改。请查看最新发布信息，访问 [GroupDocs 发布页面](https://releases.groupdocs.com/annotation/net/)。

### 许可证选项：为您的项目选择合适方案

- **免费试用** – 完整功能，带有评估水印，期限 30 天。  
- **临时许可证** – 去除水印，期限 30 天，适用于概念验证。请参阅 [临时许可证页面](https://purchase.groupdocs.com/temporary-license/)。  
- **完整许可证** – 无限的生产使用、优先支持且无水印。通过 [GroupDocs 商店](https://purchase.groupdocs.com/buy) 购买。

### 基本项目设置

创建一个新的 C# 控制台或 ASP.NET 项目，并在安装包后添加以下 using 语句：

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System.IO;
using System.Collections.Generic;

// Initialize Annotator with an input document path
string inputPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf");
```

> **重要提示：** 将 `YOUR_DOCUMENT_DIRECTORY` 替换为指向 PDF 的绝对路径。使用 `Path.Combine` 可确保在 Windows 和 Linux 上使用正确的路径分隔符。

## 步骤教程：添加您的第一个注释

### 如何加载 PDF 文档进行注释？

`Annotator` 类是加载文档并管理所有注释操作的核心组件。正确加载 PDF 可确保库在进行任何更改之前读取页面尺寸、元数据和现有注释。  
使用 `Annotator` 构造函数加载 PDF，传入文件路径和可选的加载选项。此步骤会验证文件并准备可安全修改的内存表示，同时在提供密码时处理加密文件。

```csharp
try 
{
    using (Annotator annotator = new Annotator(inputPath))
    {
        // Your annotation code goes here
        Console.WriteLine("Document loaded successfully!");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

`try‑catch` 块可防止因文件缺失、PDF 损坏或不受支持的格式而导致异常，确保应用程序能够优雅地失败，而不是崩溃。

### 如何向 PDF 添加文本注释？

`TextAnnotation` 表示一种便签式评论，可放置在 PDF 页面上。添加过程包括创建对象、定义位置、设置显示的消息，最后通过 `Annotator` 将其插入文档。  
创建 `TextAnnotation` 对象，使用 `Box` 属性定义其边界矩形，设置可见的 `Message`，然后在 `Annotator` 上调用 `Add()`。注释会立即出现在指定页面上，您还可以根据需要通过颜色和不透明度设置自定义外观。

```csharp
// Create a highlight annotation
HighlightAnnotation highlight = new HighlightAnnotation
{
    Box = new Rectangle(100, 100, 200, 20), // x, y, width, height
    CreatedOn = DateTime.Now,
    Message = "This section needs review",
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Please verify these numbers",
            RepliedOn = DateTime.Now
        }
    }
};

// Add the annotation to the document
annotator.Add(highlight);
```

> **为何 `Box` 属性重要：** 矩形使用点（1 point = 1/72 英寸）并以页面左下角为原点进行测量。精确的坐标可让您将注释准确放置在审阅者期望的位置。

### 如何在不覆盖源文件的情况下保存注释后的 PDF？

保存为新文件可保留原始文档，以便审计追踪和回滚场景。`Save` 方法将所有更改（包括新注释和元数据）写入指定路径，同时保持源文件不变。  
在 `Annotator` 上调用 `Save()` 并提供新的文件路径。这可保留原始文档，对审计追踪和回滚至关重要，若需要转换，还可以选择不同的输出格式。

```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "annotated_document.pdf");
annotator.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

> **最佳实践：** 将原始版和注释版存放在不同的版本控制文件夹中。此策略可简化合规监管和变更追踪。

## 高级注释技术

### 如何在一次操作中添加多种注释类型？

GroupDocs.Annotation 提供丰富的注释类——`HighlightAnnotation`、`StrikeoutAnnotation`、`PolylineAnnotation`、`RedactionAnnotation` 等。通过创建每个实例、配置属性并在保存前将它们添加到同一个 `Annotator`，可最小化 I/O 并保持文档状态一致。  
实例化每种注释类型，设置其特定属性（颜色、不透明度、点等），并顺序添加到同一 `Annotator` 实例中。当调用 `Save()` 时，所有注释将一起写入，确保原子更新并降低部分写入的风险。

```csharp
// Text annotation for comments
TextAnnotation textNote = new TextAnnotation
{
    Box = new Rectangle(300, 200, 100, 30),
    Message = "Review required",
    CreatedOn = DateTime.Now,
    FontColor = 16711680, // Red color in RGB
    BackgroundColor = 16777215 // White background
};

// Arrow annotation to point out specific elements
ArrowAnnotation pointer = new ArrowAnnotation
{
    Box = new Rectangle(150, 150, 50, 50),
    Message = "Important calculation here",
    CreatedOn = DateTime.Now
};

// Add all annotations at once
annotator.Add(textNote);
annotator.Add(pointer);
```

### 如何更新现有注释的颜色或评论？

`GetById` 方法通过唯一标识符检索特定注释，允许您仅修改所需字段。获取对象后，您可以更改 `Color` 或 `Message` 等属性，然后使用 `Update` 保存更改。  
使用 `GetById()` 通过唯一 `Id` 检索注释，修改所需属性（例如 `Color`、`Message`），并调用 `Update()`。此方法避免重新创建注释，保留其原始位置、版本历史以及任何附加的回复。

```csharp
// Get all annotations from the document
List<AnnotationBase> annotations = annotator.Get();

// Find and update a specific annotation
foreach (var annotation in annotations)
{
    if (annotation.Message.Contains("Review required"))
    {
        annotation.Message = "Review completed ✓";
        annotator.Update(annotation);
        break;
    }
}
```

> **性能提示：** 对于拥有成千上万注释的文档，可将注释 ID 缓存到字典中，以避免线性搜索。

## 常见问题与故障排除

### 问题 1 – “不支持的文档格式”

**直接答案：** 确认文件扩展名在 GroupDocs.Annotation 支持的格式列表中；如果不在，请先将文件转换为 PDF，或使用处理该格式的其他 GroupDocs 产品。  
**解决方案：**  
- 查看 [支持的格式列表](https://docs.groupdocs.com/annotation/net/supported-document-formats/)  
- 使用 GroupDocs.Conversion 在注释前将不支持的文件转换为 PDF。  

```csharp
// Check if format is supported before processing
string extension = Path.GetExtension(inputPath).ToLower();
if (extension != ".pdf" && extension != ".docx" && extension != ".pptx")
{
    throw new NotSupportedException($"File format {extension} is not supported");
}
```

### 问题 2 – 注释位置错误

**直接答案：** 确保使用正确的坐标系（原点在左下角），并尊重页面的旋转元数据。相应调整 `Box` 值。  
**解决方案：**  
```csharp
// Always validate coordinates before adding annotations
private bool IsValidCoordinate(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

### 问题 3 – 大文档内存问题

**直接答案：** 将大 PDF 分批处理，在每批后释放 `Annotator`，并启用流模式以避免将整个文件加载到内存。  
**解决方案：**  

```csharp
// Process large documents in chunks
using (Annotator annotator = new Annotator(inputPath))
{
    // Set memory-friendly options
    LoadOptions loadOptions = new LoadOptions
    {
        PreviewPageCount = 1 // Load pages on demand
    };
    
    // Process annotations in batches
    const int batchSize = 10;
    for (int i = 0; i < annotations.Count; i += batchSize)
    {
        var batch = annotations.Skip(i).Take(batchSize);
        foreach (var annotation in batch)
        {
            annotator.Add(annotation);
        }
        
        // Force garbage collection between batches for large documents
        if (i % 50 == 0)
        {
            GC.Collect();
            GC.WaitForPendingFinalizers();
        }
    }
}
```

## 性能优化技巧

### 如何高效批量处理数千个 PDF？

将注释请求收集到列表中，对每个文档打开一个 `Annotator`，应用所有更改，然后一次性调用 `Save()`。这可降低 I/O 开销，利用内部缓冲，并在大规模工作负载下保持内存使用可预测。  
将注释请求收集到列表中，对每个文档打开一个 `Annotator`，应用所有更改，然后一次性调用 `Save()`。这可降低 I/O 开销并利用内部缓冲。

```csharp
// Inefficient approach (don't do this)
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
    annotator.Save(outputPath); // Saving after each annotation is expensive
}

// Efficient approach
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
}
annotator.Save(outputPath); // Save once at the end
```

### 在处理数百页 PDF 时如何管理内存？

启用 `LoadOptions` 标志 `MemoryOptimization = true` 并顺序处理页面。这会指示库仅在内存中保留活动页面，从而显著降低超大文件的 RAM 占用。

```csharp
// Use using statements to ensure proper disposal
using (var annotator = new Annotator(inputPath))
{
    // Your annotation code here
} // Annotator is automatically disposed, freeing memory
```

### 应如何缓存频繁访问的文档？

将序列化的注释 JSON 存储在分布式缓存（如 Redis）中，以文档 ID 为键。当用户请求相同的 PDF 时，直接获取缓存的注释集合，而不是重新从磁盘读取文件，从而降低延迟和 I/O 负载。

```csharp
// Cache document metadata to avoid reloading
private static readonly Dictionary<string, DocumentInfo> _documentCache = 
    new Dictionary<string, DocumentInfo>();

private DocumentInfo GetDocumentInfo(string path)
{
    if (!_documentCache.ContainsKey(path))
    {
        using (var annotator = new Annotator(path))
        {
            _documentCache[path] = annotator.GetDocumentInfo();
        }
    }
    return _documentCache[path];
}
```

## 生产环境最佳实践

### 如何实现健壮的错误处理和日志记录？

将每个 `Annotator` 操作都包装在 `try‑catch` 块中，使用结构化日志记录器（Serilog、NLog）记录异常，并包含文档路径、用户 ID 和堆栈跟踪。这使得在生产环境中排查问题更加容易，并帮助满足合规审计要求。

```csharp
public async Task<bool> AddAnnotationSafely(string documentPath, AnnotationBase annotation)
{
    try
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath.Replace(".pdf", "_annotated.pdf"));
            return true;
        }
    }
    catch (Exception ex)
    {
        // Log the error (use your preferred logging framework)
        Console.WriteLine($"Annotation failed for {documentPath}: {ex.Message}");
        return false;
    }
}
```

### 如何验证用户提供的注释数据？

在构建注释对象之前，检查传入的 JSON 字段（页码、矩形坐标、注释类型）是否在可接受范围内。对超出范围的坐标返回明确的 HTTP 400 响应，并提供有帮助的错误信息。

```csharp
public bool ValidateAnnotationInput(AnnotationBase annotation)
{
    if (annotation == null)
        return false;
    
    if (string.IsNullOrWhiteSpace(annotation.Message))
        return false;
    
    if (annotation.Box.Width <= 0 || annotation.Box.Height <= 0)
        return false;
    
    return true;
}
```

### 如何在多用户 Web 服务中确保线程安全？

为每个请求实例化一个新的 `Annotator`；切勿在多个线程之间共享同一个实例。如果需要协调对共享文件的访问，请使用 `SemaphoreSlim` 或文件级锁来防止并发写入。

```csharp
private readonly object _annotationLock = new object();

public void AddAnnotationThreadSafe(string documentPath, AnnotationBase annotation)
{
    lock (_annotationLock)
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath);
        }
    }
}
```

## 何时使用 GroupDocs.Annotation 与其他方案对比

**选择 GroupDocs.Annotation 的情形**：
- 跨格式支持（PDF、DOCX、PPTX、图像）。  
- 高级注释类型，如马赛克、自由手绘和自定义元数据。  
- 企业级许可证、基于 SLA 的支持以及定期的安全更新。  

**考虑使用更轻量的替代方案的情形**：仅处理 PDF、预算受限或需要开源技术栈时。

## 常见问答

**Q: 是否可以在没有许可证的情况下使用 GroupDocs.Annotation .NET？**  
A: 可以，免费试用在 30 天内提供完整功能，但会在每个输出文件上添加评估水印。任何生产部署都必须使用临时或完整许可证来去除这些水印。

**Q: GroupDocs.Annotation 支持哪些 .NET 版本？**  
A: 该库兼容 .NET Framework 4.6.1+、.NET Core 2.0+、.NET 5、.NET 6 和 .NET 7，适用于传统 Windows 服务和现代跨平台容器。

**Q: GroupDocs.Annotation .NET 的费用是多少？**  
A: 价格约为开发者许可证 $1,999 起，随部署的应用数量而递增。请查看 [GroupDocs 价格页面](https://purchase.groupdocs.com/buy) 获取最新费率和批量折扣。

**Q: 我可以使用 GroupDocs.Annotation 注释哪些文档格式？**  
A: 支持超过 **50 种格式**，包括 PDF、DOC/DOCX、PPT/PPTX、XLS/XLSX、JPEG、PNG、TIFF 等。PDF 拥有最完整的功能集，包括基于矢量的形状和 OCR 准备的马赛克。

**Q: 能否注释受密码保护的 PDF？**  
A: 可以。在构造 `Annotator` 时提供密码：

```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your_password" };
using (Annotator annotator = new Annotator(inputPath, loadOptions))
{
    // Your annotation code here
}
```

**Q: 为什么我的注释位置错误？**  
A: GroupDocs 使用笛卡尔坐标系，(0,0) 位于左下角，单位为点。位置错误通常是因为使用像素值或忽略页面旋转导致的。将像素值转换为点（在 96 DPI 下 1 像素 ≈ 0.75 点），并根据旋转元数据进行调整。

```csharp
// Correct approach - validate coordinates
private bool ValidateCoordinates(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

**Q: 如何从 PDF 中获取已有的注释？**  
A: 在 `Annotator` 实例上调用 `Get()` 方法；它返回包含所有注释对象及其 ID、类型和元数据的集合。

```csharp
using (Annotator annotator = new Annotator(inputPath))
{
    List<AnnotationBase> annotations = annotator.Get();
    foreach (var annotation in annotations)
    {
        Console.WriteLine($"Annotation: {annotation.Message}");
    }
}
```

**Q: 能否以编程方式删除特定注释？**  
A: 可以。使用 `Delete(id)` 删除单个注释，或使用 `DeleteAll()` 完全清空文档。也可以在删除前按类型进行过滤。

```csharp
List<AnnotationBase> annotationsToDelete = annotator.Get()
    .Where(a => a.Message.Contains("obsolete"))
    .ToList();

foreach (var annotation in annotationsToDelete)
{
    annotator.Remove(annotation);
}
```

**Q: 如何更新注释属性，如颜色或消息？**  
A: 获取注释后，修改 `Color` 或 `Message`，然后调用 `Update()`。更改将在下次 `Save()` 时持久化。

```csharp
var annotations = annotator.Get();
var targetAnnotation = annotations.FirstOrDefault(a => a.Id == specificId);
if (targetAnnotation != null)
{
    targetAnnotation.Message = "Updated message";
    annotator.Update(targetAnnotation);
}
```

**Q: 能否为注释添加自定义元数据？**  
A: 完全可以。大多数注释类都提供 `Replies` 集合，您可以在其中存储键值对，从而附加审阅者 ID、时间戳或工作流状态。

```csharp
var annotation = new HighlightAnnotation
{
    // ... other properties
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Custom metadata: priority=high, category=legal",
            RepliedOn = DateTime.Now
        }
    }
};
```

**Q: GroupDocs.Annotation 是否支持在注释 PDF 上添加数字签名？**  
A: 虽然 Annotation 库专注于标记，但您可以将其与 GroupDocs.Signature .NET 结合，在添加注释后应用加密签名，从而确保视觉和法律完整性。

**Q: 能否将注释导出为 JSON 或 XML 以供外部处理？**  
A: 该库未提供内置导出功能，但您可以使用 `System.Text.Json` 或 `XmlSerializer` 手动序列化注释对象。这使得与外部审计系统的集成变得简便。

```csharp
List<AnnotationBase> annotations = annotator.Get();
string jsonAnnotations = JsonConvert.SerializeObject(annotations, Formatting.Indented);
File.WriteAllText("annotations.json", jsonAnnotations);
```

---

**最后更新：** 2026-05-21  
**测试环境：** GroupDocs.Annotation 23.12 for .NET  
**作者：** GroupDocs  

## 相关教程

- [GroupDocs Annotation .NET 教程 - 文档管理完整指南](/annotation/net/annotation-management/)
- [保存 PDF 注释 .NET - 完整文档保存指南](/annotation/net/document-saving/)
- [从 URL 加载 PDF .NET - 使用 GroupDocs.Annotation 的完整指南](/annotation/net/document-loading-essentials/load-document-from-url/)