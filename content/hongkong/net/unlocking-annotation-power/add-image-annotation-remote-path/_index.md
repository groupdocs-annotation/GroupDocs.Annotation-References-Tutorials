---
"description": "了解如何使用 GroupDocs.Annotation for .NET 為文件新增圖像註解。強大的註解功能可增強文件管理。"
"linktitle": "新增影像註解（遠端路徑）"
"second_title": "GroupDocs.Annotation .NET API"
"title": "新增影像註解（遠端路徑）"
"url": "/zh-hant/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# 新增影像註解（遠端路徑）

## 介紹
在本教學中，我們將示範如何使用 GroupDocs.Annotation for .NET 在文件中新增影像註解的過程。該庫提供了強大的工具，可用於以程式設計方式註釋各種類型的文件。
## 先決條件
在開始之前，請確保您具備以下條件：
1. GroupDocs.Annotation for .NET：從下列位置下載並安裝程式庫 [這裡](https://releases。groupdocs.com/annotation/net/).
2. 開發環境：確保您已為 .NET 開發設定了有效的開發環境。
3. 文件：準備要註釋的文件。在本教程中，我們假設您有一個名為 `input。pdf`.
4. 用於註釋的圖像：選擇要用於註釋的圖像。請確保已準備好圖像 URL 或本機路徑。

## 導入命名空間
在開始編碼之前，讓我們先導入必要的命名空間：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 步驟1：設定輸出路徑
首先，定義註解文檔的儲存輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：初始化註解器
建立一個實例 `Annotator` 類別並指定輸入文檔。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 註解程式碼將會放在這裡
}
```
## 步驟3：新增圖像註釋
現在，讓我們將圖像註釋新增到文件中。我們將指定影像註釋的屬性，例如位置、不透明度、頁碼和影像路徑。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // 指定註解的位置
    CreatedOn = DateTime.Now, // 設定建立日期
    Opacity = 0.7, // 設定不透明度（0 到 1）
    PageNumber = 0, // 指定頁碼
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 提供圖片的 URL
};
annotator.Add(image); // 新增圖像註釋
```
## 步驟4：儲存文檔
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
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增圖像註解。請按照以下步驟操作，您可以使用強大的註解功能增強文件管理應用程式。
## 常見問題解答
### GroupDocs.Annotation 可以與 PDF 以外的其他文件格式一起使用嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否與 .NET Core 相容？
是的，GroupDocs.Annotation 與 .NET Framework 和 .NET Core 也相容。
### 我可以自訂註釋的外觀嗎？
是的，您可以自訂註釋的外觀，例如顏色、不透明度和大小。
### GroupDocs.Annotation 是否支援協作註釋功能？
是的，GroupDocs.Annotation 提供協作註釋功能，可實現文件的即時協作。
### 是否有可供測試的試用版？
是的，您可以從以下網址免費試用 GroupDocs.Annotation [這裡](https://releases。groupdocs.com/).