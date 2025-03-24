---
title: 向文档添加椭圆注释
linktitle: 向文档添加椭圆注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中向文档添加椭圆注释。轻松增强协作和沟通。
weight: 13
url: /zh/net/unlocking-annotation-power/add-ellipse-annotation/
---

# 向文档添加椭圆注释

## 介绍
在本教程中，您将学习如何使用 GroupDocs.Annotation for .NET 将椭圆注释添加到文档中。本分步指南将引导您完成整个过程，确保您清楚地理解每个步骤。
## 先决条件
在开始之前，请确保您具备以下条件：
1.  GroupDocs.Annotation for .NET：确保您已下载并安装 GroupDocs.Annotation for .NET。您可以从以下位置下载：[这里](https://releases.groupdocs.com/annotation/net/).
2. IDE（集成开发环境）：您需要在系统上安装 IDE（例如 Visual Studio）来编写和执行代码。

## 导入命名空间
首先，将必要的命名空间导入到您的项目中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 第1步：设置输出路径
定义保存注释文档的输出路径：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器
通过提供输入文档路径来初始化注释器：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 第 3 步：创建椭圆注释
创建一个实例`EllipseAnnotation`类并设置其属性：
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## 第四步：添加注释
将椭圆注释添加到文档中：
```csharp
annotator.Add(ellipse);
```
## 第5步：保存文档
将注释文档保存到输出路径：
```csharp
annotator.Save(outputPath);
```

## 结论
恭喜！您已使用 GroupDocs.Annotation for .NET 成功向文档添加了椭圆注释。您现在可以将此功能集成到您的 .NET 应用程序中，以增强文档协作和通信。
## 常见问题解答
### 我可以自定义椭圆注释的外观吗？
是的，您可以根据您的要求自定义各种属性，例如背景颜色、边框颜色、不透明度等。
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、DOCX、PPTX、XLSX 等。
### 我可以在一个文档中添加多个注释吗？
是的，您可以向单个文档添加多个注释，包括椭圆、矩形、文本等。
### 是否有可用于测试目的的试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/)来评价其特点。
### 在哪里可以获得 GroupDocs.Annotation for .NET 的技术支持？
您可以从 GroupDocs.Annotation 社区论坛获得技术支持[这里](https://forum.groupdocs.com/c/annotation/10).