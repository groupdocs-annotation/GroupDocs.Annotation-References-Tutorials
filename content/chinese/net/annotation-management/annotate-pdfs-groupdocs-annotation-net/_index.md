---
categories:
- PDF Processing
date: '2026-05-26'
description: 了解如何使用 GroupDocs Annotation for .NET 创建文档审阅系统。分步教程涵盖设置、注释类型、性能调优以及针对
  C# 开发者的故障排除。
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Guide
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 创建文档审阅系统：PDF Annotation .NET Guide
type: docs
url: /zh/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# 创建文档审阅系统：PDF 注释 .NET 指南

如果您需要**创建文档审阅系统**，让用户能够直接在 .NET 应用程序中对 PDF 添加评论、突出显示和形状，那么您来对地方了。GroupDocs.Annotation for .NET 消除了低层 PDF 处理的麻烦，同时让您对每种注释类型进行细粒度控制。在本指南中，您将看到如何设置库、添加区域、椭圆和文本注释、过滤保存内容，以及即使在数百页的文件中也保持性能敏捷。

## 快速答案
- **什么库处理 .NET 中的 PDF 注释？** GroupDocs.Annotation for .NET.
- **我可以以编程方式添加高亮、圆形和评论吗？** 可以 – 使用 AreaAnnotation、EllipseAnnotation 和 TextAnnotation 对象.
- **生产环境是否需要许可证？** 有效的 GroupDocs 许可证是任何生产部署的必需条件.
- **可以处理多大的 PDF？** 可处理高达 500 MB 的文件，而无需将整个文件加载到内存中.
- **这能帮助我创建文档审阅系统吗？** 当然可以 – 您可以批量保存、过滤并为审阅者进行注释版本管理.

## 什么是文档审阅系统？
**文档审阅系统**是一种软件解决方案，允许多个利益相关者在协同工作流中对 PDF 文件进行注释、评论和批准。它集中反馈、跟踪更改，并常常导出干净的版本以供最终批准。

## 为什么使用 GroupDocs Annotation for .NET 来创建文档审阅系统？
GroupDocs Annotation 支持 **30+ 注释类型**，可处理高达 **500 MB** 的 PDF，并可运行在 **.NET Framework 4.6.1+**、**.NET Core 2.0+** 和 **.NET 6+** 上。其 API 让您在不触及 PDF 内部结构的情况下添加、删除和过滤注释，从而加快开发速度并减少错误。

## 前置条件和环境设置

在编写任何代码之前，请确保您的开发环境满足以下条件：

- **IDE：** Visual Studio 2019 或更高版本，或带有 C# 扩展的 VS Code。
- **目标框架：** .NET Framework 4.6.1 + 或 .NET Core 2.0 + （我们推荐新项目使用 .NET 6）。
- **NuGet 访问权限：** 能够从 nuget.org 安装包。
- **示例 PDF：** 至少一个多页 PDF 用于测试注释放置。
- **内存和磁盘：** 最低 4 GB RAM 并且有足够的磁盘空间用于临时文件（注释处理可能会生成临时流）。

### 推荐的开发实践
- 将您的解决方案放在源代码控制（Git）下，以便回滚与注释相关的更改。
- 在项目中使用专用的 **Annotations** 文件夹来存储配置文件和许可证密钥。
- 启用 **可空引用类型** (`<Nullable>enable</Nullable>`) 以提前捕获潜在的空引用错误。

## 入门：GroupDocs.Annotation 安装

### 安装方式

**选项 1：NuGet 包管理器控制台**  
在包管理器控制台中运行以下命令：  

`Install-Package GroupDocs.Annotation`

**选项 2：.NET CLI（推荐跨平台开发）**  
在终端中执行：  

`dotnet add package GroupDocs.Annotation`

**选项 3：Visual Studio 包管理器 UI**  
- 右键单击项目 → **管理 NuGet 包**  
- 搜索 **GroupDocs.Annotation**  
- 在最新的稳定版本上点击 **Install**

