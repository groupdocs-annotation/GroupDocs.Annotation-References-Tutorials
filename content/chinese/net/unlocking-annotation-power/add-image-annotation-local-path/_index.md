---
"description": "了解如何使用 GroupDocs.Annotation for .NET 向文档添加图像注释。轻松增强文档处理能力。"
"linktitle": "为文档添加图像注释（本地路径）"
"second_title": "GroupDocs.Annotation .NET API"
"title": "为文档添加图像注释（本地路径）"
"url": "/zh/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# 为文档添加图像注释（本地路径）

## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的库，允许开发人员以编程方式向文档添加各种类型的注释。在本教程中，我们将学习如何使用本地路径向文档添加图像注释。
## 先决条件
在开始之前，请确保您满足以下先决条件：
1. C# 编程语言的基本知识。
2. 您的系统上安装了 Visual Studio。
3. 在您的项目中安装 .NET 库或 tutorialsd 的 GroupDocs.Annotation。
4. 输入文档（例如 PDF）和用于注释的图像文件。
## 导入命名空间
首先，您需要将必要的命名空间导入到您的 C# 文件中。这些命名空间提供对使用 GroupDocs.Annotation 所需的类和方法的访问。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 步骤 1：定义输出路径
定义注释文档的保存输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤 2：初始化注释器
通过提供输入文档的路径来初始化注释器。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注释代码放在这里
}
```
## 步骤3：创建图像注释
创建一个实例 `ImageAnnotation` 类并指定其属性，如位置、不透明度、页码和图像路径。
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
## 步骤 4：添加注释
使用 `Add` 注释器的方法。
```csharp
annotator.Add(image);
```
## 步骤5：保存文档
将注释的文档保存到输出路径。
```csharp
annotator.Save(outputPath);
```
## 步骤6：显示输出路径
显示一条消息，表明文档保存成功以及输出文件的位置。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加图像注释。通过遵循这些简单的步骤，您可以使用强大的注释功能增强文档处理能力。
## 常见问题解答
### 我可以注释 PDF 以外的文档吗？
是的，GroupDocs.Annotation 支持各种文档格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否与 .NET Core 兼容？
是的，GroupDocs.Annotation 与 .NET Framework 和 .NET Core 兼容。
### 我可以自定义注释的外观吗？
当然，您可以根据您的要求自定义注释的外观、大小、颜色和其他属性。
### GroupDocs.Annotation 是否提供协作注释支持？
是的，GroupDocs.Annotation 提供协作注释功能，允许多个用户同时注释文档。
### 我可以在哪里找到额外的帮助或支持？
您可以访问 GroupDocs.Annotation 论坛以获得社区的帮助和支持。