---
categories:
- Document Management
date: '2026-07-06'
description: 了解如何設定 AWS 憑證，並使用 C# 將 GroupDocs Annotation 與 Amazon S3 整合。提供載入、註釋及管理文件的逐步指南。
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: 從 Amazon S3 載入文件
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: 設定 AWS 憑證以整合 GroupDocs Annotation 與 S3
type: docs
url: /zh-hant/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# 設定 AWS 憑證以整合 GroupDocs Annotation 與 S3

在本教學中，您將學習如何 **設定 AWS 憑證**，並使用 C# 無縫整合 GroupDocs.Annotation 與 Amazon S3。我們將示範如何從 S3 儲存桶載入文件、加入註解，並將結果儲存回雲端，同時說明最佳實踐的安全性與效能技巧。

## 快速解答
- **如何設定 AWS 憑證？** 使用帶有 `BasicAWSCredentials` 的 `AmazonS3Client` 建構子，或依賴 IAM 角色以自動解析憑證。  
- **需要哪些 NuGet 套件？** `GroupDocs.Annotation` 與 `AWSSDK.S3`。  
- **我可以註解大於 100 MB 的 PDF 嗎？** 可以 – 使用串流與非同步 API，避免將整個檔案載入記憶體。  
- **此整合是否支援執行緒安全？** 每個請求建立獨立的 `Annotator` 實例；SDK 本身是無狀態的。  
- **我需要在 S3 中加密文件嗎？** 啟用伺服器端加密（SSE‑S3 或 SSE‑KMS）以符合規範並保護資料。

## 為何使用 S3 進行文件註解？

使用 S3 進行文件註解，可為您提供高度可擴展、具成本效益且全球可存取的儲存解決方案，同時確保檔案安全。  
- **可擴展性**：S3 可處理幾乎無限制的物件，支援單檔最高 5 TB 以及每秒數百萬次請求。  
- **成本效益**：您只需為實際使用的儲存空間付費，且會自動分層至較低成本的類別。  
- **全球可存取性**：從任何 AWS 區域以低延遲存取，確保您的註解文件隨時可取得。  
- **安全性**：內建加密（SSE‑S3、SSE‑KMS）與細緻的 IAM 政策保護敏感資料。  
- **整合性**：可原生與現有的 AWS 服務（如 CloudFront、Lambda 與 IAM）協同運作。

## 前置條件

在開始開發之前，請確保您已具備以下必要條件：

