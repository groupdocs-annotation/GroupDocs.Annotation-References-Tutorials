---
"description": "了解如何使用 GroupDocs.Annotation for .NET 为文档添加文本高亮注释。借助这项全面的功能，增强协作和生产力。"
"linktitle": "向文档添加文本高亮注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "向文档添加文本高亮注释"
"url": "/zh/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# 向文档添加文本高亮注释

## 介绍
在文档管理和协作领域，GroupDocs.Annotation for .NET 是一个强大的解决方案，它使开发人员能够将文本高亮注释无缝集成到他们的应用程序中。本教程将全面指导您如何使用 GroupDocs.Annotation for .NET 为文档添加文本高亮注释。通过分步说明和详细讲解，您将能够熟练掌握这个强大库的功能。
## 先决条件
在深入研究文本高亮注释的实现之前，请确保已满足以下先决条件：
1. 环境设置：为.NET开发配置合适的开发环境。
2. 安装 GroupDocs.Annotation for .NET：从提供的 [下载链接](https://releases。groupdocs.com/annotation/net/).
3. 熟悉 C#：对 C# 编程语言有基本的了解。
4. 要注释的文档：准备您要注释的文档（例如 PDF）。

## 导入命名空间
首先，在 C# 代码中导入必要的命名空间，以利用 GroupDocs.Annotation for .NET 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#现在，让我们将添加文本高亮注释的过程分解为多个步骤：
## 步骤 1：定义输出路径
指定注释文档的保存输出路径：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤 2：初始化注释器
创建一个实例 `Annotator` 类，将文档文件名作为参数传递：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 步骤 3：创建高亮注释
实例化 `HighlightAnnotation` 对象并配置其属性：
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
将创建的高亮注释添加到文档中：
```csharp
annotator.Add(highlight);
```
## 步骤 5：保存带注释的文档
将注释后的文档保存到指定的输出路径：
```csharp
annotator.Save(outputPath);
```

## 结论
总而言之，GroupDocs.Annotation for .NET 提供了一种简化的方法，将文本高亮注释合并到文档中。通过遵循本教程中概述的步骤，开发人员可以无缝地增强其应用程序中的文档协作和生产力。
## 常见问题解答
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、Word、Excel 等。请参阅文档以获取完整列表。
### 注释是否可以根据具体要求进行定制？
是的，开发人员可以完全控制注释的属性和外观，从而进行定制以满足不同的需求。
### GroupDocs.Annotation for .NET 有免费试用版吗？
是的，您可以通过访问提供的免费试用版来探索 GroupDocs.Annotation for .NET 的功能 [关联](https://releases。groupdocs.com/).
### 如何获得与 GroupDocs.Annotation for .NET 相关的任何问题或疑问的支持？
如需支持和帮助，您可以访问 GroupDocs.Annotation 论坛 [这里](https://forum。groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET 有哪些许可选项？
GroupDocs.Annotation for .NET 提供多种许可选项，包括用于测试的临时许可证和用于生产环境的商业许可证。访问购买页面 [这里](https://purchase.groupdocs.com/buy) 了解更多详情。