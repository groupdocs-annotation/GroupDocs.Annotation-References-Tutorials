---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation for .NET 在线注释 PDF 文件。使用高效的注释技术简化文档审阅流程。"
"title": "如何使用 GroupDocs.Annotation for .NET 从 URL 注释 PDF"
"url": "/zh/net/annotation-management/annotate-pdfs-online-groupdocs-annotation-net/"
"weight": 1
---

# 如何使用 GroupDocs.Annotation for .NET 从 URL 注释 PDF

## 介绍

在当今的数字环境中，在线注释文档的能力对于有效的协作和工作流管理至关重要。无论您是开发人员还是旨在增强文档审阅流程的组织，直接从 URL 注释 PDF 都可以节省时间和资源。本教程将指导您使用 GroupDocs.Annotation for .NET——一个功能强大的库，旨在无缝注释各种文件类型，包括 PDF。

**您将学到什么：**
- 从远程 URL 加载文档
- 使用特定注释（例如区域注释）对 PDF 文件进行注释
- 在 .NET 环境中设置 GroupDocs.Annotation

让我们探索开始这一旅程所需的先决条件！

## 先决条件

在开始之前，请确保您具备以下条件：

### 所需的库和依赖项
- **适用于 .NET 的 GroupDocs.Annotation**：确保您的项目包含 25.4.0 或更高版本。
  

### 环境设置要求
- 支持.NET的开发环境（例如Visual Studio）。
- 访问互联网以下载必要的软件包。

### 知识前提
- 对 C# 和 .NET 编程有基本的了解。
- 熟悉使用 NuGet 进行包管理是有益的，但不是必需的。

## 为 .NET 设置 GroupDocs.Annotation

要开始通过 URL 注释 PDF，您首先需要在开发环境中设置 GroupDocs.Annotation。操作步骤如下：

**NuGet 包管理器控制台**

```bash
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### 许可证获取

GroupDocs 提供免费试用。您也可以申请临时许可证或购买长期许可证。

- **免费试用**：非常适合初步测试。
- **临时执照**：用于不受限制的扩展评估。
- **购买**：获得完全访问权限和支持。

### 基本初始化

以下是如何在 C# 应用程序中初始化 GroupDocs.Annotation：

```csharp
using GroupDocs.Annotation;

// 使用流或文件路径初始化注释器
Annotator annotator = new Annotator("input.pdf");
```

这个简单的设置允许您开始使用 GroupDocs.Annotation 功能。

## 实施指南

### 从 URL 加载文档

#### 概述

第一步是从远程 URL 加载文档。此功能无需本地存储即可直接处理文件，从而促进基于云的应用程序和协作。

#### 实施步骤

**1. 创建 Web 请求**

```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true”;
WebRequest request = WebRequest.Create(url);
```

此行创建一个 HTTP 请求来访问指定的 URL。

**2. 获取并转换响应流**

```csharp
private static Stream GetRemoteFile(string url)
{
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}

private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream); // 将数据复制到内存流
    fileStream.Position = 0; // 重置以进行阅读
    return fileStream;
}
```

此过程将 Web 响应转换为 GroupDocs.Annotation 可用的本地文件流。

### 向文档添加注释

#### 概述

现在您的文档已加载，您可以添加区域注释等注释来突出显示特定部分或注释。

#### 实施步骤

**1. 加载文档**

```csharp
using (Annotator annotator = new Annotator(GetRemoteFile("YOUR_DOCUMENT_DIRECTORY/input.pdf")))
{
    // 继续注释步骤
}
```

**2. 创建并添加区域注释**

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 定义矩形尺寸
    BackgroundColor = 65535, // 设置背景颜色
};

annotator.Add(area); // 向文档添加注释
```

**3. 保存注释文档**

```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY\