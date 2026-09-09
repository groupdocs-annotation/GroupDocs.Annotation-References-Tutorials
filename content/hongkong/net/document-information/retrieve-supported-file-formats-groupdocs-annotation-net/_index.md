---
categories:
- .NET Development
date: '2026-06-26'
description: 了解如何使用 GroupDocs.Annotation for .NET 取得格式、排除不支援的檔案格式問題，並套用最佳實務驗證。
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: 取得支援的檔案格式 .NET
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
title: 如何在 .NET 中使用 GroupDocs.Annotation 取得格式 – 完整指南
type: docs
url: /zh-hant/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# 如何在 .NET 中使用 GroupDocs.Annotation 取得格式

## 介紹

有沒有想過您的 .NET 應用程式實際上能處理哪些檔案格式來進行文件註解？**如何取得格式** 是許多開發人員在需要驗證使用者上傳或建立動態 UI 篩選器時會問的問題。清楚知道 GroupDocs.Annotation 實作支援哪些檔案格式不僅有幫助，更是建構不會因為意外檔案類型而崩潰的穩健應用程式的必要條件。

在本指南中，您將學會如何以程式方式取得並驗證 GroupDocs.Annotation for .NET 支援的檔案格式。我們會示範基本實作、教您如何將原始清單轉換為使用者友善的下拉選單，並提供實務除錯技巧，讓您能自信地處理任何文件格式情境。

**您將獲得的成果**

- 對 GroupDocs.Annotation 檔案格式能力的清晰認識  
- 可直接執行的程式碼，能取得並顯示所有支援的格式  
- 有效的快取、錯誤處理與授權邊緣案例策略  
- 生產環境等級的檔案類型驗證最佳實踐  

讓我們一起深入解決這個檔案格式謎題。

## 快速回答
- **「如何取得格式」是什麼意思？** 這是以程式方式詢問 GroupDocs.Annotation 能註解哪些副檔名。  
- **預設支援哪些主要格式？** 超過 50 種，包括 PDF、DOCX、XLSX、PPTX、JPEG、PNG 與 TIFF。  
- **取得完整清單是否需要授權？** 需要——有效的商業或試用授權會解鎖完整目錄。  
- **建議快取格式清單嗎？** 絕對建議；快取可避免不必要的呼叫並提升回應速度。  
- **如何以清單驗證上傳的檔案？** 將檔案副檔名與快取的支援副檔名集合做比對。

## 什麼是「如何取得格式」？
**如何取得格式** 指的是呼叫 GroupDocs.Annotation 的 API，以取得程式庫可註解的所有檔案類型集合。此操作會回傳一個唯讀的 `FileType` 物件清單，內含檔案副檔名與友善說明。

## 為什麼使用 GroupDocs.Annotation 進行格式偵測？
GroupDocs.Annotation 支援 **50+ 輸入與輸出格式**——包括 PDF、Microsoft Office（Word、Excel、PowerPoint）以及常見影像類型——同時能在不將整個檔案載入記憶體的情況下處理上百頁文件。這樣的量化能力使其成為企業級註解管線的可靠選擇。

## 前置條件與環境設定

### 您需要的項目
- **IDE：** Visual Studio 2019 或更新版本（Community 版亦可）  
- **目標框架：** .NET Framework 4.6.1 以上 或 .NET Core 2.0 以上  
- **C# 基礎：** 只要會寫「Hello World」程式，即可開始  

### 安裝 GroupDocs.Annotation
最簡單的方式是透過 NuGet。選擇符合您工作流程的方法：

**選項 1：Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**選項 2：.NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**小技巧：** 在受限的企業環境中，可自行從 [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) 下載套件，並在本機參考 DLL。

