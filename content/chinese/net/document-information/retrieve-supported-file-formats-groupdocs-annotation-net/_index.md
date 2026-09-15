---
categories:
- .NET Development
date: '2026-06-26'
description: 了解如何使用 GroupDocs.Annotation for .NET 检索格式，排除不受支持的文件格式问题，并应用最佳实践验证。
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: 检索受支持的文件格式 .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: 如何在 .NET 中使用 GroupDocs.Annotation 检索格式 – 完整指南
type: docs
url: /zh/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# 如何在 .NET 中使用 GroupDocs.Annotation 检索格式

## 介绍

是否曾经想过您的 .NET 应用程序实际上可以处理哪些文件格式进行文档注释？**How to retrieve formats** 是许多开发者在需要验证用户上传或构建动态 UI 过滤器时会提出的问题。准确了解您的 GroupDocs.Annotation 实现支持的文件格式不仅有帮助——它对于构建永不因意外文件类型而崩溃的稳健应用程序至关重要。

在本指南中，您将学习如何使用 GroupDocs.Annotation for .NET 以编程方式检索并验证受支持的文件格式。我们将演示基本实现，展示如何将原始列表转换为用户友好的下拉框，并提供真实场景的故障排查技巧，让您能够自信地处理任何文档格式情况。

**您将获得的收获**

- 对 GroupDocs.Annotation 文件格式能力有清晰的了解  
- 可直接运行的代码，检索并显示所有受支持的格式  
- 用于缓存、错误处理和授权边缘情况的成熟策略  
- 生产级文件类型验证的最佳实践建议  

让我们深入探讨，一次性解决文件格式难题。

## 快速答案
- **“how to retrieve formats” 是什么意思？** 这是以编程方式询问 GroupDocs.Annotation 能够注释哪些扩展名的方式。  
- **开箱即支持的主要格式有哪些？** 超过 50 种，包括 PDF、DOCX、XLSX、PPTX、JPEG、PNG 和 TIFF。  
- **获取完整列表是否需要许可证？** 是的——有效的商业或试用许可证会解锁完整目录。  
- **是否推荐缓存格式列表？** 绝对推荐；缓存可避免不必要的调用并提升响应时间。  
- **如何根据列表验证上传文件？** 将文件的扩展名与缓存的受支持扩展集合进行比较。

## 什么是 “how to retrieve formats”？
**How to retrieve formats** 指调用 GroupDocs.Annotation 的 API，获取库能够注释的所有文件类型的集合。此操作返回只读的 `FileType` 对象列表，包含文件扩展名和友好的描述。

## 为什么使用 GroupDocs.Annotation 进行格式检测？
GroupDocs.Annotation 支持 **50+ 输入和输出格式**——包括 PDF、Microsoft Office（Word、Excel、PowerPoint）以及常见图像类型——在处理数百页文档时无需将整个文件加载到内存中。这种量化能力使其成为企业级注释流水线的可靠选择。

## 前置条件和环境设置

### 您需要的内容
- **IDE：** Visual Studio 2019 或更高（Community 版亦可）  
- **目标框架：** .NET Framework 4.6.1 + 或 .NET Core 2.0 +   
- **C# 基础：** 能写出 “Hello World” 程序即可  

### 安装 GroupDocs.Annotation
最简方式是通过 NuGet。选择符合您工作流的方法：

**Option 1: Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Option 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Pro tip:** 在受限的企业环境中，可手动从 [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) 下载包并本地引用 DLL。

