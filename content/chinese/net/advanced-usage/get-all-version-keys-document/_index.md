---
title: 获取文档上的所有版本密钥
linktitle: 获取文档上的所有版本密钥
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 检索文档上的所有版本密钥。通过此综合功能增强您的文档管理能力。
type: docs
weight: 16
url: /zh/net/advanced-usage/get-all-version-keys-document/
---
## 介绍
在当今快节奏的数字世界中，有效的文档管理对于企业和个人都至关重要。无论您是在项目上进行协作、审查合同还是只是组织文件，拥有正确的工具都可以发挥重要作用。 GroupDocs.Annotation for .NET 提供了用于在 .NET 应用程序中注释和操作文档的全面解决方案。在本教程中，我们将探讨如何利用 GroupDocs.Annotation for .NET 检索文档上的所有版本密钥。
## 先决条件
在我们深入学习本教程之前，请确保您满足以下先决条件：
### 1.安装.NET的GroupDocs.Annotation
首先，您需要下载并安装 GroupDocs.Annotation for .NET。您可以从以下位置获取最新版本[下载链接](https://releases.groupdocs.com/annotation/net/).
### 2. 获取API凭证
确保您拥有必要的 API 凭据来访问 GroupDocs.Annotation for .NET 功能。

## 导入必要的命名空间
在继续之前，请确保将所需的命名空间导入到您的项目中：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

让我们将获取文档上所有版本密钥的过程分解为简单的步骤：
## 第 1 步：初始化注释器对象
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    //代码放在这里
}
```
初始化`Annotator`对象包含您要使用的文档的路径。
## 第 2 步：检索版本密钥
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
调用`GetVersionsList()`方法上的`Annotator`对象来检索与文档关联的所有版本密钥。此方法返回版本密钥列表。

## 结论
GroupDocs.Annotation for .NET 简化了 .NET 应用程序中的文档注释和操作任务。通过学习本教程，您已了解如何使用 GroupDocs.Annotation for .NET 检索文档上的所有版本密钥。将此功能合并到您的项目中以增强文档管理功能。
## 常见问题解答
### GroupDocs.Annotation for .NET 是否与所有文档格式兼容？
GroupDocs.Annotation for .NET 支持多种文档格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 我可以在购买前试用 GroupDocs.Annotation for .NET 吗？
是的，您可以通过访问可用的免费试用版来探索 GroupDocs.Annotation for .NET 的功能[这里](https://releases.groupdocs.com/).
### 如何获得对 GroupDocs.Annotation for .NET 的支持？
您可以通过支持论坛寻求帮助并与社区互动[这里](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET 是否有可用的临时许可证？
是的，临时许可证可用于评估目的。您可以从以下位置获取一份[这里](https://purchase.groupdocs.com/temporary-license/).
### 在哪里可以购买 GroupDocs.Annotation for .NET？
您可以从网站购买 GroupDocs.Annotation for .NET[这里](https://purchase.groupdocs.com/buy).