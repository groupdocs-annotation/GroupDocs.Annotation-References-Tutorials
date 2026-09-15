---
categories:
- Document Loading
date: '2026-07-06'
description: 了解如何在使用 GroupDocs.Annotation for .NET 从 FTP 服务器下载 PDF 文件时添加注释。包括一步一步的代码示例、故障排除和安全提示。
keywords:
- add annotations to pdf
- download file from ftp
- groupdocs annotation ftp
- ftp document loading .net
lastmod: '2026-07-06'
linktitle: 从 FTP 加载文档
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to add annotations to PDF files while downloading them from
    an FTP server using GroupDocs.Annotation for .NET. Includes step‑by‑step code,
    troubleshooting, and security tips.
  headline: Add Annotations to PDF from FTP in .NET
  type: TechArticle
- description: Learn how to add annotations to PDF files while downloading them from
    an FTP server using GroupDocs.Annotation for .NET. Includes step‑by‑step code,
    troubleshooting, and security tips.
  name: Add Annotations to PDF from FTP in .NET
  steps:
  - name: Define the local output path
    text: First, decide where the annotated PDF will be saved after processing. Using
      `Path.Combine` guarantees correct path separators on Windows and Linux. > **Note:**
      The output folder must exist before you call `Save`. Create it programmatically
      if necessary.
  - name: Retrieve the PDF stream from FTP
    text: The helper method `GetFileFromFtp` opens an `FtpWebRequest`, reads the response
      into a `MemoryStream`, and returns the stream positioned at the beginning. This
      stream is what GroupDocs.Annotation consumes. > **Security tip:** In production,
      always set `request.Credentials = new NetworkCredential(use
  - name: Initialise GroupDocs.Annotation with the stream
    text: The `AnnotationConfig` object tells GroupDocs.Annotation which file type
      you are working with and which stream to read. Passing the stream directly avoids
      temporary files and reduces I/O overhead.
  - name: Add a highlight annotation
    text: Create a `HighlightAnnotation` (or any other annotation type) and configure
      its location, size, and color. The example uses a bright yellow (`BackgroundColor
      = 65535`) that stands out on most PDFs.
  - name: Save the annotated document
    text: Call `annotation.Save(outputPath)` to write the updated PDF to the location
      you defined in Step 1. The console output confirms success and displays the
      full path.
  - name: Wrap everything in a `try/catch`
    text: Network operations are prone to timeouts and permission errors. Enclose
      the whole flow in a `try/catch` block, log the exception, and optionally retry
      the download.
  type: HowTo
- questions:
  - answer: Yes, GroupDocs.Annotation supports over 30 formats, including DOCX, PPTX,
      and common image types, all of which can be loaded from FTP using the same stream‑based
      approach.
    question: Can I annotate file types other than PDF?
  - answer: Instantiate `CommentAnnotation`, set its `Text` property, and add it to
      the `Annotations` collection just like the highlight example.
    question: How do I add a comment annotation instead of a highlight?
  - answer: Absolutely. After saving locally, open a new `FtpWebRequest` with `Method
      = WebRequestMethods.Ftp.UploadFile` and write the file stream back to the remote
      path.
    question: Is it possible to write the annotated file back to the FTP server?
  - answer: GroupDocs.Annotation for .NET works with .NET Framework 4.6.1+, .NET Core
      2.0+, .NET 5, and .NET 6.
    question: What .NET versions are officially supported?
  - answer: Pass the password to the `AnnotationConfig` constructor via the `Password`
      property before loading the stream.
    question: How can I handle password‑protected PDFs?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- FTP
- document-loading
- csharp
- annotation
title: 在 .NET 中从 FTP 为 PDF 添加注释
type: docs
url: /zh/net/document-loading-essentials/load-document-from-ftp/
weight: 12
---

# 从 FTP 在 .NET 中向 PDF 添加批注

从 FTP 服务器 **加载 PDF 并随后向 PDF 文件添加批注** 是企业在本地存储中保留遗留文档时的常见需求。在本教程中，你将看到如何从 FTP 下载文件、将其传入 GroupDocs.Annotation，并应用高亮、评论或形状——全部无需先将文件写入磁盘。完成后，你将拥有一个可复用的模式，适用于任何可通过 FTP 访问的 PDF，并可扩展到 GroupDocs.Annotation 支持的其他格式。

## 快速答案
- **本教程涵盖什么内容？** 从 FTP 加载 PDF 并使用 GroupDocs.Annotation for .NET 添加批注。  
- **目标关键字是什么？** *add annotations to pdf*。  
- **需要许可证吗？** 提供免费试用，但生产环境使用需有效的 GroupDocs.Annotation 许可证。  
- **可以在 .NET Core 上使用吗？** 可以，代码兼容 .NET Framework 4.6.1+ 和 .NET Core 2.0+。  
- **支持身份验证吗？** 示例展示了匿名 FTP；你可以为受保护的访问添加 `NetworkCredential`。

## 什么是“add annotations to pdf”？
*Add annotations to PDF* 指以编程方式在已有的 PDF 文档中插入高亮、评论、印章或形状。GroupDocs.Annotation for .NET 提供了直接操作流的高级 API，因而可以在不先将远程 FTP 上的 PDF 保存到本地的情况下进行修改。

## 为什么从 FTP 加载文档？
从 FTP 加载文档使应用程序能够访问集中存储的文件而无需手动复制，降低了因本地处理带来的延迟，并支持按需拉取文档的自动化工作流，确保始终使用最新版本，同时遵守内部数据处理策略。

- **集中存储：** 超过 70 % 的传统企业仍依赖 FTP 进行批量文档归档。  
- **批量处理：** FTP 允许一次性拉取数百个文件，便于构建自动化批注流水线。  
- **合规性：** 本地 FTP 将数据保留在受控网络区域，满足众多监管要求。

## 前置条件
- **C# 基础** – 熟悉流和异步模式。  
- **GroupDocs.Annotation for .NET** – 从[官方发布页面](https://releases.groupdocs.com/annotation/net/)下载，并参阅通用的[发布页面](https://releases.groupdocs.com/)。  
- **FTP 凭据** – 主机、用户名、密码（如需）以及读取目标文件的权限。  
- **开发工具** – Visual Studio 2019+ 和 .NET Framework 4.6.1 或 .NET Core 2.0+。

## 如何在 .NET 中从 FTP 向 PDF 添加批注？
本指南将演示如何从 FTP 服务器下载 PDF，将流传入 GroupDocs.Annotation，添加高亮批注，并保存已批注的文件——全部无需写入临时文件。`AnnotationConfig` 用于配置 GroupDocs.Annotation 以使用特定的文档流和格式。`FtpWebRequest` 是 .NET 用于处理 FTP 操作（如下载文件）的类。`HighlightAnnotation` 表示放置在 PDF 页面上的可视高亮。

### 步骤 1：定义本地输出路径
首先，确定处理完后注释 PDF 的保存位置。使用 `Path.Combine` 可确保在 Windows 和 Linux 上使用正确的路径分隔符。

> **注意：** 在调用 `Save` 之前必须确保输出文件夹已存在。如有必要，可通过代码创建它。

### 步骤 2：从 FTP 获取 PDF 流
辅助方法 `GetFileFromFtp` 打开一个 `FtpWebRequest`，将响应读取到 `MemoryStream`，并返回定位在起始位置的流。该流即为 GroupDocs.Annotation 所消费的对象。

> **安全提示：** 在生产环境中，务必设置 `request.Credentials = new NetworkCredential(user, pass)` 并启用 SSL（`EnableSsl = true`）以保护凭据。

### 步骤 3：使用流初始化 GroupDocs.Annotation
`AnnotationConfig` 对象告诉 GroupDocs.Annotation 你正在处理的文件类型以及要读取的流。直接传入流可避免临时文件并降低 I/O 开销。

### 步骤 4：添加高亮批注
创建 `HighlightAnnotation`（或其他批注类型），并配置其位置、大小和颜色。示例使用明亮的黄色（`BackgroundColor = 65535`），在大多数 PDF 上都很醒目。

### 步骤 5：保存已批注的文档
调用 `annotation.Save(outputPath)` 将更新后的 PDF 写入步骤 1 中定义的位置。控制台输出将确认成功并显示完整路径。

### 步骤 6：将所有代码包装在 `try/catch` 中
网络操作容易出现超时和权限错误。将整个流程放入 `try/catch` 块，记录异常并可选地重试下载。

## 常见 FTP 加载问题及解决方案

### 连接超时
FTP 服务器可能在短时间内关闭空闲连接。通过设置 `request.Timeout = 30000`（30 秒）或更高来延长超时时间。

### 身份验证失败
如果收到 530 错误，请再次检查用户名/密码，并确保账户对目标目录具有读取权限。切换到 FTPS（`EnableSsl = true`）通常能解决凭据相关的问题。

### 防火墙与被动模式
许多企业防火墙会阻止主动 FTP 使用的数据通道。通过 `request.UsePassive = true` 启用被动模式，让客户端打开数据连接。

### 大文件处理
对于大于 100 MB 的 PDF，考虑将响应直接流式写入临时文件，然后使用 `FileStream` 打开供 GroupDocs.Annotation 使用。这样可避免将整个文件全部加载到内存中。

## 安全注意事项

- **绝不硬编码凭据** – 将其存放在 Azure Key Vault、AWS Secrets Manager 或环境变量中。  
- **优先使用 FTPS 或 SFTP** – 明文 FTP 会以明文方式传输凭据。  
- **验证 URL** – 将 FTP 主机限制在白名单内，以防止 SSRF 攻击。  
- **清理文件名** – 拒绝包含 `..` 或异常字符的路径，以防目录遍历。

## 实际使用案例

- **合规审查门户** – 从本地 FTP 档案库拉取合规 PDF，审计员添加评论后将已批注的版本存回安全位置。  
- **遗留报告自动化** – 每日财务报告落入 FTP 投递文件夹；服务自动高亮关键数字并将已批注的报告通过电子邮件发送给相关方。  
- **迁移助手** – 在将文档从 FTP 迁移至云 DMS 时，使用批注为每个文件添加迁移状态标记，无需人工干预。

## 性能优化技巧

- **复用 `FtpWebRequest` 对象** 在处理多个文件时可减少握手开销。  
- **异步执行 FTP 调用**（`await GetFileFromFtpAsync`）以保持 UI 线程响应。  
- **短期本地缓存常用 PDF**（例如 5 分钟），当同一文件被重复批注时可提升效率。  
- **批量批注** – 将多个 PDF 加载到各自的 `Annotation` 实例中，完成批注后一次性进行 I/O 持久化。

## 常见问题

**问：我可以批注除 PDF 之外的文件类型吗？**  
答：可以，GroupDocs.Annotation 支持超过 30 种格式，包括 DOCX、PPTX 和常见图像类型，均可使用相同的基于流的方法从 FTP 加载。

**问：如何添加评论批注而不是高亮？**  
答：实例化 `CommentAnnotation`，设置其 `Text` 属性，然后像示例中的高亮一样将其加入 `Annotations` 集合。

**问：是否可以将已批注的文件写回 FTP 服务器？**  
答：完全可以。本地保存后，创建一个新的 `FtpWebRequest`，将 `Method = WebRequestMethods.Ftp.UploadFile`，并将文件流写回远程路径。

**问：官方支持哪些 .NET 版本？**  
答：GroupDocs.Annotation for .NET 支持 .NET Framework 4.6.1+、.NET Core 2.0+、.NET 5 和 .NET 6。

**问：如何处理受密码保护的 PDF？**  
答：在加载流之前，通过 `AnnotationConfig` 构造函数的 `Password` 属性传入密码。

## 结论

现在，你已经掌握了一个完整的、可用于生产环境的 **add annotations to pdf** 模式，能够直接对位于 FTP 服务器上的文件进行批注。通过将文件流直接传入 GroupDocs.Annotation，你可以避免不必要的磁盘 I/O，使应用轻量化，并对安全性和性能保持完整控制。基于此基础，你可以加入身份验证、进度报告或批量处理，以满足企业文档工作流的需求。

如需进一步帮助，请访问[支持论坛](https://forum.groupdocs.com/c/annotation/10)。

**最后更新：** 2026-07-06  
**测试环境：** GroupDocs.Annotation 23.12 for .NET  
**作者：** GroupDocs  

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Annotation code will be added here
}
```

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```

```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```

```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```

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

```csharp
request.Timeout = 30000; // 30 seconds
```

```csharp
request.Credentials = new NetworkCredential("username", "password");
```

## 相关教程

- [如何在 .NET 中从 FTP 加载文档 - 完整的 GroupDocs 指南](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [PDF 批注 .NET 教程 - C# 文档批注完整指南](/annotation/net/annotation-management/annotate-pdf-groupdocs-annotation-net/)
- [GroupDocs.Annotation .NET 文档加载要点](/annotation/net/document-loading-essentials/)