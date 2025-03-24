---
title: 從 Azure 載入文檔
linktitle: 從 Azure 載入文檔
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中註解文件。與 Azure Blob 儲存體無縫整合的逐步教學。
weight: 11
url: /zh-hant/net/document-loading-essentials/load-document-from-azure/
---

# 從 Azure 載入文檔

## 介紹
在文件管理和協作領域，GroupDocs.Annotation for .NET 作為一個強大的解決方案出現，促進 .NET 應用程式中的無縫註釋和標記功能。本教學深入探討了利用 GroupDocs.Annotation for .NET 來註解文件的複雜性，提供從先決條件到進階用法的逐步指導。
## 先決條件
在深入研究 .NET 的 GroupDocs.Annotation 之前，請確保滿足以下先決條件：
1. 安裝 .NET Framework：GroupDocs.Annotation for .NET 需要相容的 .NET 執行階段環境。確保您的系統上安裝了 .NET Framework。
2. 造訪 GroupDocs.Annotation 庫：透過從網站下載或透過 NuGet 等套件管理器存取 GroupDocs.Annotation for .NET 程式庫。
3. 要註釋的文件：準備要註釋的文件（例如 PDF）。確保可在本機或透過 Azure Blob 儲存體等雲端儲存服務存取該文件。

## 導入命名空間
若要開始使用 GroupDocs.Annotation for .NET 註解文檔，請將必要的命名空間匯入到您的專案中。此步驟可確保您可以存取所需的類別和功能。
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
若要註解儲存在 Azure Blob 儲存體中的文檔，請執行下列步驟：
### 第1步：設定輸出路徑
定義儲存註解文件的輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 步驟2：下載文檔
透過呼叫從 Azure Blob 儲存體檢索文檔`DownloadFile`方法。
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    //註解邏輯
    annotator.Save(outputPath);
}
```
## 從 Azure Blob 儲存體下載文件
若要從 Azure Blob 儲存體下載文檔，請實施`DownloadFile`方法。
### 第 1 步：檢索 Blob
存取 Azure Blob 儲存容器並擷取所需的 Blob。
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 第 2 步：下載 Blob 內容
將 blob 內容下載到記憶體流中。
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## 取得 Azure Blob 儲存容器
若要與 Azure Blob 儲存體交互，請實作`GetContainer`方法。
### 步驟1：初始化儲存憑證
提供必要的帳戶憑證和端點資訊。
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### 步驟 2：建立 Blob 用戶端
建立用戶端以與 Azure Blob 儲存體互動。
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 第 3 步：檢索容器引用
取得指定容器的引用。
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 第四步：如果不存在則建立容器
確保容器存在，如果不存在則建立它。
```csharp
container.CreateIfNotExists();
```

## 結論
GroupDocs.Annotation for .NET 為開發人員提供強大的文件註解功能，無縫整合到 .NET 應用程式中。透過遵循本教學中概述的步驟，你可以有效地利用 GroupDocs.Annotation 的功能來註解儲存在 Azure Blob 儲存體中的文件。
#### 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有文件格式相容？
GroupDocs.Annotation 支援多種文件格式，包括 PDF、DOCX、PPTX 等。
### 可以依具體需求客製註解嗎？
是的，GroupDocs.Annotation 為註釋提供了廣泛的自訂選項，允許使用者修改外觀、行為和元資料。
### GroupDocs.Annotation適合協作文件註解嗎？
絕對地！ GroupDocs.Annotation 允許多個使用者同時新增、編輯和檢視註釋，從而促進協作文件註釋。
### GroupDocs.Annotation 是否提供跨平台相容性？
是的，GroupDocs.Annotation 旨在跨各種平台無縫運作，包括 Windows、Linux 和 macOS。
### GroupDocs.Annotation 用戶可以獲得技術支援嗎？
是的，GroupDocs 透過其論壇和專用支援管道提供全面的技術支援。