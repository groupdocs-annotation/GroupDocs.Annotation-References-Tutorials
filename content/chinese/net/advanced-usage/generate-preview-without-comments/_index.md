---
title: 生成不带注释的预览
linktitle: 生成不带注释的预览
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将文档注释功能无缝集成到 .NET 应用程序中。
weight: 14
url: /zh/net/advanced-usage/generate-preview-without-comments/
---
## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的工具，允许开发人员将注释功能无缝合并到他们的 .NET 应用程序中。无论您是在文档管理系统、协作平台还是任何其他需要文档注释功能的应用程序上工作，GroupDocs.Annotation 都提供了一套全面的工具来增强应用程序的功能。
## 先决条件
在深入使用 GroupDocs.Annotation for .NET 之前，请确保您已设置以下先决条件：
### 1.安装.NET的GroupDocs.Annotation
首先，您需要下载并安装 GroupDocs.Annotation for .NET。你可以找到下载链接[这里](https://releases.groupdocs.com/annotation/net/)。请按照文档中提供的安装说明进行操作，以顺利完成设置过程。
### 2. 获取许可证
GroupDocs.Annotation for .NET 需要商业用途许可证。您可以从以下位置获取许可证[这里](https://purchase.groupdocs.com/buy)或选择临时许可证[这里](https://purchase.groupdocs.com/temporary-license/)用于测试目的。
### 3.熟悉.NET框架
.NET Framework 和 C# 编程语言的基础知识对于有效利用 GroupDocs.Annotation for .NET 至关重要。

## 导入命名空间
现在您已经设置了先决条件，让我们将必要的命名空间导入到您的 .NET 应用程序中。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

按照以下分步说明使用 GroupDocs.Annotation for .NET 生成不带注释的预览：
## 第 1 步：初始化注释器
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## 第 2 步：配置预览选项
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## 步骤 3：指定预览格式和页码
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## 第 4 步：禁用评论渲染
```csharp
    previewOptions.RenderComments = false;
```
## 第 5 步：生成预览
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
完成这些步骤后，您的 .NET 应用程序将能够从文档生成指定页面的预览，而无需呈现注释。

## 结论
借助 GroupDocs.Annotation for .NET，将注释功能合并到 .NET 应用程序中从未如此简单。通过遵循本教程中概述的步骤，您可以将文档注释功能无缝集成到您的应用程序中，从而增强协作和文档管理。
## 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、DOCX、PPTX、XLSX 等。
### 我可以自定义使用 GroupDocs.Annotation for .NET 生成的注释的外观吗？
是的，GroupDocs.Annotation for .NET 提供了广泛的自定义选项，允许您定制注释的外观以满足您的应用程序的需求。
### GroupDocs.Annotation for .NET 支持多用户协作吗？
是的，GroupDocs.Annotation for .NET 提供协作注释功能，使多个用户能够同时注释文档。
### GroupDocs.Annotation for .NET 是否提供技术支持？
是的，GroupDocs.Annotation for .NET 的技术支持可通过[支持论坛](https://forum.groupdocs.com/c/annotation/10).
### 我可以在购买前免费试用 GroupDocs.Annotation for .NET 吗？
是的，您可以通过下载免费试用版来探索 GroupDocs.Annotation for .NET 的功能[这里](https://releases.groupdocs.com/).