---
title: 向文档添加文本波浪注释
linktitle: 向文档添加文本波浪注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 Groupdocs.Annotation for .NET 轻松地将文本波浪线注释添加到文档中。加强协作和文件审查流程。
type: docs
weight: 25
url: /zh/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## 介绍

Groupdocs.Annotation for .NET 是一个多功能库，使开发人员能够轻松地将强大的注释功能集成到他们的 .NET 应用程序中。无论您使用 PDF、Word 文档还是其他流行的文件格式，Groupdocs.Annotation 都可以提供用于注释和增强文档协作的无缝解决方案。

## 先决条件

在深入学习本教程之前，请确保您具备以下先决条件：

## 导入命名空间

确保导入必要的命名空间以访问 Groupdocs.Annotation for .NET 提供的功能。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

现在我们已经满足了先决条件，让我们将添加文本波浪注释的过程分解为多个步骤。

## 第 1 步：定义输出路径

定义注释文档的保存路径。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 2 步：初始化注释器

通过提供输入文档路径来初始化 Annotator 对象。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码放在这里
}
```

## 第 3 步：创建波浪形注释

创建一个 SquigglyAnnotation 对象并指定其属性。

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## 第四步：添加注释

将创建的波浪形注释添加到文档中。

```csharp
annotator.Add(squiggly);
```

## 第5步：保存文档

将注释文档保存到指定的输出路径。

```csharp
annotator.Save(outputPath);
```

## 第 6 步：显示确认信息

显示一条消息，确认已成功保存带注释的文档。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论

总之，Groupdocs.Annotation for .NET 为开发人员提供了一组强大的工具，用于将文档注释功能无缝集成到他们的 .NET 应用程序中。通过遵循此分步指南，您可以轻松地向文档添加文本波浪线注释，从而增强协作和文档审阅流程。

## 常见问题解答

### 问：Groupdocs.Annotation 可以支持各种文件格式的注释吗？

答：是的，Groupdocs.Annotation 支持对多种文件格式进行注释，包括 PDF、Word 文档、Excel 工作表等。

### 问：Groupdocs.Annotation 是否与桌面和 Web 应用程序兼容？

答：当然！ Groupdocs.Annotation 可以无缝集成到桌面和 Web 应用程序中，提供灵活性和多功能性。

### 问：Groupdocs.Annotation 是否有可用的许可选项？

答：是的，Groupdocs.Annotation 提供灵活的许可选项，以满足个人或企业的需求，包括用于试用目的的临时许可证。

### 问：可以自定义使用 Groupdocs.Annotation 创建的注释吗？

答：当然可以！ Groupdocs.Annotation 为注释提供了广泛的自定义选项，允许开发人员根据其特定要求定制注释。

### 问：Groupdocs.Annotation 是否为开发人员提供支持和文档？

答：确实如此！ Groupdocs.Annotation 提供全面的文档和专门的支持论坛，以帮助开发人员有效地利用其功能。