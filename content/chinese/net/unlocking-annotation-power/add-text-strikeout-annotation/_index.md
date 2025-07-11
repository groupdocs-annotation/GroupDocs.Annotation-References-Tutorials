---
"description": "了解如何使用 GroupDocs.Annotation for .NET 为文档添加文本删除线注释。高效增强协作和文档审阅流程。"
"linktitle": "为文档添加文本删除线注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "为文档添加文本删除线注释"
"url": "/zh/net/unlocking-annotation-power/add-text-strikeout-annotation/"
"weight": 26
---

# 为文档添加文本删除线注释

## 介绍
在本教程中，我们将探索如何使用 GroupDocs.Annotation for .NET 为文档添加文本删除线注释。该库提供了强大的工具，可用于注释各种文档类型，从而增强协作和文档审阅流程。
## 先决条件
在开始之前，请确保您满足以下先决条件：
1. GroupDocs.Annotation for .NET：安装该库。您可以从以下位置下载 [这里](https://releases。groupdocs.com/annotation/net/).
2. 开发环境：为.NET开发设置合适的开发环境。
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
## 步骤 1：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在这里，我们定义注释文档的保存输出路径。
## 步骤 2：初始化注释器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
通过提供输入文档（在本例中为 PDF 文件）的路径来初始化 Annotator 对象。
## 步骤 3：创建删除线注释
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
## 步骤 4：添加注释
```csharp
annotator.Add(strikeout);
```
将创建的删除线注释添加到文档中。
## 步骤5：保存文档
```csharp
annotator.Save(outputPath);
```
将注释文档保存到指定的输出路径。

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 为文档添加文本删除线注释。这个强大的库可以实现高效的文档注释，从而增强协作和文档审阅流程。
## 常见问题解答
### GroupDocs.Annotation 是否兼容各种文档格式？
是的，GroupDocs.Annotation 支持多种文档格式，包括 PDF、Word、Excel、PowerPoint 等。
### 我可以自定义注释的外观吗？
当然，您可以根据您的要求自定义注释属性，例如颜色、不透明度、字体大小等。
### GroupDocs.Annotation 是否提供协作功能？
是的，GroupDocs.Annotation 允许用户向文档添加评论、回复和注释，从而促进协作。
### 有免费试用吗？
是的，您可以免费试用 [这里](https://releases。groupdocs.com/).
### 我可以在哪里获得 GroupDocs.Annotation 的支持？
您可以从 [GroupDocs.Annotation 论坛](https://forum。groupdocs.com/c/annotation/10).