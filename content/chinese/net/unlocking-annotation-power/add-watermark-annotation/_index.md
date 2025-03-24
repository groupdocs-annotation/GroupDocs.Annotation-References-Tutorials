---
title: 向文档添加水印注释
linktitle: 向文档添加水印注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 轻松地将水印注释添加到文档中。提高文档的清晰度和安全性。
weight: 28
url: /zh/net/unlocking-annotation-power/add-watermark-annotation/
---

# 向文档添加水印注释

## 介绍
在本教程中，我们将逐步介绍使用 GroupDocs.Annotation for .NET 向文档添加水印注释的过程。水印注释可用于指示文档的状态、将其标记为机密或添加任何其他相关信息。

## 先决条件

在我们开始之前，请确保您具备以下条件：

1.  GroupDocs.Annotation for .NET：您可以从以下位置下载：[这里](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio：确保您的系统上安装了 Visual Studio。
3. C# 基础知识：为了理解和实现代码示例，需要熟悉 C# 编程语言。

## 导入命名空间

在开始编码之前，让我们导入必要的名称空间：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

现在，我们将添加水印注释的过程分解为多个步骤：

## 第 1 步：定义输出路径

首先，我们需要定义保存注释文档的输出路径。我们将使用`Path`班级来自`System.IO`命名空间将输出目录路径与文件名组合在一起。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 2 步：初始化注释器

接下来，我们将通过提供输入文档的路径来初始化注释器。这将使我们能够向文档添加注释。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码将放在这里
}
```

## 步骤 3：创建水印注释

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

## 第四步：添加水印注释

现在，我们将使用以下命令将水印注释添加到文档中`Add`注释器对象的方法。

```csharp
annotator.Add(watermark);
```

## 第5步：保存文档

最后，我们将注释文档保存到指定的输出路径。

```csharp
annotator.Save(outputPath);
```

## 结论

在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加水印注释。水印注释是一种有用的工具，可以用相关信息标记文档或指示其状态。

## 常见问题解答

### 问：我可以自定义水印注释的外观吗？

答：是的，您可以自定义各种属性，如文本、字体大小、颜色、不透明度、位置等，根据您的要求定制水印。

### 问：GroupDocs.Annotation for .NET 是否兼容不同的文档格式？

答：是的，GroupDocs.Annotation 支持多种文档格式，包括 PDF、Microsoft Word、Excel、PowerPoint 和图像格式。

### 问：我可以在一个文档中添加多个注释吗？

答：当然可以，GroupDocs.Annotation 允许您向单个文档添加多个不同类型的注释，从而实现全面的文档标记。

### 问：GroupDocs.Annotation 是否提供协作注释支持？

答：是的，GroupDocs.Annotation 通过允许用户添加评论、回复和注释来促进协作注释，从而促进团队成员之间的有效协作。

### 问：GroupDocs.Annotation for .NET 是否有试用版？

答：是的，您可以从以下位置下载免费试用版：[这里](https://releases.groupdocs.com/).