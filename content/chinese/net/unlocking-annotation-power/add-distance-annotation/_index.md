---
title: 向文档添加距离注释
linktitle: 向文档添加距离注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 向文档添加距离注释。轻松增强协作和沟通。
type: docs
weight: 12
url: /zh/net/unlocking-annotation-power/add-distance-annotation/
---
## 介绍
在本教程中，您将学习如何使用 GroupDocs.Annotation for .NET 向文档添加距离注释。请按照以下步骤完成任务：
## 先决条件

在继续之前，请确保您具备以下先决条件：

-  GroupDocs.Annotation for .NET 库：从以下位置下载并安装 GroupDocs.Annotation for .NET 库[这个链接](https://releases.groupdocs.com/annotation/net/).
- 要注释的文档：准备要添加距离注释的文档（例如 PDF）。
- 开发环境：使用 Visual Studio 或您选择的任何其他 IDE 设置您的开发环境。

## 导入命名空间

开始之前，请确保在代码中包含必要的命名空间。这些命名空间对于访问所需的类和方法至关重要。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 第 1 步：初始化注释器

首先初始化`Annotator`对象，其中包含要注释的文档的路径。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码将放在这里
}
```

## 第 2 步：创建距离注释

现在，创建一个`DistanceAnnotation`对象并配置其属性，例如框尺寸、消息、不透明度、画笔颜色等。

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## 第三步：添加注释

使用以下命令将创建的距离注释添加到文档中`Add`注释器对象的方法。

```csharp
annotator.Add(distance);
```

## 第 4 步：保存文档

将带注释的文档保存到系统上的所需位置。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## 第5步：显示确认

最后，显示一条消息，确认已成功保存带注释的文档。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论

使用 GroupDocs.Annotation for .NET 向文档添加距离注释是一个简单的过程。通过遵循本教程中概述的步骤，您可以使用有价值的注释来增强文档，从而促进更好的协作和沟通。

## 常见问题解答

### 问：我可以自定义距离注释的外观吗？

答：是的，您可以自定义各种属性，例如颜色、不透明度、线条样式等，以满足您的要求。

### 问：GroupDocs.Annotation 是否支持不同类型文档的注释？

答：是的，GroupDocs.Annotation 支持多种文档格式的注释，包括 PDF、Word、Excel、PowerPoint 等。

### 问：GroupDocs.Annotation 是否有免费试用版？

答：是的，您可以访问 GroupDocs.Annotation 的免费试用版[这个链接](https://releases.groupdocs.com/).

### 问：在哪里可以找到 GroupDocs.Annotation for .NET 的文档？

 A：您可以参考详细的文档[这里](https://reference.groupdocs.com/annotation/net/).

### 问：如何获得 GroupDocs.Annotation 的支持或帮助？

答：您可以从 GroupDocs.Annotation 社区论坛寻求支持和帮助[这里](https://forum.groupdocs.com/c/annotation/10).