---
categories:
- Document Processing
date: '2026-08-25'
description: 了解如何在 .NET 中移除 PDF 註釋並建立高品質的 PDF 縮圖。使用 GroupDocs.Annotation 的乾淨預覽產生步驟說明。
keywords:
- remove pdf annotations
- generate pdf thumbnails
- render pdf as image
- create pdf thumbnails
- pdf thumbnail generation
lastmod: '2026-08-25'
linktitle: 產生無註釋的預覽
og_description: 使用 GroupDocs.Annotation 在 .NET 中移除 PDF 註釋並產生清晰的 PDF 縮圖。本指南僅需幾個步驟即可展示乾淨的預覽工作流程。
og_image_alt: 'Developer guide: remove PDF annotations and create thumbnails using
  GroupDocs.Annotation for .NET'
og_title: 如何在 .NET 中移除 PDF 註釋並產生縮圖
schemas:
- author: GroupDocs
  dateModified: '2026-08-25'
  description: Learn how to remove PDF annotations and create high‑quality PDF thumbnails
    in .NET. Step‑by‑step guide with clean preview generation using GroupDocs.Annotation.
  headline: How to remove PDF annotations and generate thumbnails in .NET
  type: TechArticle
- description: Learn how to remove PDF annotations and create high‑quality PDF thumbnails
    in .NET. Step‑by‑step guide with clean preview generation using GroupDocs.Annotation.
  name: How to remove PDF annotations and generate thumbnails in .NET
  steps:
  - name: initialize the annotator
    text: '`Annotator` is the entry point for all operations on a PDF file. It opens
      the document, manages resources, and exposes preview functionality. > **Pro
      tip:** Validate the file path and enforce security checks when handling user‑uploaded
      PDFs.'
  - name: configure preview options
    text: '`PreviewOptions` defines how the preview is rendered. Setting `RenderAnnotations
      = false` disables all markup layers, while the `OutputFormat` and `Dpi` properties
      control image quality. **Key points** - **File naming** – the lambda inside
      `GeneratePreview` (shown later) creates a unique PNG file fo'
  - name: generate the clean preview
    text: '`GeneratePreview` renders the images based on the options you defined and
      writes them to the target folder. Your clean thumbnail files (`page_1.png`,
      `page_2.png`, …) are now ready for use in any UI component.'
  type: HowTo
- questions:
  - answer: Yes. The library also supports DOCX, XLSX, PPTX, and many image formats,
      applying the same preview workflow regardless of source type.
    question: Can I use GroupDocs.Annotation for .NET with formats other than PDF?
  - answer: Absolutely. It runs on .NET Framework, .NET Core, and .NET 5/6+, so you
      can target modern cross‑platform applications.
    question: Is GroupDocs.Annotation for .NET compatible with .NET Core?
  - answer: It does, but when `RenderAnnotations = false` those tools are ignored
      for preview generation, ensuring a clean image.
    question: Does the library provide annotation editing tools?
  - answer: Yes. Just make sure the web server has appropriate file‑system permissions
      and consider streaming the PNG directly to the client to avoid temporary files.
    question: Can I integrate this into an ASP.NET web app?
  - answer: PNG delivers lossless quality, while JPEG reduces file size by up to 80
      %—choose based on your visual fidelity versus bandwidth needs.
    question: Which image format should I pick for thumbnail galleries?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- pdf-preview
- document-collaboration
- annotations
- net-development
- pdf thumbnails
title: 如何在 .NET 中移除 PDF 註釋並產生縮圖
type: docs
---

# 如何在 .NET 中移除 PDF 註解並產生縮圖

在許多以文件為中心的應用程式中，您需要顯示 PDF 的 **乾淨預覽**，同時隱藏使用者添加的任何標記。本教學將示範如何 **移除 PDF 註解** 以及 **產生 PDF 縮圖**，在 .NET 中輸出僅包含原始文件內容的清晰 PNG 圖像。完成本指南後，您將擁有可在 .NET 5/6+、.NET Core 以及傳統 .NET Framework 上運作的可投入生產的程式碼片段。

## 快速回答
- **`RenderAnnotations = false` 的作用是什麼？** 它告訴 GroupDocs.Annotation 在渲染預覽時跳過所有標記，因而輸出僅包含原始 PDF 圖形。  
- **哪種影像格式能提供最佳的縮圖品質？** PNG 保留 100 % 的來源像素；JPEG 可將檔案大小縮減最多 80 %，但會產生壓縮雜訊。  
- **我可以為縮圖集合挑選特定頁面嗎？** 可以 – 設定 `PreviewOptions.PageNumbers` 為您需要的頁碼索引。  
- **生產環境是否需要授權？** 商業授權可解鎖無限頁數、移除評估水印，並提供優先支援。  
- **這在 .NET Core 及之後的版本可用嗎？** 當然可以 – GroupDocs.Annotation 支援 .NET Framework、.NET Core 以及 .NET 5/6+。

## 什麼是移除 PDF 註解？
**移除 PDF 註解是指在渲染文件時不包含任何評論、標記或繪圖層。** 這會產生一張純淨的影像，呈現作者的原始意圖，適合公開分享或法律審查。透過省略註解層，您可以保持原始視覺版面不變，同時仍保留 PDF 內的標記資料以供日後使用。

## 為何要產生不含註解的預覽？
產生不含註解的預覽可讓使用者清晰看到原始文件，沒有分散注意力的註記或標記。這種乾淨的呈現可加速決策、保護機密評論，並確保任何後續處理（例如列印或 OCR）皆在未被修改的內容上執行。

您將獲得一個乾淨的視覺呈現，具備以下優點：

- **加速審批流程** – 審閱者看到原始版面而不受干擾，審查時間可縮短最多 30 %。  
- **隱藏私人筆記** – 註解仍保留在原始 PDF 中，但不會出現在公開的縮圖畫廊裡。  
- **降低頻寬需求** – 單頁的 PNG 縮圖通常小於 200 KB，遠低於傳送完整 PDF。  
- **提升列印品質** – 當預覽用於列印就緒的資產時，零散的標記不會導致意外的列印錯誤。

## 前置條件
- **GroupDocs.Annotation for .NET** – 從官方 [releases page](https://releases.groupdocs.com/annotation/net/) 安裝。  
- **授權（可選但建議）** – 透過 [purchase page](https://purchase.groupdocs.com/buy) 購買完整授權，或向 [temporary license](https://purchase.groupdocs.com/temporary-license/) 申請臨時授權。  
- 基本的 C#/.NET 知識。  
- PDF 檢視器（例如 Adobe Acrobat Reader）以驗證產生的縮圖。

## 匯入命名空間
加入必要的 `using` 陳述式，以便使用註解 API：

`Annotation` 命名空間提供載入 PDF 與設定預覽選項的核心類別。  

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System.IO;
```