1. **C# 開發環境** – Visual Studio 或具 .NET 支援的 VS Code。  
2. **GroupDocs.Annotation for .NET** – 從[官方網站](https://releases.groupdocs.com/annotation/net/)下載。  
3. **AWS S3 存取權** – 具備對目標儲存桶讀寫權限的有效 AWS 憑證。  
4. **基本 C# 知識** – 了解類別、async/await 與串流。  
5. **Amazon S3 SDK** – 透過 NuGet 安裝（`AWSSDK.S3`）。

## 如何設定 AWS 憑證以存取 S3？

`BasicAWSCredentials` 是一個保存 AWS 存取金鑰 ID 與密鑰的類別。`AmazonS3Client` 是用於與 S3 服務互動的 AWS SDK 客戶端。

只需載入一次 AWS 金鑰，讓 SDK 在每次請求時重複使用。最直接的方式是建立 `BasicAWSCredentials` 物件，並將其傳入 `AmazonS3Client` 建構子。對於正式環境，建議使用 IAM 角色或環境變數，以避免硬編碼機密。

**專業提示：** 在 EC2、ECS 或 Lambda 上執行時，省略明確的憑證，讓 SDK 自動從實例設定檔取得臨時憑證。

## 匯入命名空間

讓我們先匯入 S3 整合所需的所有命名空間：

```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

這些匯入讓我們能使用 AWS S3 操作與 GroupDocs 註解功能。`Amazon.S3` 命名空間負責雲端儲存互動，而 `GroupDocs.Annotation.Models` 提供註解框架。

## 步驟式實作

現在讓我們逐步說明從 S3 載入文件並加入註解的完整流程。我們會將其拆解為可操作的步驟，方便您跟隨。

### 步驟 1：定義輸出路徑

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

此程式碼會建立本機路徑，用於儲存已註解的文件。`Path.Combine` 方法確保跨平台相容性，且我們保留原始檔案副檔名以維持文件類型完整性。

**專業提示**：考慮在輸出檔名中加入時間戳記，以避免覆寫先前的註解，例如 `"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`。

### 步驟 2：指定文件金鑰

```csharp
string key = "sample.pdf";
```

這是您在 S3 儲存桶中的文件唯一識別碼。在實務情境中，通常會從使用者輸入、資料庫紀錄或 API 參數取得。請確保金鑰與 S3 物件名稱完全相符，包含任何資料夾前綴（例如 `documents/2025/sample.pdf`）。

### 步驟 3：初始化 Annotator

`Annotator` 是 GroupDocs.Annotation 的核心類別，代表可編輯的文件會話。它提供新增、修改與刪除註解的方法。

```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

透過在 `using` 區塊中包裹 S3 下載串流，我們確保串流與 annotator 實例皆能正確釋放。

### 步驟 4：建立區域註解

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

此程式碼在文件上建立矩形註解。`Rectangle(100, 100, 100, 100)` 參數分別代表 X 位置、Y 位置、寬度與高度。`BackgroundColor` 值 `65535` 產生黃色高亮——您可使用標準 RGB 色碼自訂顏色。

**區域註解的常見使用情境**：
- 在合約中突顯重要段落  
- 在技術規格中標記審查區域  
- 在簡報投影片上加入視覺說明  

### 步驟 5：將註解加入文件

```csharp
annotator.Add(area);
```

此方法將我們的區域註解加入文件。您可以多次呼叫 `Add()`，加入文字評論、箭頭或印章等不同類型的註解。註解會保留在記憶體中，直至您明確儲存文件。

### 步驟 6：儲存已註解的文件

```csharp
annotator.Save(outputPath);
```

現在我們將已註解的文件儲存至先前指定的輸出路徑。這會產生一個包含所有註解的新檔案。若需將結果再次存回 S3（常見的生產情境），只要在此步驟之後使用 S3 SDK 上傳檔案即可。

### 步驟 7：顯示成功訊息

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

簡單的確認訊息，可協助除錯並提供使用者回饋。在實際應用中，您會以適當的日誌或 UI 通知取代此訊息。

## 實作 S3 下載方法

您會注意到我們提到過 `DownloadFile(key)` 方法，但尚未實作。以下說明如何建立此必要的輔助函式：

```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**安全性說明**：切勿在正式程式碼中硬編碼 AWS 憑證。請使用 IAM 角色、環境變數或共用憑證檔，以避免機密洩漏至原始碼管理。

## 如何從 Amazon S3 載入文件？

`GetObjectAsync` 是非同步方法，可從 S3 取得物件並回傳包含串流的回應。`MemoryStream` 是 .NET 的記憶體串流，可在不使用磁碟 I/O 的情況下快速讀寫資料。`Annotator`（如前所述）是用於載入文件以進行註解的類別。

使用 `GetObjectAsync` 方法直接從 S3 載入 PDF，將回應串流包裹於 `MemoryStream`，再傳入 `Annotator` 建構子。此做法避免將原始檔案寫入磁碟，減少 I/O 負擔，且能有效處理大型檔案，同時控制記憶體使用量。

```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## 常見整合問題與解決方案

根據實務實作經驗，以下列出最常見的問題以及對應的解決方式：

### 問題 1：「Access Denied」錯誤
**問題**：您的應用程式無法存取 S3 物件。  
**解決方案**：確認您的 IAM 使用者或角色對該儲存桶及物件具備 `s3:GetObject` 權限。

### 問題 2：大型檔案逾時
**問題**：超過 50 MB 的文件會導致逾時錯誤。  
**解決方案**：實作非同步操作並提升逾時設定值：

```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### 問題 3：多文件記憶體問題
**問題**：處理大量文件時會發生記憶體不足例外。  
**解決方案**：及時釋放串流，並以批次方式處理文件。

### 問題 4：區域不匹配錯誤
**問題**：S3 客戶端找不到您的儲存桶。  
**解決方案**：確保 `RegionEndpoint` 與儲存桶實際所在區域相符。

## 效能與安全性最佳實踐

### 效能最佳化
- **使用非同步方法**：優先使用 `GetObjectAsync()` 而非同步呼叫。  
- **實作快取**：將常用文件暫存於本機一段時間。  
- **批次操作**：在適當情況下平行處理多個檔案。  
- **串流處理**：避免將整個大型文件載入記憶體，改以串流方式處理。

### 安全性考量
- **使用 IAM 角色**：避免硬編碼憑證。  
- **啟用 S3 加密**：啟動伺服器端加密（SSE‑S3 或 SSE‑KMS）。  
- **實作存取日誌**：追蹤誰存取了哪些文件。  
- **驗證檔案類型**：在處理前檢查副檔名與 MIME 類型。

## 真實案例應用

此 S3 整合模式在多個產業中表現卓越：

1. **法律文件審查** – 律師事務所對儲存在 S3 的合約進行註解。  
2. **教育平台** – 教師標註雲端上學生的提交作品。  
3. **建築管理** – 建築師在不同區域註解藍圖。  
4. **醫療紀錄** – 醫療機構安全地為患者文件添加備註。  
5. **金融服務** – 審計師協作處理儲存在 S3 的合規文件。

## 疑難排解指南

**無法從 S3 載入文件**  
- 核實 AWS 憑證與儲存桶權限。  
- 再次確認儲存桶名稱與物件金鑰拼寫。  
- 確保文件在 S3 中未損壞。

**註解未顯示**  
- 確認在加入註解後已呼叫 `annotator.Save()`。  
- 檢查文件格式是否支援您使用的註解類型。  
- 確保註解座標落在頁面範圍內。

**效能問題**  
- 監控 S3 請求速率並實作指數退避。  
- 為常存取檔案使用 CloudFront CDN。  
- 考慮使用 S3 Transfer Acceleration 以支援全球應用。

## 常見問答

**Q: GroupDocs.Annotation for .NET 是否相容所有文件格式？**  
A: GroupDocs.Annotation 支援超過 50 種輸入與輸出格式——包括 PDF、DOCX、PPTX 與 HTML——但註解類型可能因格式而異。

**Q: 我可以在購買前試用 GroupDocs.Annotation for .NET 嗎？**  
A: 可以，您可透過[此處](https://releases.groupdocs.com/)取得免費試用版，探索 GroupDocs.Annotation for .NET 的功能，並無風險測試 S3 整合與註解能力。

**Q: 我在哪裡可以找到 GroupDocs.Annotation for .NET 的文件說明？**  
A: 完整的文件說明可於[此處](https://tutorials.groupdocs.com/annotation/net/)取得，內容包括 API 參考、進階範例與整合指南。

**Q: 評估 GroupDocs.Annotation for .NET 是否需要臨時授權？**  
A: 您可從[此處](https://purchase.groupdocs.com/temporary-license/)取得評估用臨時授權，解除試用限制，讓您完整測試生產情境。

**Q: 我可以在哪裡尋求 GroupDocs.Annotation for .NET 的協助或支援？**  
A: 若有任何問題或支援需求，請前往 GroupDocs.Annotation 論壇[此處](https://forum.groupdocs.com/c/annotation/10)。社群與支援團隊皆相當活躍，能協助排除整合問題。

**Q: 我可以將已註解的文件儲存回 S3 而非本機嗎？**  
A: 當然可以！在呼叫 `annotator.Save(localPath)` 後，您可使用 `PutObjectAsync()` 方法將已註解的檔案上傳回 S3，形成完整的雲端對雲端工作流程，特別適合 Web 應用。

**Q: S3 文件註解支援的最大檔案大小為何？**  
A: 雖然 GroupDocs.Annotation 能處理大型檔案，但實際上限取決於伺服器記憶體與 S3 傳輸逾時設定。對於超過 100 MB 的檔案，請實作串流或分塊處理，以避免記憶體耗盡。

---

**最後更新：** 2026-07-06  
**測試環境：** GroupDocs.Annotation 23.12 for .NET  
**作者：** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## 相關教學

- [GroupDocs.Annotation .NET 文件載入](/annotation/net/document-loading-essentials/)
- [如何從 FTP 載入文件（.NET） - 完整 GroupDocs 指南](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [文件預覽 .NET 教學 - 完整 GroupDocs.Annotation 指南](/annotation/net/document-preview/)