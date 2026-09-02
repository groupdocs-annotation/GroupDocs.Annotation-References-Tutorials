---
categories:
- Document Management
date: '2026-07-06'
description: 了解如何使用 C# 配置 AWS 凭证并将 GroupDocs Annotation 与 Amazon S3 集成。一步步指南，帮助您加载、注释和管理文档。
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: 从 Amazon S3 加载文档
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: 为 GroupDocs Annotation S3 集成配置 AWS 凭证
type: docs
url: /zh/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# 配置 AWS 凭证以实现 GroupDocs Annotation 与 S3 的集成

在本教程中，您将学习如何 **配置 AWS 凭证** 并使用 C# 将 GroupDocs.Annotation 与 Amazon S3 无缝集成。我们将演示如何从 S3 存储桶加载文档、添加批注，并将结果保存回云端，同时涵盖最佳实践的安全性和性能提示。

## 快速答案
- **如何配置 AWS 凭证？** 使用 `AmazonS3Client` 构造函数与 `BasicAWSCredentials`，或依赖 IAM 角色进行自动凭证解析。  
- **需要哪些 NuGet 包？** `GroupDocs.Annotation` 和 `AWSSDK.S3`。  
- **我可以对大于 100 MB 的 PDF 进行批注吗？** 可以 — 使用流式和异步 API，以避免将整个文件加载到内存中。  
- **集成是否线程安全？** 为每个请求创建单独的 `Annotator` 实例；SDK 本身是无状态的。  
- **我需要在 S3 中加密文档吗？** 启用服务器端加密（SSE‑S3 或 SSE‑KMS）以满足合规性和数据保护需求。

## 为什么使用 S3 进行文档批注？

使用 S3 进行文档批注可为您提供高度可扩展、成本效益高且全球可访问的存储解决方案，同时确保文件安全。  
- **可扩展性**：S3 能处理几乎无限的对象，支持单文件最高 5 TB 以及每秒数百万请求。  
- **成本效益**：您只为实际使用的存储付费，且自动分层至更低成本的存储类别。  
- **全球可访问性**：从任何 AWS 区域的低延迟访问，确保您的批注文档始终可达。  
- **安全性**：内置加密（SSE‑S3、SSE‑KMS）和细粒度 IAM 策略保护敏感数据。  
- **集成性**：可原生与现有 AWS 服务（如 CloudFront、Lambda 和 IAM）协同工作。

## 前置条件

在开始构建之前，请确保您已具备以下必备条件：

