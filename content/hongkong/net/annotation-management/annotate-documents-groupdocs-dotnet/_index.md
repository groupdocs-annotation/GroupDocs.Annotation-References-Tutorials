---
categories:
- Document Processing
date: '2026-05-21'
description: 了解如何在 C# 中使用 GroupDocs Annotation .NET 為 PDF 檔案添加註解。本分步指南涵蓋設定、添加、更新以及管理
  PDF 註解，適用於法律、教育及企業等使用情境。
keywords:
- how to annotate pdf
- legal document annotation
- collaborative pdf markup
- create document review system
lastmod: '2026-05-21'
linktitle: GroupDocs Annotation .NET 指南
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to annotate PDF files with GroupDocs Annotation .NET in C#.
    This step‑by‑step guide covers setup, adding, updating, and managing PDF annotations
    for legal, education, and enterprise use cases.
  headline: How to Annotate PDF using GroupDocs Annotation .NET (C#) Guide
  type: TechArticle
- questions:
  - answer: Yes, the free trial provides full functionality for 30 days but adds evaluation
      watermarks to every output file. For any production deployment you must apply
      a temporary or full license to remove those watermarks.
    question: Can I use GroupDocs.Annotation .NET without a license?
  - answer: The library works with .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5,
      .NET 6, and .NET 7, making it suitable for both legacy Windows services and
      modern cross‑platform containers.
    question: Which .NET versions are supported by GroupDocs.Annotation?
  - answer: Pricing starts around $1,999 for a developer license and scales with the
      number of deployed applications. Check the [GroupDocs pricing page](https://purchase.groupdocs.com/buy)
      for the latest rates and volume discounts.
    question: How much does GroupDocs.Annotation .NET cost?
  - answer: Over **50 formats** are supported, including PDF, DOC/DOCX, PPT/PPTX,
      XLS/XLSX, JPEG, PNG, TIFF, and many more. PDF receives the most comprehensive
      feature set, including vector‑based shapes and OCR‑ready redaction.
    question: What document formats can I annotate with GroupDocs.Annotation?
  - answer: 'Yes. Provide the password when constructing the `Annotator`:'
    question: Can I annotate password‑protected PDFs?
  type: FAQPage
tags:
- GroupDocs
- Annotation
- C#
- PDF
- Document Management
title: 如何使用 GroupDocs Annotation .NET (C#) 進行 PDF 註解指南
type: docs
url: /zh-hant/net/annotation-management/annotate-documents-groupdocs-dotnet/
weight: 1
---

# 如何使用 GroupDocs Annotation .NET (C#) 為 PDF 加註

是否曾經需要以程式方式 **how to annotate pdf** 檔案，並且想知道哪個函式庫既強大又簡單？無論您是建立法律審查平台、電子學習系統，或是協作文件工作流程，GroupDocs.Annotation .NET 都提供可直接在 C# 程式碼中新增、編輯與刪除 PDF 加註的正式級 API。本指南將教您從初始設定到大規模文件庫的效能調校，完整實作功能完整的加註引擎所需的一切。

## 快速答案
- **什麼是向 PDF 新增文字註記的最快方法？** 使用 `Annotator` 載入文件，建立 `TextAnnotation`，設定其 `Box` 與 `Message`，然後呼叫 `Add()` —— 在一般頁面下可於一秒內完成。  
- **支援哪些 .NET 版本？** .NET Framework 4.6.1+、.NET Core 2.0+、.NET 5、.NET 6 以及 .NET 7。  
- **生產環境需要授權嗎？** 需要 — 完整或暫時授權會移除浮水印並解鎖全部功能。  
- **能在 4 GB 伺服器上處理 200 頁的 PDF 嗎？** 可以，透過批次處理與稍後示範的正確釋放模式即可。  
- **GroupDocs.Annotation 適合用於法律文件加註嗎？** 絕對適合 — 支援超過 50 種格式、細緻的權限控制，以及符合稽核需求的中繼資料。  

## 什麼是「how to annotate pdf」？
**「How to annotate pdf」** 指的是以程式方式為 PDF 檔案加入標記（例如註解、醒目標示、圖形或塗銷）的過程。使用 GroupDocs.Annotation .NET，您可以自動化此工作流程、將加註資料儲存於資料庫，並即時在 Web 或桌面檢視器中呈現結果。

## 為何使用 GroupDocs.Annotation 進行 PDF 標記？
GroupDocs.Annotation 支援 **超過 50 種輸入與輸出格式**，可處理高達 **500 MB** 的 PDF 而無需將整個檔案載入記憶體，且在每個請求建立獨立 `Annotator` 實例時提供 **執行緒安全** 的操作。相較於較輕量的僅支援 PDF 的函式庫，它亦允許使用相同 API 為 Word、PowerPoint 與影像檔案加註，顯著降低多格式平台的開發工作量。

## 真實案例應用：文件加註的發光點

了解業務情境有助於您選擇適當的加註類型。

- **法律文件審查** — 律師加入註解、醒目標示條款，並附加修訂歷史。GroupDocs.Annotation 會以使用者 ID、時間戳記以及可選的數位簽章追蹤每筆變更，以符合稽核要求。  
- **教育平台** — 教師可透過繪製圖形、添加便利貼或嵌入音訊回饋，直接在學生的 PDF 上批改作業。  
- **醫療文件** — 醫護人員在放射報告或病歷圖表上加註，同時保留符合 HIPAA 標準的中繼資料。  
- **軟體文件** — 技術寫手在 API 規格上協作，插入說明框與修訂備註，無需離開原始 PDF。  
- **金融服務** — 合規人員在貸款合約、風險評估與稽核追蹤上加註，然後匯出加註版本以作存檔。  

## 前置條件與設定：準備開發環境

### 系統需求
- **IDE**：Visual Studio 2019 或更新版本（Community 版亦可）。  
- **執行環境**：.NET Framework 4.6.1+ **或** .NET Core 2.0+（大型 PDF 建議配備 8 GB 記憶體）。  
- **權限**：對儲存加註 PDF 的資料夾具有寫入權限。  

### 知識前置條件
- 基本的 C# 語法與物件導向概念。  
- 熟悉 NuGet 套件管理。  
- 了解檔案 I/O（讀寫串流）。  

### 安裝 GroupDocs.Annotation .NET
您可以透過 NuGet 加入此函式庫。選擇符合您工作流程的方法。

**使用 NuGet 套件管理員主控台**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**使用 .NET CLI**（建議用於 CI/CD 流程）  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

> **專業提示：** 永遠固定版本（例如 `Install-Package GroupDocs.Annotation -Version 23.12`）。這可避免套件自動更新時產生意外的破壞性變更。請參閱 [GroupDocs 發行頁面](https://releases.groupdocs.com/annotation/net/) 了解最新發行版本。

### 授權選項：為您的專案挑選合適方案
- **免費試用** — 完整功能，並於 30 天內加上評估浮水印。  
- **暫時授權** — 於 30 天內移除浮水印，適合概念驗證。請參閱 [暫時授權頁面](https://purchase.groupdocs.com/temporary-license/)。  
- **完整授權** — 無限制的生產使用、優先支援，且不會有浮水印。可透過 [GroupDocs 商店](https://purchase.groupdocs.com/buy) 購買。  

### 基本專案設定
建立新的 C# 主控台或 ASP.NET 專案，並在安裝套件後加入以下 using 陳述式：
```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System.IO;
using System.Collections.Generic;

// Initialize Annotator with an input document path
string inputPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf");
```

> **重要提示：** 請將 `YOUR_DOCUMENT_DIRECTORY` 替換為 PDF 的絕對路徑。使用 `Path.Combine` 可確保在 Windows 與 Linux 上的路徑分隔符正確。

## 步驟教學：新增您的第一個加註

### 如何載入 PDF 文件以進行加註？
`Annotator` 類別是載入文件並管理所有加註操作的核心元件。正確載入 PDF 可確保函式庫在套用任何變更前，能讀取頁面尺寸、元資料與現有加註。  
使用 `Annotator` 建構子載入 PDF，傳入檔案路徑與可選的載入選項。此步驟會驗證檔案並建立可安全修改的記憶體表示，同時若提供密碼亦能處理加密檔案。

```csharp
try 
{
    using (Annotator annotator = new Annotator(inputPath))
    {
        // Your annotation code goes here
        Console.WriteLine("Document loaded successfully!");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

`try‑catch` 區塊可防止檔案遺失、PDF 損毀或不支援的格式，確保應用程式能優雅失敗而非直接崩潰。

### 如何在 PDF 中新增文字加註？
`TextAnnotation` 代表可放置於 PDF 頁面的便利貼式註解。新增方式包括建立物件、定義其位置、設定顯示訊息，最後透過 `Annotator` 插入文件。  
建立 `TextAnnotation` 物件，使用 `Box` 屬性定義其邊界矩形，設定可見的 `Message`，然後在 `Annotator` 上呼叫 `Add()`。加註會立即出現在指定頁面，若需要亦可透過顏色與不透明度設定自訂外觀。

```csharp
// Create a highlight annotation
HighlightAnnotation highlight = new HighlightAnnotation
{
    Box = new Rectangle(100, 100, 200, 20), // x, y, width, height
    CreatedOn = DateTime.Now,
    Message = "This section needs review",
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Please verify these numbers",
            RepliedOn = DateTime.Now
        }
    }
};

// Add the annotation to the document
annotator.Add(highlight);
```

> **為何 `Box` 屬性重要：** 矩形使用點 (1 point = 1/72 inch) 為單位，測量自頁面左下角。精確座標可讓您將註記放置在審閱者預期的位置。

### 如何在不覆寫原始檔的情況下儲存加註的 PDF？
儲存為新檔案可保留原始文件以供稽核追蹤與回溯情境。`Save` 方法會將所有變更（包括新加註與中繼資料）寫入指定路徑，同時不影響來源檔。  
在 `Annotator` 上呼叫 `Save()` 並提供新檔案路徑。此作法保留原始文件，對於稽核追蹤與回溯情境至關重要，若需轉換亦可選擇不同的輸出格式。

```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "annotated_document.pdf");
annotator.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

> **最佳實踐：** 將原始與加註版本分別存放於不同的版本控制資料夾。此策略可簡化法規遵循與變更追蹤。

## 進階加註技巧

### 如何在單一次操作中新增多種加註類型？
GroupDocs.Annotation 提供豐富的加註類別 — `HighlightAnnotation`、`StrikeoutAnnotation`、`PolylineAnnotation`、`RedactionAnnotation` 等。透過建立每個實例、設定屬性，並在儲存前將它們加入同一個 `Annotator`，即可減少 I/O 並保持文件狀態一致。  
建立每種加註類型的實例，設定其特定屬性（顏色、不透明度、點等），並依序加入同一個 `Annotator` 實例。呼叫 `Save()` 時，所有加註會一次寫入，確保原子更新並降低部分寫入的風險。

```csharp
// Text annotation for comments
TextAnnotation textNote = new TextAnnotation
{
    Box = new Rectangle(300, 200, 100, 30),
    Message = "Review required",
    CreatedOn = DateTime.Now,
    FontColor = 16711680, // Red color in RGB
    BackgroundColor = 16777215 // White background
};

// Arrow annotation to point out specific elements
ArrowAnnotation pointer = new ArrowAnnotation
{
    Box = new Rectangle(150, 150, 50, 50),
    Message = "Important calculation here",
    CreatedOn = DateTime.Now
};

// Add all annotations at once
annotator.Add(textNote);
annotator.Add(pointer);
```

### 如何更新既有加註的顏色或註解？
`GetById` 方法可依唯一識別碼取得特定加註，讓您僅修改所需欄位。取得物件後，可變更 `Color` 或 `Message` 等屬性，然後使用 `Update` 保存變更。  
使用 `GetById()` 依唯一 `Id` 取得加註，修改所需屬性（例如 `Color`、`Message`），再呼叫 `Update()`。此方式避免重新建立加註，並保留原始位置、版本歷史與任何回覆。

```csharp
// Get all annotations from the document
List<AnnotationBase> annotations = annotator.Get();

// Find and update a specific annotation
foreach (var annotation in annotations)
{
    if (annotation.Message.Contains("Review required"))
    {
        annotation.Message = "Review completed ✓";
        annotator.Update(annotation);
        break;
    }
}
```

> **效能說明：** 對於擁有數千筆加註的文件，請將加註 ID 快取於字典中，以避免線性搜尋。

## 常見問題與疑難排解

### 問題 1 – 「不支援的文件格式」
**直接答案：** 確認檔案副檔名是否在 GroupDocs.Annotation 支援的格式清單中；若不在，請先將檔案轉為 PDF，或使用能處理該格式的其他 GroupDocs 產品。  
**解決方案：**  
- 查看 [支援格式清單](https://docs.groupdocs.com/annotation/net/supported-document-formats/)  
- 使用 GroupDocs.Conversion 在加註前將不支援的檔案轉為 PDF。

```csharp
// Check if format is supported before processing
string extension = Path.GetExtension(inputPath).ToLower();
if (extension != ".pdf" && extension != ".docx" && extension != ".pptx")
{
    throw new NotSupportedException($"File format {extension} is not supported");
}
```

### 問題 2 – 加註出現在錯誤位置
**直接答案：** 確認使用正確的座標系統（原點在左下角），且頁面的旋轉中繼資料被正確處理。相應調整 `Box` 值。  
**解決方案：**

```csharp
// Always validate coordinates before adding annotations
private bool IsValidCoordinate(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

### 問題 3 – 大型文件的記憶體問題
**直接答案：** 將大型 PDF 分批處理，於每批完成後釋放 `Annotator`，並啟用串流模式以避免將整個檔案載入記憶體。  
**解決方案：**

```csharp
// Process large documents in chunks
using (Annotator annotator = new Annotator(inputPath))
{
    // Set memory-friendly options
    LoadOptions loadOptions = new LoadOptions
    {
        PreviewPageCount = 1 // Load pages on demand
    };
    
    // Process annotations in batches
    const int batchSize = 10;
    for (int i = 0; i < annotations.Count; i += batchSize)
    {
        var batch = annotations.Skip(i).Take(batchSize);
        foreach (var annotation in batch)
        {
            annotator.Add(annotation);
        }
        
        // Force garbage collection between batches for large documents
        if (i % 50 == 0)
        {
            GC.Collect();
            GC.WaitForPendingFinalizers();
        }
    }
}
```

## 效能最佳化技巧

### 如何有效率地批次處理數千份 PDF？
將加註請求收集至清單，對每份文件開啟單一 `Annotator`，套用所有變更，最後一次呼叫 `Save()`。此作法可減少 I/O 開銷、利用內部緩衝，並在大量工作負載下保持記憶體使用可預測。  
將加註請求收集至清單，對每份文件開啟單一 `Annotator`，套用所有變更，最後一次呼叫 `Save()`。此作法可減少 I/O 開銷並利用內部緩衝。

```csharp
// Inefficient approach (don't do this)
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
    annotator.Save(outputPath); // Saving after each annotation is expensive
}

// Efficient approach
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
}
annotator.Save(outputPath); // Save once at the end
```

### 處理數百頁 PDF 時，如何管理記憶體？
啟用 `LoadOptions` 的 `MemoryOptimization = true` 旗標，並逐頁處理。此設定會讓函式庫僅在記憶體中保留當前頁面，顯著降低超大型檔案的 RAM 佔用。

```csharp
// Use using statements to ensure proper disposal
using (var annotator = new Annotator(inputPath))
{
    // Your annotation code here
} // Annotator is automatically disposed, freeing memory
```

### 應如何快取常被存取的文件？
將序列化的加註 JSON 以文件 ID 為鍵存放於分散式快取（例如 Redis）中。使用者請求相同 PDF 時，直接取得快取的加註集合，而非重新從磁碟讀取檔案，從而降低延遲與 I/O 負載。

```csharp
// Cache document metadata to avoid reloading
private static readonly Dictionary<string, DocumentInfo> _documentCache = 
    new Dictionary<string, DocumentInfo>();

private DocumentInfo GetDocumentInfo(string path)
{
    if (!_documentCache.ContainsKey(path))
    {
        using (var annotator = new Annotator(path))
        {
            _documentCache[path] = annotator.GetDocumentInfo();
        }
    }
    return _documentCache[path];
}
```

## 生產環境最佳實踐

### 如何實作健全的錯誤處理與日誌記錄？
將每個 `Annotator` 操作包於 `try‑catch` 區塊，使用結構化日誌記錄器（Serilog、NLog）記錄例外，並包含文件路徑、使用者 ID 與堆疊追蹤。此方式可大幅簡化生產環境的除錯，並協助符合合規稽核需求。

```csharp
public async Task<bool> AddAnnotationSafely(string documentPath, AnnotationBase annotation)
{
    try
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath.Replace(".pdf", "_annotated.pdf"));
            return true;
        }
    }
    catch (Exception ex)
    {
        // Log the error (use your preferred logging framework)
        Console.WriteLine($"Annotation failed for {documentPath}: {ex.Message}");
        return false;
    }
}
```

### 如何驗證使用者提供的加註資料？
在建立加註物件前，先檢查傳入的 JSON 欄位（頁碼、矩形座標、加註類型）是否在允許範圍內。對超出範圍的座標回傳明確的 HTTP 400 錯誤，並提供有用的錯誤訊息。

```csharp
public bool ValidateAnnotationInput(AnnotationBase annotation)
{
    if (annotation == null)
        return false;
    
    if (string.IsNullOrWhiteSpace(annotation.Message))
        return false;
    
    if (annotation.Box.Width <= 0 || annotation.Box.Height <= 0)
        return false;
    
    return true;
}
```

### 如何在多使用者 Web 服務中確保執行緒安全？
每個請求都建立新的 `Annotator` 實例；切勿在多執行緒間共用同一實例。若需協調對共享檔案的存取，可使用 `SemaphoreSlim` 或檔案層級鎖定，以防止同時寫入。

```csharp
private readonly object _annotationLock = new object();

