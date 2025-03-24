---
title: 從 URL 載入文檔
linktitle: 從 URL 載入文檔
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 以程式設計方式註解 PDF 文件。帶有程式碼範例的分步教程。
weight: 15
url: /zh-hant/net/document-loading-essentials/load-document-from-url/
---
## 介紹
GroupDocs.Annotation for .NET 是一個功能豐富的程式庫，可讓開發人員輕鬆地將註解功能新增至其 .NET 應用程式。透過 GroupDocs.Annotation，您可以透過程式設計對 PDF 文件進行註釋，從而允許使用者突出顯示文字、添加註釋、繪製形狀等。本教學將引導您完成從 URL 載入文件、新增註解以及使用 GroupDocs.Annotation for .NET 儲存已註解的文件的步驟。
## 先決條件
在開始之前，請確保您具備以下先決條件：
1. Visual Studio：確保您的開發電腦上安裝了 Visual Studio。
2.  GroupDocs.Annotation for .NET：從下列位置下載並安裝 GroupDocs.Annotation for .NET[網站](https://releases.groupdocs.com/annotation/net/).
3. C# 基礎知識：熟悉 C# 程式語言。
4. Internet 連線：您需要 Internet 連線才能存取外部資源並下載範例檔案。

## 導入命名空間
首先，讓我們在 C# 專案中導入必要的命名空間：
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## 第 1 步：從 URL 載入文檔
若要從 URL 註釋 PDF 文檔，請依照下列步驟操作：
### 步驟1.1：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 步驟1.2：指定URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### 步驟1.3：載入文檔
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    //在這裡添加註釋
    annotator.Save(outputPath);
}
```
## 第 2 步：新增註釋
現在，讓我們為載入的文檔新增註解。在此範例中，我們將新增區域註解：
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 第 3 步：儲存已註釋的文檔
最後將註解文檔儲存到指定的輸出路徑：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 對 PDF 文件進行註解。透過遵循逐步指南，您可以將註釋功能無縫整合到 .NET 應用程式中，使用戶能夠有效地協作處理 PDF 檔案。

## 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有 .NET 框架相容？
是的，GroupDocs.Annotation for .NET 與各種 .NET 框架相容，包括 .NET Framework、.NET Core 和 .NET Standard。
### 我可以自訂註釋的外觀嗎？
絕對地！ GroupDocs.Annotation for .NET 提供了廣泛的自訂選項，可讓您根據需要修改註解的外觀和行為。
### GroupDocs.Annotation for .NET 是否有免費試用版？
是的，您可以從以下位置下載 GroupDocs.Annotation for .NET 的免費試用版：[網站](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Annotation for .NET 的技術支援？
如果您遇到任何技術問題或對 GroupDocs.Annotation for .NET 有疑問，可以尋求協助[支援論壇](https://forum.groupdocs.com/c/annotation/10).
### 哪裡可以購買 GroupDocs.Annotation for .NET 的授權？
您可以向 GroupDocs.Annotation for .NET 購買許可證[購買頁面](https://purchase.groupdocs.com/buy).