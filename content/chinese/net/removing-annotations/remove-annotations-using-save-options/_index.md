---
title: 使用 .NET 中的保存选项删除注释
linktitle: 使用 .NET 中的保存选项删除注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 从 PDF 和 .NET 中的其他文档中删除注释。带有代码示例的分步指南。
weight: 14
url: /zh/net/removing-annotations/remove-annotations-using-save-options/
---

# 使用 .NET 中的保存选项删除注释

## 介绍

GroupDocs.Annotation for .NET 是一个功能强大的工具，允许开发人员轻松地将注释功能添加到他们的 .NET 应用程序中。无论您是在文档管理系统、协作平台还是涉及文档处理的任何其他应用程序上工作，GroupDocs.Annotation 都提供了一套全面的功能来无缝注释 PDF 和其他文档格式。

## 先决条件

在深入使用 GroupDocs.Annotation for .NET 对文档进行注释之前，请确保满足以下先决条件：

### 1.安装.NET的GroupDocs.Annotation

首先下载并安装 GroupDocs.Annotation for .NET。您可以从以下位置下载最新版本[download page](https://releases.groupdocs.com/annotation/net/).

## 导入命名空间

要开始在 .NET 项目中使用 GroupDocs.Annotation，您需要导入必要的命名空间。以下是您常用的命名空间：

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


现在，让我们逐步了解使用 .NET 中的“保存选项”功能从文档中删除注释的过程：

## 第 1 步：定义输出路径

首先，定义保存已删除注释的文档的输出路径。您可以使用`Path.Combine`方法将目录路径与输出文件名组合起来。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 2 步：初始化注释器

接下来，初始化一个实例`Annotator`类，通过提供包含注释的文档的路径。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    //注释删除代码将放在这里
}
```

## 步骤 3：保存文档并删除注释

现在，使用`Save`的方法`Annotator`类与`SaveOptions`保存已删除注释的文档。在里面`SaveOptions`，设置`AnnotationTypes`财产给`AnnotationType.None`删除所有注释。

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## 第4步：显示成功消息

最后，显示一条成功消息，表明文档已成功保存并删除了注释。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论

总之，GroupDocs.Annotation for .NET 简化了从文档中删除注释的过程。通过遵循上述分步指南，开发人员可以将注释删除功能无缝集成到他们的 .NET 应用程序中。

## 常见问题解答

### 问：GroupDocs.Annotation 是否可以删除除 PDF 之外的其他文档格式的注释？

答：GroupDocs.Annotation 支持多种文档格式，包括 PDF、Word、Excel 和 PowerPoint，允许您从各种文档中删除注释。

### 问：GroupDocs.Annotation 是否易于集成到现有的 .NET 项目中？

答：是的，GroupDocs.Annotation 提供了简单的 API 和全面的文档，使开发人员可以轻松地将注释功能集成到他们的 .NET 应用程序中。

### 问：GroupDocs.Annotation 是否支持选择性删除注释？

答：是的，GroupDocs.Annotation 允许开发人员指定要删除的注释类型，从而使他们能够灵活地管理文档中的注释。

### 问：我可以在购买前免费试用 GroupDocs.Annotation 吗？

答：是的，您可以从 GroupDocs.Annotation 下载免费试用版[发布页面](https://releases.groupdocs.com/)在做出购买决定之前探索其功能。

### 问：在哪里可以获得 GroupDocs.Annotation 的支持？

答： 如需技术援助和社区支持，您可以访问[GroupDocs.Annotation 论坛](https://forum.groupdocs.com/c/annotation/10).