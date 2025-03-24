---
title: 在文件中新增文字波浪註釋
linktitle: 在文件中新增文字波浪註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 Groupdocs.Annotation for .NET 輕鬆地將文字波浪線註解新增至文件中。加強協作和文件審查流程。
weight: 25
url: /zh-hant/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## 介紹

Groupdocs.Annotation for .NET 是一個多功能函式庫，讓開發人員能夠輕鬆地將強大的註解功能整合到他們的 .NET 應用程式中。無論您使用 PDF、Word 文件或其他流行的文件格式，Groupdocs.Annotation 都可以提供用於註釋和增強文件協作的無縫解決方案。

## 先決條件

在深入學習本教程之前，請確保您具備以下先決條件：

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

現在我們已經滿足了先決條件，讓我們將添加文字波浪註釋的過程分解為多個步驟。

## 第 1 步：定義輸出路徑

定義註解文檔的儲存路徑。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 2 步：初始化註釋器

透過提供輸入文件路徑來初始化 Annotator 物件。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼放在這裡
}
```

## 第 3 步：建立波浪形註釋

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

## 第四步：新增註釋

將建立的波浪形註解新增至文件中。

```csharp
annotator.Add(squiggly);
```

## 第5步：儲存文檔

將註解文件儲存到指定的輸出路徑。

```csharp
annotator.Save(outputPath);
```

## 第 6 步：顯示確認訊息

顯示一則訊息，確認已成功儲存已附註解的文件。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

總而言之，Groupdocs.Annotation for .NET 為開發人員提供了一組強大的工具，用於將文件註釋功能無縫整合到他們的 .NET 應用程式中。透過遵循此逐步指南，您可以輕鬆地在文件中添加文字波浪線註釋，從而增強協作和文件審閱流程。

## 常見問題解答

### Q：Groupdocs.Annotation 可以支援各種檔案格式的註解嗎？

答：是的，Groupdocs.Annotation 支援對多種文件格式進行註釋，包括 PDF、Word 文件、Excel 工作表等。

### Q：Groupdocs.Annotation 是否與桌面和 Web 應用程式相容？

答：當然！ Groupdocs.Annotation 可以無縫整合到桌面和 Web 應用程式中，提供靈活性和多功能性。

### Q：Groupdocs.Annotation 是否有可用的授權選項？

答：是的，Groupdocs.Annotation 提供靈活的授權選項，以滿足個人或企業的需求，包括用於試用目的的臨時授權。

### Q：可以自訂使用 Groupdocs.Annotation 建立的註解嗎？

答：當然可以！ Groupdocs.Annotation 為註釋提供了廣泛的自訂選項，可讓開發人員根據其特定要求自訂註釋。

### Q：Groupdocs.Annotation 是否為開發人員提供支援和文件？

答：確實如此！ Groupdocs.Annotation 提供全面的文件和專門的支援論壇，以協助開發人員有效地利用其功能。