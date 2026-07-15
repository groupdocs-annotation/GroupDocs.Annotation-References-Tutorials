---
categories:
- License Management
date: '2026-06-06'
description: 逐步指南，介绍如何在 .NET 中使用 GroupDocs.Annotation 从流设置许可证，包括代码示例、故障排除和最佳实践。
keywords:
- how to set license
- license from database
- stream based licensing
lastmod: '2026-06-06'
linktitle: 从流设置许可证
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Step-by-step guide on how to set license from stream in .NET with GroupDocs.Annotation,
    including code examples, troubleshooting, and best practices.
  headline: How to Set License from Stream in .NET with GroupDocs.Annotation
  type: TechArticle
- description: Step-by-step guide on how to set license from stream in .NET with GroupDocs.Annotation,
    including code examples, troubleshooting, and best practices.
  name: How to Set License from Stream in .NET with GroupDocs.Annotation
  steps:
  - name: Verify License Path Configuration
    text: 'The first step involves ensuring your license path is correctly configured.
      This might seem basic, but it''s the source of many licensing headaches: **What''s
      happening here?** The code checks whether your license file exists at the specified
      path before attempting to read it. This prevents runtime er'
  - name: Create and Configure the License Stream
    text: 'The `License` class is the entry point for applying a GroupDocs.Annotation
      license. It represents the licensing engine that validates the provided license
      data. Load your license with a stream, then apply it: The `SetLicense(stream)`
      method loads the license data from the given stream and activates '
  - name: Handle Success and Error Cases
    text: 'Robust error handling ensures your app fails gracefully if the license
      cannot be applied: The code catches `FileNotFoundException` for missing files
      and a generic `Exception` for any other issues, then writes a clear message
      to the console. In production, replace `Console.WriteLine` with a proper lo'
  type: HowTo
