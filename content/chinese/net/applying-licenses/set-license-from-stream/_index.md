---
title: 从 Stream 设置许可证
linktitle: 从 Stream 设置许可证
second_title: GroupDocs.Annotation .NET API
description: 使用 GroupDocs.Annotation 释放 .NET 中文档注释的全部潜力。请按照我们的分步指南进行无缝集成。
weight: 11
url: /zh/net/applying-licenses/set-license-from-stream/
---

# 从 Stream 设置许可证

## 介绍
欢迎阅读有关使用 GroupDocs.Annotation for .NET 增强文档注释功能的综合指南。无论您是经验丰富的开发人员还是刚刚起步，本教程都将引导您完成每个步骤，确保您充分利用这个强大工具的潜力。
## 先决条件
在深入学习本教程之前，请确保您具备以下先决条件：
1.  GroupDocs.Annotation for .NET：确保您已从以下位置下载并安装了 GroupDocs.Annotation for .NET[下载链接](https://releases.groupdocs.com/annotation/net/).
2. 许可证：获取 GroupDocs.Annotation 的有效许可证。您可以从以下位置购买一个[这里](https://purchase.groupdocs.com/buy)或申请临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
3. 文档：熟悉[文档](https://tutorials.groupdocs.com/annotation/net/)对于 GroupDocs.Annotation。它提供了对 API 功能的详细见解。

## 导入命名空间
首先，让我们导入必要的命名空间以开始在 .NET 项目中使用 GroupDocs.Annotation：
```csharp
using System;
using System.IO;
```

## 第 1 步：检查许可证路径
确保您的项目中正确设置了许可证文件路径。它应该指向存储许可证文件的位置。
## 第 2 步：设置许可证
```csharp
if (File.Exists(Constants.LicensePath))
{
```
在此步骤中，代码检查指定路径中是否存在许可证文件。
```csharp
    using (FileStream stream = File.OpenRead(Constants.LicensePath))
    {
        License license = new License();
        license.SetLicense(stream);
    }
```
如果许可证文件存在，则读取文件流并使用`SetLicense`方法。
```csharp
    Console.WriteLine("License set successfully.");
}
else
{
```
如果许可证文件不存在，则会提示用户从 GroupDocs 站点获取许可证。
```csharp
    Console.WriteLine("\nWe do not ship any license with this example. " +
                      "\nVisit the GroupDocs site to obtain either a temporary or permanent license. " +
                      "\nLearn more about licensing at https://buy.groupdocs.com/faqs/licensing。 ” +
                      "\nLear how to request temporary license at https://buy.groupdocs.com/temporary-license。”）；
}
```

## 结论
总之，掌握 GroupDocs.Annotation for .NET 可以显着提高您的文档注释能力。通过遵循此分步指南，您将能够将强大的注释功能无缝集成到 .NET 应用程序中。
## 常见问题解答
### 我是否需要购买许可证才能使用 GroupDocs.Annotation for .NET？
是的，您需要有效的许可证才能解锁 GroupDocs.Annotation 的全部功能。您可以购买永久许可证或请求临时许可证以用于评估目的。
### 在哪里可以找到对 GroupDocs.Annotation for .NET 的支持？
您可以在以下位置找到全面的支持并与社区互动[GroupDocs.Annotation 论坛](https://forum.groupdocs.com/c/annotation/10).
### 我可以在购买前试用 GroupDocs.Annotation for .NET 吗？
是的，您可以申请免费试用许可证[这里](https://releases.groupdocs.com/)探索 GroupDocs.Annotation for .NET 的功能。
### 如何获取 GroupDocs.Annotation for .NET 的最新文档？
您可以参考[文档](https://tutorials.groupdocs.com/annotation/net/)用于 GroupDocs.Annotation for .NET 来访问详细的 API 参考和教程。
### 如果我的许可证遇到问题怎么办？
如果您遇到任何许可证问题，请联系 GroupDocs 支持团队寻求帮助。