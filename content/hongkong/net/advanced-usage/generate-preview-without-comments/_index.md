---
categories:
- Document Processing
date: '2026-04-01'
description: 學習如何使用 GroupDocs.Annotation 在 .NET 中產生不含批註的縮圖。本指南涵蓋如何隱藏批註、移除批註預覽，以及產生乾淨的
  PDF 預覽。
keywords:
- how to generate thumbnails
- how to hide annotations
- remove comments preview
- document preview without comments
- clean pdf preview
lastmod: '2026-04-01'
linktitle: 產生預覽（不含評論）
second_title: GroupDocs.Annotation .NET API
tags:
- document-preview
- pdf-thumbnails
- groupdocs
- dotnet
title: 如何在 .NET 中產生縮圖 – 清晰的 PDF 預覽
type: docs
url: /zh-hant/net/advanced-usage/generate-preview-without-comments/
weight: 14
---

# 如何在 .NET 中產生縮圖 – 清晰的 PDF 預覽

## 簡介

是否曾需要為文件檢視器、檔案總管或內容管理系統產生 **縮圖**，同時保持圖像不含任何使用者註記？您並不孤單。許多 .NET 開發人員在嘗試建立隱藏批註與評論的文件預覽時，常會卡關。

在本教學中，我們將逐步說明如何使用 **GroupDocs.Annotation for .NET** 產生乾淨的 PDF 預覽。您將看到如何隱藏批註、移除評論預覽，並產生專業外觀的縮圖，完美適用於相簿、儀表板或任何需要無雜訊快照的使用者介面。

## 快速解答
- **哪個函式庫可產生無評論的縮圖？** GroupDocs.Annotation for .NET  
- **哪個屬性可停用批註？** `RenderComments = false`  
- **我可以選擇影像格式嗎？** 是 – 可透過 `PreviewFormat` 使用 PNG、JPEG、BMP 等格式  
- **生產環境需要授權嗎？** 需要商業授權；臨時授權可用於測試。  
- **它只支援 .NET 嗎？** 可在 .NET Framework、.NET Core 以及 .NET 5/6+ 上使用。

## 什麼是無評論的縮圖產生？

無評論的縮圖產生是指將每頁渲染成視覺快照 **不含** 任何標記、註記或可能已加入原始檔案的協作批註。其結果是一張乾淨、靜態的影像，呈現文件的真實內容——非常適合面向公眾的入口網站、法律檔案庫，或任何需要隱藏內部備註的情境。

## 為什麼在建立預覽時要隱藏批註？

- **專業外觀：** 最終使用者只會看到文件內容，而非審閱討論。  
- **安全與隱私：** 敏感評論保持在內部。  
- **效能：** 渲染較少圖層可加速影像產生。  
- **一致性：** 縮圖與已列印或匯出的版本相符，亦會省略評論。

## 前置條件

