---
"description": "了解如何为 GroupDocs.Annotation .NET 设置计量许可证，以便在您的 .NET 应用程序中使用资源和记录注释功能。"
"linktitle": "设置计量许可证"
"second_title": "GroupDocs.Annotation .NET API"
"title": "设置计量许可证"
"url": "/zh/net/applying-licenses/set-metered-license/"
"weight": 12
---

# 设置计量许可证

## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的库，可帮助开发人员轻松地为其 .NET 应用程序添加文档注释功能。无论您是构建文档管理系统、协作平台，还是任何涉及文档审阅和标记的应用程序，GroupDocs.Annotation for .NET 都提供了一套全面的工具来简化流程。
在本教程中，我们将深入探讨如何为 GroupDocs.Annotation .NET 设置计量许可证。计量许可证允许您仅按实际使用的资源付费，使其成为适用于任何规模项目的经济高效的解决方案。按照以下步骤操作，您将能够将 GroupDocs.Annotation 无缝集成到您的 .NET 应用程序中，同时优化资源使用率并控制预算。
## 先决条件
在深入学习本教程之前，请确保您满足以下先决条件：
1. GroupDocs.Annotation for .NET 库：从 [网站](https://releases。groupdocs.com/annotation/net/).
2. 访问 GroupDocs 帐户：您需要一个 GroupDocs 帐户来获取设置计量许可证所需的公钥和私钥。如果您还没有帐户，可以注册免费试用 [这里](https://releases。groupdocs.com/).
3. 对 C# 和 .NET Framework 的基本了解：熟悉 C# 编程语言和 .NET 框架将有助于实现本教程中概述的步骤。

## 导入命名空间
首先，请确保将必要的命名空间导入到您的 C# 项目中。这些命名空间对于与 GroupDocs.Annotation 功能交互至关重要。
```csharp
using System;
```
## 步骤1：获取公钥和私钥
在设置计量许可证之前，您需要从 GroupDocs 帐户仪表板获取公钥和私钥。
1. 登录您的 GroupDocs 帐户。
2. 导航到许可证管理部分。
3. 复制 GroupDocs 提供的公钥和私钥。
## 步骤 2：设置计量许可证
一旦您获得了公钥和私钥，您就可以在 .NET 应用程序中设置计量许可证。
```csharp
string publicKey = "*****"; // 将 ***** 替换为您的公钥
string privateKey = "*****"; // 将 ***** 替换为您的私钥
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 结论
总而言之，为 GroupDocs.Annotation .NET 设置计量许可证是一个简单的过程，可确保您的文档注释项目高效利用资源并实现成本效益。按照本教程中概述的步骤，您可以将 GroupDocs.Annotation 无缝集成到您的 .NET 应用程序中，并增强文档协作和审阅功能。
## 常见问题解答
### 我可以在商业项目中使用 GroupDocs.Annotation for .NET 吗？
是的，GroupDocs.Annotation for .NET 可用于商业和非商业项目。但是，您需要根据项目需求获取相应的许可证。
### GroupDocs.Annotation for .NET 有试用版吗？
是的，您可以通过访问以下网址免费试用 GroupDocs.Annotation for .NET [此链接](https://releases。groupdocs.com/).
### 如何获得 GroupDocs.Annotation for .NET 的技术支持？
您可以通过访问 GroupDocs 论坛寻求技术支持 [这里](https://forum。groupdocs.com/c/annotation/10).
### 是否有可用的临时许可证选项？
是的，您可以从 GroupDocs 获取临时许可证，用于短期使用或评估。访问 [此链接](https://purchase.groupdocs.com/temporary-license/) 了解更多信息。
### 我可以根据我的项目要求定制注释功能吗？
是的，GroupDocs.Annotation for .NET 提供了广泛的自定义选项，允许您定制注释功能以满足您的特定项目需求。