### 授權說明
- **開發與測試：** 使用免費試用版即可取得完整功能。  
- **延伸評估：** 取得 [temporary license](https://purchase.groupdocs.com/temporary-license/)（約 5 分鐘內發放）。  
- **正式上線：** 從 [GroupDocs Purchase](https://purchase.groupdocs.com/buy) 購買商業授權；單一授權可覆蓋所有部署情境。

## 如何以程式方式取得支援的檔案格式？

只要呼叫 `FileType.GetSupportedFileTypes()` 即可載入支援的格式，然後將結果轉換為使用者友善的清單，以供 UI 控制項或驗證使用。此方法回傳 `FileType` 物件的唯讀集合，每個物件皆包含副檔名與說明，使用上相當便利。

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

上述程式碼會查詢 GroupDocs.Annotation 內部的中繼資料，將副檔名按字母排序，並回傳可綁定至 UI 控制項或用於驗證的輕量集合。

### 定義錨點：FileType 類別
`FileType` 類別是 GroupDocs.Annotation 對單一文件格式的表示，公開 `Extension` 與 `Description` 等屬性。

### 步驟說明
1. **加入命名空間** – 在檔案頂部加入 `using GroupDocs.Annotation;`。  
2. **呼叫靜態方法** – `FileType.GetSupportedFileTypes()` 會回傳 `IEnumerable<FileType>`。  
3. **排序與投影** – 使用 LINQ 的 `OrderBy` 與 `Select` 來塑造顯示資料。  
4. **呈現** – 在 Console、MVC View 或 WinForms 下拉選單中迭代清單。

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## 如何在正式環境中快取格式清單？

快取可消除重複的中繼資料查詢，確保每次請求的回應時間在毫秒以下，這對高流量應用程式至關重要。將格式清單儲存在靜態欄位，並於首次使用時延遲載入，即可保證資料只被載入一次，之後在整個應用程式生命週期內重複使用。

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

**為什麼要快取？** 支援的格式集合在執行期間不會變動，於應用程式啟動時載入一次即可節省 CPU 時間，並避免每次呼叫都觸發授權檢查。

## 常見問題與解決方案

### 問題 1：「GroupDocs.Annotation not found」編譯錯誤
**直接答案：** 確認 NuGet 套件已正確安裝，清理並重新建置解決方案，且確保目標框架符合套件支援的版本。  

**根本原因分析** – 缺少參考、框架不相容，或公司內部的套件來源受限。

### 問題 2：格式清單為空或不完整
**直接答案：** 授權過期或設定錯誤常會截斷清單；重新套用有效的授權檔並重新啟動應用程式。  

**可能原因：**  
- 未載入授權檔 (`License.SetLicense("license.json")` 缺失)  
- NuGet 套件損毀  
- 缺少原生相依性  

**快速修復：**  
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

### 問題 3：頻繁呼叫導致效能下降
**直接答案：** 如「快取」章節所示，將結果快取；之後的呼叫即為 O(1)。  

**實作提示：** 將清單存於 `MemoryCache` 或靜態欄位，僅在升級程式庫時重新載入。

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

## 真實案例與使用情境

### 如何使用快取清單驗證檔案上傳？
使用者提交文件時，擷取檔案副檔名並與快取集合比對：

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

### 如何為 OpenFileDialog 產生動態檔案篩選字串？
從快取的副檔名產生對話框的 filter 字串，確保 UI 永遠反映程式庫的能力：

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

### 如何在批次資料夾掃描時跳過不支援的檔案？
遍歷目錄，使用 `IsSupported` 檢查每個檔案，僅處理符合條件的：

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

## 效能考量與最佳實踐

- **一次快取，隨處使用** – 在應用程式啟動時（如 `Program.cs` 或 `Startup.cs`）初始化 `FormatCache`。  
- **延遲載入** – 靜態屬性確保清單僅在首次需要時載入，避免不必要的啟動負擔。  
- **執行緒安全** – `??=` 空值合併運算子在大多數單執行緒情境下安全；若為高併發應用，建議使用 `Lazy<IReadOnlyList<FileType>>` 包裝快取。  
- **釋放註解物件** – 雖然格式清單本身不需釋放，但任何 `Annotation` 實例應以 `using` 包裝，以釋放原生資源。  

### 授權問題的錯誤處理模式
將格式取得包在 try‑catch 中，特別捕捉 `LicenseException`，並記錄清晰訊息：

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

## 除錯指南

### 步驟 1：驗證安裝
執行 `dotnet list package` 或檢查 NuGet 主控台輸出是否有警告。  

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

### 步驟 2：檢查授權狀態
確保在任何 API 呼叫前先執行 `License.SetLicense("path/to/license.json")`。  

### 步驟 3：診斷環境限制
- 確認 .NET 執行環境版本符合程式庫需求。  
- 確認執行程序對 GroupDocs.Annotation 使用的暫存資料夾具有讀寫權限。  

## 常見問答

**Q: GroupDocs.Annotation 實際支援哪些檔案格式？**  
A: 程式庫支援 **超過 50 種格式**，包括 PDF、DOCX、XLSX、PPTX、JPEG、PNG、TIFF 等等。執行範例程式碼即可取得您授權下的完整清單。

**Q: 為什麼取得的支援格式比預期少？**  
A: 多半是授權問題——試用期過期或授權檔載入失敗。重新套用有效授權並重新啟動應用程式。

**Q: 能否在不取得整個清單的情況下檢查單一格式？**  
A: 沒有直接的 `IsSupported` 方法；建議一次快取完整清單，之後在本機查詢以獲得快速回應。

**Q: 高流量 Web 應用該如何處理格式檢查？**  
A: 在應用程式啟動時（例如 `ConfigureServices`）初始化格式快取，並將其存於靜態或 Singleton 服務中，從而消除每次請求的額外開銷。

**Q: 若 GetSupportedFileTypes() 拋出例外該怎麼辦？**  
A: 例外通常源於授權或安裝損毀。檢查套件完整性、必要時重新安裝，並確保授權檔可被存取。

## 結論

現在您已掌握使用 GroupDocs.Annotation 在 .NET 中 **如何取得格式** 的完整、可投入生產的策略。從單行 API 呼叫到穩健快取、錯誤處理與 UI 整合，您可以自信地驗證上傳、產生動態檔案篩選，並建構可擴展的註解管線。

**後續步驟：**  
- 探索 [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/) 以深入了解更多註解功能。  
- 若遇到邊緣案例，請前往 [Support Forum](https://forum.groupdocs.com/c/annotation/) 加入社群討論。  
- 嘗試將格式驗證與自訂業務規則（如大小限制、安全掃描）結合，進一步強化文件工作流程。

## 參考資源
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

---

**最後更新：** 2026-06-26  
**測試環境：** GroupDocs.Annotation 25.4.0 for .NET  
**作者：** GroupDocs  

---

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

## 相關教學

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)