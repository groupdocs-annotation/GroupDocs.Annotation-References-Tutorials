---
"description": "了解如何使用 Groupdocs.Annotation for .NET 轻松地向文档添加文本波浪注释。增强协作和文档审查流程。"
"linktitle": "向文档添加文本波浪注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "向文档添加文本波浪注释"
"url": "/zh/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# 向文档添加文本波浪注释

## 介绍

Groupdocs.Annotation for .NET 是一个多功能库，可帮助开发人员轻松地将强大的注释功能集成到其 .NET 应用程序中。无论您处理的是 PDF、Word 文档还是其他常用文件格式，Groupdocs.Annotation 都能提供无缝的解决方案，帮助您注释文档并增强协作。

## 先决条件

在深入学习本教程之前，请确保您已满足以下先决条件：

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

现在我们已经了解了先决条件，让我们将添加文本波浪注释的过程分解为多个步骤。

## 步骤 1：定义输出路径

定义注释文档的保存路径。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 步骤 2：初始化注释器

通过提供输入文档路径来初始化 Annotator 对象。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注释代码放在这里
}
```

## 步骤 3：创建波浪注释

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

## 步骤 4：添加注释

将创建的波浪注释添加到文档中。

```csharp
annotator.Add(squiggly);
```

## 步骤5：保存文档

将注释文档保存到指定的输出路径。

```csharp
annotator.Save(outputPath);
```

## 步骤6：显示确认

显示一条消息，确认注释文档已成功保存。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论

总而言之，Groupdocs.Annotation for .NET 为开发人员提供了一套强大的工具，可将文档注释功能无缝集成到他们的 .NET 应用程序中。按照本分步指南，您可以轻松地在文档中添加文本波浪注释，从而增强协作和文档审阅流程。

## 常见问题解答

### 问：Groupdocs.Annotation 可以支持各种文件格式的注释吗？

答：是的，Groupdocs.Annotation 支持多种文件格式的注释，包括 PDF、Word 文档、Excel 表格等。

### 问：Groupdocs.Annotation 是否兼容桌面和 Web 应用程序？

答：当然！Groupdocs.Annotation 可以无缝集成到桌面和 Web 应用程序中，提供灵活性和多功能性。

### 问：Groupdocs.Annotation 是否有任何可用的许可选项？

答：是的，Groupdocs.Annotation 提供灵活的许可选项，以满足个人或企业的需求，包括用于试用的临时许可证。

### 问：使用 Groupdocs.Annotation 创建的注释可以自定义吗？

答：当然！Groupdocs.Annotation 为注释提供了广泛的自定义选项，允许开发人员根据他们的特定需求定制注释。

### 问：Groupdocs.Annotation 是否为开发人员提供支持和文档？

答：确实如此！Groupdocs.Annotation 提供了全面的文档和专门的支持论坛，以帮助开发人员有效地利用其功能。