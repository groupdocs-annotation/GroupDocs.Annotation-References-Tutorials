---
categories:
- Advanced Usage
date: '2026-04-06'
description: 学习如何使用版本键在 GroupDocs.Annotation .NET 中按版本检索注释。分步教程，附代码示例和最佳实践。
keywords:
- retrieve annotations by version
- version key
- GroupDocs.Annotation .NET
lastmod: '2026-04-06'
linktitle: 使用版本键获取注释列表
second_title: GroupDocs.Annotation .NET API
tags:
- groupdocs-annotation
- version-control
- document-annotations
- dotnet-api
title: 在 GroupDocs.Annotation .NET 中按版本检索注释
type: docs
url: /zh/net/advanced-usage/get-list-annotations-version-key/
weight: 18
---

# 如何使用 GroupDocs.Annotation .NET 中的版本键获取注释列表

在本教程中，您将学习**按版本检索注释**，使用 .NET 的 GroupDocs.Annotation。管理不同的注释版本是构建协作文档工作流时的常见挑战，而此方法可让您准确定位属于特定文档版本的注释。

## 快速答案
- **“按版本检索注释”是什么意思？** 这意味着仅获取使用特定版本键保存的注释。  
- **使用哪个 API 调用？** `Annotator.GetVersion(string versionKey)`。  
- **我需要特殊许可证吗？** 生产环境使用需要有效的 GroupDocs.Annotation 许可证。  
- **是否支持所有文件类型？** 是的 – PDF、DOCX、XLSX、PPTX 等等。  
- **我可以过滤结果吗？** 当然可以 – 检索后您可以按注释类型、作者或日期进行过滤。

## 为什么基于版本的注释检索很重要

在深入代码之前，让我们了解何时真正需要此功能：

- **文档审阅工作流**：跟踪哪些注释属于特定的审阅轮次  
- **审计追踪**：通过保留跨文档版本的注释历史来保持合规性  
- **协同编辑**：允许多个用户同时在不同的文档版本上工作  
- **变更管理**：在需要时回滚到先前的注释状态  

可以把它想象成文档注释的 Git – 您随时可以查阅哪些内容发生了变化以及何时变化。

## 什么是“按版本检索注释”？

按版本检索注释是针对特定 **版本键** 查询注释存储的过程。版本键是开发者定义的标识符（例如 `v1.0`、`review‑round‑2`），用于将注释分组，从而轻松隔离文档特定迭代期间的更改。

## GroupDocs.Annotation .NET 设置的先决条件

在开始按版本键检索注释之前，您需要一个合适的开发环境。以下是您需要的内容（以及一些常见的坑需要避免）：

### 1. .NET 开发环境设置

您需要一个可用的 .NET 开发环境。这不仅仅是安装 Visual Studio——还需要正确的 SDK 版本。

#### 设置 .NET SDK
1. 访问 .NET 网站并下载最新版本的 .NET SDK。  
2. 按照为您的操作系统提供的安装说明进行操作。  
3. 打开命令提示符并键入 `dotnet --version`，以验证安装。  

**技巧**：如果您在团队环境中工作，请在 `global.json` 文件中固定 .NET SDK 版本，以避免“在我的机器上可以运行”问题。

### 2. GroupDocs.Annotation 安装

安装 GroupDocs.Annotation 很简单，但根据项目设置有几种不同的方式。

#### 通过 NuGet 包管理器安装
1. 在 Visual Studio 中打开您的项目。  
2. 在解决方案资源管理器中右键单击项目，选择 **Manage NuGet Packages**。  
3. 搜索 **GroupDocs.Annotation** 并安装可用的最新版本。  

**重要**：始终检查包的最低 .NET 版本要求是否符合您项目的目标框架。版本不匹配是运行时错误的常见来源。

## 注释操作的必需命名空间

