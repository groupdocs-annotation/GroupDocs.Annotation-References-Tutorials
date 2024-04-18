---
title: 在文件中新增距離註釋
linktitle: 在文件中新增距離註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 為文件新增距離註解。輕鬆增強協作和溝通。
type: docs
weight: 12
url: /zh-hant/net/unlocking-annotation-power/add-distance-annotation/
---
## 介紹
在本教學中，您將學習如何使用 GroupDocs.Annotation for .NET 在文件中新增距離註解。請依照以下步驟完成任務：
## 先決條件

在繼續之前，請確保您具備以下先決條件：

-  GroupDocs.Annotation for .NET 函式庫：從下列位置下載並安裝 GroupDocs.Annotation for .NET 函式庫[這個連結](https://releases.groupdocs.com/annotation/net/).
- 要註釋的文件：準備要新增距離註釋的文件（例如 PDF）。
- 開發環境：使用 Visual Studio 或您選擇的任何其他 IDE 設定您的開發環境。

## 導入命名空間

開始之前，請確保在程式碼中包含必要的命名空間。這些命名空間對於存取所需的類別和方法至關重要。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 第 1 步：初始化註釋器

首先初始化`Annotator`對象，其中包含要註釋的文檔的路徑。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將會放在這裡
}
```

## 第 2 步：建立距離註釋

現在，建立一個`DistanceAnnotation`物件並配置其屬性，例如框尺寸、訊息、不透明度、畫筆顏色等。

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## 第三步：新增註釋

使用以下命令將建立的距離註解新增至文件中`Add`註釋器物件的方法。

```csharp
annotator.Add(distance);
```

## 第 4 步：儲存文檔

將已註記的文件儲存到系統上的所需位置。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## 第5步：顯示確認

最後，顯示一則訊息，確認已成功儲存已包含註釋的文件。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

使用 GroupDocs.Annotation for .NET 為文件新增距離註解是一個簡單的過程。透過遵循本教程中概述的步驟，您可以使用有價值的註釋來增強文檔，從而促進更好的協作和溝通。

## 常見問題解答

### Q：我可以自訂距離註釋的外觀嗎？

答：是的，您可以自訂各種屬性，例如顏色、不透明度、線條樣式等，以滿足您的要求。

### Q：GroupDocs.Annotation 是否支援不同類型文件的註解？

答：是的，GroupDocs.Annotation 支援多種文件格式的註釋，包括 PDF、Word、Excel、PowerPoint 等。

### Q：GroupDocs.Annotation 是否有免費試用版？

答：是的，您可以存取 GroupDocs.Annotation 的免費試用版[這個連結](https://releases.groupdocs.com/).

### Q：在哪裡可以找到 GroupDocs.Annotation for .NET 的文件？

 A：您可以參考詳細的文檔[這裡](https://reference.groupdocs.com/annotation/net/).

### Q：如何獲得 GroupDocs.Annotation 的支援或協助？

答：您可以向 GroupDocs.Annotation 社群論壇尋求支援和協助[這裡](https://forum.groupdocs.com/c/annotation/10).