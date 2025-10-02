---
"description": "了解如何使用 GroupDocs.Annotation for .NET 轻松地为文档添加水印注释。增强文档的清晰度和安全性。"
"linktitle": "为文档添加水印注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "为文档添加水印注释"
"url": "/zh/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# 为文档添加水印注释

## 介绍
在本教程中，我们将演示如何使用 GroupDocs.Annotation for .NET 向文档添加水印注释。水印注释可用于指示文档的状态、将其标记为机密或添加任何其他相关信息。

## 先决条件

在开始之前，请确保您具备以下条件：

1. GroupDocs.Annotation for .NET：您可以从 [这里](https://releases。groupdocs.com/annotation/net/).
2. Visual Studio：确保您的系统上安装了 Visual Studio。
3. C# 基础知识：熟悉 C# 编程语言对于理解和实现代码示例是必要的。

## 导入命名空间

在开始编码之前，让我们导入必要的命名空间：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

现在，让我们将添加水印注释的过程分解为多个步骤：

## 步骤 1：定义输出路径

首先，我们需要定义注释文档的保存路径。我们将使用 `Path` 来自的类 `System.IO` 命名空间将输出目录路径与文件名结合起来。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 步骤 2：初始化注释器

接下来，我们将通过提供输入文档的路径来初始化注释器。这将允许我们向文档添加注释。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注释代码将放在这里
}
```

## 步骤3：创建水印注释

现在，让我们创建一个具有所需属性的水印注释对象，例如角度、位置、文本、字体颜色、不透明度等。

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## 步骤4：添加水印注释

现在，我们将使用 `Add` 注释器对象的方法。

```csharp
annotator.Add(watermark);
```

## 步骤5：保存文档

最后，我们将注释的文档保存到指定的输出路径。

```csharp
annotator.Save(outputPath);
```

## 结论

在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加水印注释。水印注释是一种非常有用的工具，可用于在文档中标记相关信息或指示其状态。

## 常见问题解答

### 问：我可以自定义水印注释的外观吗？

答：是的，您可以自定义各种属性，例如文本、字体大小、颜色、不透明度、位置等，以根据您的要求定制水印。

### 问：GroupDocs.Annotation for .NET 是否兼容不同的文档格式？

答：是的，GroupDocs.Annotation 支持多种文档格式，包括 PDF、Microsoft Word、Excel、PowerPoint 和图像格式。

### 问：我可以向单个文档添加多个注释吗？

答：当然，GroupDocs.Annotation 允许您向单个文档添加不同类型的多个注释，从而实现全面的文档标记。

### 问：GroupDocs.Annotation 是否提供协作注释支持？

答：是的，GroupDocs.Annotation 允许用户添加评论、回复和注释，从而促进协作注释，促进团队成员之间的有效协作。

### 问：GroupDocs.Annotation for .NET 有试用版吗？

答：是的，您可以从以下网址下载免费试用版 [这里](https://releases。groupdocs.com/).