---
"description": "探索 GroupDocs.Annotation for .NET 的強大功能，並輕鬆為您的應用程式新增文件註解功能。"
"linktitle": "在文件中新增搜尋文字片段註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "在文件中新增搜尋文字片段註釋"
"url": "/zh-hant/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# 在文件中新增搜尋文字片段註釋

## 介紹
在 .NET 開發領域，GroupDocs.Annotation 是一款功能強大的工具，可無縫註釋文件。無論您是經驗豐富的開發人員，還是剛踏入 .NET 領域，本教學都將帶您了解 GroupDocs.Annotation for .NET 的基本使用方法，從導入命名空間到掌握向文件添加搜尋文字片段註解的複雜技巧。
## 介紹
GroupDocs.Annotation for .NET 讓開發人員能夠輕鬆地將文件註釋功能整合到他們的應用程式中。憑藉其直覺的 API 和強大的功能，開發人員可以註釋各種文件格式，包括 PDF、Microsoft Office 文件、圖像等。
## 先決條件
在深入研究 .NET 的 GroupDocs.Annotation 之前，請確保您已滿足以下先決條件：

## 導入命名空間
首先，匯入必要的命名空間以存取 .NET 專案中的 GroupDocs.Annotation 類別和方法：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 步驟 1：定義輸出路徑
首先定義註解文檔的儲存輸出路徑：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：初始化註解器
接下來，初始化一個實例 `Annotator` 透過提供要註解的文件的路徑來類別：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 步驟 3：建立搜尋文字片段註釋
創建一個 `SearchTextFragment` 具有所需屬性的對象，例如要搜尋的文字、字體大小、字體系列、字體顏色和背景顏色：
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## 步驟 4：新增註釋
使用 `Add` 註釋器的方法：
```csharp
annotator.Add(searchText);
```
## 步驟 5：儲存已註記的文檔
將註解後的文件儲存到指定的輸出路徑：
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
通知使用者文件已成功儲存：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
總而言之，GroupDocs.Annotation for .NET 簡化了在文件中添加註釋的過程，並增強了協作和文件審查流程。按照本指南中概述的步驟，您可以將文件註解功能無縫整合到您的 .NET 應用程式中。
## 常見問題解答
### GroupDocs.Annotation 是否與所有文件格式相容？
是的，GroupDocs.Annotation 支援多種文件格式，包括 PDF、Microsoft Office 文件、圖像等。
### 我可以自訂註釋的外觀嗎？
當然！ GroupDocs.Annotation 為註釋提供了廣泛的自訂選項，可讓您調整字體大小、顏色和樣式等屬性。
### GroupDocs.Annotation 有免費試用版嗎？
是的，您可以免費試用 GroupDocs.Annotation，在購買之前了解其功能和功能 [這裡](https://releases.groupdocs.com/)..
### 在哪裡可以找到對 GroupDocs.Annotation 的支援？
如需 GroupDocs.Annotation 的支援和協助，您可以存取 GroupDocs [論壇](https://forum.groupdocs.com/c/annotation/10) 專用於註釋相關的查詢與討論。
### 如何取得 GroupDocs.Annotation 的臨時授權？
您可以透過 GroupDocs 取得 GroupDocs.Annotation 的臨時許可證 [網站](https://purchase.groupdocs.com/temporary-license/)，使您能夠全面評估產品。