- questions:
  - answer: Yes, a valid license unlocks full functionality. A free trial or temporary
      license is available for evaluation and development.
    question: Do I need to purchase a license to use GroupDocs.Annotation for .NET?
  - answer: Visit the [GroupDocs.Annotation forum](https://forum.groupdocs.com/c/annotation/10)
      for community help and official support from the GroupDocs team.
    question: Where can I find support for GroupDocs.Annotation licensing issues?
  - answer: Absolutely! You can request a free trial license [here](https://releases.groupdocs.com/)
      to explore all capabilities for 30 days.
    question: Can I try GroupDocs.Annotation before buying a full license?
  - answer: The most up‑to‑date docs are at the [documentation site](https://tutorials.groupdocs.com/annotation/net/),
      which includes API references, tutorials, and advanced licensing scenarios.
    question: How do I obtain the latest documentation?
  - answer: Verify the stream contains the exact binary data of a valid `.lic` file,
      ensure the stream is not disposed before `SetLicense` runs, and check that the
      license matches your product version.
    question: What should I do if my license stream fails to load?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- licensing
- stream
- groupdocs
- dotnet
- configuration
title: 如何在 .NET 中使用 GroupDocs.Annotation 从流设置许可证
type: docs
url: /zh/net/applying-licenses/set-license-from-stream/
weight: 11
---

# 如何在 .NET 中使用 GroupDocs.Annotation 从流设置许可证

## 介绍

在生产应用中使用 GroupDocs.Annotation for .NET 时，正确设置许可证至关重要。如果你曾经为许可证配置而苦恼，或疑惑为何注释功能未如预期工作，你来对地方了。本指南展示了**如何从流设置许可证**，逐步引导你完成每一步，并解释为何基于流的方法通常是现代部署的最佳选择。

## 快速答案
- **第一行代码是什么？** `new License().SetLicense(stream);`
- **开发时需要完整许可证吗？** 不，需要一个临时评估许可证即可用于测试。
- **可以从数据库加载许可证吗？** 可以，将二进制数据读取到流中并调用 `SetLicense`。
- **流许可证是线程安全的吗？** 是的，在应用启动时设置一次许可证即可。
- **这会影响应用性能吗？** 许可证只会在启动时应用一次，影响可以忽略不计。

## 为什么使用基于流的许可证？

直接从 `Stream` 加载许可证，可避免将许可证文件放在文件系统中，并可控制许可证的存放位置。基于流的许可证允许你将许可证嵌入资源、从数据库读取或通过 HTTPS 获取，然后使用单个 `SetLicense(stream)` 调用进行激活——无需文件路径，也无需额外权限。这提升了部署的灵活性并增强了安全性。

## 前提条件

在深入实现之前，请确保以下必备条件已就绪：

1. **GroupDocs.Annotation for .NET**：从[下载页面](https://releases.groupdocs.com/annotation/net/)下载并安装最新版本。基于流的许可证功能在所有近期版本中均可用。  
2. **有效许可证**：你需要从[GroupDocs](https://purchase.groupdocs.com/buy)购买的许可证，或从[此处](https://purchase.groupdocs.com/temporary-license/)获取的临时评估许可证。  
3. **开发环境**：任意兼容 .NET 的 IDE（Visual Studio、JetBrains Rider 或 VS Code），并使用 .NET Framework 4.6.1+ 或 .NET Core 2.0+。  
4. **文档访问**：随时准备好[文档](https://tutorials.groupdocs.com/annotation/net/)以供参考。

## 导入命名空间

让我们先导入在整个实现过程中需要的关键命名空间：

```csharp
using System;
using System.IO;
```

这些命名空间提供了文件操作和基本控制台输出所需的一切。GroupDocs.Annotation 的优势在于，基本的许可证操作并不需要大量额外的导入。

## 步骤式实现指南

### 步骤 1：验证许可证路径配置

第一步是确保你的许可证路径配置正确。这看似基础，却是许多许可证问题的根源：

```csharp
if (File.Exists(Constants.LicensePath))
{
```

**这段代码在做什么？** 代码在尝试读取之前检查指定路径下是否存在许可证文件。这可以防止运行时错误并提供更清晰的用户体验。

**专业提示**：确保你的 `Constants.LicensePath` 指向正确的位置。在开发环境中，这可能是本地路径，但在生产环境中，建议使用相对路径或基于配置的路径以获得更好的灵活性。

### 步骤 2：创建并配置许可证流

`License` 类是应用 GroupDocs.Annotation 许可证的入口点。它代表验证提供的许可证数据的授权引擎。

使用流加载许可证，然后进行激活：

`SetLicense(stream)` 方法从给定的流中加载许可证数据并激活它。

```csharp
    using (FileStream stream = File.OpenRead(Constants.LicensePath))
    {
        License license = new License();
        license.SetLicense(stream);
    }
```

**拆解说明：**  
- `File.OpenRead()` 从许可证文件创建只读流。  
- `using` 语句确保流在使用后被释放，防止内存泄漏。  
- `new License()` 实例化授权引擎。  
- `SetLicense(stream)` 使用提供的流数据验证并激活许可证。

**为何使用流**：这种方式意味着你不局限于基于文件的许可证。你可以轻松修改为从嵌入资源、HTTP 响应，甚至解密后的数据流中读取。

### 步骤 3：处理成功和错误情况

健壮的错误处理可确保在许可证无法应用时，应用能够优雅地失败：

```csharp
    Console.WriteLine("License set successfully.");
}
else
{
    Console.WriteLine("\nWe do not ship any license with this example. " +
                      "\nVisit the GroupDocs site to obtain either a temporary or permanent license. " +
                      "\nLearn more about licensing at https://purchase.groupdocs.com/faqs/licensing. " +
                      "\nLear how to request temporary license at https://purchase.groupdocs.com/temporary-license.");
}
```

代码捕获 `FileNotFoundException` 以处理文件缺失情况，并捕获通用 `Exception` 处理其他问题，然后在控制台输出清晰的提示信息。在生产环境中，请将 `Console.WriteLine` 替换为合适的日志框架，并考虑对瞬时故障进行重试逻辑。

## 常见许可证问题与解决方案

### 问题：“未找到许可证文件”错误

**症状**：在尝试设置许可证时，应用抛出文件未找到异常。

**解决方案**：  
- 验证 `Constants` 类中的许可证文件路径。  
- 确保许可证文件已包含在构建输出中（`Copy to Output Directory`）。  
- 检查部署服务器上的文件权限。  
- 优先使用相对路径或基于配置的路径，以避免环境特定的问题。

### 问题：“许可证格式无效”信息

**症状**：许可证文件存在，但 GroupDocs.Annotation 拒绝它。

**解决方案**：  
- 确认使用的是 GroupDocs.Annotation 许可证（而非其他 GroupDocs 产品的许可证）。  
- 核实许可证未过期。  
- 确保文件在传输过程中未损坏——如有必要，比较文件哈希。  
- 使用与许可证匹配的相同产品版本；版本不匹配可能导致验证失败。

### 问题：流释放问题

**症状**：生产环境中出现随机错误或内存泄漏。

**解决方案**：  
- 始终像示例中那样使用 `using` 包装流。  
- 在将流传递给 `SetLicense()` 后**不要**手动释放流——库会自行处理释放。  
- 将流的生命周期保持尽可能短；加载、激活后立即丢弃。

## 基于流的许可证管理最佳实践

### 1. 安全的许可证存储

绝不要在源代码中硬编码许可证路径或嵌入原始许可证文件。相反：  
- 将许可证路径存储在配置文件中（例如 `appsettings.json`）。  
- 对许可证文件进行加密，并在运行时解密后再创建流。  
- 在 CI/CD 流水线中使用环境变量存放敏感的许可证信息。

### 2. 实现回退机制

`MemoryStream` 提供基于字节数组的内存流，可用于加载存储在数据库中的许可证。

```csharp
// Example of multiple license source attempts
var licenseSources = new[] { 
    "license.lic", 
    "backup-license.lic", 
    GetLicenseFromDatabase() 
};

foreach (var source in licenseSources)
{
    if (TrySetLicense(source))
        break;
}
```

典型的回退逻辑会先尝试嵌入资源，其次是文件路径，最后是远程端点。这确保即使某个来源不可用，应用仍能启动。

### 3. 开发阶段的许可证验证

在开发期间，添加检查以显示许可证的到期日期和功能限制：  
- 调用 `license.IsValid`（如果可用）并记录剩余天数。  
- 测试试用版和正式版许可证，以验证功能开关。

## 性能考虑

基于流的许可证通常速度很快，但需注意以下要点：  
- **启动影响**：许可证设置在应用初始化时只执行一次，性能影响可以忽略不计。如果从远程服务获取许可证，请在本地缓存结果，以避免重复的网络调用。  
- **内存使用**：许可证文件通常小于 10 KB，加载到流中占用的内存极少。  
- **线程安全**：GroupDocs.Annotation 的许可证引擎是线程安全的。请在创建工作线程之前设置许可证，以避免竞争条件。

## 替代许可证方案

虽然本指南侧重于基于流的许可证，GroupDocs.Annotation 还支持以下方式：  
- **基于文件的许可证** – 简单的基于路径的激活。  
- **嵌入资源许可证** – 将 `.lic` 文件编译进程序集，并使用 `Assembly.GetManifestResourceStream` 加载。  
- **计量许可证** – 基于使用量的计费，适用于云原生场景。

## 结论

使用 GroupDocs.Annotation for .NET 的基于流的许可证为现代 .NET 应用提供了所需的灵活性和安全性。通过本指南，你已学会如何从任意流来源加载许可证、处理常见陷阱，并采用最佳实践模式实现安全部署。许可证配置正确后，你即可专注于构建强大的注释功能，确保在所有环境中可靠运行。

## 常见问答

**问：使用 GroupDocs.Annotation for .NET 是否需要购买许可证？**  
答：是的，只有有效许可证才能解锁全部功能。可获取免费试用或临时许可证用于评估和开发。

**问：在哪里可以找到 GroupDocs.Annotation 许可证问题的支持？**  
答：请访问[GroupDocs.Annotation 论坛](https://forum.groupdocs.com/c/annotation/10)，获取社区帮助和 GroupDocs 官方支持。

**问：在购买完整许可证之前，我可以先试用 GroupDocs.Annotation 吗？**  
答：当然可以！你可以在[此处](https://releases.groupdocs.com/)申请免费试用许可证，体验全部功能 30 天。

**问：如何获取最新的文档？**  
答：最新文档位于[文档站点](https://tutorials.groupdocs.com/annotation/net/)，其中包含 API 参考、教程以及高级许可证场景。

**问：如果我的许可证流加载失败，我该怎么办？**  
答：请确认流中包含有效 `.lic` 文件的完整二进制数据，确保在 `SetLicense` 执行前流未被释放，并检查许可证是否与产品版本匹配。

**问：是否可以将许可证存储在数据库中？**  
答：可以。检索许可证 BLOB，使用字节数组创建 `MemoryStream`，并将其传递给 `SetLicense`。这样可将许可证从文件系统中移除，并利用现有的数据访问安全控制。

---

**最后更新：** 2026-06-06  
**测试环境：** GroupDocs.Annotation 23.9 for .NET  
**作者：** GroupDocs

## 相关教程

- [GroupDocs Annotation .NET 许可证设置 - 完整实现指南](/annotation/net/applying-licenses/set-license-from-file/)
- [GroupDocs.Annotation .NET 计量许可证设置 - 成本效益文档注释](/annotation/net/applying-licenses/set-metered-license/)
- [GroupDocs.Annotation .NET 许可证 - 完整设置与配置](/annotation/net/licensing-and-configuration/)