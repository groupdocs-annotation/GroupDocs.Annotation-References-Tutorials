---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中新增橢圓註解。輕鬆增強協作和溝通。"
"linktitle": "在文件中新增橢圓註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "在文件中新增橢圓註釋"
"url": "/zh-hant/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# 在文件中新增橢圓註釋

## 介紹
在本教學中，您將學習如何使用 GroupDocs.Annotation for .NET 在文件中新增橢圓註解。本逐步指南將引導您完成整個過程，確保您清楚地理解每個步驟。
## 先決條件
在開始之前，請確保您已具備以下條件：
1. GroupDocs.Annotation for .NET：請確保您已下載並安裝了 GroupDocs.Annotation for .NET。您可以從以下網址下載： [這裡](https://releases。groupdocs.com/annotation/net/).
2. IDE（整合開發環境）：您需要在系統上安裝一個 IDE，例如 Visual Studio，來編寫和執行程式碼。

## 導入命名空間
首先，將必要的命名空間匯入到您的專案中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 步驟1：設定輸出路徑
定義註解文檔的儲存輸出路徑：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：初始化註解器
透過提供輸入文檔路徑來初始化註釋器：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 步驟 3：建立橢圓註釋
建立一個實例 `EllipseAnnotation` 類別並設定其屬性：
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
    }
};
```
## 步驟 4：新增註釋
將橢圓註解新增至文件：
```csharp
annotator.Add(ellipse);
```
## 步驟5：儲存文檔
將註解後的文件儲存到輸出路徑：
```csharp
annotator.Save(outputPath);
```

## 結論
恭喜！您已成功使用 GroupDocs.Annotation for .NET 為文件新增橢圓註解。現在，您可以將此功能整合到您的 .NET 應用程式中，以增強文件協作和溝通。
## 常見問題解答
### 我可以自訂橢圓註解的外觀嗎？
是的，您可以根據您的要求自訂各種屬性，例如背景顏色、邊框顏色、不透明度等。
### .NET 的 GroupDocs.Annotation 是否與所有文件格式相容？
GroupDocs.Annotation for .NET 支援多種文件格式，包括 PDF、DOCX、PPTX、XLSX 等。
### 我可以在單一文件中新增多個註解嗎？
是的，您可以在單一文件中新增多個註釋，包括橢圓、矩形、文字等。
### 是否有可供測試的試用版？
是的，您可以從下載免費試用版 [這裡](https://releases.groupdocs.com/) 來評估其特徵。
### 在哪裡可以獲得 GroupDocs.Annotation for .NET 的技術支援？
您可以從 GroupDocs.Annotation 社群論壇獲得技術支持 [這裡](https://forum。groupdocs.com/c/annotation/10).