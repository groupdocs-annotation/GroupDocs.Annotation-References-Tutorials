---
title: 从 Azure 加载文档
linktitle: 从 Azure 加载文档
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中对文档进行注释。与 Azure Blob 存储无缝集成的分步教程。
weight: 11
url: /zh/net/document-loading-essentials/load-document-from-azure/
---
## 介绍
在文档管理和协作领域，GroupDocs.Annotation for .NET 作为一个强大的解决方案出现，促进 .NET 应用程序中的无缝注释和标记功能。本教程深入探讨了利用 GroupDocs.Annotation for .NET 来注释文档的复杂性，提供从先决条件到高级用法的分步指导。
## 先决条件
在深入研究 .NET 的 GroupDocs.Annotation 之前，请确保满足以下先决条件：
1. 安装 .NET Framework：GroupDocs.Annotation for .NET 需要兼容的 .NET 运行时环境。确保您的系统上安装了 .NET Framework。
2. 访问 GroupDocs.Annotation 库：通过从网站下载或通过 NuGet 等包管理器来访问 GroupDocs.Annotation for .NET 库。
3. 要注释的文档：准备要注释的文档（例如 PDF）。确保可在本地或通过 Azure Blob 存储等云存储服务访问该文档。

## 导入命名空间
要开始使用 GroupDocs.Annotation for .NET 注释文档，请将必要的命名空间导入到您的项目中。此步骤确保您可以访问所需的类和功能。
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
要注释存储在 Azure Blob 存储中的文档，请执行以下步骤：
### 第1步：设置输出路径
定义保存注释文档的输出路径。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 第2步：下载文档
通过调用从 Azure Blob 存储检索文档`DownloadFile`方法。
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    //注释逻辑
    annotator.Save(outputPath);
}
```
## 从 Azure Blob 存储下载文件
要从 Azure Blob 存储下载文档，请实施`DownloadFile`方法。
### 第 1 步：检索 Blob
访问 Azure Blob 存储容器并检索所需的 Blob。
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 第 2 步：下载 Blob 内容
将 blob 内容下载到内存流中。
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## 获取 Azure Blob 存储容器
要与 Azure Blob 存储交互，请实施`GetContainer`方法。
### 第1步：初始化存储凭证
提供必要的帐户凭据和端点信息。
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### 第 2 步：创建 Blob 客户端
创建客户端以与 Azure Blob 存储交互。
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 第 3 步：检索容器引用
获取对指定容器的引用。
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 第四步：如果不存在则创建容器
确保容器存在，如果不存在则创建它。
```csharp
container.CreateIfNotExists();
```

## 结论
GroupDocs.Annotation for .NET 为开发人员提供强大的文档注释功能，无缝集成到 .NET 应用程序中。通过遵循本教程中概述的步骤，你可以有效地利用 GroupDocs.Annotation 的功能来注释存储在 Azure Blob 存储中的文档。
#### 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
GroupDocs.Annotation 支持多种文档格式，包括 PDF、DOCX、PPTX 等。
### 可以根据具体需求定制注释吗？
是的，GroupDocs.Annotation 为注释提供了广泛的自定义选项，允许用户修改外观、行为和元数据。
### GroupDocs.Annotation适合协作文档注释吗？
绝对地！ GroupDocs.Annotation 允许多个用户同时添加、编辑和查看注释，从而促进协作文档注释。
### GroupDocs.Annotation 是否提供跨平台兼容性？
是的，GroupDocs.Annotation 旨在跨各种平台无缝工作，包括 Windows、Linux 和 macOS。
### GroupDocs.Annotation 用户可以获得技术支持吗？
是的，GroupDocs 通过其论坛和专用支持渠道提供全面的技术支持。