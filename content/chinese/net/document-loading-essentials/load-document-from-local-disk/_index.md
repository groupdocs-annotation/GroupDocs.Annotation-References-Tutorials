---
title: 从本地磁盘加载文档
linktitle: 从本地磁盘加载文档
second_title: GroupDocs.Annotation .NET API
description: 使用 GroupDocs.Annotation for .NET 释放文档注释的强大功能。将注释功能无缝集成到您的 .NET 应用程序中。
type: docs
weight: 13
url: /zh/net/document-loading-essentials/load-document-from-local-disk/
---
## 介绍
使用 GroupDocs.Annotation for .NET 释放文档注释的潜力从未如此简单。这个强大的工具使开发人员能够将强大的注释功能无缝集成到他们的 .NET 应用程序中。在这份综合指南中，我们将引导您逐步完成利用 GroupDocs.Annotation for .NET 来注释文档的过程。无论您是经验丰富的开发人员还是新手，本教程都将为您提供增强文档协作和简化工作流程的知识。
## 先决条件
在深入研究使用 GroupDocs.Annotation for .NET 进行文档注释之前，请确保您具备以下先决条件：
1. C# 基础知识：熟悉 C# 编程语言基础知识至关重要。
2. 安装 GroupDocs.Annotation for .NET：从以下位置下载并安装 GroupDocs.Annotation for .NET[这里](https://releases.groupdocs.com/annotation/net/).
3. 开发环境：使用 Visual Studio 或任何兼容的 IDE 设置开发环境。

## 导入命名空间
要开始使用 GroupDocs.Annotation for .NET 注释文档，请将必要的命名空间导入到您的项目中：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 步骤1：从本地磁盘加载文档
首先，您需要从本地磁盘加载文档。使用以下代码片段：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 第2步：定义注释区域
接下来，定义注释区域。在此示例中，我们将创建一个 AreaAnnotation：
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## 步骤 3：保存带注释的文档
对文档进行注释后，将其与注释一起保存：
```csharp
    annotator.Save(outputPath);
}
```
## 第4步：显示成功消息
最后，显示一条成功消息以及输出路径：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
总之，GroupDocs.Annotation for .NET 提供了一个强大的解决方案，用于将文档注释功能集成到 .NET 应用程序中。通过遵循此分步指南，您可以轻松地为文档添加注释并增强项目中的协作。
## 常见问题解答
### 我可以在购买前试用 GroupDocs.Annotation for .NET 吗？
是的，您可以从以下位置下载免费试用版[这里](https://releases.groupdocs.com/).
### 在哪里可以找到 GroupDocs.Annotation for .NET 的文档？
您可以访问文档[这里](https://reference.groupdocs.com/annotation/net/).
### 如何获取 GroupDocs.Annotation for .NET 的临时许可证？
您可以从以下地址获取临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
### 是否支持 GroupDocs.Annotation for .NET？
是的，您可以在 GroupDocs 论坛上找到支持[这里](https://forum.groupdocs.com/c/annotation/10).
### 在哪里可以购买 GroupDocs.Annotation for .NET？
您可以购买 GroupDocs.Annotation for .NET[这里](https://purchase.groupdocs.com/buy).