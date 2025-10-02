---
"description": "了解如何使用 GroupDocs.Annotation for .NET 為文件新增圖像註解。輕鬆增強文件處理能力。"
"linktitle": "為文件新增影像註解（本機路徑）"
"second_title": "GroupDocs.Annotation .NET API"
"title": "為文件新增影像註解（本機路徑）"
"url": "/zh-hant/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# 為文件新增影像註解（本機路徑）

## 介紹
GroupDocs.Annotation for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式為文件添加各種類型的註解。在本教程中，我們將學習如何使用本機路徑向文件添加圖像註釋。
## 先決條件
在開始之前，請確保您符合以下先決條件：
1. C# 程式語言的基本知識。
2. 您的系統上安裝了 Visual Studio。
3. 在您的專案中安裝 .NET 程式庫或 tutorialsd 的 GroupDocs.Annotation。
4. 輸入文件（例如 PDF）和用於註釋的圖像文件。
## 導入命名空間
首先，您需要將必要的命名空間匯入到您的 C# 檔案中。這些命名空間提供對使用 GroupDocs.Annotation 所需的類別和方法的存取。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 步驟 1：定義輸出路徑
定義註解文檔的儲存輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：初始化註解器
透過提供輸入文件的路徑來初始化註釋器。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 註解程式碼放在這裡
}
```
## 步驟3：建立影像註釋
建立一個實例 `ImageAnnotation` 類別並指定其屬性，如位置、不透明度、頁碼和影像路徑。
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
## 步驟 4：新增註釋
使用 `Add` 註釋器的方法。
```csharp
annotator.Add(image);
```
## 步驟5：儲存文檔
將註解的文檔儲存到輸出路徑。
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示輸出路徑
顯示一則訊息，表示文件儲存成功以及輸出檔案的位置。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增圖像註解。透過遵循這些簡單的步驟，您可以使用強大的註解功能來增強文件處理能力。
## 常見問題解答
### 我可以註釋 PDF 以外的文件嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否與 .NET Core 相容？
是的，GroupDocs.Annotation 與 .NET Framework 和 .NET Core 也相容。
### 我可以自訂註釋的外觀嗎？
當然，您可以根據您的要求自訂註釋的外觀、大小、顏色和其他屬性。
### GroupDocs.Annotation 是否提供協作註釋支援？
是的，GroupDocs.Annotation 提供協作註釋功能，允許多個使用者同時註釋文件。
### 我可以在哪裡找到額外的幫助或支援？
您可以造訪 GroupDocs.Annotation 論壇以獲得社群的協助和支援。