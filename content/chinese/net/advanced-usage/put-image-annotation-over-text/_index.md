---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中在文本上添加图像注释，以实现高效的文档管理和协作。"
"linktitle": "将图像注释置于文本之上"
"second_title": "GroupDocs.Annotation .NET API"
"title": "将图像注释置于文本之上"
"url": "/zh/net/advanced-usage/put-image-annotation-over-text/"
"weight": 21
---

# 将图像注释置于文本之上

## 介绍
在 .NET 开发领域，GroupDocs.Annotation 提供了一个强大的解决方案，用于向文档添加注释，从而提高协作和文档管理的效率。一个常见的需求是将图像注释添加到文本上，这可以通过 GroupDocs.Annotation for .NET 无缝实现。
## 先决条件
在深入使用 GroupDocs.Annotation for .NET 将图像注释放在文本上之前，请确保您已具备以下条件：
1. GroupDocs.Annotation for .NET 库：从以下位置下载并安装该库 [这里](https://releases。groupdocs.com/annotation/net/).
2. 开发环境：设置合适的开发环境，例如 Visual Studio 或任何其他 .NET IDE。
3. 文档和图像文件：准备要用于注释的文档文件（PDF、DOCX 等）和图像文件。
4. 对 C# 的基本了解：熟悉 C# 编程语言对于实现本教程中提供的代码片段是必要的。

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
## 步骤 1：定义输出路径
首先，定义注释文档的保存输出路径：
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 步骤 2：初始化注释器
初始化 `Annotator` 通过提供输入文档路径来对象：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注释代码将放在这里
}
```
## 步骤3：创建图像注释
创建一个 `ImageAnnotation` 具有所需属性的对象，例如框尺寸、不透明度、页码、图像路径和 z 索引：
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
## 步骤 4：添加注释
使用 `Add` 方法 `Annotator` 目的：
```csharp
annotator.Add(image);
```
## 步骤 5：保存带注释的文档
将注释后的文档保存到指定的输出路径：
```csharp
annotator.Save(outputPath);
```
## 步骤6：显示成功消息
显示带有注释文档路径的成功消息：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
总而言之，使用 GroupDocs.Annotation 在 .NET 应用程序中为文本添加图像注释是一个简单的过程。按照本教程提供的分步指南，您可以高效地注释文档，并增强 .NET 项目中的协作和文档管理功能。
## 常见问题解答
### 我可以注释 PDF 以外的文档吗？
是的，GroupDocs.Annotation 支持各种文档格式，例如 DOCX、XLSX、PPTX 等。
### GroupDocs.Annotation 有免费试用版吗？
是的，您可以从下载免费试用版 [这里](https://releases。groupdocs.com/).
### 如何获得 GroupDocs.Annotation 的支持？
您可以从 GroupDocs.Annotation 社区论坛获得支持 [这里](https://forum。groupdocs.com/c/annotation/10).
### 我是否需要临时许可证来进行测试？
是的，你可以从 [这里](https://purchase.groupdocs.com/temporary-license/) 用于测试目的。
### 我可以自定义注释的外观吗？
是的，GroupDocs.Annotation 提供了各种选项来自定义注释的外观，例如颜色、不透明度、字体大小等。