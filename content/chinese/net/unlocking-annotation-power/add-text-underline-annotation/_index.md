---
"description": "了解如何使用 GroupDocs.Annotation for .NET 为文档添加文本下划线注释。轻松增强协作和沟通。"
"linktitle": "为文档添加文本下划线注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "为文档添加文本下划线注释"
"url": "/zh/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# 为文档添加文本下划线注释

## 介绍
在本教程中，我们将演示如何使用 GroupDocs.Annotation for .NET 向文档添加文本下划线批注。文本下划线批注可用于强调文档的特定部分，例如重要段落或关键点。
## 先决条件
在开始之前，请确保您已安装以下先决条件：
1. GroupDocs.Annotation for .NET：从以下位置下载并安装 GroupDocs.Annotation for .NET [这里](https://releases。groupdocs.com/annotation/net/).
2. .NET Framework：确保您的系统上安装了 .NET Framework。

## 导入命名空间
首先，让我们将必要的命名空间导入到我们的项目中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

现在，让我们将示例分解为多个步骤：
## 步骤 1：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步骤中，我们定义注释文档的保存输出路径。
## 步骤 2：初始化注释器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
在这里，我们初始化一个实例 `Annotator` 通过提供输入文档的路径来类。
## 步骤 3：创建下划线注释
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // 仅支持 Word 和 PDF 文档
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
此步骤涉及创建一个 `UnderlineAnnotation` 具有各种属性的对象，例如字体颜色、消息、不透明度、页码、背景颜色、下划线颜色、点和回复。
## 步骤 4：向文档添加注释
```csharp
annotator.Add(underline);
```
在这里，我们为文档添加下划线注释。
## 步骤 5：保存带注释的文档
```csharp
annotator.Save(outputPath);
```
最后我们将注释后的文档保存到指定的输出路径。

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加文本下划线注释。这个强大的库提供了各种注释选项，以增强文档协作和沟通。
## 常见问题解答
### 我可以自定义下划线注释的外观吗？
是的，您可以根据您的要求自定义颜色、不透明度和位置等属性。
### GroupDocs.Annotation 是否兼容不同的文档格式？
是的，GroupDocs.Annotation 支持多种文档格式，包括 Word 和 PDF。
### 我可以在单个文档中添加多个注释吗？
当然，GroupDocs.Annotation 允许您向文档添加不同类型的多个注释。
### GroupDocs.Annotation 有免费试用版吗？
是的，您可以从 [这里](https://releases。groupdocs.com/).
### 我可以在哪里获得 GroupDocs.Annotation 的支持？
您可以从 GroupDocs.Annotation 社区论坛获得支持 [这里](https://forum。groupdocs.com/c/annotation/10).