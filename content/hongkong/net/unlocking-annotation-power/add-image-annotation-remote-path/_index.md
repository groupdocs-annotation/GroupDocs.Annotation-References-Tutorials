---
title: 將影像註釋新增至文件（遠端路徑）
linktitle: 將影像註釋新增至文件（遠端路徑）
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 將影像註解新增至文件。透過強大的註解功能增強文件管理。
weight: 15
url: /zh-hant/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## 介紹
在本教學中，我們將逐步介紹使用 GroupDocs.Annotation for .NET 將影像註解新增至文件的過程。該庫提供了強大的工具，用於以程式設計方式註釋各種類型的文件。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1.  GroupDocs.Annotation for .NET：從下列位置下載並安裝程式庫[這裡](https://releases.groupdocs.com/annotation/net/).
2. 開發環境：確保您有一個用於 .NET 開發的工作開發環境。
3. 文件：準備要註釋的文件。對於本教程，我們假設您有一個名為的 PDF 文檔`input.pdf`.
4. 用於註釋的圖像：選擇要用於註釋的圖像。確保您已準備好圖像 URL 或本機路徑。

## 導入命名空間
在開始編碼之前，讓我們先導入必要的名稱空間：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 第1步：設定輸出路徑
首先，定義儲存註解文檔的輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化註釋器
建立一個實例`Annotator`類別並指定輸入文檔。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將會放在這裡
}
```
## 步驟3：新增圖像註釋
現在，讓我們將圖像註釋新增到文件中。我們將指定影像註釋的屬性，例如位置、不透明度、頁碼和影像路徑。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), //指定註解的位置
    CreatedOn = DateTime.Now, //設定建立日期
    Opacity = 0.7, //設定不透明度（0 到 1）
    PageNumber = 0, //指定頁碼
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 提供圖片的網址
};
annotator.Add(image); //新增圖像註釋
```
## 第 4 步：儲存文檔
將註解文件儲存到指定的輸出路徑。
```csharp
annotator.Save(outputPath);
```
## 步驟5：顯示輸出路徑
通知使用者文件儲存操作成功並顯示輸出路徑。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 將影像註解新增至文件。透過執行以下步驟，您可以透過強大的註解功能增強文件管理應用程式。
## 常見問題解答
### GroupDocs.Annotation 可以與 PDF 以外的其他文件格式一起使用嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 與 .NET Core 相容嗎？
是的，GroupDocs.Annotation 與 .NET Framework 和 .NET Core 也相容。
### 我可以自訂註釋的外觀嗎？
是的，您可以自訂註釋的外觀，例如顏色、不透明度和大小。
### GroupDocs.Annotation 是否支援協作註釋功能？
是的，GroupDocs.Annotation 提供了文件即時協作的協作註釋功能。
### 有試用版可供測試嗎？
是的，您可以從以下位置獲得 GroupDocs.Annotation 的免費試用版：[這裡](https://releases.groupdocs.com/).