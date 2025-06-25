---
"description": "了解如何使用 GroupDocs.Annotation 从 .NET 中的 PDF 和其他文档中删除注释。包含代码示例的分步指南。"
"linktitle": "使用 .NET 中的保存选项删除注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "使用 .NET 中的保存选项删除注释"
"url": "/zh/net/removing-annotations/remove-annotations-using-save-options/"
"weight": 14
---

# 使用 .NET 中的保存选项删除注释

## 介绍

GroupDocs.Annotation for .NET 是一款功能强大的工具，可帮助开发人员轻松地为其 .NET 应用程序添加注释功能。无论您是在使用文档管理系统、协作平台还是任何其他涉及文档处理的应用程序，GroupDocs.Annotation 都能提供一套全面的功能，让您无缝地注释 PDF 和其他文档格式。

## 先决条件

在使用 GroupDocs.Annotation for .NET 注释文档之前，请确保您已满足以下先决条件：

### 1. 安装 GroupDocs.Annotation for .NET

首先下载并安装 GroupDocs.Annotation for .NET。您可以从 [下载页面](https://releases。groupdocs.com/annotation/net/).

## 导入命名空间

要在 .NET 项目中开始使用 GroupDocs.Annotation，您需要导入必要的命名空间。以下是您常用的命名空间：

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


现在，让我们逐步介绍使用 .NET 中的“保存选项”功能从文档中删除注释的过程：

## 步骤 1：定义输出路径

首先，定义已删除注释的文档的保存路径。您可以使用 `Path.Combine` 方法将目录路径与输出文件名结合起来。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 步骤 2：初始化注释器

接下来，初始化一个实例 `Annotator` 类，通过提供包含注释的文档的路径。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // 注释删除代码将放在这里
}
```

## 步骤 3：保存文档并删除注释

现在，使用 `Save` 方法 `Annotator` 类以及 `SaveOptions` 保存已删除注释的文档。在 `SaveOptions`，设置 `AnnotationTypes` 财产 `AnnotationType.None` 删除所有注释。

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## 步骤4：显示成功消息

最后，显示一条成功消息，表明文档已成功保存并删除了注释。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论

总而言之，GroupDocs.Annotation for .NET 简化了从文档中删除注释的过程。通过遵循上面概述的分步指南，开发人员可以将注释删除功能无缝集成到他们的 .NET 应用程序中。

## 常见问题解答

### 问：GroupDocs.Annotation 可以从 PDF 以外的其他文档格式中删除注释吗？

答：GroupDocs.Annotation 支持各种文档格式，包括 PDF、Word、Excel 和 PowerPoint，允许您从各种文档中删除注释。

### 问：GroupDocs.Annotation 是否易于集成到现有的 .NET 项目中？

答：是的，GroupDocs.Annotation 提供了简单的 API 和全面的文档，使开发人员可以轻松地将注释功能集成到他们的 .NET 应用程序中。

### 问：GroupDocs.Annotation 是否支持选择性删除注释？

答：是的，GroupDocs.Annotation 允许开发人员指定要删除哪些类型的注释，从而使他们能够灵活地管理文档中的注释。

### 问：购买之前我可以免费试用 GroupDocs.Annotation 吗？

答：是的，您可以从 [发布页面](https://releases.groupdocs.com/) 在做出购买决定之前探索其功能。

### 问：在哪里可以获得 GroupDocs.Annotation 的支持？

答：如需技术援助和社区支持，您可以访问 [GroupDocs.Annotation 论坛](https://forum。groupdocs.com/c/annotation/10).