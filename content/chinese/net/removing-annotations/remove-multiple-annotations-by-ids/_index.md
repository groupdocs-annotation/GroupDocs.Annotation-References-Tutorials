---
title: 按 ID 删除多个注释
linktitle: 按 ID 删除多个注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中按 ID 删除多个注释，从而轻松增强您的文档管理功能。
weight: 13
url: /zh/net/removing-annotations/remove-multiple-annotations-by-ids/
---
## 介绍
在文档管理和协作领域，GroupDocs.Annotation for .NET 成为一种强大的工具，使开发人员能够在其 .NET 应用程序中无缝地注释和操作文档。本教程将深入研究 GroupDocs.Annotation for .NET 提供的基本功能之一：通过 ID 删除多个注释。通过遵循本分步指南，您将全面了解如何有效删除注释，从而增强您的文档管理能力。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
### 1.安装GroupDocs.Annotation for .NET
首先，您需要在开发环境中安装 GroupDocs.Annotation for .NET。您可以从以下地址下载所需的软件包[下载链接](https://releases.groupdocs.com/annotation/net/)由 GroupDocs 提供。
### 2. .NET Framework 的基本了解
要理解代码示例并有效地实现所提供的解决方案，必须对 .NET Framework 有基本的了解。

## 导入命名空间
首先，将必要的命名空间导入到您的 .NET 应用程序中。这些命名空间提供对注释操作所需的功能的访问。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## 第 1 步：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步骤中，我们定义删除注释的修改文档的保存路径。
## 第 2 步：实例化注释器对象
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
在这里，我们创建一个实例`Annotator`类，将带注释的 PDF 文档的路径作为参数传递。
## 步骤 3：按 ID 删除注释
```csharp
annotator.Remove(new List<int>{0,1});
```
在这个关键步骤中，我们指定要删除的注释的 ID。可以在列表中传递多个 ID 以同时删除。
## 第四步：保存修改后的文档
```csharp
annotator.Save(outputPath);
```
删除指定的注释后，我们将修改后的文档保存在之前定义的输出路径中。
## 第5步：显示成功消息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
最后，我们通知用户该过程已成功完成，并提供修改后的文档的保存路径。

## 结论
总之，本教程阐明了使用 GroupDocs.Annotation for .NET 按 ID 删除多个注释的过程。通过遵循概述的步骤，开发人员可以将此功能无缝集成到他们的 .NET 应用程序中，从而提高文档管理效率和协作。
## 常见问题解答
### 不同类型的注解可以同时删除吗？
是的，通过在删除列表中指定各自的 ID，可以同时删除不同类型的注释。
### GroupDocs.Annotation for .NET 是否与所有版本的 .NET Framework 兼容？
是的，GroupDocs.Annotation for .NET 与各种版本的 .NET Framework 兼容，确保了多功能性和易于集成。
### 我可以在购买前试用 GroupDocs.Annotation for .NET 吗？
绝对地！您可以从以下位置免费试用 GroupDocs.Annotation for .NET[发布页面](https://releases.groupdocs.com/)探索其特性和功能。
### 我需要临时许可证才能进行测试吗？
虽然临时许可证可以增强您的测试体验，但出于试用目的，它并不是强制性的。但是，对于生产用途，需要有效的许可证。
### 实施过程中遇到问题可以到哪里寻求帮助？
您可以通过以下方式寻求帮助并与充满活力的 GroupDocs 社区互动：[支持论坛](https://forum.groupdocs.com/c/annotation/10)，专家和爱好者随时可以解答您的疑问和疑虑。