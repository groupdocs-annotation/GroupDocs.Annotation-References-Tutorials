---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中注释文档。与 Azure Blob 存储无缝集成的分步教程。"
"linktitle": "从 Azure 加载文档"
"second_title": "GroupDocs.Annotation .NET API"
"title": "从 Azure 加载文档"
"url": "/zh/net/document-loading-essentials/load-document-from-azure/"
"weight": 11
---

# 从 Azure 加载文档

## 介绍
在文档管理和协作领域，GroupDocs.Annotation for .NET 是一个强大的解决方案，可在 .NET 应用程序中实现无缝的注释和标记功能。本教程深入探讨了如何利用 GroupDocs.Annotation for .NET 注释文档，并提供从入门到高级使用的分步指导。
## 先决条件
在深入研究 .NET 的 GroupDocs.Annotation 之前，请确保您已满足以下先决条件：
1. .NET Framework 的安装：GroupDocs.Annotation for .NET 需要兼容的 .NET 运行时环境。请确保您的系统上已安装 .NET Framework。
2. 访问 GroupDocs.Annotation 库：通过从网站下载或通过 NuGet 等包管理器获取 .NET 库的 GroupDocs.Annotation 的访问权限。
3. 待注释文档：准备要注释的文档（例如 PDF）。确保该文档可在本地或通过 Azure Blob Storage 等云存储服务访问。

## 导入命名空间
要开始使用 GroupDocs.Annotation for .NET 注释文档，请将必要的命名空间导入您的项目。此步骤可确保您能够访问所需的类和功能。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## 从 Azure 加载文档
要注释存储在 Azure Blob 存储中的文档，请按照以下步骤操作：
### 步骤1：设置输出路径
定义注释文档的保存输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 第 2 步：下载文档
通过调用 `DownloadFile` 方法。
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // 注释逻辑
    annotator.Save(outputPath);
}
```
## 从 Azure Blob 存储下载文件
要从 Azure Blob 存储下载文档，请执行 `DownloadFile` 方法。
### 步骤 1：检索 Blob
访问 Azure Blob 存储容器并检索所需的 Blob。
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 步骤 2：下载 Blob 内容
将 Blob 内容下载到内存流中。
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## 获取 Azure Blob 存储容器
要与 Azure Blob 存储进行交互，请实现 `GetContainer` 方法。
### 步骤 1：初始化存储凭证
提供必要的帐户凭据和端点信息。
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/”；
```
### 步骤 2：创建 Blob 客户端
创建一个客户端来与 Azure Blob 存储进行交互。
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 步骤 3：检索容器引用
获取指定容器的教程。
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 步骤 4：如果不存在则创建容器
确保容器存在，如果不存在则创建。
```csharp
container.CreateIfNotExists();
```

## 结论
GroupDocs.Annotation for .NET 为开发人员提供了强大的文档注释功能，可无缝集成到 .NET 应用程序中。按照本教程中概述的步骤操作，您可以有效地利用 GroupDocs.Annotation 的功能来注释存储在 Azure Blob 存储中的文档。
#### 常见问题解答
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
GroupDocs.Annotation 支持多种文档格式，包括 PDF、DOCX、PPTX 等。
### 注释是否可以根据具体要求进行定制？
是的，GroupDocs.Annotation 为注释提供了广泛的自定义选项，允许用户修改外观、行为和元数据。
### GroupDocs.Annotation 是否适合协作文档注释？
当然！GroupDocs.Annotation 支持多个用户同时添加、编辑和审阅注释，从而促进协作文档注释。
### GroupDocs.Annotation 是否提供跨平台兼容性？
是的，GroupDocs.Annotation 旨在跨各种平台无缝运行，包括 Windows、Linux 和 macOS。
### GroupDocs.Annotation 用户可以获得技术支持吗？
是的，GroupDocs 通过其论坛和专用支持渠道提供全面的技术支持。