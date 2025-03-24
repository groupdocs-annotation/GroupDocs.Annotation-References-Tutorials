---
title: 將圖像註釋放在文字上
linktitle: 將圖像註釋放在文字上
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中的文字上新增圖像註釋，以實現高效的文件管理和協作。
weight: 21
url: /zh-hant/net/advanced-usage/put-image-annotation-over-text/
---
## 介紹
在 .NET 開發領域，GroupDocs.Annotation 提供了一個強大的解決方案，用於在文件中添加註釋，從而使協作和文件管理更加高效。一個常見的要求是將圖像註釋放在文字上，這可以使用 GroupDocs.Annotation for .NET 無縫完成。
## 先決條件
在深入研究使用 GroupDocs.Annotation for .NET 在文字上新增圖像註解的過程之前，請確保您具備以下條件：
1.  GroupDocs.Annotation for .NET Library：從下列位置下載並安裝程式庫[這裡](https://releases.groupdocs.com/annotation/net/).
2. 開發環境：設定適當的開發環境，例如 Visual Studio 或任何其他 .NET IDE。
3. 文件和圖像文件：準備文件文件（PDF、DOCX 等）和要用於註釋的圖像文件。
4. 對 C# 的基本了解：要實現本教程中提供的程式碼片段，需要熟悉 C# 程式語言。

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
## 第 1 步：定義輸出路徑
首先，定義儲存註解文件的輸出路徑：
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 第 2 步：初始化註釋器
初始化`Annotator`透過提供輸入文檔路徑來物件：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將會放在這裡
}
```
## 第 3 步：建立圖像註釋
創建一個`ImageAnnotation`具有所需屬性的對象，例如框尺寸、不透明度、頁碼、影像路徑和 z 索引：
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
## 第四步：新增註釋
使用以下命令將圖像註釋新增至文件中`Add`的方法`Annotator`目的：
```csharp
annotator.Add(image);
```
## 第 5 步：儲存附註解的文檔
將註解文件儲存到指定的輸出路徑：
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
顯示一條成功訊息以及帶有註釋的文檔的路徑：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
總之，使用 GroupDocs.Annotation 在 .NET 應用程式中的文字上新增圖像註解是一個簡單的過程。透過遵循本教學中提供的逐步指南，您可以有效地註解文件並增強 .NET 專案中的協作和文件管理功能。
## 常見問題解答
### 我可以為 PDF 以外的文件添加註釋嗎？
是的，GroupDocs.Annotation 支援各種文件格式，例如 DOCX、XLSX、PPTX 等。
### GroupDocs.Annotation 是否有免費試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 如何獲得對 GroupDocs.Annotation 的支援？
您可以從 GroupDocs.Annotation 社群論壇獲得支持[這裡](https://forum.groupdocs.com/c/annotation/10).
### 我需要臨時許可證才能進行測試嗎？
是的，您可以從以下地址獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/)用於測試目的。
### 我可以自訂註釋的外觀嗎？
是的，GroupDocs.Annotation 提供了各種選項來自訂註釋的外觀，例如顏色、不透明度、字體大小等。