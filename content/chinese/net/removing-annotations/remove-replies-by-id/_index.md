---
title: 在 .NET 中按 ID 删除回复
linktitle: 在 .NET 中按 ID 删除回复
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中按 ID 删除回复。按照我们的分步教程进行高效的文档注释管理。
weight: 16
url: /zh/net/removing-annotations/remove-replies-by-id/
---
## 介绍
在 .NET 开发领域，管理文档中的注释的能力对于各种应用程序至关重要。无论您使用的是 PDF、Word 文档还是其他格式，以编程方式操作注释的能力都将开启一个充满可能性的世界。 GroupDocs.Annotation 是处理 .NET 中注释的强大工具之一。
## 先决条件
在深入了解有关使用 GroupDocs.Annotation 在 .NET 中按 ID 删除回复的教程之前，请确保您具备以下先决条件：
### 1.GroupDocs.Annotation安装
首先，您需要安装 GroupDocs.Annotation for .NET。您可以从以下位置下载该库[这里](https://releases.groupdocs.com/annotation/net/)并按照文档中提供的安装说明进行操作[这里](https://tutorials.groupdocs.com/annotation/net/).
### 2. 对 C# 和 .NET 的基本了解
要理解本教程中的示例，需要熟悉 C# 编程语言和 .NET 框架。
### 3. 带回复的注释文档
准备一份包含注释和回复的文档。该文档将作为删除过程的输入。

## 导入命名空间
在您的 .NET 项目中，导入必要的命名空间以访问 GroupDocs.Annotation 功能。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## 第 1 步：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
指定删除回复后要保存修改文档的路径。
## 第 2 步：加载文档和注释
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    List<AnnotationBase> annotations = annotator.Get();
```
使用以下命令加载包含注释和回复的文档`Annotator`类并检索注释集合。
## 步骤 3：按 ID 删除回复
```csharp
annotations[0].Replies.RemoveAll(x => x.Id == 4);
```
根据回复 ID 识别要删除的回复，并将其从相应注释的回复集合中删除。
## 第 4 步：保存更改
```csharp
annotator.Update(annotations);
annotator.Save(outputPath);
```
使用删除的回复更新注释，并将修改后的文档保存到指定的输出路径。
## 第5步：确认成功
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
显示一条确认消息，表明文档已成功保存并删除了回复。

## 结论
总之，GroupDocs.Annotation for .NET 为管理文档中的注释提供了一个简单的解决方案。通过遵循本教程中概述的步骤，您可以轻松地按 ID 删除回复，从而使您能够轻松高效地根据您的特定要求定制文档注释。
## 常见问题解答
### GroupDocs.Annotation 可以与除 PDF 之外的其他文档格式一起使用吗？
是的，GroupDocs.Annotation 支持各种文档格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否有免费试用版？
是的，您可以免费试用[这里](https://releases.groupdocs.com/).
### 在哪里可以找到对 GroupDocs.Annotation 的支持？
您可以寻求支持并参与社区[这里](https://forum.groupdocs.com/c/annotation/10).
### 如何获得 GroupDocs.Annotation 的临时许可证？
您可以获得临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以购买 GroupDocs.Annotation for .NET？
您可以购买 GroupDocs.Annotation[这里](https://purchase.groupdocs.com/buy).