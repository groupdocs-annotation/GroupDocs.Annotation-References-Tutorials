---
"description": "了解如何使用 GroupDocs.Annotation for .NET 以程式設計方式註解 PDF 文件。包含程式碼範例的逐步教學。"
"linktitle": "從 URL 載入文檔"
"second_title": "GroupDocs.Annotation .NET API"
"title": "從 URL 載入文檔"
"url": "/zh-hant/net/document-loading-essentials/load-document-from-url/"
type: docs
"weight": 15
---

# 從 URL 載入文檔

## 介紹
GroupDocs.Annotation for .NET 是一個功能豐富的程式庫，可讓開發人員輕鬆為其 .NET 應用程式新增註解功能。使用 GroupDocs.Annotation，您可以以程式設計方式註釋 PDF 文檔，讓使用者可以反白顯示文字、新增註釋、繪製形狀等。本教學課程將引導您完成使用 GroupDocs.Annotation for .NET 從 URL 載入文件、新增註解以及儲存註解文件的步驟。
## 先決條件
在開始之前，請確保您符合以下先決條件：
1. Visual Studio：確保您的開發機器上安裝了 Visual Studio。
2. GroupDocs.Annotation for .NET：從 [網站](https://releases。groupdocs.com/annotation/net/).
3. C# 基礎知識：熟悉 C# 程式語言。
4. 網路連線：您需要網路連線才能存取外部資源和下載範例檔案。

## 導入命名空間
首先，讓我們在 C# 專案中導入必要的命名空間：
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## 步驟 1：從 URL 載入文檔
若要透過 URL 註釋 PDF 文檔，請依照下列步驟操作：
### 步驟 1.1：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 步驟 1.2：指定 URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true”;
```
### 步驟 1.3：載入文檔
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // 在此處新增註釋
    annotator.Save(outputPath);
}
```
## 步驟 2：新增註釋
現在，讓我們為已載入的文件新增註解。在此範例中，我們將新增一個區域註解：
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 步驟 3：儲存附註解的文檔
最後將註解後的文件儲存到指定的輸出路徑：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 為 PDF 文件新增註解。按照逐步指南操作，您可以將註釋功能無縫整合到您的 .NET 應用程式中，使用戶能夠有效地協作處理 PDF 文件。

## 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有 .NET 框架相容？
是的，GroupDocs.Annotation for .NET 與各種 .NET 框架相容，包括 .NET Framework、.NET Core 和 .NET Standard。
### 我可以自訂註釋的外觀嗎？
當然！ GroupDocs.Annotation for .NET 提供了豐富的自訂選項，您可以根據需求修改註解的外觀和行為。
### GroupDocs.Annotation for .NET 有免費試用版嗎？
是的，您可以從 [網站](https://releases。groupdocs.com/).
### 如何獲得 GroupDocs.Annotation for .NET 的技術支援？
如果您遇到任何技術問題或對 GroupDocs.Annotation for .NET 有任何疑問，您可以向 [支援論壇](https://forum。groupdocs.com/c/annotation/10).
### 我可以在哪裡購買 GroupDocs.Annotation for .NET 的授權？
您可以從 [購買頁面](https://purchase。groupdocs.com/buy).