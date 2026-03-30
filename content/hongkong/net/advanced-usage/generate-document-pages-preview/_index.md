---
categories:
- Document Processing
date: '2026-03-30'
description: 學習如何在 .NET 中使用 GroupDocs.Annotation 建立 PDF 縮圖。逐步指南涵蓋預覽產生、錯誤處理與自訂。
keywords: create pdf thumbnail, GroupDocs.Annotation preview, document pages preview
  C#, .NET document preview API, create PDF thumbnail preview
lastmod: '2026-03-30'
linktitle: Create PDF Thumbnail .NET
second_title: GroupDocs.Annotation .NET API
tags:
- GroupDocs.Annotation
- document-preview
- NET-API
- PDF-processing
title: 使用 GroupDocs.Annotation for .NET 建立 PDF 縮圖
type: docs
url: /zh-hant/net/advanced-usage/generate-document-pages-preview/
weight: 12
---

# 使用 GroupDocs.Annotation for .NET 建立 PDF 縮圖

為文件的每一頁產生 **create pdf thumbnail** 圖像是一種提升任何檔案總管式介面使用者體驗的實用方法。在本教學中，您將會看到如何使用 GroupDocs.Annotation for .NET 為 PDF、Word 檔案、試算表和簡報產生高品質的縮圖。我們將逐步說明所需的設定、核心程式碼，以及一些可直接投入生產的技巧，讓您在數分鐘內即可交付可靠的預覽功能。

## 快速解答
- **What does “create pdf thumbnail” mean?** 它表示將 PDF（或其他支援格式）的每一頁渲染為圖像檔案，例如 PNG 或 JPEG。  
- **Which library handles the conversion?** GroupDocs.Annotation for .NET 提供簡單的 `GeneratePreview` API。  
- **Do I need a license?** 提供免費試用版，但在正式環境中需要商業授權。  
- **Can I preview non‑PDF formats?** 是的 – 支援 DOCX、XLSX、PPTX 以及更多其他格式。  
- **Is async generation possible?** 絕對可以；您可以將預覽呼叫包在 `Task.Run` 中，或使用自己的非同步模式。

## PDF 縮圖是什麼以及為何要建立它？
PDF 縮圖是一種小型點陣圖（通常為 PNG 或 JPEG），用於表示原始文件的單一頁面。縮圖讓使用者能在不開啟完整檔案的情況下快速瀏覽內容，使文件瀏覽器、線上學習平台以及法律案件管理系統更為流暢且直觀。

## 何時使用文件預覽

- **Document Management Systems** – 透過快速視覺導覽大型文件庫。  
- **Collaboration Platforms** – 團隊成員能一眼辨識正確檔案。  
- **E‑learning Applications** – 為學習者提供課程教材的預覽。  
- **Legal Software** – 在不載入大型 PDF 的情況下快速瀏覽案件檔案。  
- **Content Management** – 為可搜尋的媒體畫廊產生縮圖。  

GroupDocs.Annotation 會自動處理所有主要辦公格式的繁重工作，您無需額外的轉換器。

## 前置條件