## 如何在不含註解的情況下建立 PDF 縮圖
載入來源 PDF，停用註解渲染，並將每頁匯出為 PNG 圖像。工作流程相當簡單：建立 `Annotator`、以 `RenderAnnotations = false` 設定 `PreviewOptions`、視需要限制頁面，最後呼叫 `GeneratePreview`。此方法可在一次處理中產生乾淨的縮圖，無需額外的後處理。

### 步驟 1：初始化 annotator
`Annotator` 是對 PDF 檔案執行所有操作的入口點。它會開啟文件、管理資源，並提供預覽功能。

```csharp
using (var annotator = new Annotator("sample.pdf"))
{
```

> **專業提示：** 在處理使用者上傳的 PDF 時，請驗證檔案路徑並執行安全檢查。

### 步驟 2：設定預覽選項
`PreviewOptions` 定義預覽的渲染方式。設定 `RenderAnnotations = false` 會停用所有標記層，而 `OutputFormat` 與 `Dpi` 屬性則控制影像品質。

```csharp
    var previewOptions = new PreviewOptions
    {
        OutputFormat = PreviewOutputFormat.Png,   // lossless PNG for crisp thumbnails
        Dpi = 150,                               // 150 DPI balances quality and size
        RenderAnnotations = false,               // core flag that removes annotations
        PageNumbers = new[] { 1, 2, 3 }           // generate thumbnails for the first three pages
    };
```

**重點**

- **檔案命名** – `GeneratePreview` 內的 lambda（稍後示範）會為每頁建立唯一的 PNG 檔案。  
- **格式選擇** – PNG 保留每個像素；若需較小的檔案，可改用 `Jpeg`。  
- **頁面選擇** – 明確指定要 **建立 PDF 縮圖** 的頁面，以節省 CPU 時間。  

### 步驟 3：產生乾淨的預覽
`GeneratePreview` 依據您定義的選項渲染影像，並寫入目標資料夾。

```csharp
    annotator.GeneratePreview(previewOptions, (pageNumber, stream) =>
    {
        var filePath = Path.Combine("thumbnails", $"page_{pageNumber}.png");
        using (var fileStream = File.Create(filePath))
        {
            stream.CopyTo(fileStream);
        }
    });
}
```

您的乾淨縮圖檔案（`page_1.png`、`page_2.png`、…）現在已可在任何 UI 元件中使用。

## 真實應用中的常見使用情境
- **文件管理系統** – 顯示乾淨的縮圖格子，同時為內部審閱者保留一個帶註解的版本。  
- **法律平台** – 向客戶展示原始合約，避免洩露律師註記。  
- **線上學習平台** – 顯示作業預覽，教師的評分註解則保持私密。  
- **行銷工作流程** – 為手冊產生預覽圖像，去除內部審核標記。

