---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中在文字上新增圖像註釋，以實現高效的文件管理和協作。"
"linktitle": "將圖像註釋置於文字之上"
"second_title": "GroupDocs.Annotation .NET API"
"title": "將圖像註釋置於文字之上"
"url": "/zh-hant/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# 將圖像註釋置於文字之上

## 介紹
在 .NET 開發領域，GroupDocs.Annotation 提供了一個強大的解決方案，用於為文件添加註釋，從而提高協作和文件管理的效率。一個常見的需求是將圖像註釋添加到文字上，這可以透過 GroupDocs.Annotation for .NET 無縫實現。
## 先決條件
在深入使用 GroupDocs.Annotation for .NET 將圖像註釋放在文字上之前，請確保您已具備以下條件：
1. GroupDocs.Annotation for .NET 函式庫：從下列位置下載並安裝程式庫 [這裡](https://releases。groupdocs.com/annotation/net/).
2. 開發環境：設定適當的開發環境，例如 Visual Studio 或任何其他 .NET IDE。
3. 文件和圖像文件：準備要用於註釋的文件文件（PDF、DOCX 等）和圖像文件。
4. 對 C# 的基本了解：熟悉 C# 程式語言對於實作本教學中提供的程式碼片段是必要的。

## 導入命名空間
在繼續註釋過程之前，請確保在 C# 專案中匯入必要的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 步驟 1：定義輸出路徑
首先，定義註解文檔的儲存輸出路徑：
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 步驟 2：初始化註解器
初始化 `Annotator` 透過提供輸入文檔路徑來物件：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 註解程式碼將會放在這裡
}
```
## 步驟3：建立影像註釋
創建一個 `ImageAnnotation` 具有所需屬性的對象，例如框尺寸、不透明度、頁碼、圖像路徑和 z 索引：
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## 步驟 4：新增註釋
使用 `Add` 方法 `Annotator` 目的：
```csharp
annotator.Add(image);
```
## 步驟 5：儲存已註記的文檔
將註解後的文件儲存到指定的輸出路徑：
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
顯示帶有註釋文檔路徑的成功訊息：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
總而言之，使用 GroupDocs.Annotation 在 .NET 應用程式中為文字添加圖像註釋是一個簡單的過程。請依照本教學提供的逐步指南，您可以有效率地註解文檔，並增強 .NET 專案中的協作和文檔管理功能。
## 常見問題解答
### 我可以註釋 PDF 以外的文件嗎？
是的，GroupDocs.Annotation 支援各種文件格式，例如 DOCX、XLSX、PPTX 等。
### GroupDocs.Annotation 有免費試用版嗎？
是的，您可以從下載免費試用版 [這裡](https://releases。groupdocs.com/).
### 如何獲得 GroupDocs.Annotation 的支援？
您可以從 GroupDocs.Annotation 社群論壇獲得支持 [這裡](https://forum。groupdocs.com/c/annotation/10).
### 我是否需要臨時許可證來進行測試？
是的，你可以從 [這裡](https://purchase.groupdocs.com/temporary-license/) 用於測試目的。
### 我可以自訂註釋的外觀嗎？
是的，GroupDocs.Annotation 提供了各種選項來自訂註釋的外觀，例如顏色、不透明度、字體大小等。