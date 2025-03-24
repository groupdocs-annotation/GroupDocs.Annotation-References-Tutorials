---
title: 将图像注释添加到文档（本地路径）
linktitle: 将图像注释添加到文档（本地路径）
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将图像注释添加到文档中。轻松增强文档处理能力。
weight: 14
url: /zh/net/unlocking-annotation-power/add-image-annotation-local-path/
---

# 将图像注释添加到文档（本地路径）

## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的库，允许开发人员以编程方式向文档添加各种类型的注释。在本教程中，我们将学习如何使用本地路径向文档添加图像注释。
## 先决条件
在我们开始之前，请确保您具备以下先决条件：
1. C# 编程语言的基础知识。
2. Visual Studio 安装在您的系统上。
3. 项目中安装或引用的 .NET 库的 GroupDocs.Annotation。
4. 输入文档（例如 PDF）和用于注释的图像文件。
## 导入命名空间
首先，您需要将必要的命名空间导入到 C# 文件中。这些命名空间提供对使用 GroupDocs.Annotation 所需的类和方法的访问。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 第 1 步：定义输出路径
定义保存注释文档的输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器
通过提供输入文档的路径来初始化注释器。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码放在这里
}
```
## 第 3 步：创建图像注释
创建一个实例`ImageAnnotation`类并指定其属性，例如位置、不透明度、页码和图像路径。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## 第四步：添加注释
使用以下命令将创建的图像注释添加到文档中`Add`注释器的方法。
```csharp
annotator.Add(image);
```
## 第5步：保存文档
将注释文档保存到输出路径。
```csharp
annotator.Save(outputPath);
```
## 第6步：显示输出路径
显示一条消息，指示文档已成功保存以及输出文件的位置。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 将图像注释添加到文档中。通过执行这些简单的步骤，您可以通过强大的注释功能增强文档处理能力。
## 常见问题解答
### 我可以为 PDF 以外的文档添加注释吗？
是的，GroupDocs.Annotation 支持各种文档格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 与 .NET Core 兼容吗？
是的，GroupDocs.Annotation 与 .NET Framework 和 .NET Core 兼容。
### 我可以自定义注释的外观吗？
当然，您可以根据您的需求自定义注释的外观、大小、颜色和其他属性。
### GroupDocs.Annotation 是否提供协作注释支持？
是的，GroupDocs.Annotation 提供协作注释功能，使多个用户能够同时注释文档。
### 我在哪里可以找到额外的帮助或支持？
您可以访问 GroupDocs.Annotation 论坛以获得社区的帮助和支持。