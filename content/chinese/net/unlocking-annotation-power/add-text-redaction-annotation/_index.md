---
"description": "了解如何使用 GroupDocs.Annotation for .NET 向 PDF 文档添加文本编辑注释。轻松保护敏感信息。"
"linktitle": "为文档添加文本编辑注释"
"second_title": "GroupDocs.Annotation .NET API"
"title": "为文档添加文本编辑注释"
"url": "/zh/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# 为文档添加文本编辑注释

## 介绍
在文档中添加文本编辑注释是安全管理敏感信息的关键步骤。GroupDocs.Annotation for .NET 提供了一个强大的解决方案，可以无缝实现这一点。在本教程中，我们将逐步指导您完成向文档添加文本编辑注释的过程。
## 先决条件
在开始之前，请确保您已满足以下先决条件：
1. GroupDocs.Annotation for .NET：确保您已安装 GroupDocs.Annotation for .NET 库。您可以从 [网站](https://releases。groupdocs.com/annotation/net/).
2. 开发环境：使用与 .NET 兼容的 IDE（例如 Visual Studio）设置开发环境。

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
## 步骤 1：定义输出路径
定义要保存带注释文档的输出路径。确保该路径可访问且可写入。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤 2：初始化注释器
使用输入文档路径初始化注释器。替换 `"input.pdf"` 以及您的文档的路径。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注释代码将放在这里
}
```
## 步骤 3：创建文本编辑注释
创建一个 `TextRedactionAnnotation` 具有所需属性的对象，例如 `PageNumber`， `FontColor`， 和 `Points`根据您的要求定制注释。
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
## 步骤 4：添加注释并保存
使用注释器将创建的注释添加到文档中，并将注释后的文档保存到指定的输出路径。
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## 步骤5：检查输出
最后确认文档已成功保存到指定的输出路径。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 结论
在本教程中，我们演示了如何使用 GroupDocs.Annotation for .NET 向文档添加文本修订注释的过程。完成这些步骤后，您现在可以安全地管理文档中的敏感信息。
## 常见问题解答
### 我可以自定义文本编辑注释的外观吗？
是的，您可以自定义各种属性，例如字体颜色、填充颜色和不透明度，以满足您的要求。
### 购买前是否有试用版？
是的，您可以从 [网站](https://releases。groupdocs.com/).
### 如果我遇到任何问题，如何获得支持？
您可以从 GroupDocs.Annotation 社区论坛获得支持 [这里](https://forum。groupdocs.com/c/annotation/10).
### 我是否需要临时许可证来进行测试？
是的，你可以从 [购买页面](https://purchase.groupdocs.com/temporary-license/) 用于测试。
### 我可以在单个文档中添加多个注释吗？
当然，GroupDocs.Annotation 允许您向单个文档添加各种类型的注释和多个实例。