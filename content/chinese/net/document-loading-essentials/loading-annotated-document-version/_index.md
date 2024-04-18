---
title: 加载带注释的文档版本
linktitle: 加载带注释的文档版本
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 轻松加载带注释的文档版本。简化协作和审核流程。
type: docs
weight: 16
url: /zh/net/document-loading-essentials/loading-annotated-document-version/
---
## 介绍
在当今的数字时代，文档注释已成为各行业协作、审阅和反馈的重要工具。无论您是将注释功能集成到应用程序中的开发人员还是希望利用这些功能的用户，GroupDocs.Annotation for .NET 都提供了强大的解决方案。在本教程中，我们将深入研究使用 GroupDocs.Annotation for .NET 加载带注释的文档版本的过程。
## 先决条件
在我们开始之前，请确保您具备以下先决条件：
### 1.安装.NET的GroupDocs.Annotation
您可以从以下位置下载必要的文件[发布页面](https://releases.groupdocs.com/annotation/net/)。按照提供的安装说明在 .NET 环境中设置库。
### 2. 获取带注释的文档
对于本教程，您将需要带有注释的文档。确保您拥有包含要加载的注释的兼容文档格式（例如 PDF）。

## 导入命名空间
要启动该过程，您需要将所需的命名空间导入到您的项目中。这些命名空间提供对 GroupDocs.Annotation for .NET 功能的访问。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


现在我们已经介绍了先决条件和命名空间导入，接下来让我们深入了解使用 GroupDocs.Annotation for .NET 加载带注释的文档版本的分步过程。
## 第 1 步：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：指定加载选项
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## 第 3 步：初始化注释器
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## 第 4 步：检索注释
```csharp
var annotations = annotator.Get();
```
## 第 5 步：保存带注释的文档
```csharp
annotator.Save(outputPath);
```
## 第 6 步：显示确认消息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Annotation for .NET 加载带注释的文档版本。通过遵循分步指南并利用这个强大库的功能，您可以将文档注释功能无缝集成到您的 .NET 应用程序中。
## 常见问题解答
### 我可以使用 GroupDocs.Annotation for .NET 对各种格式的文档进行注释吗？
是的，GroupDocs.Annotation 支持对 PDF、DOCX、PPTX、XLSX 等格式的文档进行注释。
### GroupDocs.Annotation for .NET 是否有免费试用版？
是的，您可以从以下位置访问免费试用版：[这里](https://releases.groupdocs.com/).
### 在哪里可以找到 GroupDocs.Annotation for .NET 的文档？
您可以参考详细文档[这里](https://reference.groupdocs.com/annotation/net/).
### 如何获取 GroupDocs.Annotation for .NET 的临时许可证？
您可以从以下位置获取临时许可证[这个链接](https://purchase.groupdocs.com/temporary-license/).
### 我可以在哪里寻求有关 GroupDocs.Annotation for .NET 的支持或提出问题？
您可以访问 GroupDocs.Annotation 论坛[这里](https://forum.groupdocs.com/c/annotation/10).