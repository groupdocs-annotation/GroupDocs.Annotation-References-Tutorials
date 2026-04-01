---
categories:
- Document Processing
date: '2026-04-01'
description: 學習如何在 .NET 中建立 PDF 縮圖，並產生不含註解的純淨 PDF 預覽。提供使用 GroupDocs.Annotation 進行
  PDF 縮圖生成的逐步教學與程式碼範例。
keywords:
- create pdf thumbnails
- generate pdf preview
- remove annotations preview
- render pdf without markup
- pdf thumbnail generation
lastmod: '2025-01-02'
linktitle: 產生未加註解的預覽
second_title: GroupDocs.Annotation .NET API
tags:
- pdf-preview
- document-collaboration
- annotations
- net-development
title: 在 .NET 中建立 PDF 縮圖 – 無註解的純淨預覽
type: docs
url: /zh-hant/net/advanced-usage/generate-preview-without-annotations/
weight: 13
---

# 在 .NET 中建立 PDF 縮圖 – 無註解的乾淨預覽

產生乾淨的文件預覽是為畫廊、審批工作流程或公開分享 **create pdf thumbnails** 時的常見需求。在本教學中，您將學習如何 **create pdf thumbnails**，省略所有註解，為使用者提供原始 PDF 內容的純淨視圖。

## 快速解答
- **RenderAnnotations = false** 的作用是什麼？它告訴 GroupDocs.Annotation 在渲染預覽時跳過所有標記。  
- **哪種影像格式適合高品質縮圖？** PNG 提供無損品質；JPEG 體積較小但為有損壓縮。  
- **我可以為縮圖集合選擇特定頁面嗎？** 可以 – 設定 `PreviewOptions.PageNumbers` 為您需要的頁碼。  
- **在正式環境使用是否需要授權？** 建議取得授權以獲得無限制功能與支援。  
- **此方法是否相容於 .NET Core？** 絕對相容 – GroupDocs.Annotation 可在 .NET Framework 與 .NET Core 上運作。

## 什麼是 “create pdf thumbnails”？
建立 PDF 縮圖是指將 PDF 的每一頁渲染為影像（PNG/JPEG），以便在使用者介面中顯示。縮圖可用於快速預覽、文件瀏覽器，以及在不載入完整 PDF 的情況下產生預覽格子。

## 為何產生無註解的預覽？
從預覽中移除註解可讓焦點保持在原始文件內容上。這在以下情況尤為重要：
- **文件審批工作流程** – 將乾淨版本與已註解的版本進行比較。  
- **縮圖畫廊** – 避免評論或標記造成的視覺雜亂。  
- **公開分享** – 在仍顯示文件的同時保護敏感的標記。  
- **列印準備** – 產生乾淨的 PDF 供列印，同時將數位註記分開保存。

