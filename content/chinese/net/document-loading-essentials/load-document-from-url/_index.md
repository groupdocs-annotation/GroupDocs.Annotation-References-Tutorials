---
title: 从 URL 加载文档
linktitle: 从 URL 加载文档
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 以编程方式注释 PDF 文档。带有代码示例的分步教程。
weight: 15
url: /zh/net/document-loading-essentials/load-document-from-url/
---
## 介绍
GroupDocs.Annotation for .NET 是一个功能丰富的库，使开发人员能够轻松地将注释功能添加到其 .NET 应用程序中。借助 GroupDocs.Annotation，您可以通过编程方式对 PDF 文档进行注释，从而允许用户突出显示文本、添加注释、绘制形状等。本教程将引导您完成从 URL 加载文档、添加注释以及使用 GroupDocs.Annotation for .NET 保存带注释的文档的步骤。
## 先决条件
在开始之前，请确保您具备以下先决条件：
1. Visual Studio：确保您的开发计算机上安装了 Visual Studio。
2.  GroupDocs.Annotation for .NET：从以下位置下载并安装 GroupDocs.Annotation for .NET[网站](https://releases.groupdocs.com/annotation/net/).
3. C# 基础知识：熟悉 C# 编程语言。
4. Internet 连接：您需要 Internet 连接才能访问外部资源并下载示例文件。

## 导入命名空间
首先，让我们在 C# 项目中导入必要的命名空间：
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## 第 1 步：从 URL 加载文档
要从 URL 注释 PDF 文档，请按照下列步骤操作：
### 步骤1.1：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 步骤1.2：指定URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### 步骤1.3：加载文档
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    //在这里添加注释
    annotator.Save(outputPath);
}
```
## 第 2 步：添加注释
现在，让我们向加载的文档添加注释。在此示例中，我们将添加区域注释：
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 第 3 步：保存带注释的文档
最后将注释文档保存到指定的输出路径：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 对 PDF 文档进行注释。通过遵循分步指南，您可以将注释功能无缝集成到 .NET 应用程序中，使用户能够有效地协作处理 PDF 文件。

## 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有 .NET 框架兼容？
是的，GroupDocs.Annotation for .NET 与各种 .NET 框架兼容，包括 .NET Framework、.NET Core 和 .NET Standard。
### 我可以自定义注释的外观吗？
绝对地！ GroupDocs.Annotation for .NET 提供了广泛的自定义选项，允许您根据需要修改注释的外观和行为。
### GroupDocs.Annotation for .NET 是否有免费试用版？
是的，您可以从以下位置下载 GroupDocs.Annotation for .NET 的免费试用版：[网站](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Annotation for .NET 的技术支持？
如果您遇到任何技术问题或对 GroupDocs.Annotation for .NET 有疑问，可以寻求帮助[支持论坛](https://forum.groupdocs.com/c/annotation/10).
### 在哪里可以购买 GroupDocs.Annotation for .NET 的许可证？
您可以从 GroupDocs.Annotation for .NET 购买许可证[购买页面](https://purchase.groupdocs.com/buy).