### 简化授权
- **开发与测试：** 使用免费试用版获取完整功能。  
- **扩展评估：** 获取 [temporary license](https://purchase.groupdocs.com/temporary-license/)（约 5 分钟内发放）。  
- **生产环境：** 从 [GroupDocs Purchase](https://purchase.groupdocs.com/buy) 购买商业许可证；单一许可证覆盖所有部署场景。

## 如何以编程方式检索受支持的文件格式？

使用单行调用 `FileType.GetSupportedFileTypes()` 加载受支持的格式，然后将结果转换为可在 UI 控件中显示或用于验证的用户友好列表。该方法返回只读的 `FileType` 集合，每个对象包含扩展名和描述，使用起来非常方便。

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

上述代码查询 GroupDocs.Annotation 的内部元数据，按字母顺序排序扩展名，并返回一个轻量级集合，可绑定到 UI 控件或用于验证。

### 定义锚点：FileType 类
`FileType` 类是 GroupDocs.Annotation 对单一文档格式的表示，公开 `Extension` 和 `Description` 等属性。  

### 步骤演练
1. **Add the namespace** – 在文件顶部添加 `using GroupDocs.Annotation;`。  
2. **Call the static method** – `FileType.GetSupportedFileTypes()` 返回 `IEnumerable<FileType>`。  
3. **Sort and project** – 使用 LINQ 的 `OrderBy` 和 `Select` 形成用于显示的数据。  
4. **Render** – 在控制台、MVC 视图或 WinForms 下拉框中遍历列表。

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## 如何在生产环境中缓存格式列表？

缓存消除重复的元数据查找，并保证每次请求的子毫秒响应时间，这在高流量应用中至关重要。通过将格式列表存储在静态字段并在首次使用时惰性加载，确保数据仅在应用启动时加载一次，随后在整个应用生命周期内高效复用。

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Why cache?** 支持的格式集合在运行时永不改变，单次在应用启动时加载即可节省 CPU 周期，并避免每次调用都进行潜在的授权检查。

## 常见问题及解决方案

### 问题 1：“GroupDocs.Annotation 未找到” 编译错误
**Direct answer:** 验证 NuGet 包已正确安装，清理并重新生成解决方案，并确保目标框架匹配包支持的版本。  

**Root cause analysis** – 缺少引用、框架不兼容或企业包源限制。

### 问题 2：格式列表为空或不完整
**Direct answer:** 过期或配置错误的许可证常导致列表被截断；请重新应用有效的许可证文件并重启应用。  

**Possible causes:**  
- 未加载许可证文件 (`License.SetLicense("license.json")` 缺失)  
- NuGet 包损坏  
- 缺少本机依赖  

**Quick fix:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### 问题 3：频繁调用导致性能下降
**Direct answer:** 如 “How to cache” 部分所示缓存结果；后续调用将变为 O(1)。  

**Implementation tip:** 将列表存入 `MemoryCache` 或静态字段，仅在升级库时刷新。

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## 实际应用和使用案例

### 如何使用缓存列表验证文件上传？
用户提交文档时，提取文件扩展名并与缓存集合进行比较：

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### 如何为 OpenFileDialog 生成动态文件过滤器？
从缓存的扩展名生成对话框的过滤字符串，确保 UI 始终反映库的能力：

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### 如何在批量文件夹扫描中跳过不支持的文件？
遍历目录，使用 `IsSupported` 检查每个文件，仅处理有效文件：

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## 性能考虑因素和最佳实践

- **Cache once, reuse everywhere** – 在应用启动时（如 `Program.cs` 或 `Startup.cs`）初始化 `FormatCache`。  
- **Lazy loading** – 静态属性确保列表仅在首次需要时加载，避免不必要的启动开销。  
- **Thread safety** – 空合并运算符 (`??=`) 对大多数单线程场景安全；高并发场景可将缓存包装在 `Lazy<IReadOnlyList<FileType>>` 中。  
- **Dispose annotation objects** – 虽然格式列表本身无需释放，但任何 `Annotation` 实例应使用 `using` 语句包装，以释放本机资源。  

### 许可证问题的错误处理模式
将格式检索包装在 try‑catch 块中，专门捕获 `LicenseException` 并记录清晰的错误信息：

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## 故障排查指南

### 步骤 1：验证安装
运行 `dotnet list package` 或检查 NuGet 控制台输出是否有警告。  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### 步骤 2：检查许可证状态
确保在任何 API 调用之前执行 `License.SetLicense("path/to/license.json")`。  

### 步骤 3：诊断环境约束
- 确认 .NET 运行时版本符合库的要求。  
- 验证进程对 GroupDocs.Annotation 使用的临时文件夹具有读写权限。  

## 常见问题

**Q: GroupDocs.Annotation 实际支持哪些文件格式？**  
A: 库支持 **50 多种格式**，包括 PDF、DOCX、XLSX、PPTX、JPEG、PNG、TIFF 等。运行示例代码即可获取针对您许可证的完整列表。

**Q: 为什么得到的受支持格式比预期少？**  
A: 通常是授权问题——试用期已过或许可证文件加载不正确。请重新应用有效许可证并重启应用。

**Q: 能否在不获取完整列表的情况下检查单一格式？**  
A: 没有直接的 “IsSupported” 方法；推荐的做法是一次性缓存完整列表，然后在本地进行快速查询。

**Q: 在高流量 Web 应用中应如何处理格式检查？**  
A: 在应用启动时（如 `ConfigureServices`）初始化格式缓存，并将其存放在静态或单例服务中，以消除每次请求的开销。

**Q: 如果 GetSupportedFileTypes() 抛出异常怎么办？**  
A: 异常通常源于授权或安装损坏。请检查包完整性，必要时重新安装，并确保许可证文件可访问。

## 结论

您现在拥有一套完整的、可投入生产的 **how to retrieve formats** 策略，适用于 .NET 中的 GroupDocs.Annotation。从单行 API 调用到稳健的缓存、错误处理以及 UI 集成，您可以自信地验证上传、生成动态文件过滤器，并构建可扩展的注释流水线。

**下一步：**  
- 浏览 [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)，深入了解注释功能。  
- 如遇边缘案例，可前往 [Support Forum](https://forum.groupdocs.com/c/annotation/) 与社区交流。  
- 尝试将格式验证与自定义业务规则（如大小限制、安全扫描）结合，以进一步强化文档工作流。

## 资源
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/net/)
- [Free Trial](https://releases.groupdocs.com/annotation/net/)
- [temporary license](https://purchase.groupdocs.com/temporary-license/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy)
- [Purchase Licensing](https://purchase.groupdocs.com/buy)
- [Documentation](https://docs.groupdocs.com/annotation/net/)
- [API Reference](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
- [Community Support](https://forum.groupdocs.com/c/annotation/)

**最后更新：** 2026-06-26  
**测试环境：** GroupDocs.Annotation 25.4.0 for .NET  
**作者：** GroupDocs  

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## 相关教程

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)