---
title: 将折线注释添加到文档
linktitle: 将折线注释添加到文档
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将折线注释添加到文档中。轻松增强协作和文档审核流程。
type: docs
weight: 18
url: /zh/net/unlocking-annotation-power/add-polyline-annotation/
---
## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的工具，允许开发人员以编程方式对 PDF 和 Microsoft Office 文档进行注释。其功能之一是能够向文档添加折线注释，从而增强协作和文档审阅流程。
## 先决条件
在继续本教程之前，请确保您具备以下条件：
- Visual Studio 安装在您的系统上。
- C# 编程语言的基础知识。
- 安装了 .NET 库的 GroupDocs.Annotation。您可以从以下位置下载：[这里](https://releases.groupdocs.com/annotation/net/).

## 导入命名空间
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 第 1 步：定义输出路径
首先，定义保存注释文档的输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器
通过提供输入文档名称来初始化注释器。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 第 3 步：创建折线注释对象
创建折线注释对象并设置其属性，例如位置、消息、不透明度、画笔颜色、画笔样式和画笔宽度。
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## 第 4 步：添加折线注释
使用注释器对象将折线注释添加到文档中。
```csharp
annotator.Add(polyline);
```
## 第5步：保存文档
将注释文档保存到指定的输出路径。
```csharp
annotator.Save(outputPath);
```
## 第6步：显示成功消息
显示一条消息，确认文档保存成功。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 将折线注释添加到文档中。此功能增强了协作和文档审阅流程，使用户更容易有效地传达反馈和建议。
## 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持流行的文档格式，例如 PDF 和 Microsoft Office 格式（包括 Word、Excel 和 PowerPoint）。
### 我可以自定义注释的外观吗？
是的，您可以自定义注释的各种属性，例如颜色、不透明度、样式和宽度，以满足您的要求。
### GroupDocs.Annotation for .NET 是否提供免费试用？
是的，您可以访问 GroupDocs.Annotation for .NET 免费试用版[这个链接](https://releases.groupdocs.com/).
### 在哪里可以找到 GroupDocs.Annotation for .NET 的文档？
您可以找到 GroupDocs.Annotation for .NET 的文档[这里](https://reference.groupdocs.com/annotation/net/).
### 对于与 GroupDocs.Annotation for .NET 相关的任何问题或查询，如何获得支持？
您可以通过访问 GroupDocs.Annotation 论坛获得支持[这里](https://forum.groupdocs.com/c/annotation/10).