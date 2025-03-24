---
title: 将图像注释添加到文档（远程路径）
linktitle: 将图像注释添加到文档（远程路径）
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将图像注释添加到文档中。通过强大的注释功能增强文档管理。
weight: 15
url: /zh/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## 介绍
在本教程中，我们将逐步介绍使用 GroupDocs.Annotation for .NET 将图像注释添加到文档的过程。该库提供了强大的工具，用于以编程方式注释各种类型的文档。
## 先决条件
在我们开始之前，请确保您具备以下条件：
1.  GroupDocs.Annotation for .NET：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/annotation/net/).
2. 开发环境：确保您有一个用于 .NET 开发的工作开发环境。
3. 文档：准备要注释的文档。对于本教程，我们假设您有一个名为的 PDF 文档`input.pdf`.
4. 用于注释的图像：选择要用于注释的图像。确保您已准备好图像 URL 或本地路径。

## 导入命名空间
在开始编码之前，让我们导入必要的名称空间：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 第1步：设置输出路径
首先，定义保存注释文档的输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器
创建一个实例`Annotator`类并指定输入文档。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码将放在这里
}
```
## 第3步：添加图像注释
现在，让我们将图像注释添加到文档中。我们将指定图像注释的属性，例如位置、不透明度、页码和图像路径。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), //指定注释的位置
    CreatedOn = DateTime.Now, //设置创建日期
    Opacity = 0.7, //设置不透明度（0 到 1）
    PageNumber = 0, //指定页码
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 提供图片的网址
};
annotator.Add(image); //添加图像注释
```
## 第 4 步：保存文档
将注释文档保存到指定的输出路径。
```csharp
annotator.Save(outputPath);
```
## 第5步：显示输出路径
通知用户文档保存操作成功并显示输出路径。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 将图像注释添加到文档中。通过执行以下步骤，您可以通过强大的注释功能增强文档管理应用程序。
## 常见问题解答
### GroupDocs.Annotation 可以与除 PDF 之外的其他文档格式一起使用吗？
是的，GroupDocs.Annotation 支持各种文档格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 与 .NET Core 兼容吗？
是的，GroupDocs.Annotation 与 .NET Framework 和 .NET Core 兼容。
### 我可以自定义注释的外观吗？
是的，您可以自定义注释的外观，例如颜色、不透明度和大小。
### GroupDocs.Annotation 是否支持协作注释功能？
是的，GroupDocs.Annotation 提供了用于文档实时协作的协作注释功能。
### 有试用版可供测试吗？
是的，您可以从以下位置获得 GroupDocs.Annotation 的免费试用版：[这里](https://releases.groupdocs.com/).