---
title: 向文档添加文本密文注释
linktitle: 向文档添加文本密文注释
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 将文本密文注释添加到 PDF 文档。轻松保护敏感信息。
type: docs
weight: 23
url: /zh/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## 介绍
向文档添加文本编辑注释可能是安全管理敏感信息的关键步骤。 GroupDocs.Annotation for .NET 提供了一个强大的解决方案来无缝实现这一目标。在本教程中，我们将指导您逐步完成向文档添加文本密文注释的过程。
## 先决条件
在我们开始之前，请确保您具备以下先决条件：
1.  GroupDocs.Annotation for .NET：确保您已安装 GroupDocs.Annotation for .NET 库。您可以从[网站](https://releases.groupdocs.com/annotation/net/).
2. 开发环境：使用 .NET 兼容 IDE（例如 Visual Studio）设置开发环境。

## 导入命名空间
首先，让我们将必要的命名空间导入到我们的项目中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 第 1 步：定义输出路径
定义要保存注释文档的输出路径。确保它可访问且可写。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化注释器
使用输入文档路径初始化注释器。代替`"input.pdf"`以及您的文档的路径。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注释代码将放在这里
}
```
## 第 3 步：创建文本密文注释
创建一个`TextRedactionAnnotation`具有所需属性的对象，例如`PageNumber`, `FontColor`， 和`Points`。根据您的要求自定义注释。
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
    }
};
```
## 第四步：添加注释并保存
使用注释器将创建的注释添加到文档中，并将注释后的文档保存到指定的输出路径。
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## 第 5 步：检查输出
最后确认文档已成功保存到指定的输出路径。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们演示了使用 GroupDocs.Annotation for .NET 将文本编辑注释添加到文档的过程。通过这些步骤，您现在可以安全地管理文档中的敏感信息。
## 常见问题解答
### 我可以自定义文本密文注释的外观吗？
是的，您可以自定义各种属性，例如字体颜色、填充颜色和不透明度，以满足您的要求。
### 购买前是否有试用版？
是的，您可以从以下位置访问免费试用版：[网站](https://releases.groupdocs.com/).
### 如果遇到任何问题，我如何获得支持？
您可以从 GroupDocs.Annotation 社区论坛获得支持[这里](https://forum.groupdocs.com/c/annotation/10).
### 我需要临时许可证才能进行测试吗？
是的，您可以从以下机构获得临时许可证[购买页面](https://purchase.groupdocs.com/temporary-license/)供测试用。
### 我可以在一个文档中添加多个注释吗？
当然，GroupDocs.Annotation 允许您向单个文档添加各种类型的注释和多个实例。