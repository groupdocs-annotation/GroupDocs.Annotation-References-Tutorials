---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中向文档添加椭圆注释。轻松增强协作和沟通。"
"linktitle": "向文档添加椭圆注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "向文档添加椭圆注释"
"url": "/zh/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# 向文档添加椭圆注释

## 介绍
在本教程中，您将学习如何使用 GroupDocs.Annotation for .NET 向文档添加椭圆注释。本分步指南将引导您完成整个过程，确保您清楚地理解每个步骤。
## 先决条件
开始之前，请确保您已具备以下条件：
1. GroupDocs.Annotation for .NET：请确保您已下载并安装了 GroupDocs.Annotation for .NET。您可以从以下网址下载： [这里](https://releases。groupdocs.com/annotation/net/).
2. IDE（集成开发环境）：您需要在系统上安装一个 IDE，例如 Visual Studio，来编写和执行代码。

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
## 步骤1：设置输出路径
定义注释文档的保存输出路径：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤 2：初始化注释器
通过提供输入文档路径来初始化注释器：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 步骤 3：创建椭圆注释
创建一个实例 `EllipseAnnotation` 类并设置其属性：
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
## 步骤 4：添加注释
将椭圆注释添加到文档中：
```csharp
annotator.Add(ellipse);
```
## 步骤5：保存文档
将注释后的文档保存到输出路径：
```csharp
annotator.Save(outputPath);
```

## 结论
恭喜！您已成功使用 GroupDocs.Annotation for .NET 向文档添加椭圆注释。现在，您可以将此功能集成到您的 .NET 应用程序中，以增强文档协作和沟通。
## 常见问题解答
### 我可以自定义椭圆注释的外观吗？
是的，您可以根据您的要求自定义各种属性，例如背景颜色、边框颜色、不透明度等。
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、DOCX、PPTX、XLSX 等。
### 我可以在单个文档中添加多个注释吗？
是的，您可以在单个文档中添加多个注释，包括椭圆、矩形、文本等。
### 是否有可供测试的试用版？
是的，您可以从下载免费试用版 [这里](https://releases.groupdocs.com/) 来评估其特征。
### 在哪里可以获得 GroupDocs.Annotation for .NET 的技术支持？
您可以从 GroupDocs.Annotation 社区论坛获得技术支持 [这里](https://forum。groupdocs.com/c/annotation/10).