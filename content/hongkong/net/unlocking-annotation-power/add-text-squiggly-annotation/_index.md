---
"description": "了解如何使用 Groupdocs.Annotation for .NET 輕鬆地在文件中新增文字波浪註解。增強協作和文件審查流程。"
"linktitle": "在文件中新增文字波浪註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "在文件中新增文字波浪註釋"
"url": "/zh-hant/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# 在文件中新增文字波浪註釋

## 介紹

Groupdocs.Annotation for .NET 是一個多功能函式庫，可協助開發人員輕鬆地將強大的註解功能整合到其 .NET 應用程式中。無論您處理的是 PDF、Word 文件或其他常用文件格式，Groupdocs.Annotation 都能提供無縫的解決方案，協助您註解文件並增強協作。

## 先決條件

在深入學習本教程之前，請確保您已滿足以下先決條件：

## 導入命名空間

確保匯入必要的命名空間以存取 Groupdocs.Annotation for .NET 提供的功能。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

現在我們已經了解了先決條件，讓我們將添加文字波浪註釋的過程分解為多個步驟。

## 步驟 1：定義輸出路徑

定義註解文檔的儲存路徑。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 步驟 2：初始化註解器

透過提供輸入文件路徑來初始化 Annotator 物件。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 註解程式碼放在這裡
}
```

## 步驟 3：建立波浪註釋

建立一個 SquigglyAnnotation 物件並指定其屬性。

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## 步驟 4：新增註釋

將已建立的波浪註釋新增至文件中。

```csharp
annotator.Add(squiggly);
```

## 步驟5：儲存文檔

將註解文件儲存到指定的輸出路徑。

```csharp
annotator.Save(outputPath);
```

## 步驟6：顯示確認

顯示一則訊息，確認註釋文件已成功儲存。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

總而言之，Groupdocs.Annotation for .NET 為開發人員提供了一套強大的工具，可將文件註釋功能無縫整合到他們的 .NET 應用程式中。按照本逐步指南，您可以輕鬆地在文件中添加文字波浪註釋，從而增強協作和文件審閱流程。

## 常見問題解答

### Q：Groupdocs.Annotation 可以支援各種檔案格式的註解嗎？

答：是的，Groupdocs.Annotation 支援多種文件格式的註釋，包括 PDF、Word 文件、Excel 表格等。

### Q：Groupdocs.Annotation 是否相容於桌面和 Web 應用程式？

答：當然！ Groupdocs.Annotation 可以無縫整合到桌面和 Web 應用程式中，提供靈活性和多功能性。

### Q：Groupdocs.Annotation 是否有任何可用的授權選項？

答：是的，Groupdocs.Annotation 提供靈活的授權選項，以滿足個人或企業的需求，包括用於試用的臨時授權。

### Q：使用 Groupdocs.Annotation 建立的註解可以自訂嗎？

答：當然！ Groupdocs.Annotation 為註釋提供了廣泛的自訂選項，可讓開發人員根據他們的特定需求自訂註釋。

### Q：Groupdocs.Annotation 是否為開發人員提供支援和文件？

答：確實如此！ Groupdocs.Annotation 提供了全面的文件和專門的支援論壇，以幫助開發人員有效地利用其功能。