### 1. 安裝 GroupDocs.Annotation for .NET
從官方發佈頁面 **[此處](https://releases.groupdocs.com/annotation/net/)** 取得套件，或透過 NuGet 安裝。請確保您的專案目標為受支援的 .NET 版本。

### 2. 取得授權
生產環境使用需購買商業授權。可於 **[此處](https://purchase.groupdocs.com/buy)** 購買，或於 **[此處](https://purchase.groupdocs.com/temporary-license/)** 申請臨時評估授權。

### 3. .NET 知識
您應熟悉 C# 基礎、檔案 I/O，以及使用 `using` 陳述式進行資源管理。

## 匯入命名空間

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## 步驟指南：產生乾淨的文件預覽

### 步驟 1：初始化 Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
`Annotator` 物件會載入來源檔案。`using` 區塊確保在完成後釋放所有非受控資源。

### 步驟 2：設定預覽選項
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
此處告訴函式庫每頁影像的儲存位置。lambda 會接收頁碼並回傳可寫入的 `FileStream`。

### 步驟 3：選擇格式與頁面
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
PNG 可產生清晰的縮圖，但若檔案大小較為重要，可改用 JPEG。選擇部分頁面可減少處理時間——非常適合只需前幾頁的縮圖相簿。

### 步驟 4：停用評論渲染
```csharp
    previewOptions.RenderComments = false;
```
**此行是「如何隱藏批註」的關鍵。** 將 `RenderComments` 設為 `false` 會去除所有評論層，為您提供乾淨的 PDF 預覽。

### 步驟 5：產生預覽影像
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
函式庫會處理文件，並將影像寫入先前定義的位置。

## 文件預覽產生的最佳實踐

- **縮放以作縮圖：** 產生 PNG 後，可考慮將其調整至約 200 × 300 px，以加快 UI 載入速度。  
- **分批處理大型檔案：** 初始僅產生前幾頁，之後視需求再產生其餘頁面。  
- **始終使用 `using` 包裹：** 確保正確的記憶體清理，特別是在處理大量文件時。  
- **加入錯誤處理：** 捕捉 `FileNotFoundException`、`InvalidOperationException` 以及授權錯誤，以提升應用程式的穩定性。

## 常見問題與故障排除

- **未出現影像：** 確認輸出資料夾存在且應用程式具有寫入權限。  
- **縮圖模糊：** 嘗試透過設定 `previewOptions.Dpi = 150;` 提高 DPI（此行未顯示於程式碼區塊中，以保持原始區塊完整）。  
- **大型 PDF 記憶體不足錯誤：** 可一次處理單頁，或在背景工作者中使用非同步 API。  
- **未找到授權：** 請確保在建立 `Annotator` 前已載入 `License` 物件。

## 效能優化技巧

- **批次處理多個文件：** 迭代集合時，盡可能重複使用單一 `Annotator` 實例。  
- **非同步產生：** 將預覽建立交給背景服務，以保持 UI 響應。  
- **快取結果：** 將產生的縮圖存放於 CDN 或本機快取，以避免重複處理相同檔案。  
- **選擇合適格式：** PNG 提供無損品質，若文件含大量影像則可使用 JPEG 以減小檔案。

## 支援的文件格式

GroupDocs.Annotation for .NET 可產生以下格式的預覽：

- **PDF** – 最常見的使用情境。  
- **Microsoft Office** – 包括 DOCX、XLSX、PPTX 以及其舊版格式。  
- **影像** – TIFF、JPEG、PNG、BMP（適用於掃描文件）。  
- **OpenDocument** – ODT、ODS、ODP 及其他開放標準。

## 何時使用無評論的預覽產生

- **公共入口網站**：內部審閱備註需保持隱藏。  
- **檔案庫瀏覽器**：顯示乾淨的縮圖格子。  
- **列印就緒工作流程**：在送印前顯示最終外觀。  
- **品質檢查**：比較「含評論」與「無評論」版本。

## 結論

您現在已了解如何在 .NET 中 **產生縮圖**，同時徹底移除批註與評論。只要將 `RenderComments = false`，即可取得乾淨、專業的 PDF 預覽，完美嵌入任何使用者介面。請依照具體需求調整預覽格式、頁面選擇與影像尺寸，並始終妥善處理授權與錯誤情況。透過這些步驟，您的應用程式將提供快速、無雜訊的文件縮圖，提升使用者體驗。

## 常見問答

**Q: GroupDocs.Annotation for .NET 是否相容所有文件格式？**  
A: 是的。它支援 PDF、DOCX、PPTX、XLSX、常見影像類型，以及多種 OpenDocument 格式。

**Q: 我可以自訂產生的預覽外觀嗎？**  
A: 當然可以。您可以變更 `PreviewFormat`、設定影像尺寸、DPI，並選擇特定頁面進行渲染。

**Q: 此函式庫支援多使用者協作嗎？**  
A: GroupDocs.Annotation 提供協作批註功能。預覽產生可用於建立隱藏所有使用者評論的乾淨視圖。

**Q: 若遇到問題，我該向哪裡尋求協助？**  
A: 社群與支援團隊活躍於 **[支援論壇](https://forum.groupdocs.com/c/annotation/10)**，您可在此提出問題並分享經驗。

**Q: 是否提供免費試用？**  
A: 是的，您可於 **[此處](https://releases.groupdocs.com/)** 下載完整功能試用版，以在購買前測試預覽產生功能。

---

**最後更新：** 2026-04-01  
**測試環境：** GroupDocs.Annotation for .NET (latest release)  
**作者：** GroupDocs  

---