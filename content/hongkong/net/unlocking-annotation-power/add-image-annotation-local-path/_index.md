---
title: 將圖像註釋新增至文件（本機路徑）
linktitle: 將圖像註釋新增至文件（本機路徑）
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 將影像註解新增至文件。輕鬆增強文件處理能力。
weight: 14
url: /zh-hant/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## 介紹
GroupDocs.Annotation for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式為文件添加各種類型的註解。在本教程中，我們將學習如何使用本機路徑向文件添加圖像註釋。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
1. C# 程式語言的基礎知識。
2. Visual Studio 安裝在您的系統上。
3. 專案中安裝或引用的 .NET 程式庫的 GroupDocs.Annotation。
4. 輸入文件（例如 PDF）和用於註釋的圖像文件。
## 導入命名空間
首先，您需要將必要的命名空間匯入到 C# 檔案中。這些命名空間提供對使用 GroupDocs.Annotation 所需的類別和方法的存取。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 第 1 步：定義輸出路徑
定義儲存註解文件的輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化註釋器
透過提供輸入文件的路徑來初始化註釋器。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼放在這裡
}
```
## 第 3 步：建立圖像註釋
建立一個實例`ImageAnnotation`類別並指定其屬性，例如位置、不透明度、頁碼和影像路徑。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## 第四步：新增註釋
使用以下命令將已建立的圖像註釋新增至文件中`Add`註釋器的方法。
```csharp
annotator.Add(image);
```
## 第5步：儲存文檔
將註解文檔儲存到輸出路徑。
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示輸出路徑
顯示一則訊息，指示文件已成功儲存以及輸出檔案的位置。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 將影像註解新增至文件。透過執行這些簡單的步驟，您可以透過強大的註解功能來增強文件處理能力。
## 常見問題解答
### 我可以為 PDF 以外的文件添加註釋嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 與 .NET Core 相容嗎？
是的，GroupDocs.Annotation 與 .NET Framework 和 .NET Core 也相容。
### 我可以自訂註釋的外觀嗎？
當然，您可以根據您的需求自訂註釋的外觀、大小、顏色和其他屬性。
### GroupDocs.Annotation 是否提供協作註釋支援？
是的，GroupDocs.Annotation 提供協作註釋功能，使多個使用者能夠同時註釋文件。
### 我可以在哪裡找到額外的幫助或支援？
您可以造訪 GroupDocs.Annotation 論壇以獲得社群的協助和支援。