1. **C# 开发环境** – Visual Studio 或带 .NET 支持的 VS Code。  
2. **GroupDocs.Annotation for .NET** – 从[官方网站](https://releases.groupdocs.com/annotation/net/)下载。  
3. **AWS S3 访问权限** – 具备对目标存储桶的读写权限的有效 AWS 凭证。  
4. **基础 C# 知识** – 了解类、async/await 和流。  
5. **Amazon S3 SDK** – 通过 NuGet 安装（`AWSSDK.S3`）。

## 如何配置用于 S3 访问的 AWS 凭证？

`BasicAWSCredentials` 是一个保存 AWS 访问密钥 ID 和秘密访问密钥的类。  
`AmazonS3Client` 是用于与 S3 服务交互的 AWS SDK 客户端。

一次性加载您的 AWS 密钥，让 SDK 在每个请求中复用它们。最直接的方式是创建 `BasicAWSCredentials` 对象并将其传递给 `AmazonS3Client` 构造函数。对于生产环境，建议使用 IAM 角色或环境变量，以避免硬编码机密。

**技巧提示：** 在 EC2、ECS 或 Lambda 上运行时，省略显式凭证，让 SDK 自动从实例配置文件获取临时凭证。

## 导入命名空间

让我们开始导入 S3 集成所需的所有命名空间：

```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

这些导入使我们能够访问 AWS S3 操作和 GroupDocs 批注功能。`Amazon.S3` 命名空间处理我们的云存储交互，而 `GroupDocs.Annotation.Models` 提供批注框架。

## 步骤实现

现在让我们逐步演示从 S3 加载文档并添加批注的完整过程。我们将把它拆分为可管理的步骤，供您跟随。

### 步骤 1：定义输出路径

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

这会创建一个本地路径，用于保存您的批注文档。`Path.Combine` 方法确保跨平台兼容性，并且我们保留原始文件扩展名以保持文档类型完整性。

**技巧提示**：考虑在输出文件名中使用时间戳，以避免覆盖之前的批注，例如：`"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`。

### 步骤 2：指定文档键

```csharp
string key = "sample.pdf";
```

这是您文档在 S3 存储桶中的唯一标识符。在实际场景中，通常会从用户输入、数据库记录或 API 参数获取。确保键名完全匹配 S3 对象名称，包括任何文件夹前缀（例如 `documents/2025/sample.pdf`）。

### 步骤 3：初始化 Annotator

`Annotator` 是 GroupDocs.Annotation 的核心类，代表可编辑的文档会话。它提供添加、修改和删除批注的方法。

```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

通过在 `using` 块中包装 S3 下载流，我们确保流和 annotator 实例都能得到正确释放。

### 步骤 4：创建区域批注

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

这将在文档上创建一个矩形批注。`Rectangle(100, 100, 100, 100)` 参数分别代表 X 位置、Y 位置、宽度和高度。`BackgroundColor` 值 `65535` 生成黄色高亮——您可以使用标准 RGB 颜色码进行自定义。

**区域批注的常见用例**：  
- 高亮合同中的重要章节  
- 标记技术规范中的审阅区域  
- 为演示幻灯片添加视觉标注

### 步骤 5：将批注添加到文档

```csharp
annotator.Add(area);
```

此方法将我们的区域批注添加到文档中。您可以多次调用 `Add()`，以包含文本评论、箭头或印章等不同类型的批注。批注会保留在内存中，直到您显式保存文档。

### 步骤 6：保存批注文档

```csharp
annotator.Save(outputPath);
```

现在我们将批注文档保存到指定的输出路径。这会创建一个包含所有批注的新文件。如果需要将结果重新存回 S3——这在生产环境中很常见——只需在此步骤后使用 S3 SDK 上传该文件即可。

### 步骤 7：显示成功信息

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

一个简易的确认信息，有助于调试并提供用户反馈。在实际应用中，您应将其替换为适当的日志记录或 UI 通知。

## 实现 S3 下载方法

您会注意到我们引用了一个尚未实现的 `DownloadFile(key)` 方法。下面展示如何创建此关键辅助方法：

```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**安全提示**：切勿在生产代码中硬编码 AWS 凭证。请使用 IAM 角色、环境变量或共享凭证文件，将机密信息从源代码管理中剔除。

## 如何从 Amazon S3 加载文档？

`GetObjectAsync` 是一个异步方法，用于从 S3 检索对象并返回包含流的响应。  
`MemoryStream` 是 .NET 的内存流，可在内存中存储数据，实现快速读写，无需磁盘 I/O。  
`Annotator`（如前所述）是用于加载文档进行批注的类。

使用 `GetObjectAsync` 方法直接从 S3 加载 PDF，将响应流包装在 `MemoryStream` 中，并传递给 `Annotator` 构造函数。此方法避免将原始文件写入磁盘，降低 I/O 开销，并在保持内存使用受控的同时高效处理大文件。

```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## 常见集成问题与解决方案

根据实际实现经验，以下是您可能遇到的最常见问题及其解决方案：

### 问题 1：“Access Denied” 错误

**问题**：您的应用无法访问 S3 对象。  
**解决方案**：确认您的 IAM 用户或角色对特定存储桶及对象拥有 `s3:GetObject` 权限。

### 问题 2：大文件超时

**问题**：超过 50 MB 的文档会导致超时错误。  
**解决方案**：实现异步操作并增加超时时间值：

```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### 问题 3：多文档内存问题

**问题**：处理大量文档导致内存不足异常。  
**解决方案**：及时释放流并批量处理文档。

### 问题 4：区域不匹配错误

**问题**：S3 客户端无法定位您的存储桶。  
**解决方案**：确保 `RegionEndpoint` 与存储桶实际所在的区域匹配。

## 性能与安全最佳实践

### 性能优化
- **使用异步方法**：优先使用 `GetObjectAsync()` 而非同步调用。  
- **实现缓存**：将频繁访问的文档在本地短期存储。  
- **批量操作**：在合适时并行处理多个文件。  
- **流式处理**：避免将整个大文档加载到内存中，使用流进行处理。

### 安全注意事项
- **使用 IAM 角色**：消除硬编码凭证。  
- **启用 S3 加密**：激活服务器端加密（SSE‑S3 或 SSE‑KMS）。  
- **实施访问日志**：记录谁访问了哪些文档。  
- **验证文件类型**：在处理前检查扩展名和 MIME 类型。

## 实际使用案例

此 S3 集成模式在多个行业中表现出色：

1. **法律文档审阅** – 律师事务所在 S3 中存储的合同进行批注。  
2. **教育平台** – 教师批注托管在云端的学生提交作品。  
3. **建筑管理** – 建筑师跨地区批注蓝图。  
4. **医疗记录** – 医疗机构安全地为患者文档添加备注。  
5. **金融服务** – 审计员在 S3 中存储的合规文档上协作。

## 故障排查指南

**无法从 S3 加载文档**  
- 验证 AWS 凭证和存储桶权限。  
- 再次检查存储桶名称和对象键的拼写。  
- 确保文档在 S3 中未损坏。

**批注未显示**  
- 确认在添加批注后调用了 `annotator.Save()`。  
- 检查文档格式是否支持您使用的批注类型。  
- 确保批注坐标在页面范围内。

**性能问题**  
- 监控 S3 请求速率并实现指数退避。  
- 对频繁访问的文件使用 CloudFront CDN。  
- 对全球应用考虑使用 S3 Transfer Acceleration。

## 常见问题

**Q: GroupDocs.Annotation for .NET 是否兼容所有文档格式？**  
A: GroupDocs.Annotation 支持 50 多种输入和输出格式——包括 PDF、DOCX、PPTX 和 HTML——但批注类型可能因格式而异。

**Q: 我可以在购买前试用 GroupDocs.Annotation for .NET 吗？**  
A: 可以，您可以通过访问此处的免费试用版 [here](https://releases.groupdocs.com/) 来体验 GroupDocs.Annotation for .NET 的功能。这让您可以无风险地测试 S3 集成和批注功能。

**Q: 我在哪里可以找到 GroupDocs.Annotation for .NET 的文档？**  
A: 完整的 GroupDocs.Annotation for .NET 文档可在此处获取 [here](https://tutorials.groupdocs.com/annotation/net/)。文档包括 API 参考、进阶示例和集成指南。

**Q: 我需要临时许可证来评估 GroupDocs.Annotation for .NET 吗？**  
A: 您可以从此处获取用于评估的临时许可证 [here](https://purchase.groupdocs.com/temporary-license/)。这将解除试用限制，允许您完整测试生产场景。

**Q: 我在哪里可以获得 GroupDocs.Annotation for .NET 的帮助或支持？**  
A: 如有任何疑问或支持相关问题，您可以访问 GroupDocs.Annotation 论坛 [here](https://forum.groupdocs.com/c/annotation/10)。社区和支持团队活跃且乐于帮助解决集成问题。

**Q: 我可以将批注后的文档保存回 S3 而不是本地存储吗？**  
A: 当然可以！在调用 `annotator.Save(localPath)` 后，您可以使用 `PutObjectAsync()` 方法将批注文件上传回 S3。这实现了完整的云到云工作流，非常适合 Web 应用。

**Q: S3 文档批注支持的最大文件大小是多少？**  
A: 虽然 GroupDocs.Annotation 能处理大文件，但实际限制取决于服务器内存和 S3 传输超时。对于超过 100 MB 的文件，请实现流式或分块处理，以避免内存耗尽。

---

**最后更新：** 2026-07-06  
**测试环境：** GroupDocs.Annotation 23.12 for .NET  
**作者：** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## 相关教程

- [GroupDocs.Annotation .NET 文档加载](/annotation/net/document-loading-essentials/)
- [如何从 FTP 加载文档 .NET - 完整的 GroupDocs 指南](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [文档预览 .NET 教程 - 完整的 GroupDocs.Annotation 指南](/annotation/net/document-preview/)