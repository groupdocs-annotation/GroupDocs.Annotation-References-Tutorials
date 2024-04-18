---
title: 在文件中新增文字替換註釋
linktitle: 在文件中新增文字替換註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 輕鬆地將文字取代註解新增至 .NET 文件。增強您的文件處理能力。
type: docs
weight: 24
url: /zh-hant/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## 介紹
在本教學中，我們將引導您完成使用 GroupDocs.Annotation for .NET 將文字取代註解新增至文件的流程。這個功能強大的庫允許開發人員以程式設計方式操作和註釋各種類型的文件。在本教程結束時，您將具備將文字替換註解無縫整合到 .NET 應用程式中的知識。
## 先決條件
在開始之前，請確保您已安裝以下先決條件：
### 1.安裝.NET框架
確保您的開發電腦上安裝了 .NET Framework。您可以從 Microsoft 網站下載它。
### 2. .NET 函式庫的 GroupDocs.Annotation
從下列位置下載並安裝 GroupDocs.Annotation for .NET 程式庫[網站](https://releases.groupdocs.com/annotation/net/)。該庫提供了處理各種文檔格式的註釋所需的工具和功能。
### 3. 開發環境搭建
設定您的首選開發環境（例如 Visual Studio）來建立和執行 .NET 應用程式。

## 導入命名空間
在深入編碼部分之前，讓我們先匯入使用 GroupDocs.Annotation for .NET 所需的必要命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在這裡，我們定義保存註解文件的輸出路徑。
## 第 2 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將放置在這裡
}
```
我們透過在 using 區塊中指定輸入文件（「input.pdf」）來初始化 Annotator 對象，以確保正確處置資源。
## 第 3 步：建立替換註釋
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    TextToReplace = "replaced text"
};
```
在這裡，我們建立一個 ReplacementAnnotation 對象，該物件具有各種屬性，例如建立日期、字體顏色、訊息、不透明度、頁碼、背景顏色、點（座標）、回應（評論）和要替換的文字。
## 第四步：新增註釋
```csharp
annotator.Add(replacement);
```
我們將建立的替換註釋新增到註釋器中。
## 第5步：儲存文檔
```csharp
annotator.Save(outputPath);
```
最後，我們將註解文檔儲存到指定的輸出路徑。
## 步驟6：顯示成功訊息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
顯示成功訊息，表示文件已成功儲存。

## 結論
在本教學中，我們介紹了使用 GroupDocs.Annotation for .NET 為文件新增文字取代註解的過程。透過遵循逐步指南並了解先決條件，您可以輕鬆地將此功能整合到您的 .NET 應用程式中。
## 常見問題解答
### 我可以使用 GroupDocs.Annotation for .NET 對不同格式的文件進行註解嗎？
是的，GroupDocs.Annotation for .NET 支援註解各種文件格式，例如 PDF、DOCX、PPTX、XLSX 等。
### GroupDocs.Annotation for .NET 是否同時適用於桌面和 Web 應用程式？
是的，GroupDocs.Annotation for .NET 可以在桌面和 Web 應用程式中使用，為開發人員提供靈活性。
### 我可以自訂使用 GroupDocs.Annotation for .NET 新增的註解的外觀嗎？
當然，您可以透過修改顏色、不透明度、字體等屬性來自訂註解的外觀。
### GroupDocs.Annotation for .NET 是否提供對協作註解功能的支援？
是的，GroupDocs.Annotation for .NET 提供了協作註解功能，讓多個使用者同時註解文件。
### GroupDocs.Annotation for .NET 是否有免費試用版？
是的，您可以免費從以下網站試用 GroupDocs.Annotation for .NET[網站](https://releases.groupdocs.com/).