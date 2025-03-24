---
title: 设置计量许可证
linktitle: 设置计量许可证
second_title: GroupDocs.Annotation .NET API
description: 了解如何为 GroupDocs.Annotation .NET 设置计量许可证，以实现 .NET 应用程序中的资源使用和文档注释功能。
weight: 12
url: /zh/net/applying-licenses/set-metered-license/
---

# 设置计量许可证

## 介绍
GroupDocs.Annotation for .NET 是一个功能强大的库，使开发人员能够轻松地将文档注释功能添加到其 .NET 应用程序中。无论您是构建文档管理系统、协作平台还是任何涉及文档审阅和标记的应用程序，GroupDocs.Annotation for .NET 都提供了一套全面的工具来简化流程。
在本教程中，我们将深入研究为 GroupDocs.Annotation .NET 设置计量许可证的过程。计量许可证允许您只需为您消耗的资源付费，使其成为适合任何规模项目的经济高效的解决方案。通过执行下面概述的步骤，您将能够将 GroupDocs.Annotation 无缝集成到您的 .NET 应用程序中，同时优化资源使用并保持预算控制。
## 先决条件
在深入学习本教程之前，请确保您满足以下先决条件：
1.  GroupDocs.Annotation for .NET 库：从以下位置下载库：[网站](https://releases.groupdocs.com/annotation/net/).
2. 访问 GroupDocs 帐户：您需要一个 GroupDocs 帐户来获取设置计量许可证所需的公钥和私钥。如果您还没有帐户，可以注册免费试用[这里](https://releases.groupdocs.com/).
3. 对 C# 和 .NET Framework 的基本了解：熟悉 C# 编程语言和 .NET Framework 将有助于实现本教程中概述的步骤。

## 导入命名空间
首先，请确保将必要的命名空间导入到您的 C# 项目中。这些命名空间对于与 GroupDocs.Annotation 功能进行交互至关重要。
```csharp
using System;
```
## 第1步：获取公钥和私钥
在设置计量许可证之前，您需要从 GroupDocs 帐户仪表板获取公钥和私钥。
1. 登录您的 GroupDocs 帐户。
2. 导航到许可证管理部分。
3. 复制 GroupDocs 提供的公钥和私钥。
## 第 2 步：设置计量许可证
获得公钥和私钥后，您可以在 .NET 应用程序中设置计量许可证。
```csharp
string publicKey = "*****"; //将 ***** 替换为您的公钥
string privateKey = "*****"; //将 ***** 替换为您的私钥
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 结论
总之，为 GroupDocs.Annotation .NET 设置计量许可证是一个简单的过程，可确保文档注释项目的资源高效利用和成本效益。通过遵循本教程中概述的步骤，您可以将 GroupDocs.Annotation 无缝集成到 .NET 应用程序中，并增强文档协作和审阅功能。
## 常见问题解答
### 我可以在商业项目中使用 GroupDocs.Annotation for .NET 吗？
是的，GroupDocs.Annotation for .NET 可用于商业和非商业项目。但是，您需要根据您的项目要求获取适当的许可证。
### GroupDocs.Annotation for .NET 是否有试用版？
是的，您可以访问 GroupDocs.Annotation for .NET 免费试用版[这个链接](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Annotation for .NET 的技术支持？
您可以访问 GroupDocs 论坛寻求技术支持[这里](https://forum.groupdocs.com/c/annotation/10).
### 是否有可用的临时许可证选项？
是的，您可以从 GroupDocs 获取临时许可证以用于短期使用或评估目的。访问[这个链接](https://purchase.groupdocs.com/temporary-license/)了解更多信息。
### 我可以根据我的项目需求定制注释功能吗？
是的，GroupDocs.Annotation for .NET 提供了广泛的自定义选项，允许您定制注释功能以满足您的特定项目需求。