## 效能考量
- **批次處理** – 在背景工作者中排隊多個 PDF，以分攤 I/O 開銷。  
- **快取** – 首次上傳後將產生的縮圖存入 CDN 快取；之後的請求可即時命中快取。  
- **頁數限制** – 若 PDF 超過 500 頁，將預覽限制在前 5 頁，以在一般 2.5 GHz 伺服器上將每份文件的 CPU 使用時間控制在 2 秒以內。  
- **檔案格式取捨** – PNG 提供無損品質；JPEG 可將儲存空間減少最多 80 %，且在縮圖畫廊中仍具可接受的視覺真實度。

## 常見問題排除
- **未產生縮圖** – 確認輸出資料夾已存在且應用程式具有寫入權限；同時檢查來源 PDF 是否損毀。  
- **影像品質低** – 提高 `Dpi` 數值（例如 300），或若目前使用 JPEG，改為 PNG。  
- **記憶體使用量高** – 將頁面分成較小批次處理，或啟用串流模式（`annotator.Stream = true`），以避免一次載入整個 PDF。  
- **路徑問題** – 總是使用 `Path.Combine()` 來組合檔案路徑，以確保跨平台相容性。

## 生產環境最佳實踐
- 將預覽產生程式碼包在 `try‑catch` 區塊中，以優雅地處理 I/O 與權限錯誤。  
- 使用 `using` 陳述式（如示範）確保正確釋放檔案句柄與非受控資源。  
- 在處理前驗證輸入的 PDF（大小、格式、密碼保護），以防止拒絕服務攻擊。  
- 記錄每次預覽產生事件（包括頁數與耗時），以便監控與除錯。

## 進階設定選項
- **自訂 DPI** – 某些 GroupDocs.Annotation 版本允許設定 `previewOptions.Dpi = 300`，以產生超高銳利度的縮圖。  
- **加水印** – 在呼叫 `GeneratePreview` 前串接 `WatermarkOptions` 物件，加入「僅供預覽」的覆蓋層。  
- **智慧頁面選擇** – 使用 `DocumentInfo` 偵測目錄頁，並自動將其納入縮圖集合。

## 結論
您現在已擁有完整且可投入生產的作法，使用 GroupDocs.Annotation for .NET **移除 PDF 註解** 並 **建立 PDF 縮圖**。透過設定 `RenderAnnotations = false`，即可產生適合用於畫廊、審批流程與公開分享的乾淨預覽圖像，且無需額外的後處理步驟。

---

## 常見問與答

**Q: 我可以在 .NET 中使用 GroupDocs.Annotation 處理 PDF 以外的格式嗎？**  
A: 可以。此函式庫亦支援 DOCX、XLSX、PPTX 以及多種影像格式，無論來源類型皆可套用相同的預覽工作流程。

**Q: GroupDocs.Annotation for .NET 是否相容於 .NET Core？**  
A: 當然相容。它可在 .NET Framework、.NET Core 以及 .NET 5/6+ 上執行，讓您能針對現代跨平台應用程式開發。

**Q: 此函式庫提供註解編輯工具嗎？**  
A: 有提供，但在 `RenderAnnotations = false` 時，這些工具在產生預覽時會被忽略，確保產出乾淨的影像。

**Q: 我可以將此整合到 ASP.NET 網頁應用程式嗎？**  
A: 可以。只要確保 Web 伺服器具備適當的檔案系統權限，並考慮直接將 PNG 串流傳送給客戶端，以避免產生暫存檔案。

**Q: 縮圖畫廊應該選擇哪種影像格式？**  
A: PNG 提供無損品質，而 JPEG 可將檔案大小縮減最多 80 %，請依視覺真實度與頻寬需求做選擇。

**Q: 我可以在哪裡取得社群支援？**  
A: 前往 GroupDocs.Annotation 論壇 [GroupDocs.Annotation forum](https://forum.groupdocs.com/c/annotation/10)。社群活躍且回應迅速。

**最後更新：** 2026-08-25  
**測試環境：** GroupDocs.Annotation for .NET 23.12  
**作者：** GroupDocs  

---

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```

```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

## 相關教學

- [如何在 .NET 中產生縮圖 – 乾淨的 PDF 預覽](/annotation/net/advanced-usage/generate-preview-without-comments/)
- [使用 GroupDocs.Annotation for .NET 建立 PDF 縮圖](/annotation/net/advanced-usage/generate-document-pages-preview/)
- [建立 PDF 註解 .NET 教學 – 完整 GroupDocs 指南](/annotation/net/annotation-management/annotate-pdf-groupdocs-annotation-net/)