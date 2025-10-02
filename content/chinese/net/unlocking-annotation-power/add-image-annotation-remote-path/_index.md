---
"description": "了解如何使用 GroupDocs.Annotation for .NET 向文档添加图像注释。强大的注释功能可增强文档管理。"
"linktitle": "向文档添加图像注释（远程路径）"
"second_title": "GroupDocs.Annotation .NET API"
"title": "向文档添加图像注释（远程路径）"
"url": "/zh/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# 向文档添加图像注释（远程路径）

## 介绍
在本教程中，我们将演示如何使用 GroupDocs.Annotation for .NET 向文档添加图像注释的过程。该库提供了强大的工具，可用于以编程方式注释各种类型的文档。
## 先决条件
在开始之前，请确保您具备以下条件：
1. GroupDocs.Annotation for .NET：从以下位置下载并安装该库 [这里](https://releases。groupdocs.com/annotation/net/).
2. 开发环境：确保您已为 .NET 开发设置了有效的开发环境。
3. 文档：准备要注释的文档。在本教程中，我们假设您有一个名为 `input。pdf`.
4. 用于注释的图像：选择要用于注释的图像。请确保已准备好图像 URL 或本地路径。

## 导入命名空间
在开始编码之前，让我们导入必要的命名空间：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 步骤1：设置输出路径
首先，定义注释文档的保存输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤 2：初始化注释器
创建一个实例 `Annotator` 类并指定输入文档。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注释代码将放在这里
}
```
## 步骤3：添加图像注释
现在，让我们将图像注释添加到文档中。我们将指定图像注释的属性，例如位置、不透明度、页码和图像路径。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // 指定注释的位置
    CreatedOn = DateTime.Now, // 设置创建日期
    Opacity = 0.7, // 设置不透明度（0 到 1）
    PageNumber = 0, // 指定页码
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 提供图片的 URL
};
annotator.Add(image); // 添加图像注释
```
## 步骤4：保存文档
将注释文档保存到指定的输出路径。
```csharp
annotator.Save(outputPath);
```
## 步骤5：显示输出路径
通知用户文档保存操作成功并显示输出路径。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加图像注释。按照以下步骤操作，您可以使用强大的注释功能增强文档管理应用程序。
## 常见问题解答
### GroupDocs.Annotation 可以与 PDF 以外的其他文档格式一起使用吗？
是的，GroupDocs.Annotation 支持各种文档格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否与 .NET Core 兼容？
是的，GroupDocs.Annotation 与 .NET Framework 和 .NET Core 兼容。
### 我可以自定义注释的外观吗？
是的，您可以自定义注释的外观，例如颜色、不透明度和大小。
### GroupDocs.Annotation 是否支持协作注释功能？
是的，GroupDocs.Annotation 提供协作注释功能，可实现文档的实时协作。
### 是否有可供测试的试用版？
是的，您可以从以下网址免费试用 GroupDocs.Annotation [这里](https://releases。groupdocs.com/).