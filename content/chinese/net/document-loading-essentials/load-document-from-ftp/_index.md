---
"description": "使用 GroupDocs.Annotation 增强您的 .NET 应用程序，实现无缝文档注释。内含分步教程。"
"linktitle": "从 FTP 加载文档"
"second_title": "GroupDocs.Annotation .NET API"
"title": "从 FTP 加载文档"
"url": "/zh/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# 从 FTP 加载文档

## 介绍
GroupDocs.Annotation for .NET 是一个多功能库，旨在轻松实现 .NET 应用程序中的文档注释功能。无论您处理的是 PDF、Microsoft Office 文档、图像还是其他格式，此库都能提供统一的解决方案来添加注释（例如评论、高亮和形状），从而增强协作和文档管理。
## 先决条件
在深入学习本教程之前，请确保您已满足以下先决条件：
1. C# 知识：熟练掌握 C# 编程语言对于理解和实现本教程中提供的代码示例至关重要。
2. GroupDocs.Annotation for .NET：确保从 [下载链接](https://releases.groupdocs.com/annotation/net/)按照安装说明将库成功集成到您的 .NET 项目中。
## 导入命名空间
为了利用 GroupDocs.Annotation 的 .NET 功能，您需要将所需的命名空间导入到您的 C# 项目中。请遵循以下步骤：

在您的 C# 项目中，在代码文件的开头包含必要的命名空间：
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

现在，让我们深入研究从 FTP 加载文档并使用 GroupDocs.Annotation for .NET 向其添加注释的过程。
## 步骤 1：定义输出路径
指定注释文档的保存输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步骤2：从FTP加载文档
使用提供的文件路径从 FTP 服务器检索文档。
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // 注释代码将在此处添加
}
```
## 步骤 3：添加注释
定义并添加所需的注释（例如区域注释）到文档中。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 步骤 4：保存带注释的文档
将注释文档保存到指定的输出路径。
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## 步骤5：从FTP检索文件
实现从 FTP 服务器获取文件的方法。
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## 步骤6：创建FTP请求
生成 FTP 请求来下载文件。
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## 步骤 7：获取文件流
从 FTP 响应中检索文件流。
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## 结论
总而言之，GroupDocs.Annotation for .NET 使开发人员能够将文档注释功能无缝集成到他们的 .NET 应用程序中。按照本教程中概述的分步指南，您可以高效地从 FTP 加载文档并轻松添加注释，从而增强应用程序内的协作和文档管理。
## 常见问题解答
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
是的，GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、Microsoft Office 文档、图像等。
### 我可以自定义使用 GroupDocs.Annotation for .NET 添加的注释的外观吗？
当然，GroupDocs.Annotation for .NET 为注释外观提供了广泛的自定义选项，包括颜色、样式和形状。
### GroupDocs.Annotation for .NET 是否提供对云存储服务的支持？
是的，GroupDocs.Annotation for .NET 与流行的云存储服务无缝集成，允许您从 Dropbox、Google Drive 和 OneDrive 等服务加载和保存文档。
### GroupDocs.Annotation for .NET 有试用版吗？
是的，您可以通过从下载免费试用版来探索 GroupDocs.Annotation for .NET 的功能 [发布页面](https://releases。groupdocs.com/).
### 如何获得 GroupDocs.Annotation for .NET 的技术帮助或支持？
如需技术帮助、故障排除或一般咨询，您可以访问 GroupDocs.Annotation for .NET [支持论坛](https://forum。groupdocs.com/c/annotation/10).