---
title: 在文件中新增文字刪除線註釋
linktitle: 在文件中新增文字刪除線註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 將文字刪除線註解新增至文件。有效增強協作和文件審核流程。
type: docs
weight: 26
url: /zh-hant/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Annotation for .NET 將文字刪除線註解新增至文件。該庫提供了強大的工具來註釋各種文件類型、增強協作和文件審閱流程。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1.  GroupDocs.Annotation for .NET：安裝程式庫。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/annotation/net/).
2. 開發環境：為.NET開發建置合適的開發環境。
3. 文件：準備好要註釋的文檔，例如 PDF 文件。

## 導入命名空間
首先，匯入必要的命名空間以存取 GroupDocs.Annotation 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

現在，讓我們將新增文字刪除線註解的過程分解為多個步驟：
## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在這裡，我們定義保存註解文件的輸出路徑。
## 第 2 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
透過提供輸入文件（本例中為 PDF 文件）的路徑來初始化 Annotator 物件。
## 第 3 步：建立刪除線註釋
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    }
};
```
建立具有所需屬性（例如訊息、不透明度、頁碼、背景顏色、點（座標）和回應）的 StrikeoutAnnotation 物件。
## 第四步：新增註釋
```csharp
annotator.Add(strikeout);
```
將已建立的刪除線註解新增至文件中。
## 第5步：儲存文檔
```csharp
annotator.Save(outputPath);
```
將註解文件儲存到指定的輸出路徑。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增文字刪除線註解。這個功能強大的函式庫可實現高效率的文件註釋，增強協作和文件審閱流程。
## 常見問題解答
### GroupDocs.Annotation 是否相容於各種文件格式？
是的，GroupDocs.Annotation 支援多種文件格式，包括 PDF、Word、Excel、PowerPoint 等。
### 我可以自訂註釋的外觀嗎？
當然，您可以根據您的要求自訂註釋屬性，例如顏色、不透明度、字體大小等。
### GroupDocs.Annotation 是否提供協作功能？
是的，GroupDocs.Annotation 允許使用者在文件中添加評論、回覆和註釋，從而促進協作。
### 有免費試用嗎？
是的，您可以免費試用[這裡](https://releases.groupdocs.com/).
### 在哪裡可以獲得 GroupDocs.Annotation 的支援？
您可以從以下方面獲得支持[GroupDocs.Annotation 論壇](https://forum.groupdocs.com/c/annotation/10).