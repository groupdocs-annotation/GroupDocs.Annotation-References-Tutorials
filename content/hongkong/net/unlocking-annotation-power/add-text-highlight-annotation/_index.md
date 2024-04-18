---
title: 在文件中新增文字突出顯示註釋
linktitle: 在文件中新增文字突出顯示註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 將文字反白顯示註解新增至文件。透過此綜合性增強協作和生產力。
type: docs
weight: 22
url: /zh-hant/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## 介紹
在文件管理和協作領域，GroupDocs.Annotation for .NET 作為一個強大的解決方案出現，使開發人員能夠將文字突出顯示註釋無縫整合到他們的應用程式中。本教學課程作為使用 GroupDocs.Annotation for .NET 為文件新增文字突出顯示註解的綜合指南。透過逐步說明和詳細解釋，您將能夠熟練地利用這個強大的庫的功能。
## 先決條件
在深入研究文本突出顯示註釋的實現之前，請確保滿足以下先決條件：
1. 環境設定：為.NET 開發配置適當的開發環境。
2. 安裝 GroupDocs.Annotation for .NET：從提供的下載並安裝 GroupDocs.Annotation for .NET[下載連結](https://releases.groupdocs.com/annotation/net/).
3. 熟悉 C#：對 C# 程式語言有基本了解。
4. 要註釋的文件：準備要註釋的文件（例如 PDF）。

## 導入命名空間
首先，在 C# 程式碼中匯入必要的命名空間，以利用 GroupDocs.Annotation for .NET 的功能：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#現在，讓我們將添加文字突出顯示註釋的過程分解為多個步驟：
## 第 1 步：定義輸出路徑
指定儲存註解文件的輸出路徑：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化註釋器
建立一個實例`Annotator`類，將文檔文件名作為參數傳遞：
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 第 3 步：建立突出顯示註釋
實例化一個`HighlightAnnotation`物件並配置其屬性：
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## 第四步：新增註釋
將已建立的高亮註解新增至文件：
```csharp
annotator.Add(highlight);
```
## 第 5 步：儲存附註解的文檔
將註解文件儲存到指定的輸出路徑：
```csharp
annotator.Save(outputPath);
```

## 結論
總之，GroupDocs.Annotation for .NET 提供了將文字反白顯示註解合併到文件中的簡化方法。透過遵循本教程中概述的步驟，開發人員可以無縫地增強其應用程式中的文件協作和生產力。
## 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有文件格式相容？
GroupDocs.Annotation for .NET 支援各種文件格式，包括 PDF、Word、Excel 等。請參閱文件以取得完整清單。
### 可以依具體需求客製註解嗎？
是的，開發人員可以完全控制註釋的屬性和外觀，從而可以進行自訂以滿足不同的需求。
### GroupDocs.Annotation for .NET 是否有免費試用版？
是的，您可以透過存取提供的免費試用版來探索 GroupDocs.Annotation for .NET 的功能[關聯](https://releases.groupdocs.com/).
### 對於與 GroupDocs.Annotation for .NET 相關的任何問題或查詢，如何獲得支援？
如需支援和協助，您可以造訪 GroupDocs.Annotation 論壇[這裡](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET 有哪些可用的授權選項？
 GroupDocs.Annotation for .NET 提供各種許可選項，包括用於測試目的的臨時許可證和用於生產環境的商業許可證。造訪購買頁面[這裡](https://purchase.groupdocs.com/buy)更多細節。