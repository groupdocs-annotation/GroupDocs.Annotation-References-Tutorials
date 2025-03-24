---
title: 在文件中添加浮水印註釋
linktitle: 在文件中添加浮水印註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 輕鬆地將浮水印註解新增至文件。提高文件的清晰度和安全性。
weight: 28
url: /zh-hant/net/unlocking-annotation-power/add-watermark-annotation/
---

# 在文件中添加浮水印註釋

## 介紹
在本教學中，我們將逐步介紹使用 GroupDocs.Annotation for .NET 在文件中新增浮水印註解的過程。水印註釋可用於指示文件的狀態、將其標記為機密或新增任何其他相關資訊。

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  GroupDocs.Annotation for .NET：您可以從下列位置下載：[這裡](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio：確保您的系統上安裝了 Visual Studio。
3. C# 基礎知識：為了理解和實作程式碼範例，需要熟悉 C# 程式語言。

## 導入命名空間

在開始編碼之前，讓我們先導入必要的名稱空間：

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

現在，我們將新增浮水印註解的過程分解為多個步驟：

## 第 1 步：定義輸出路徑

首先，我們需要定義保存註解文檔的輸出路徑。我們將使用`Path`班級來自`System.IO`命名空間將輸出目錄路徑與檔案名稱組合在一起。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 2 步：初始化註釋器

接下來，我們將透過提供輸入文件的路徑來初始化註釋者。這將使我們能夠向文件添加註釋。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將會放在這裡
}
```

## 步驟 3：建立浮水印註釋

現在，讓我們建立一個具有所需屬性的水印註釋對象，例如角度、位置、文字、字體顏色、不透明度等。

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## 第四步：新增浮水印註釋

現在，我們將使用以下命令將浮水印註解新增至文件中`Add`註釋器物件的方法。

```csharp
annotator.Add(watermark);
```

## 第5步：儲存文檔

最後，我們將註解文檔儲存到指定的輸出路徑。

```csharp
annotator.Save(outputPath);
```

## 結論

在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增浮水印註解。水印註釋是一種有用的工具，可以用相關資訊標記文件或指示其狀態。

## 常見問題解答

### Q：我可以自訂浮水印註解的外觀嗎？

答：是的，您可以自訂各種屬性，如文字、字體大小、顏色、不透明度、位置等，並根據您的要求自訂浮水印。

### Q：GroupDocs.Annotation for .NET 是否相容於不同的文件格式？

答：是的，GroupDocs.Annotation 支援多種文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 和圖片格式。

### Q：我可以在一個文件中新增多個註解嗎？

答：當然可以，GroupDocs.Annotation 允許您在單一文件中新增多個不同類型的註釋，從而實現全面的文件標記。

### Q：GroupDocs.Annotation 是否提供協作註釋支援？

答：是的，GroupDocs.Annotation 透過允許使用者添加評論、回覆和註釋來促進協作註釋，從而促進團隊成員之間的有效協作。

### Q：GroupDocs.Annotation for .NET 是否有試用版？

答：是的，您可以從以下位置下載免費試用版：[這裡](https://releases.groupdocs.com/).