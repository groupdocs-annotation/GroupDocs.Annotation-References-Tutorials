---
title: 将资源编辑注释添加到文档
linktitle: 将资源编辑注释添加到文档
second_title: GroupDocs.Annotation .NET API
description: 使用 GroupDocs.Annotation for .NET 增强文档管理工作流程。将资源编辑注释无缝集成到您的 .NET 中以提高效率。
type: docs
weight: 19
url: /zh/net/unlocking-annotation-power/add-resources-redaction-annotation/
---
## 介绍
在 .NET 开发领域，集成高效的文档注释工具可以显着提高生产力并简化工作流程。 GroupDocs.Annotation for .NET 作为一个强大的解决方案出现，提供了大量的功能来无缝注释和操作文档。本教程深入探讨了集成和利用资源修订注释的过程，这是 GroupDocs.Annotation for .NET 中的一项强大功能。
## 先决条件
在深入实施之前，请确保满足以下先决条件：
### 1..NET开发环境
确保您的计算机上设置了功能齐全的 .NET 开发环境。如果没有，您可以从 Microsoft 网站下载并安装最新版本的 .NET SDK。
### 2..NET 的 GroupDocs.Annotation
从提供的下载并安装 GroupDocs.Annotation for .NET 库[下载链接](https://releases.groupdocs.com/annotation/net/)。请按照文档中概述的安装说明进行无缝集成。
### 3.C#的基本理解
熟悉 C# 编程语言语法和概念，以有效实现所提供的代码片段。

## 导入命名空间
使用 GroupDocs.Annotation for .NET 合并必要的命名空间来访问文档注释所需的类和方法。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 第 1 步：定义输出路径
指定保存注释文档的输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器对象
通过提供输入文档的路径来实例化 Annotator 对象。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //这里会添加注释代码
}
```
## 步骤 3：创建资源编辑注释
定义具有所需属性的 ResourcesRedactionAnnotation 对象，例如框尺寸、消息、页码和回复。
```csharp
ResourcesRedactionAnnotation resourcesRedaction = new ResourcesRedactionAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is resources redaction annotation",
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
## 第四步：添加注释
使用注释器对象将创建的资源编辑注释添加到文档中。
```csharp
annotator.Add(resourcesRedaction);
```
## 第 5 步：保存带注释的文档
将注释文档保存到指定的输出路径。
```csharp
annotator.Save(outputPath);
```
## 第6步：显示成功消息
通知用户注释过程已成功完成，并提供注释文档的路径。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
总之，GroupDocs.Annotation for .NET 提供了一套全面的文档注释工具，使 .NET 开发人员能够有效地增强文档管理工作流程。通过遵循本教程中概述的分步指南，您可以将资源编辑注释无缝集成到您的 .NET 应用程序中，从而提高协作和工作效率。
## 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、DOCX、PPTX、XLSX 等。
### 我可以自定义使用 GroupDocs.Annotation for .NET 创建的注释的外观吗？
是的，您可以通过调整颜色、不透明度和线条粗细等属性来自定义注释的外观。
### GroupDocs.Annotation for .NET 是否有免费试用版？
是的，您可以从提供的产品中免费试用 GroupDocs.Annotation for .NET[关联](https://releases.groupdocs.com/).
### 如何寻求 GroupDocs.Annotation for .NET 的帮助或支持？
您可以访问 GroupDocs.Annotation 论坛[这里](https://forum.groupdocs.com/c/annotation/10)向社区寻求帮助或提交您的疑问。
### 在哪里可以获得 GroupDocs.Annotation for .NET 的临时许可证？
您可以从提供的提供的 GroupDocs.Annotation for .NET 中获取临时许可证。[关联](https://purchase.groupdocs.com/temporary-license/).