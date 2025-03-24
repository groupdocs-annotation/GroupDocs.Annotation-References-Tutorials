---
title: 將搜尋文字片段註解新增至文檔
linktitle: 將搜尋文字片段註解新增至文檔
second_title: GroupDocs.Annotation .NET API
description: 探索 GroupDocs.Annotation for .NET 的強大功能，輕鬆地將文件註解功能新增至您的應用程式。
weight: 20
url: /zh-hant/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## 介紹
在 .NET 開發領域，GroupDocs.Annotation 作為無縫註釋文件的強大工具脫穎而出。無論您是經驗豐富的開發人員還是剛剛踏入.NET 世界，這個全面的教程將引導您了解使用GroupDocs.Annotation for .NET 的基本知識，從導入命名空間到掌握向您的文檔添加搜索文本片段註釋的複雜性。
## 介紹
GroupDocs.Annotation for .NET 讓開發人員能夠輕鬆地將文件註釋功能合併到他們的應用程式中。憑藉其直覺的 API 和強大的功能，開發人員可以對各種文件格式進行註釋，包括 PDF、Microsoft Office 文件、圖像等。
## 先決條件
在深入研究 .NET 的 GroupDocs.Annotation 之前，請確保滿足以下先決條件：

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
## 第 1 步：定義輸出路徑
首先定義儲存註解文件的輸出路徑：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化註釋器
接下來，初始化一個實例`Annotator`透過提供要註解的文件的路徑來建立類別：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 第 3 步：建立搜尋文字片段註釋
創建一個`SearchTextFragment`具有所需屬性的對象，例如要搜尋的文字、字體大小、字體系列、字體顏色和背景顏色：
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
## 第四步：新增註釋
使用以下命令將已建立的搜尋文字片段註解新增至文件中`Add`註釋器的方法：
```csharp
annotator.Add(searchText);
```
## 第 5 步：儲存附註解的文檔
將註解文件儲存到指定的輸出路徑：
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
通知使用者文件已成功儲存：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
總之，GroupDocs.Annotation for .NET 簡化了在文件中加入註解的過程，並增強了協作和文件審查過程。透過遵循本指南中概述的步驟，您可以將文件註釋功能無縫整合到您的 .NET 應用程式中。
## 常見問題解答
### GroupDocs.Annotation 是否與所有文件格式相容？
是的，GroupDocs.Annotation 支援多種文件格式，包括 PDF、Microsoft Office 文件、圖像等。
### 我可以自訂註釋的外觀嗎？
絕對地！ GroupDocs.Annotation 為註釋提供了廣泛的自訂選項，可讓您調整字體大小、顏色和樣式等屬性。
### GroupDocs.Annotation 是否有免費試用版？
是的，您可以在購買前免費試用 GroupDocs.Annotation 以探索其功能和功能[這裡](https://releases.groupdocs.com/)..
### 在哪裡可以找到對 GroupDocs.Annotation 的支援？
如需 GroupDocs.Annotation 的支援和協助，您可以存取 GroupDocs[論壇](https://forum.groupdocs.com/c/annotation/10)致力於與註釋相關的查詢和討論。
### 如何取得 GroupDocs.Annotation 的臨時授權？
您可以透過 GroupDocs 取得 GroupDocs.Annotation 的臨時許可證[網站](https://purchase.groupdocs.com/temporary-license/)，使您能夠全面評估產品。