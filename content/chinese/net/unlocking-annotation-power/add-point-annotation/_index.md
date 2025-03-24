---
title: 向文档添加点注释
linktitle: 向文档添加点注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将点注释添加到 PDF。无缝集成的分步指南。
weight: 17
url: /zh/net/unlocking-annotation-power/add-point-annotation/
---

# 向文档添加点注释

## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的工具，允许开发人员以编程方式向文档添加各种类型的注释。在本教程中，我们将重点介绍如何使用 C# 将点注释添加到文档中。
## 先决条件
在我们开始之前，请确保您具备以下条件：
1. 对 C# 编程语言有基本了解。
2. Visual Studio 安装在您的系统上。
3. 安装了 .NET 库的 GroupDocs.Annotation。您可以从以下位置下载：[这里](https://releases.groupdocs.com/annotation/net/).

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
## 第 1 步：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步骤中，我们定义保存带注释的文档的输出路径。
## 第 2 步：初始化注释器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
在这里，我们初始化`Annotator`对象与输入文档（“input.pdf”）。
## 第 3 步：创建点注释
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
在这一步中，我们创建一个`PointAnnotation`对象并指定其属性，例如位置、消息、页码和回复。
## 第四步：添加注释
```csharp
annotator.Add(point);
```
在这里，我们将创建的点注释添加到文档中。
## 第5步：保存文档
```csharp
annotator.Save(outputPath);
```
最后，我们将注释文档保存到指定的输出路径。

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 将点注释添加到文档中。借助这个强大的库，您可以通过合并注释功能来增强文档管理应用程序。
## 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
是的，GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以自定义注释的外观吗？
绝对地！ GroupDocs.Annotation for .NET 提供了广泛的选项来自定义注释的外观以满足您的应用程序的需求。
### GroupDocs.Annotation for .NET 是否有免费试用版？
是的，您可以免费试用[这里](https://releases.groupdocs.com/).
### 对于与 GroupDocs.Annotation for .NET 相关的任何问题或查询，如何获得支持？
您可以从 GroupDocs.Annotation 论坛获得支持[这里](https://forum.groupdocs.com/c/annotation/10).
### 我可以获得用于测试目的的临时许可证吗？
是的，您可以从以下地址获得临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).