这三种方法都会安装相同的二进制文件；请选择符合您工作流的方式。

### 许可证配置

GroupDocs 对任何生产使用都需要有效的许可证。您有三种途径：

- **免费试用：** 30 天完整功能评估。  
- **临时许可证：** 用于开发和测试的延长评估。  
- **商业许可证：** 在生产环境中无限制使用。

`License` 类加载并应用 GroupDocs 许可证文件以启用完整功能。您可以从 [GroupDocs 购买页面](https://purchase.groupdocs.com/buy) 获取许可证。收到 `.lic` 文件后，将其放在应用程序可读取的文件夹中，并在启动时将 `License` 类指向该文件。

### 初始设置验证

创建一个小型控制台程序，加载 PDF 并将页数写入控制台。如果程序运行时没有抛出异常，则说明库已正确安装并获得许可证。

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **注意：** 上面的代码仅用于说明；您 **不需要** 在最终文章中添加围栏代码块，但内联片段展示了确切的 API 用法。

如果您看到打印出的页数，说明您已准备好开始添加真实的注释。

## 核心实现：向 PDF 添加注释

### 定义锚点 – Annotator

`Annotator` 类是 GroupDocs.Annotation for .NET 中所有 PDF 注释操作的入口点。它将 PDF 加载到内存中，提供添加、编辑和检索注释的方法，并处理保存修改后的文档。

### 如何添加区域和椭圆注释？

使用 `new Annotator(...)` 加载 PDF，创建 `AreaAnnotation` 和 `EllipseAnnotation` 对象，设置它们的坐标，并将它们添加到 annotator 的集合中。最后，调用 `Save` 以持久化更改。此工作流让您能够以编程方式突出显示区域（area）或在单个原子操作中圈出重要图形（ellipse）。

#### 步骤 1：初始化 Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### 步骤 2：创建 AreaAnnotation
`AreaAnnotation` represents a rectangular highlight area on a PDF page.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### 步骤 3：创建 EllipseAnnotation
`EllipseAnnotation` represents an elliptical shape annotation on a PDF page.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### 步骤 4：批量添加注释
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**专业提示：** 将注释放入列表中并一次调用 `Add` 可以减少 I/O 开销，尤其是在需要在多页上插入数十个标记时。

### 如何有选择地保存注释？

`SaveOptions` 配置注释 PDF 的保存方式，包括要包含的注释类型。GroupDocs.Annotation 允许您过滤写入输出文件的注释类型。创建 `SaveOptions` 实例，将 `AnnotationTypes` 集合设置为您想保留的类型，然后将选项传递给 `Save`。这非常适合生成仅审阅者可见的 PDF 或在归档前剥离临时笔记。

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## 实际实现场景

### 场景 1：文档审阅工作流
多个审阅者添加 **Area**、**Ellipse** 和 **Text** 注释。审阅轮次结束后，您生成三个 PDF：
1. 包含所有评论的完整版本。  
2. 仅审阅者可见的版本（过滤内部备注）。  
3. 用于最终批准的干净版本（仅保留高亮）。

### 场景 2：自动化报告生成
您的后端处理每日销售报告，自动使用区域注释突出关键指标，并使用椭圆注释圈出异常图表。生成的 PDF 随后发送给利益相关者，无需任何人工干预。

### 场景 3：协作法律文档
律所经常需要将合伙人评论与初级助理的备注分离。通过使用自定义元数据标记注释并使用选择性保存，您可以生成隐藏初级备注的合伙人审阅 PDF，从而简化版本控制。

## 生产使用的性能优化

### 如何在注释大型 PDF 时管理内存？

`LoadOptions` 允许您指定 PDF 的加载方式，例如页面范围或密码。当 PDF 超过 100 MB 时，使用接受页面范围的 `LoadOptions` 构造函数来避免加载整个文件。批量处理页面，在 `using` 块中释放每个 `Annotator` 实例，并在每批处理后清理临时文件。即使是 500 页的文档，此方法也能将峰值内存使用保持在 200 MB 以下。

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### 内存管理最佳实践
- **始终在 `using` 语句中包装 `Annotator`** 以确保释放非托管资源。  
- **批量处理注释**：收集文档的所有注释，然后一次调用 `Add`。  
- **避免加载完整 PDF**，当只需修改部分页面时；使用 `LoadOptions.PageNumbers`。

### 大文件处理策略
1. **逐页处理** – 一次加载、注释并保存一页。  
2. **流式输出** – 将 `Save` 方法指向 `MemoryStream`，以避免中间磁盘写入。  
3. **临时文件清理** – 在每次操作后删除 annotator 创建的任何临时文件。

### 并发处理注意事项
- **线程安全性：** `Annotator` 实例不是线程安全的。每个线程创建单独的实例。  
- **资源节流：** 将并发作业限制为 CPU 核心数，以防止 CPU 饱和。  
- **异步 API：** `SaveAsync` 异步保存注释文档，返回 Task，这在 ASP.NET Core 环境中很有用。

## 常见问题排查

### 问题 1：“未找到文件”错误

**直接答案：** 验证传递给 `new Annotator(...)` 的文件路径是绝对路径或相对于执行程序集的正确相对路径，并确保应用程序进程对该位置具有读取权限。如果文件位于网络共享，请映射共享或使用 UNC 路径。

**常见解决方案：**  
- 使用 `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- 为 IIS 应用池身份授予文件夹的读/写权限。

### 问题 2：注释出现在错误位置

**直接答案：** 确保使用相同的坐标系（左上原点），并且页面的 DPI 与您提供的值匹配。通过 `annotator.GetPageInfo(pageNumber)` 获取页面尺寸，并相对于该尺寸计算坐标。

**常见解决方案：**  
- 如果 PDF 使用非标准 DPI 创建，则将坐标乘以页面的缩放因子。  
- 再次确认未将点（1/72 英寸）与像素混用。

### 问题 3：大文件的性能问题

**直接答案：** 切换到页面范围加载，批量处理注释，并及时释放每个 `Annotator` 实例。同时在 `LoadOptions` 中启用 `MemoryCache` 选项，以在操作之间复用缓冲区。

**常见解决方案：**  
- 设置 `LoadOptions.UseMemoryCache = true`.  
- 使用 `await annotator.SaveAsync(...)` 异步处理文件。

### 问题 4：许可证相关错误

**直接答案：** 将 `.lic` 文件放在应用程序可读取的文件夹中，并在任何其他 GroupDocs 调用之前调用 `License license = new License(); license.SetLicense("path/to/license.lic");`. 验证许可证版本与您使用的库版本匹配。

**常见解决方案：**  
- 检查许可证文件是否损坏（比较文件大小）。  
- 确保在同一环境中未混用试用许可证和商业许可证。

## 高级技巧和最佳实践

### 颜色管理

一致的颜色提升审阅者的可读性。定义调色板（例如，黄色用于高亮，红色用于关键问题），并将其存储在静态帮助类中。记得使用高对比度颜色以满足可访问性需求，并在 PDF 中添加图例页以供参考。

### 错误处理模式

将所有注释调用包装在 try‑catch 块中，专门捕获 `GroupDocs.Annotation.Exceptions.AnnotationException`. 记录异常信息、堆栈跟踪和 PDF 名称，以帮助调试。

### 测试策略

- **单元测试：** 使用已知尺寸的小 PDF，添加注释，并断言 `GetAnnotations()` 返回预期坐标。  
- **集成测试：** 在 1 页到 200 页的 PDF 上运行完整工作流，并验证文件小于 50 MB 时处理时间保持在 5 秒以内。  
- **负载测试：** 使用 k6 或 Apache JMeter 等工具模拟 50 个并发注释请求，并监控 CPU/内存。

## 常见问题

**问：如何处理不同页面尺寸的 PDF？**  
**答：** GroupDocs 会自动读取每页的尺寸。定位注释时，始终查询 `annotator.GetPageInfo(pageNumber)` 并基于该页的宽高计算坐标。

**问：我可以注释受密码保护的 PDF 吗？**  
**答：** 可以。使用接受密码字符串的 `LoadOptions` 构造函数，例如 `new LoadOptions { Password = "secret" }`，并将其传递给 `Annotator` 构造函数。

**问：单个 PDF 能添加的注释最大数量是多少？**  
**答：** 没有硬性限制，但在几千个注释后性能会下降。对于非常大的注释集合，请将其分组为逻辑段落并分别处理。

**问：如何以编程方式删除特定注释？**  
**答：** 通过 `GetAnnotations()` 获取注释的 `Id`，然后调用 `Delete(id)`，或创建一个排除不需要的 `AnnotationType` 的 `SaveOptions` 实例。

**问：我可以自定义注释外观（超出颜色）吗？**  
**答：** 当然可以。您可以设置不透明度、边框粗细、虚线样式，甚至为印章注释嵌入自定义 SVG 图标。

**问：如果尝试注释扫描（基于图像）的 PDF 会怎样？**  
**答：** 注释将作为覆盖对象渲染在页面图像之上。它们不会修改底层光栅数据，因此如果存在 OCR 层，PDF 仍然可搜索。

**问：如何在不耗尽内存的情况下处理非常大的 PDF？**  
**答：** 使用 `LoadOptions.PageNumbers` 按页处理文档，使用后立即释放每个 `Annotator` 实例，并启用流式保存到 `MemoryStream`，以避免磁盘峰值。

## 与 ASP.NET 应用程序集成

当您通过 Web API 暴露注释功能时，请遵循以下模式：

1. **控制器从客户端接收 PDF 流。**  
2. **验证文件大小**（除非有特殊处理，否则拒绝 > 200 MB 的文件）。  
3. **在 `using` 块中实例化 `Annotator`**，以确保释放。  
4. **根据描述注释类型、坐标和文本的 JSON 负载** 应用注释。  
5. **保存到临时位置**，然后使用适当的 `Content‑Disposition` 头将结果流回客户端。

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## 其他资源
- [GroupDocs 购买页面](https://purchase.groupdocs.com/buy)  
- [购买 GroupDocs](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation 文档](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API 参考](https://reference.groupdocs.com/annotation/net/)  
- [最新发布](https://releases.groupdocs.com/annotation/net/)  
- [免费试用 GroupDocs](https://releases.groupdocs.com/annotation/net/)  
- [请求临时许可证](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs 论坛](https://forum.groupdocs.com/c/annotation/)

## 结论与后续步骤

您现在拥有一份 **完整、可投入生产的路线图**，用于构建由 GroupDocs.Annotation for .NET 驱动的 **创建文档审阅系统**。您已经学习了如何设置库、添加区域、椭圆和文本注释、过滤保存，以及即使在超大 PDF 中也保持低内存使用。

**您今天可以采取的后续行动：**
1. **尝试** 其他注释类型，如 `ArrowAnnotation` 和 `StampAnnotation`。  
2. **将工作流集成** 到您现有的 ASP.NET Core API 或桌面 WPF 应用程序中。  
3. **探索** 完整的 API 参考，发现如注释版本管理和自定义元数据等高级功能。  
4. **加入** GroupDocs 社区论坛，获取同行支持并随时了解新版本发布。

---

**最后更新：** 2026-05-26  
**测试环境：** GroupDocs.Annotation 23.11 for .NET  
**作者：** GroupDocs  

---

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## 相关教程
- [GroupDocs Annotation .NET 教程 - 文档管理完整指南](/annotation/net/annotation-management/)
- [文档预览 .NET 教程 - 完整 GroupDocs.Annotation 指南](/annotation/net/document-preview/)
- [GroupDocs Annotation 按量计费许可证教程 - 完整 .NET 设置指南](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)