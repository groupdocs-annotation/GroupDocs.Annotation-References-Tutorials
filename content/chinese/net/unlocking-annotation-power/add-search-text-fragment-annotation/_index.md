---
title: 将搜索文本片段注释添加到文档
linktitle: 将搜索文本片段注释添加到文档
second_title: GroupDocs.Annotation .NET API
description: 探索 GroupDocs.Annotation for .NET 的强大功能，轻松地将文档注释功能添加到您的应用程序中。
weight: 20
url: /zh/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## 介绍
在 .NET 开发领域，GroupDocs.Annotation 作为无缝注释文档的强大工具脱颖而出。无论您是经验丰富的开发人员还是刚刚踏入 .NET 世界，这个全面的教程将引导您了解使用 GroupDocs.Annotation for .NET 的基本知识，从导入命名空间到掌握向您的文档添加搜索文本片段注释的复杂性。文件。
## 介绍
GroupDocs.Annotation for .NET 使开发人员能够轻松地将文档注释功能合并到他们的应用程序中。凭借其直观的 API 和强大的功能，开发人员可以对各种文档格式进行注释，包括 PDF、Microsoft Office 文档、图像等。
## 先决条件
在深入研究 .NET 的 GroupDocs.Annotation 之前，请确保满足以下先决条件：

## 导入命名空间
首先，导入必要的命名空间以访问 .NET 项目中的 GroupDocs.Annotation 类和方法：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 第 1 步：定义输出路径
首先定义保存注释文档的输出路径：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器
接下来，初始化一个实例`Annotator`通过提供要注释的文档的路径来创建类：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 第 3 步：创建搜索文本片段注释
创建一个`SearchTextFragment`具有所需属性的对象，例如要搜索的文本、字体大小、字体系列、字体颜色和背景颜色：
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## 第四步：添加注释
使用以下命令将创建的搜索文本片段注释添加到文档中`Add`注释器的方法：
```csharp
annotator.Add(searchText);
```
## 第 5 步：保存带注释的文档
将注释文档保存到指定的输出路径：
```csharp
annotator.Save(outputPath);
```
## 第6步：显示成功消息
通知用户文档已成功保存：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
总之，GroupDocs.Annotation for .NET 简化了向文档添加注释的过程，增强了协作和文档审阅过程。通过遵循本指南中概述的步骤，您可以将文档注释功能无缝集成到您的 .NET 应用程序中。
## 常见问题解答
### GroupDocs.Annotation 是否与所有文档格式兼容？
是的，GroupDocs.Annotation 支持多种文档格式，包括 PDF、Microsoft Office 文档、图像等。
### 我可以自定义注释的外观吗？
绝对地！ GroupDocs.Annotation 为注释提供了广泛的自定义选项，允许您调整字体大小、颜色和样式等属性。
### GroupDocs.Annotation 是否有免费试用版？
是的，您可以在购买前免费试用 GroupDocs.Annotation 以探索其特性和功能[这里](https://releases.groupdocs.com/)..
### 在哪里可以找到对 GroupDocs.Annotation 的支持？
如需 GroupDocs.Annotation 的支持和帮助，您可以访问 GroupDocs[论坛](https://forum.groupdocs.com/c/annotation/10)致力于与注释相关的查询和讨论。
### 如何获得 GroupDocs.Annotation 的临时许可证？
您可以通过 GroupDocs 获取 GroupDocs.Annotation 的临时许可证[网站](https://purchase.groupdocs.com/temporary-license/)，使您能够全面评估产品。