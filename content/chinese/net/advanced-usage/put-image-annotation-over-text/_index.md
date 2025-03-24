---
title: 将图像注释放在文本上
linktitle: 将图像注释放在文本上
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中的文本上添加图像注释，以实现高效的文档管理和协作。
weight: 21
url: /zh/net/advanced-usage/put-image-annotation-over-text/
---
## 介绍
在 .NET 开发领域，GroupDocs.Annotation 提供了一个强大的解决方案，用于向文档添加注释，从而使协作和文档管理更加高效。一项常见的要求是将图像注释放在文本上，这可以使用 GroupDocs.Annotation for .NET 无缝完成。
## 先决条件
在深入研究使用 GroupDocs.Annotation for .NET 在文本上添加图像注释的过程之前，请确保您具备以下条件：
1.  GroupDocs.Annotation for .NET Library：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/annotation/net/).
2. 开发环境：设置合适的开发环境，例如 Visual Studio 或任何其他 .NET IDE。
3. 文档和图像文件：准备文档文件（PDF、DOCX 等）和要用于注释的图像文件。
4. 对 C# 的基本了解：要实现本教程中提供的代码片段，需要熟悉 C# 编程语言。

## 导入命名空间
在继续注释过程之前，请确保在 C# 项目中导入必要的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 第 1 步：定义输出路径
首先，定义保存注释文档的输出路径：
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 第 2 步：初始化注释器
初始化`Annotator`通过提供输入文档路径来对象：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码将放在这里
}
```
## 第 3 步：创建图像注释
创建一个`ImageAnnotation`具有所需属性的对象，例如框尺寸、不透明度、页码、图像路径和 z 索引：
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## 第四步：添加注释
使用以下命令将图像注释添加到文档中`Add`的方法`Annotator`目的：
```csharp
annotator.Add(image);
```
## 第 5 步：保存带注释的文档
将注释文档保存到指定的输出路径：
```csharp
annotator.Save(outputPath);
```
## 第6步：显示成功消息
显示一条成功消息以及带注释的文档的路径：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
总之，使用 GroupDocs.Annotation 在 .NET 应用程序中的文本上添加图像注释是一个简单的过程。通过遵循本教程中提供的分步指南，您可以有效地注释文档并增强 .NET 项目中的协作和文档管理功能。
## 常见问题解答
### 我可以为 PDF 以外的文档添加注释吗？
是的，GroupDocs.Annotation 支持各种文档格式，例如 DOCX、XLSX、PPTX 等。
### GroupDocs.Annotation 是否有免费试用版？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 如何获得对 GroupDocs.Annotation 的支持？
您可以从 GroupDocs.Annotation 社区论坛获得支持[这里](https://forum.groupdocs.com/c/annotation/10).
### 我需要临时许可证才能进行测试吗？
是的，您可以从以下地址获得临时许可证[这里](https://purchase.groupdocs.com/temporary-license/)用于测试目的。
### 我可以自定义注释的外观吗？
是的，GroupDocs.Annotation 提供了各种选项来自定义注释的外观，例如颜色、不透明度、字体大小等。