## 前置條件
- **GroupDocs.Annotation for .NET** – 從官方的 [releases page](https://releases.groupdocs.com/annotation/net/) 下載並安裝。  
- **License（可選但建議）** – 透過 [purchase page](https://purchase.groupdocs.com/buy) 購買完整授權，或向 [temporary license](https://purchase.groupdocs.com/temporary-license/) 申請臨時授權。  
- 具備 C#/.NET 基礎知識。  
- PDF 檢視器（例如 Adobe Acrobat Reader）用於驗證產生的縮圖。

## 匯入命名空間
加入必要的 `using` 陳述式，以便使用註解 API：

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

## 如何在無註解的情況下建立 PDF 縮圖

以下是逐步說明，展示如何 **generate pdf preview** 圖像，同時從輸出中 **removing annotations preview**。

### 步驟 1：初始化 Annotator
建立指向來源 PDF 的 `Annotator` 實例。`using` 區塊會自動釋放資源。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```

> **專業提示：** 在處理使用者上傳的 PDF 時，請驗證檔案路徑並執行適當的安全檢查。

### 步驟 2：設定 Preview Options
設定 `PreviewOptions` 以定義輸出格式、頁面範圍，且最重要的是停用註解渲染。

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

**要點**
- **檔案命名** – lambda 為每一頁建立唯一的 PNG 檔案。  
- **格式選擇** – PNG 用於高品質縮圖；若需較小檔案可改用 JPEG。  
- **頁面選擇** – 明確指定您想要進行 **pdf thumbnail generation** 的頁碼。  
- **`RenderAnnotations = false`** – 這會停用所有標記，是 **disable annotations preview** 的核心。

### 步驟 3：產生乾淨的預覽
呼叫 `GeneratePreview` 方法，根據您設定的選項渲染影像。

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

您的乾淨縮圖檔案（`result1.png`、`result2.png`、…）現在已可使用。

## 真實應用中的常見使用情境
- **文件管理系統** – 為檔案瀏覽器提供乾淨的縮圖，同時保留分開的註解版本。  
- **法律審查平台** – 向客戶展示未含內部評論的原始合約。  
- **線上學習平台** – 顯示原始作業，同時教師將批改註記保密。  
- **出版工作流程** – 為行銷素材建立預覽影像，避免編輯標記。

## 效能考量
- **批次處理** – 在單一背景工作中處理多個 PDF，以降低額外負擔。  
- **快取** – 首次上傳後儲存產生的縮圖，避免每次請求都重新渲染。  
- **頁數限制** – 對於非常大的 PDF，將預覽限制在前幾頁，以縮短處理時間。  
- **檔案格式取捨** – PNG 可提供清晰的縮圖；當頻寬受限時，JPEG 可減少儲存空間。

## 常見問題排除
- **未產生縮圖** – 檢查輸出資料夾的寫入權限，並確認來源 PDF 未損毀。  
- **影像品質低** – 若您的 GroupDocs.Annotation 版本支援，請改用 PNG 或調整 DPI 設定。  
- **記憶體使用量高** – 將頁面分成較小批次處理，或以串流方式讀取 PDF，避免一次載入全部至記憶體。  
- **路徑問題** – 為確保跨平台安全，請始終使用 `Path.Combine()` 建立檔案路徑。

## 生產環境最佳實踐
- 將預覽產生程式包在 `try‑catch` 區塊中，以優雅地處理 I/O 錯誤。  
- 使用 `using` 陳述式（如範例所示），確保正確釋放檔案句柄。  
- 在處理前驗證傳入的 PDF（大小、格式、密碼保護）。  
- 記錄每一次預覽產生事件，以便監控與除錯。

## 進階設定選項
- **Custom DPI** – 某些版本允許設定更高解析度，以獲得更銳利的縮圖。  
- **加水印** – 加入 “Preview Only” 水印，以表明此影像非最終文件。  
- **智慧頁面選擇** – 根據文件中繼資料，自動挑選最相關的頁面（如首頁、目錄）。

## 結論
您現在已掌握完整且適合生產環境的作法，可 **create pdf thumbnails** 並 **generate pdf preview** 影像，且不含任何標記。透過設定 `RenderAnnotations = false`，您 **remove annotations preview**，並提供乾淨、專業的縮圖，無縫融入任何以文件為中心的應用程式。

---

## 常見問與答

**Q: 我可以在 .NET 中使用 GroupDocs.Annotation 處理非 PDF 格式嗎？**  
A: 可以。此函式庫支援 DOCX、XLSX、PPTX 等多種格式。無論來源格式為何，皆可使用相同的預覽工作流程。

**Q: GroupDocs.Annotation for .NET 是否相容於 .NET Core？**  
A: 絕對相容。它支援 .NET Framework、 .NET Core 以及 .NET 5/6+，讓您能針對現代跨平台應用程式開發。

**Q: 此函式庫是否提供可自訂的註解工具？**  
A: 有提供，但當您設定 `RenderAnnotations = false` 時，這些工具在預覽產生時會被忽略。

**Q: 我可以將此整合到 Web 應用程式中嗎？**  
A: 可以。只需確保 Web 伺服器具備適當的檔案 I/O 權限，並考慮直接將輸出串流至用戶端，以避免產生暫存檔案。

**Q: 縮圖畫廊應選擇哪種影像格式？**  
A: PNG 提供最佳品質，JPEG 則可減少檔案大小。請依據所需的視覺真實度與頻寬限制做出選擇。

**Q: 我可以在哪裡取得社群支援？**  
A: 您可於 GroupDocs.Annotation 論壇 [here](https://forum.groupdocs.com/c/annotation/10) 尋求協助。社群活躍且回應迅速。

**最後更新：** 2026-04-01  
**測試環境：** GroupDocs.Annotation for .NET 23.12  
**作者：** GroupDocs