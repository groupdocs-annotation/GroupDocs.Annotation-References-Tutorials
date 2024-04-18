---
title: 在文件中新增文字下劃線註釋
linktitle: 在文件中新增文字下劃線註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 為文件新增文字下劃線註解。輕鬆增強協作和溝通。
type: docs
weight: 27
url: /zh-hant/net/unlocking-annotation-power/add-text-underline-annotation/
---
## 介紹
在本教學中，我們將逐步介紹使用 GroupDocs.Annotation for .NET 在文件中新增文字下劃線註解的過程。文字下劃線註釋可用於強調文件的特定部分，例如重要段落或關鍵點。
## 先決條件
在開始之前，請確保您已安裝以下先決條件：
1.  GroupDocs.Annotation for .NET：從下列位置下載並安裝 GroupDocs.Annotation for .NET[這裡](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework：確保您的系統上安裝了 .NET Framework。

## 導入命名空間
首先，讓我們將必要的命名空間匯入到我們的專案中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

現在，讓我們將範例分解為多個步驟：
## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步驟中，我們定義保存已註解的文件的輸出路徑。
## 第 2 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
在這裡，我們初始化一個實例`Annotator`透過提供輸入文件的路徑來建立類別。
## 第 3 步：建立底線註釋
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, //作品僅支援Word和PDF文檔
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
此步驟涉及建立一個`UnderlineAnnotation`具有各種屬性的對象，例如字體顏色、訊息、不透明度、頁碼、背景顏色、底線顏色、點和回應。
## 步驟 4：為文件新增註釋
```csharp
annotator.Add(underline);
```
在這裡，我們將下劃線註釋新增到文件中。
## 第 5 步：儲存附註解的文檔
```csharp
annotator.Save(outputPath);
```
最後，我們將註解文檔儲存到指定的輸出路徑。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增文字下劃線註解。這個功能強大的庫提供了各種註釋選項來增強文件協作和通訊。
## 常見問題解答
### 我可以自訂底線註解的外觀嗎？
是的，您可以根據您的要求自訂顏色、不透明度和位置等屬性。
### GroupDocs.Annotation 是否相容於不同的文件格式？
是的，GroupDocs.Annotation 支援多種文件格式，包括 Word 和 PDF。
### 我可以在一個文件中新增多個註解嗎？
當然，GroupDocs.Annotation 允許您在文件中添加多個不同類型的註釋。
### GroupDocs.Annotation 是否有免費試用版？
是的，您可以從以下位置存取免費試用版：[這裡](https://releases.groupdocs.com/).
### 在哪裡可以獲得 GroupDocs.Annotation 的支援？
您可以從 GroupDocs.Annotation 社群論壇獲得支持[這裡](https://forum.groupdocs.com/c/annotation/10).