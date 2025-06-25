---
"description": "了解如何使用 GroupDocs.Annotation for .NET 检索文档的所有版本密钥。借助这项全面的功能，增强您的文档管理能力。"
"linktitle": "获取文档所有版本密钥"
"second_title": "GroupDocs.Annotation .NET API"
"title": "获取文档所有版本密钥"
"url": "/zh/net/advanced-usage/get-all-version-keys-document/"
"weight": 16
---

# 获取文档所有版本密钥

## 介绍
在当今快节奏的数字世界中，有效的文档管理对企业和个人都至关重要。无论您是在进行项目协作、审查合同，还是简单地整理文件，拥有合适的工具都能带来显著的效果。GroupDocs.Annotation for .NET 为在 .NET 应用程序中注释和操作文档提供了全面的解决方案。在本教程中，我们将探索如何利用 GroupDocs.Annotation for .NET 检索文档的所有版本密钥。
## 先决条件
在深入学习本教程之前，请确保您满足以下先决条件：
### 1. 安装 GroupDocs.Annotation for .NET
首先，您需要下载并安装 GroupDocs.Annotation for .NET。您可以从 [下载链接](https://releases。groupdocs.com/annotation/net/).
### 2.获取 API 凭证
确保您拥有访问 GroupDocs.Annotation .NET 功能所需的 API 凭证。

## 导入必要的命名空间
在继续之前，请确保将所需的命名空间导入到您的项目中：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

让我们将获取文档上所有版本密钥的过程分解为几个简单的步骤：
## 步骤 1：初始化注释器对象
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // 代码在这里
}
```
初始化 `Annotator` 对象与您要处理的文档的路径。
## 第 2 步：检索版本密钥
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
调用 `GetVersionsList()` 方法 `Annotator` 对象用于检索与文档关联的所有版本键。此方法返回版本键列表。

## 结论
GroupDocs.Annotation for .NET 简化了 .NET 应用程序中的文档注释和操作任务。通过学习本教程，您学习了如何使用 GroupDocs.Annotation for .NET 检索文档中的所有版本密钥。将此功能集成到您的项目中，以增强文档管理能力。
## 常见问题解答
### .NET 的 GroupDocs.Annotation 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以在购买之前试用 GroupDocs.Annotation for .NET 吗？
是的，您可以通过访问免费试用版来探索 GroupDocs.Annotation for .NET 的功能 [这里](https://releases。groupdocs.com/).
### 如何获得 .NET 的 GroupDocs.Annotation 支持？
您可以通过支持论坛寻求帮助并与社区互动 [这里](https://forum。groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET 是否有临时许可证？
是的，临时许可证可用于评估目的。您可以从 [这里](https://purchase。groupdocs.com/temporary-license/).
### 我可以在哪里购买适用于 .NET 的 GroupDocs.Annotation？
您可以从网站购买 GroupDocs.Annotation for .NET [这里](https://purchase。groupdocs.com/buy).