| 需求 | 說明 |
|-------------|---------|
| **GroupDocs.Annotation for .NET** | 透過 NuGet 安裝或從 [download page](https://releases.groupdocs.com/annotation/net/) 下載。 |
| **.NET runtime** | .NET Framework 4.6.1+ 或 .NET Core 2.0+。 |
| **C# basics** | 熟悉 `using` 陳述式、檔案 I/O 與例外處理。 |

### 透過 NuGet 安裝 GroupDocs.Annotation
```powershell
Install-Package GroupDocs.Annotation
```

## 匯入命名空間
```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

## 如何建立 PDF 縮圖 – 步驟說明指南

### 步驟 1：初始化 Annotator 並定義預覽選項
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_{pageNumber}.png");
    return File.Create(pagePath);
});
```
- `using` 區塊可確保所有非受控資源皆被釋放。  
- 傳遞給 `PreviewOptions` 的委派告訴 API 每頁圖像的寫入位置。

### 步驟 2：設定預覽參數（格式、頁面、尺寸）並產生縮圖
```csharp
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
annotator.Document.GeneratePreview(previewOptions);
```
- **Why PNG?** PNG 能保留清晰的文字渲染，特別適合文字密集的頁面。  
- 調整 `PageNumbers` 以僅處理您需要的頁面。

#### 自訂預覽頁面尺寸
```csharp
previewOptions.Width = 800;  // Increase width for sharper images
previewOptions.Height = 1000; // Adjust height proportionally
```
增大尺寸可提升可讀性，但同時也會增加檔案大小。

#### 當頻寬受限時切換至較小的格式（JPEG）
```csharp
previewOptions.PreviewFormat = PreviewFormats.JPEG;
```

#### 處理部分頁面以加快結果產出
```csharp
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5 };
```

### 步驟 3：實作健全的錯誤處理
```csharp
try 
{
    annotator.Document.GeneratePreview(previewOptions);
    Console.WriteLine("Preview generation completed successfully!");
}
catch (Exception ex)
{
    Console.WriteLine($"Error generating preview: {ex.Message}");
    // Log the error appropriately
}
```
將呼叫包在 `try‑catch` 區塊中，可向使用者或日誌系統顯示有意義的訊息。

### 步驟 4：在處理前驗證輸入檔案
```csharp
if (!File.Exists(inputPath))
{
    throw new FileNotFoundException($"Document not found: {inputPath}");
}
```
務必確認來源檔案是否存在，以避免執行時當機。

### 步驟 5：為正式環境產生唯一且帶時間戳記的檔名
```csharp
var timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
var pagePath = Path.Combine(outputDirectory, $"{documentName}_{timestamp}_page_{pageNumber}.png");
```
時間戳記的檔名可防止覆寫舊有預覽，且讓清理工作更簡單。

### 步驟 6（可選）：非同步執行預覽產生
```csharp
await Task.Run(() => annotator.Document.GeneratePreview(previewOptions));
```
將工作卸載至背景執行緒，可保持 UI 的回應性。

## 常見問題與解決方案

| 問題 | 徵兆 | 解決方案 |
|-------|---------|-----|
| **File not found** | `FileNotFoundException` | 使用 `File.Exists` 檢查路徑（參見步驟 4）。 |
| **Blurry images** | Low resolution thumbnails | 增加 `Width`/`Height` 或改用 PNG。 |
| **Large output files** | PNG files consume too much storage | 使用 `PreviewFormats.JPEG` 或縮小尺寸。 |
| **Slow processing on huge docs** | Timeout or UI freeze | 僅處理所需頁面、批次文件，或使用非同步（步驟 6）。 |

## 生產環境最佳實踐

1. **Memory Management** – 總是將 `Annotator` 包在 `using` 陳述式中。  
2. **Batch Processing** – 將文件排入佇列，分小批次處理，以降低記憶體使用。  
3. **Caching** – 將產生的縮圖儲存在 CDN 或本機快取，以避免重複產生相同預覽。  
4. **Security** – 在開啟使用者提供的檔案前，清理檔案路徑並執行適當的存取控制。  

## 常見問答

**Q: GroupDocs.Annotation for .NET 是否相容所有 .NET 版本？**  
A: 是的。它支援 .NET Framework 4.6.1+、.NET Core 2.0+、.NET 5/6 以及 .NET Standard 2.0。

**Q: 我可以自訂預覽圖像上註解的外觀嗎？**  
A: 當然可以。可在呼叫 `GeneratePreview` 前，透過 `AnnotationAppearance` 類別設定註解樣式（顏色、字型、線寬）。

**Q: API 能處理受密碼保護的 PDF 嗎？**  
A: 可以。建立 `Annotator` 實例時提供密碼即可。

**Q: 我可以從哪裡下載免費試用版？**  
A: 從 [發佈頁面](https://releases.groupdocs.com/annotation/net/) 下載。

**Q: 我該如何取得社群支援？**  
A: 活躍的 GroupDocs.Annotation 論壇可於 [此連結](https://forum.groupdocs.com/c/annotation/10) 取得。

**Q: 我可以為非 PDF 格式（如 DOCX）產生縮圖嗎？**  
A: 相同的預覽工作流程亦適用於 DOCX、XLSX、PPTX 以及 GroupDocs.Annotation 支援的其他多種格式。

---

**Last Updated:** 2026-03-30  
**Tested With:** GroupDocs.Annotation 23.9 for .NET  
**Author:** GroupDocs