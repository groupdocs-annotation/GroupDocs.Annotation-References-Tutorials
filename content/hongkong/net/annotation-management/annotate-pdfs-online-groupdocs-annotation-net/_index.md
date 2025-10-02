---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation for .NET 線上註解 PDF 檔案。使用高效率的註釋技術簡化文件審閱流程。"
"title": "如何使用 GroupDocs.Annotation for .NET 從 URL 註解 PDF"
"url": "/zh-hant/net/annotation-management/annotate-pdfs-online-groupdocs-annotation-net/"
type: docs
"weight": 1
---

# 如何使用 GroupDocs.Annotation for .NET 從 URL 註解 PDF

## 介紹

在當今的數位環境中，線上註釋文件的能力對於有效的協作和工作流程管理至關重要。無論您是開發人員還是旨在增強文件審閱流程的組織，直接從 URL 註釋 PDF 都可以節省時間和資源。本教學將指導您使用 GroupDocs.Annotation for .NET——一個功能強大的程式庫，旨在無縫註釋各種文件類型，包括 PDF。

**您將學到什麼：**
- 從遠端 URL 載入文檔
- 使用特定註釋（例如區域註釋）對 PDF 文件進行註釋
- 在 .NET 環境中設定 GroupDocs.Annotation

讓我們探索開始這趟旅程所需的先決條件！

## 先決條件

在開始之前，請確保您具備以下條件：

### 所需的庫和依賴項
- **適用於 .NET 的 GroupDocs.Annotation**：確保您的專案包含 25.4.0 或更高版本。
  

### 環境設定要求
- 支援.NET的開發環境（例如Visual Studio）。
- 訪問互聯網以下載必要的軟體包。

### 知識前提
- 對 C# 和 .NET 程式設計有基本的了解。
- 熟悉使用 NuGet 進行套件管理是有益的，但不是必需的。

## 為 .NET 設定 GroupDocs.Annotation

要開始透過 URL 註釋 PDF，您首先需要在開發環境中設定 GroupDocs.Annotation。操作步驟如下：

**NuGet 套件管理器控制台**

```bash
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### 許可證獲取

GroupDocs 提供免費試用。您也可以申請臨時許可證或購買長期許可證。

- **免費試用**：非常適合初步測試。
- **臨時執照**：用於不受限制的擴展評估。
- **購買**：獲得完全存取權和支援。

### 基本初始化

以下是如何在 C# 應用程式中初始化 GroupDocs.Annotation：

```csharp
using GroupDocs.Annotation;

// 使用流或檔案路徑初始化註釋器
Annotator annotator = new Annotator("input.pdf");
```

這個簡單的設定可讓您開始使用 GroupDocs.Annotation 功能。

## 實施指南

### 從 URL 載入文檔

#### 概述

第一步是從遠端 URL 載入文件。此功能無需本地儲存即可直接處理文件，從而促進基於雲端的應用程式和協作。

#### 實施步驟

**1. 建立 Web 請求**

```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true”;
WebRequest request = WebRequest.Create(url);
```

此行會建立一個 HTTP 請求來存取指定的 URL。

**2. 取得並轉換響應流**

```csharp
private static Stream GetRemoteFile(string url)
{
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}

private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream); // 將資料複製到記憶體流
    fileStream.Position = 0; // 重置以進行閱讀
    return fileStream;
}
```

此程序將 Web 回應轉換為 GroupDocs.Annotation 可用的本機檔案流。

### 新增註釋

#### 概述

現在您的文件已加載，您可以添加區域註釋等註釋來突出顯示特定部分或註釋。

#### 實施步驟

**1. 載入文檔**

```csharp
using (Annotator annotator = new Annotator(GetRemoteFile("YOUR_DOCUMENT_DIRECTORY/input.pdf")))
{
    // 繼續註釋步驟
}
```

**2. 建立並新增區域註釋**

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 定義矩形尺寸
    BackgroundColor = 65535, // 設定背景顏色
};

annotator.Add(area); // 新增註釋
```

**3. 儲存註解文檔**

```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY\