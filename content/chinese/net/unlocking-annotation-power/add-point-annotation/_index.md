---
"description": "了解如何使用 GroupDocs.Annotation for .NET 为 PDF 添加点注释。无缝集成的分步指南。"
"linktitle": "向文档添加点注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "向文档添加点注释"
"url": "/zh/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# 向文档添加点注释

## 介绍
GroupDocs.Annotation for .NET 是一款功能强大的工具，允许开发人员以编程方式向文档添加各种类型的注释。在本教程中，我们将重点介绍如何使用 C# 向文档添加点注释 (Point Annotation)。
## 先决条件
在开始之前，请确保您具备以下条件：
1. 对 C# 编程语言有基本的了解。
2. 您的系统上安装了 Visual Studio。
3. 已安装 GroupDocs.Annotation for .NET 库。您可以从 [这里](https://releases。groupdocs.com/annotation/net/).

## 导入必要的命名空间
首先，您需要将所需的命名空间导入到您的 C# 项目中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 步骤 1：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步骤中，我们定义注释文档的保存输出路径。
## 步骤 2：初始化注释器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
在这里，我们初始化 `Annotator` 具有输入文档的对象（“input.pdf”）。
## 步骤 3：创建点注释
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
在此步骤中，我们创建一个 `PointAnnotation` 对象并指定其属性，例如位置、消息、页码和回复。
## 步骤 4：添加注释
```csharp
annotator.Add(point);
```
在这里，我们将创建的点注释添加到文档中。
## 步骤5：保存文档
```csharp
annotator.Save(outputPath);
```
最后我们将注释后的文档保存到指定的输出路径。

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加点注释。借助这个强大的库，您可以通过合并注释功能来增强文档管理应用程序。
## 常见问题解答
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
是的，GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以自定义注释的外观吗？
当然！GroupDocs.Annotation for .NET 提供了丰富的选项，可自定义注释的外观以满足您的应用程序需求。
### GroupDocs.Annotation for .NET 有免费试用版吗？
是的，您可以免费试用 [这里](https://releases。groupdocs.com/).
### 如何获得与 GroupDocs.Annotation for .NET 相关的任何问题或疑问的支持？
您可以从 GroupDocs.Annotation 论坛获得支持 [这里](https://forum。groupdocs.com/c/annotation/10).
### 我可以获得临时许可证以用于测试吗？
是的，你可以从 [这里](https://purchase。groupdocs.com/temporary-license/).