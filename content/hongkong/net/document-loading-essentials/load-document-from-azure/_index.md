---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中註解文件。與 Azure Blob 儲存體無縫整合的逐步教學。"
"linktitle": "從 Azure 載入文檔"
"second_title": "GroupDocs.Annotation .NET API"
"title": "從 Azure 載入文檔"
"url": "/zh-hant/net/document-loading-essentials/load-document-from-azure/"
type: docs
"weight": 11
---

# 從 Azure 載入文檔

## 介紹
在文件管理和協作領域，GroupDocs.Annotation for .NET 是一個強大的解決方案，可在 .NET 應用程式中實現無縫的註解和標記功能。本教學深入探討如何利用 GroupDocs.Annotation for .NET 註解文檔，並提供從入門到進階使用的逐步指導。
## 先決條件
在深入研究 .NET 的 GroupDocs.Annotation 之前，請確保您已滿足以下先決條件：
1. .NET Framework 的安裝：GroupDocs.Annotation for .NET 需要相容的 .NET 執行階段環境。請確保您的系統上已安裝 .NET Framework。
2. 造訪 GroupDocs.Annotation 函式庫：透過從網站下載或透過 NuGet 等套件管理器取得 .NET 函式庫的 GroupDocs.Annotation 的存取權。
3. 待註釋文件：準備要註釋的文件（例如 PDF）。確保該文件可在本機或透過 Azure Blob Storage 等雲端儲存服務存取。

## 導入命名空間
若要開始使用 GroupDocs.Annotation for .NET 註解文檔，請將必要的命名空間匯入您的專案。此步驟可確保您能夠存取所需的類別和功能。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## 從 Azure 載入文檔
若要註解儲存在 Azure Blob 儲存體中的文檔，請依照下列步驟操作：
### 步驟1：設定輸出路徑
定義註解文檔的儲存輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 第 2 步：下載文檔
透過調用 `DownloadFile` 方法。
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // 註解邏輯
    annotator.Save(outputPath);
}
```
## 從 Azure Blob 儲存體下載文件
若要從 Azure Blob 儲存體下載文檔，請執行 `DownloadFile` 方法。
### 步驟 1：檢索 Blob
存取 Azure Blob 儲存容器並擷取所需的 Blob。
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 步驟 2：下載 Blob 內容
將 Blob 內容下載到記憶體流中。
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## 取得 Azure Blob 儲存容器
若要與 Azure Blob 儲存體進行交互，請實現 `GetContainer` 方法。
### 步驟 1：初始化儲存憑證
提供必要的帳戶憑證和端點資訊。
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/”；
```
### 步驟 2：建立 Blob 用戶端
建立一個用戶端來與 Azure Blob 儲存體進行互動。
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 步驟 3：檢索容器引用
取得指定容器的教學。
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 步驟 4：如果不存在則建立容器
確保容器存在，如果不存在則建立。
```csharp
container.CreateIfNotExists();
```

## 結論
GroupDocs.Annotation for .NET 為開發人員提供了強大的文件註解功能，可無縫整合到 .NET 應用程式中。請按照本教學中概述的步驟操作，您可以有效地利用 GroupDocs.Annotation 的功能來註解儲存在 Azure Blob 儲存體中的文件。
#### 常見問題解答
### .NET 的 GroupDocs.Annotation 是否與所有文件格式相容？
GroupDocs.Annotation 支援多種文件格式，包括 PDF、DOCX、PPTX 等。
### 註釋是否可以根據具體要求進行客製化？
是的，GroupDocs.Annotation 為註釋提供了廣泛的自訂選項，允許使用者修改外觀、行為和元資料。
### GroupDocs.Annotation 是否適合協作文件註解？
當然！ GroupDocs.Annotation 支援多個使用者同時新增、編輯和審查註釋，從而促進協作文件註釋。
### GroupDocs.Annotation 是否提供跨平台相容性？
是的，GroupDocs.Annotation 旨在跨各種平台無縫運行，包括 Windows、Linux 和 macOS。
### GroupDocs.Annotation 用戶可以獲得技術支援嗎？
是的，GroupDocs 透過其論壇和專用支援管道提供全面的技術支援。