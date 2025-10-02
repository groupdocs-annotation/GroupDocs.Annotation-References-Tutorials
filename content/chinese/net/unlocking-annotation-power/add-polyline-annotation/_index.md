---
"description": "了解如何使用 GroupDocs.Annotation for .NET 向文档添加折线注释。轻松增强协作和文档审阅流程。"
"linktitle": "向文档添加折线注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "向文档添加折线注释"
"url": "/zh/net/unlocking-annotation-power/add-polyline-annotation/"
type: docs
"weight": 18
---

# 向文档添加折线注释

## 介绍
GroupDocs.Annotation for .NET 是一款功能强大的工具，允许开发人员以编程方式注释 PDF 和 Microsoft Office 文档。其功能之一是能够向文档添加折线注释，从而增强协作和文档审阅流程。
## 先决条件
在继续本教程之前，请确保您已具备以下条件：
- 您的系统上安装了 Visual Studio。
- C# 编程语言的基本知识。
- 已安装 GroupDocs.Annotation for .NET 库。您可以从 [这里](https://releases。groupdocs.com/annotation/net/).

## 导入命名空间
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 步骤 1：定义输出路径
首先，定义注释文档的保存输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤 2：初始化注释器
通过提供输入文档名称来初始化注释器。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 步骤3：创建折线注释对象
创建折线注释对象并设置其属性，例如位置、消息、不透明度、笔颜色、笔样式和笔宽度。
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
## 步骤 4：添加折线注释
使用注释器对象将折线注释添加到文档。
```csharp
annotator.Add(polyline);
```
## 步骤5：保存文档
将注释文档保存到指定的输出路径。
```csharp
annotator.Save(outputPath);
```
## 步骤6：显示成功消息
显示一条确认文档成功保存的消息。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们学习了如何使用 GroupDocs.Annotation for .NET 向文档添加折线注释。此功能增强了协作和文档审阅流程，使用户能够更轻松地有效地传达反馈和建议。
## 常见问题解答
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持流行的文档格式，例如 PDF 和 Microsoft Office 格式，包括 Word、Excel 和 PowerPoint。
### 我可以自定义注释的外观吗？
是的，您可以自定义注释的各种属性，例如颜色、不透明度、样式和宽度，以满足您的要求。
### GroupDocs.Annotation for .NET 是否提供免费试用？
是的，您可以通过访问以下网址免费试用 GroupDocs.Annotation for .NET [此链接](https://releases。groupdocs.com/).
### 在哪里可以找到 .NET 的 GroupDocs.Annotation 文档？
您可以找到 GroupDocs.Annotation for .NET 的文档 [这里](https://tutorials。groupdocs.com/annotation/net/).
### 如何获得与 GroupDocs.Annotation for .NET 相关的任何问题或疑问的支持？
您可以通过访问 GroupDocs.Annotation 论坛获得支持 [这里](https://forum。groupdocs.com/c/annotation/10).