在使用注释之前，您需要导入正确的命名空间。以下是您需要的内容：

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Annotation.Models.AnnotationModels;
```

**注意**：`GroupDocs.Annotation.Models.AnnotationModels` 命名空间包含您将使用的所有注释类型。不要省略此导入，否则会出现令人困惑的编译错误。

## 分步指南：按版本键检索注释

现在进入主要环节——实际获取这些注释。该过程包括两个关键步骤，能够无缝协作。

### 步骤 1：初始化 Annotator 对象

首先，您需要使用目标文档初始化 `Annotator` 对象。这将在您的代码与带注释的文档之间建立连接。

```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Annotation operations will be performed here
}
```

**此步骤的关键点**  
- 文件路径可以是绝对路径，也可以是相对于应用程序工作目录的相对路径。  
- GroupDocs.Annotation 支持多种文档格式（PDF、DOCX、XLSX、PPTX 等）。  
- `using` 语句确保正确释放资源——请始终使用它！

### 步骤 2：使用版本键检索注释

一旦初始化了 annotator，检索特定版本的注释只需一次方法调用：

```csharp
List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
```

此方法返回与指定版本键关联的所有注释列表。随后您可以遍历该列表、按类型过滤注释，或执行任何其他所需操作。

**您可以对结果进行的操作**  
- 按类型过滤注释（评论、突出显示、印章等）  
- 提取注释元数据（作者、创建日期、修改历史）  
- 将注释导出为不同格式  
- 将注释应用于新文档版本  

## 常见问题及解决方案

即使代码很直接，您仍可能遇到一些常见挑战。以下是最常见的问题及其解决方案：

### 未找到版本键

**问题**：您的版本键未返回任何注释。  
**解决方案**：再次确认注释确实已使用该特定版本键保存。版本键区分大小写。

### 大量注释集的性能问题

**问题**：在包含数百条注释的文档中检索注释耗时过长。  
**解决方案**：考虑在检索前实现分页或按日期范围或注释类型过滤注释。

### 内存管理

**问题**：在处理多个带版本的文档时，应用程序消耗过多内存。  
**解决方案**：始终正确释放 `Annotator` 对象（使用 `using` 语句），并考虑分批处理文档，而不是一次性全部处理。

## 版本管理的最佳实践

要充分利用基于版本的注释检索，请遵循以下成熟策略：

### 1. 一致的版本命名

为版本键使用清晰、一致的命名约定。考虑以下模式：  
- `v1.0`、`v1.1`、`v2.0` 用于主/次版本  
- `review-round-1`、`review-round-2` 用于审阅周期  
- `2025-01-02-draft`、`2025-01-05-final` 用于基于日期的版本  

### 2. 版本元数据跟踪

在版本键旁存储额外的元数据：  
- 创建时间戳  
- 作者信息  
- 版本描述或变更说明  
- 父版本关系  

### 3. 清理策略

实施管理旧版本的策略，以防止存储膨胀：  
- 归档早于特定日期的版本  
- 限制每个文档的版本数量  
- 对长期存储的注释数据进行压缩  

## 高级实现场景

以下是您可能遇到的一些真实场景模式：

### 跨版本比较注释

```csharp
using (Annotator annotator = new Annotator("document.pdf"))
{
    var v1Annotations = annotator.GetVersion("v1.0");
    var v2Annotations = annotator.GetVersion("v2.0");
    
    // Compare annotation sets to identify changes
    // Implementation depends on your specific comparison logic
}
```

### 批量处理多个版本

当需要高效处理多个版本时，考虑将操作批量化以降低资源开销。遍历版本键集合，并在可能的情况下复用单个 `Annotator` 实例。

## 常见问答

### 我可以使用 GroupDocs.Annotation for .NET 对除 PDF 之外的文档进行注释吗？

当然可以！GroupDocs.Annotation 支持多种文档格式，包括 Word（DOCX）、Excel（XLSX）、PowerPoint（PPTX）以及许多图像格式。版本键功能在所有受支持的格式中均保持一致。

### 当版本键不存在时，我该如何处理？

如果指定的版本键不存在，`GetVersion()` 方法将返回空列表。处理前请始终检查返回的列表是否包含任何项。您也可以实现 try‑catch 块，以优雅地处理可能的异常。

### 在处理拥有多个版本的文档时，是否会有性能影响？

性能取决于每个版本的注释数量，而不是版本本身的数量。每个版本的注释是单独存储的，因此检索单个版本时不会加载其他版本的数据。然而，每个版本拥有数百条注释的文档可能需要分页策略。

### 我可以同时检索多个版本的注释吗？

虽然 `GetVersion()` 方法一次只能检索一个版本，但您可以连续多次调用它。对于批量操作，考虑实现自己的缓存机制，以避免重复的文件访问。

### 是否有 GroupDocs.Annotation for .NET 的免费试用？

是的，您可以通过访问[网站](https://releases.groupdocs.com/annotation/net/)获取 GroupDocs.Annotation for .NET 的免费试用。试用版提供完整功能，但有一定的使用限制。

### 我如何获得与 GroupDocs.Annotation 相关的问题或查询的支持？

您可以通过访问 GroupDocs.Annotation 论坛或直接联系其支持团队来获取帮助。社区论坛对实现问题和最佳实践尤为有用。

### 我可以购买临时许可证用于测试 GroupDocs.Annotation 吗？

是的，可购买临时许可证以便进行产品测试和评估。这对于概念验证项目或延长评估期特别有用。

### 我在哪里可以找到 GroupDocs.Annotation for .NET 的完整文档？

您可以参考 GroupDocs 网站上提供的文档，以获取关于使用该产品的详细指南[此处]( https://tutorials.groupdocs.com/annotation/net/)。文档包括 API 参考、代码示例和高级使用场景。

## 常见问题

**Q: 检索按版本的注释会影响原始文档吗？**  
A: 不会。`GetVersion()` 方法是只读的；它不会修改源文件。

**Q: 我可以将版本过滤与其他查询参数结合使用吗？**  
A: 可以。检索列表后，您可以在内存中进一步按作者、注释类型或日期进行过滤。

**Q: 版本键在内部是如何存储的？**  
A: 版本键作为每个注释元数据的一部分保存，能够快速查找而无需扫描整个注释集合。

**Q: 在保存注释后可以重命名版本键吗？**  
A: 不直接支持重命名；您需要通过编程方式将注释复制到新的版本键。

**Q: 如果我删除文档版本文件会怎样？**  
A: 删除底层文档会移除所有关联的注释，包括绑定到版本键的注释。删除前请确保备份所需的版本。

## 目标关键词

**主要关键词（最高优先级）：**  
retrieve annotations by version

**次要关键词（支持）：**  
（未指定）

---

**最后更新：** 2026-04-06  
**测试环境：** GroupDocs.Annotation 2.0 for .NET（撰写时的最新版本）  
**作者：** GroupDocs