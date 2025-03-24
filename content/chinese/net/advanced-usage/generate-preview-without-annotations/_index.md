---
title: 生成不带注释的预览
linktitle: 生成不带注释的预览
second_title: GroupDocs.Annotation .NET API
description: 使用 GroupDocs.Annotation for .NET 增强 .NET 应用程序内的文档协作和注释。使用这个功能强大的库轻松注释、标记和审阅文档。
weight: 13
url: /zh/net/advanced-usage/generate-preview-without-annotations/
---

# 生成不带注释的预览

## 介绍
在当今的数字时代，文档的高效协作是生产力和成功的关键。无论您是与分散在全球各地的团队成员一起开展项目，还是与客户就重要合同进行协作，无缝注释和审查文档的能力都至关重要。借助 GroupDocs.Annotation for .NET，您可以将文档协作提升到新的水平，从而可以直接在 .NET 应用程序中轻松进行注释、标记和审阅。
## 先决条件
在使用 GroupDocs.Annotation for .NET 深入了解文档注释世界之前，您需要满足一些先决条件：
### 1.安装.NET的GroupDocs.Annotation
首先，您需要下载并安装 GroupDocs.Annotation for .NET。你可以找到下载链接[这里](https://releases.groupdocs.com/annotation/net/)。按照提供的安装说明在 .NET 环境中设置库。
### 2. 获取许可证（可选）
虽然 GroupDocs.Annotation for .NET 提供免费试用版，但您可能需要考虑获取许可证以完全访问其功能。您可以购买许可证[这里](https://purchase.groupdocs.com/buy)或申请临时许可证[这里](https://purchase.groupdocs.com/temporary-license/)用于测试目的。
### 3.熟悉C#和.NET开发
要充分利用适用于 .NET 的 GroupDocs.Annotation，对 C# 和 .NET 开发有基本的了解会很有帮助。这将使您能够将该库无缝集成到您现有的应用程序和工作流程中。
### 4.安装PDF查看器
由于 GroupDocs.Annotation for .NET 可以处理 PDF 文档，因此您需要在系统上安装 PDF 查看器来预览带注释的文档。 Adobe Acrobat Reader 或任何其他 PDF 查看器就足够了。

## 导入命名空间
在开始注释文档之前，您需要将必要的命名空间导入到 .NET 项目中。这允许您访问 GroupDocs.Annotation for .NET 提供的类和方法。

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

现在您已完成所有设置，让我们生成不带任何注释的文档预览。请按照以下步骤来完成此操作：
## 第 1 步：初始化注释器
首先，创建一个实例`Annotator`类，传递要注释的文档的路径。
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## 第 2 步：配置预览选项
接下来，根据您的要求配置预览选项。您可以指定要在预览中包含的页码、预览格式（例如 PNG）以及是否呈现注释。
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## 第 3 步：生成预览
最后，使用以下命令生成预览`GeneratePreview`的方法`Document`类，传递配置的预览选项。
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
通过执行这些简单的步骤，您可以使用 GroupDocs.Annotation for .NET 生成不带注释的文档预览。

## 结论
总之，GroupDocs.Annotation for .NET 为 .NET 应用程序中的文档协作和注释提供了强大的解决方案。通过遵循本教程中概述的步骤，您可以将文档注释功能无缝集成到您的项目中，从而增强协作和生产力。
## 常见问题解答
### 问：我可以将 GroupDocs.Annotation for .NET 与除 PDF 之外的其他文档格式一起使用吗？
是的，GroupDocs.Annotation for .NET 支持多种文档格式，包括 DOCX、XLSX、PPTX 等。
### 问：GroupDocs.Annotation for .NET 是否与 .NET Core 兼容？
是的，GroupDocs.Annotation for .NET 与 .NET Framework 和 .NET Core 环境兼容。
### 问：GroupDocs.Annotation for .NET 是否提供可自定义的注释工具？
是的，GroupDocs.Annotation for .NET 提供了一系列注释工具，可以根据您的特定要求进行自定义。
### 问：我可以将 GroupDocs.Annotation for .NET 集成到我的 Web 应用程序中吗？
是的，GroupDocs.Annotation for .NET 可以集成到桌面和 Web 应用程序中，提供无缝文档协作功能。
### 问：是否有社区论坛可以让我获得有关 GroupDocs.Annotation for .NET 的支持和帮助？
是的，您可以在 GroupDocs.Annotation 论坛上找到支持和帮助[这里](https://forum.groupdocs.com/c/annotation/10).