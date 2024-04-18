---
title: 在文件中新增連結註釋
linktitle: 在文件中新增連結註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 Groupdocs.Annotation for .NET 將連結註解新增至文件。輕鬆增強協作和互動。
type: docs
weight: 16
url: /zh-hant/net/unlocking-annotation-power/add-link-annotation/
---
## 介紹
Groupdocs.Annotation for .NET 是一個功能強大的程式庫，使開發人員能夠輕鬆地將全面的註釋功能整合到他們的 .NET 應用程式中。它提供的關鍵功能之一是能夠為文件添加連結註釋，從而增強協作和互動性。
## 先決條件
在深入了解新增連結註解的過程之前，請確保您符合以下先決條件：
- 對 C# 程式語言有基本了解。
- 為 .NET 函式庫安裝了 Groupdocs.Annotation。
- 存取您想要註釋的文件。

## 導入命名空間
首先，您需要匯入必要的命名空間以利用 Groupdocs.Annotation 實作 .NET 功能。這允許您的應用程式存取註釋文件所需的類別和方法。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 第1步：設定輸出路徑
定義要儲存註解文檔的路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化註釋器
建立一個實例`Annotator`透過提供要註釋的文件的路徑來新增類別。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將會放在這裡
}
```
## 第 3 步：建立連結註釋
定義一個`LinkAnnotation`物件並指定其屬性，例如訊息、不透明度、頁碼、背景顏色、點、回覆和 URL。
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com”
};
```
## 第四步：新增註釋
使用以下命令將已建立的連結註解新增至文件中`Add`註釋器實例的方法。
```csharp
annotator.Add(link);
```
## 第5步：儲存文檔
將註解文件儲存到指定的輸出路徑。
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
通知使用者已成功保存已註釋的文件。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
總而言之，透過執行上述步驟，您可以使用 Groupdocs.Annotation for .NET 將連結註解無縫地新增至文件中。這增強了文件協作並為使用者提供了互動功能。
## 常見問題解答
### Groupdocs.Annotation for .NET 是否與所有類型的文件相容？
Groupdocs.Annotation for .NET 支援多種文件格式，包括 PDF、Word、Excel 等。
### 我可以自訂註釋的外觀嗎？
是的，您可以自訂註釋的各種屬性，例如顏色、不透明度和大小，以滿足您的要求。
### Groupdocs.Annotation for .NET 是否提供即時協作功能？
是的，Groupdocs.Annotation for .NET 提供即時協作功能，讓多個使用者同時註解文件。
### Groupdocs 產品是否提供技術支援？
是的，可以透過論壇和支援獲得 Groupdocs 產品的技術支持[這裡](https://forum.groupdocs.com/c/annotation/10).
### 我可以在購買前嘗試 Groupdocs.Annotation for .NET 嗎？
是的，您可以在購買之前免費試用 Groupdocs.Annotation for .NET 以探索其功能[這裡](https://purchase.groupdocs.com/temporary-license/).