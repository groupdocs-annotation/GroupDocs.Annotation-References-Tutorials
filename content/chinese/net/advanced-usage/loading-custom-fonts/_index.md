---
title: 加载自定义字体
linktitle: 加载自定义字体
second_title: GroupDocs.Annotation .NET API
description: 了解如何在 GroupDocs.Annotation for .NET 中无缝加载自定义字体以增强文档注释。请按照我们的步骤轻松集成。
weight: 20
url: /zh/net/advanced-usage/loading-custom-fonts/
---
## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的库，使开发人员能够轻松地将注释功能添加到其 .NET 应用程序中。它提供的关键功能之一是能够加载自定义字体，从而增强文档注释的自定义和灵活性。
## 先决条件
在继续学习本教程之前，请确保您满足以下先决条件：
1.  GroupDocs.Annotation for .NET Library：从以下位置下载并安装该库[这里](https://releases.groupdocs.com/annotation/net/).
2. .NET 开发环境：确保您已设置用于 .NET 开发的工作环境。
3. 访问自定义字体：准备要加载到应用程序中的自定义字体。

## 导入命名空间
在您的 .NET 项目中，导入使用 GroupDocs.Annotation 所需的命名空间：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 第 1 步：实例化注释器对象
创建一个实例`Annotator`类，通过提供输入 PDF 文档的路径以及自定义字体目录：
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    //您的进一步操作代码将位于此处
}
```
## 第 2 步：配置预览选项
定义预览选项以指定如何生成文档预览。您可以设置预览格式、页码等选项：
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## 第 3 步：生成文档预览
利用`GeneratePreview`的方法`Document`属性来生成带有自定义字体的预览：
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## 第四步：显示输出路径
最后，显示一条消息，指示已成功生成文档预览以及输出目录路径：
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## 结论
总之，在 GroupDocs.Annotation for .NET 中加载自定义字体使开发人员可以根据自己的要求灵活地自定义文档注释。通过遵循本教程中概述的步骤，您可以将自定义字体无缝集成到 .NET 应用程序中，并增强用户的注释体验。
## 常见问题解答
### 我可以同时加载多种自定义字体吗？
是的，实例化时可以指定多个字体目录`Annotator`目的。
### 支持的字体类型有限制吗？
GroupDocs.Annotation for .NET 支持多种字体类型，包括 TrueType (.ttf) 和 OpenType (.otf) 字体。
### 我可以在运行时动态更改加载的字体吗？
是的，您可以根据需要动态修改字体目录并重新加载文档注释。
### GroupDocs.Annotation 是否支持在输出文档中嵌入字体？
是的，您可以在输出文档中嵌入自定义字体，以确保跨不同平台的一致渲染。
### 有没有办法在应用程序中处理字体许可？
GroupDocs.Annotation 提供了管理字体许可的选项，包括用于评估目的的临时许可。