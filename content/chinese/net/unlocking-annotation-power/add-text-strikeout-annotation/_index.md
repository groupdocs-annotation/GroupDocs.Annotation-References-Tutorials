---
title: 向文档添加文本删除线注释
linktitle: 向文档添加文本删除线注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将文本删除线注释添加到文档中。有效增强协作和文档审核流程。
type: docs
weight: 26
url: /zh/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Annotation for .NET 将文本删除线注释添加到文档中。该库提供了强大的工具来注释各种文档类型、增强协作和文档审阅流程。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1.  GroupDocs.Annotation for .NET：安装库。您可以从以下位置下载：[这里](https://releases.groupdocs.com/annotation/net/).
2. 开发环境：为.NET开发搭建合适的开发环境。
3. 文档：准备好要注释的文档，例如 PDF 文件。

## 导入命名空间
首先，导入必要的命名空间以访问 GroupDocs.Annotation 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

现在，让我们将添加文本删除线注释的过程分解为多个步骤：
## 第 1 步：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在这里，我们定义保存注释文档的输出路径。
## 第 2 步：初始化注释器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
通过提供输入文档（本例中为 PDF 文件）的路径来初始化 Annotator 对象。
## 第 3 步：创建删除线注释
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
创建具有所需属性（例如消息、不透明度、页码、背景颜色、点（坐标）和回复）的 StrikeoutAnnotation 对象。
## 第四步：添加注释
```csharp
annotator.Add(strikeout);
```
将创建的删除线注释添加到文档中。
## 第5步：保存文档
```csharp
annotator.Save(outputPath);
```
将注释文档保存到指定的输出路径。

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加文本删除线注释。这个功能强大的库可实现高效的文档注释，增强协作和文档审阅流程。
## 常见问题解答
### GroupDocs.Annotation 是否兼容各种文档格式？
是的，GroupDocs.Annotation 支持多种文档格式，包括 PDF、Word、Excel、PowerPoint 等。
### 我可以自定义注释的外观吗？
当然，您可以根据您的要求自定义注释属性，例如颜色、不透明度、字体大小等。
### GroupDocs.Annotation 是否提供协作功能？
是的，GroupDocs.Annotation 允许用户向文档添加评论、回复和注释，从而促进协作。
### 有免费试用吗？
是的，您可以免费试用[这里](https://releases.groupdocs.com/).
### 在哪里可以获得 GroupDocs.Annotation 的支持？
您可以从以下方面获得支持[GroupDocs.Annotation 论坛](https://forum.groupdocs.com/c/annotation/10).