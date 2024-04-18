---
title: 按 ID 删除注释
linktitle: 按 ID 删除注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 按 ID 删除注释。高效简化您的文档工作流程。
type: docs
weight: 11
url: /zh/net/removing-annotations/remove-annotations-by-id/
---
## 介绍
在本教程中，我们将引导您完成使用 GroupDocs.Annotation for .NET 按 ID 删除注释的过程。注释可能会使您的文档变得混乱，有选择地删除它们可以简化您的工作流程。我们将逐步指导您，确保您清楚地了解每个阶段。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
1.  GroupDocs.Annotation for .NET：确保您已安装 GroupDocs.Annotation for .NET 库。您可以从以下位置下载：[这里](https://releases.groupdocs.com/annotation/net/).
2. 访问带注释的文档：使用 GroupDocs.Annotation 注释文档。如果您没有，您可以按照我们之前的教程来注释文档。
3. C# 基础知识：需要熟悉 C# 编程语言才能理解代码示例。

## 导入命名空间
在开始编码之前，让我们导入必要的名称空间：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```

## 第 1 步：定义输出路径
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
我们定义保存已删除注释的文档的输出路径。
## 第 2 步：初始化注释器
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
在这里，我们初始化`Annotator`带有注释的 PDF 文档路径的对象。
## 第 3 步：删除注释
```csharp
annotator.Remove(0);
```
我们通过指定 ID 来删除注释。在这个例子中，我们删除带有ID的注释`0`。您可以更换`0`以及您要删除的注释的 ID。
## 第 4 步：保存文档
```csharp
annotator.Save(outputPath);
```
删除注释后，我们将修改后的文档保存到之前指定的输出路径中。
## 第5步：显示成功消息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
最后，我们显示一条成功消息以及保存修改后的文档的路径。

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 按 ID 删除注释。此功能通过有选择地删除注释来帮助更有效地管理带注释的文档。
## 常见问题解答
### 我可以一次删除多个注释吗？
是的，您可以通过在`Remove`方法。
### 有没有办法撤消注释的删除？
不可以，一旦删除注释，就无法撤消。请确保在删除注释之前备份您的文档。
### 我可以从 PDF 以外的文档中删除注释吗？
是的，GroupDocs.Annotation 支持各种文档格式，包括 DOCX、XLSX、PPTX 等。
### 可删除的注释数量是否有限制？
不，只要正确指定注释 ID，您就可以从文档中删除任意数量的注释。
### 如果我遇到任何问题，可以获得技术支持吗？
是的，您可以从 GroupDocs.Annotation 论坛获得技术支持[这里](https://forum.groupdocs.com/c/annotation/10).