public void AddAnnotationThreadSafe(string documentPath, AnnotationBase annotation)
{
    lock (_annotationLock)
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath);
        }
    }
}
```

## 何時選擇 GroupDocs.Annotation 而非其他方案

**選擇 GroupDocs.Annotation 的情境** 包括：
- 跨格式支援（PDF、DOCX、PPTX、影像）。  
- 進階加註類型，如塗銷、手繪、以及自訂中繼資料。  
- 企業級授權、符合 SLA 的支援與定期安全更新。  

**若僅處理 PDF、預算受限或需開源堆疊**，可考慮較輕量的替代方案。

## 常見問與答

**Q: 是否可以在未取得授權的情況下使用 GroupDocs.Annotation .NET？**  
A: 可以，免費試用在 30 天內提供完整功能，但會在每個輸出檔案上加上評估浮水印。任何生產環境的部署皆必須套用暫時或完整授權以移除浮水印。

**Q: GroupDocs.Annotation 支援哪些 .NET 版本？**  
A: 此函式庫相容於 .NET Framework 4.6.1+、 .NET Core 2.0+、 .NET 5、 .NET 6 以及 .NET 7，適用於傳統 Windows 服務與現代跨平台容器。

**Q: GroupDocs.Annotation .NET 的費用是多少？**  
A: 價格約從 $1,999 美元起，視部署的應用程式數量而遞增。請參閱 [GroupDocs 定價頁面](https://purchase.groupdocs.com/buy) 了解最新價格與批量折扣。

**Q: 我可以使用 GroupDocs.Annotation 加註哪些文件格式？**  
A: 支援超過 **50 種格式**，包括 PDF、DOC/DOCX、PPT/PPTX、XLS/XLSX、JPEG、PNG、TIFF 等等。PDF 享有最完整的功能集，包含向量圖形與 OCR 準備的塗銷。

**Q: 能對受密碼保護的 PDF 加註嗎？**  
A: 可以。於建立 `Annotator` 時提供密碼：

```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your_password" };
using (Annotator annotator = new Annotator(inputPath, loadOptions))
{
    // Your annotation code here
}
```

**Q: 為何我的加註出現在錯誤的位置？**  
A: GroupDocs 使用笛卡爾座標系統，(0,0) 位於左下角，單位為點。錯誤的定位通常是因使用像素值或忽略頁面旋轉所致。將像素值轉換為點（在 96 DPI 下 1 像素 ≈ 0.75 點），並依旋轉中繼資料調整。

```csharp
// Correct approach - validate coordinates
private bool ValidateCoordinates(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

**Q: 如何從 PDF 取得現有的加註？**  
A: 呼叫 `Annotator` 實例的 `Get()` 方法；它會回傳包含所有加註物件、其 ID、類型與中繼資料的集合。

```csharp
using (Annotator annotator = new Annotator(inputPath))
{
    List<AnnotationBase> annotations = annotator.Get();
    foreach (var annotation in annotations)
    {
        Console.WriteLine($"Annotation: {annotation.Message}");
    }
}
```

**Q: 能以程式方式刪除特定加註嗎？**  
A: 可以。使用 `Delete(id)` 刪除單一加註，或 `DeleteAll()` 完全清空文件。也可在刪除前依類型過濾。 

```csharp
List<AnnotationBase> annotationsToDelete = annotator.Get()
    .Where(a => a.Message.Contains("obsolete"))
    .ToList();

foreach (var annotation in annotationsToDelete)
{
    annotator.Remove(annotation);
}
```

**Q: 如何更新加註屬性，例如顏色或訊息？**  
A: 取得加註後，修改 `Color` 或 `Message`，再呼叫 `Update()`。變更會在下一次 `Save()` 時持久化。

```csharp
var annotations = annotator.Get();
var targetAnnotation = annotations.FirstOrDefault(a => a.Id == specificId);
if (targetAnnotation != null)
{
    targetAnnotation.Message = "Updated message";
    annotator.Update(targetAnnotation);
}
```

**Q: 能為加註加入自訂中繼資料嗎？**  
A: 當然可以。大多數加註類別提供 `Replies` 集合，您可在其中存放鍵值對，以附加審閱者 ID、時間戳記或工作流程狀態。

```csharp
var annotation = new HighlightAnnotation
{
    // ... other properties
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Custom metadata: priority=high, category=legal",
            RepliedOn = DateTime.Now
        }
    }
};
```

**Q: GroupDocs.Annotation 是否支援在加註的 PDF 上加上數位簽章？**  
A: 雖然 Annotation 函式庫專注於標記，但您可與 GroupDocs.Signature .NET 結合，在加註後套用加密簽章，確保視覺與法律完整性。

**Q: 能將加註匯出為 JSON 或 XML 以供外部處理嗎？**  
A: 此函式庫未內建匯出功能，但您可自行使用 `System.Text.Json` 或 `XmlSerializer` 序列化加註物件。這讓整合外部稽核系統變得容易。

```csharp
List<AnnotationBase> annotations = annotator.Get();
string jsonAnnotations = JsonConvert.SerializeObject(annotations, Formatting.Indented);
File.WriteAllText("annotations.json", jsonAnnotations);
```

---

**最後更新：** 2026-05-21  
**測試環境：** GroupDocs.Annotation 23.12 for .NET  
**作者：** GroupDocs  

---

## 相關教學

- [GroupDocs Annotation .NET 教學 - 文件管理完整指南](/annotation/net/annotation-management/)
- [儲存 PDF 加註 .NET - 完整文件儲存指南](/annotation/net/document-saving/)
- [從 URL 載入 PDF .NET - GroupDocs.Annotation 完整指南](/annotation/net/document-loading-essentials/load-document-from-url/)