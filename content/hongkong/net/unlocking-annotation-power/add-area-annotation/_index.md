---
title: 將區域註釋新增至文檔
linktitle: 將區域註釋新增至文檔
second_title: GroupDocs.Annotation .NET API
description: 使用 Groupdocs.Annotation for .NET 增強文件協作。了解如何逐步新增區域註解。
weight: 10
url: /zh-hant/net/unlocking-annotation-power/add-area-annotation/
---
## 介紹
在本教學中，我們將引導您完成使用 Groupdocs.Annotation for .NET 為文件新增區域註解的過程。區域註釋是一項很有價值的功能，它允許使用者突出顯示文件的特定區域，從而提供內容的清晰度和上下文。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1.  Groupdocs.Annotation for .NET：確保安裝了必要的程式庫和相依性。您可以從以下位置下載它們[網站](https://releases.groupdocs.com/annotation/net/).
2. 開發環境：為.NET 開發設定合適的開發環境。

## 導入命名空間
首先，將所需的命名空間匯入到您的專案中。這些命名空間包含使用註解所需的類別和方法。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## 第1步：初始化輸出路徑
定義儲存註解文件的輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：初始化註釋器
建立一個實例`Annotator`透過將文件的路徑作為參數傳遞來建立類別。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //註解程式碼將會放在這裡
}
```
## 第 3 步：建立區域註釋
定義區域註釋的屬性，例如背景顏色、位置、訊息、不透明度等。
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
## 第四步：新增註釋
使用以下命令將區域註解新增至文件中`Add`的方法`Annotator`實例。
```csharp
annotator.Add(area);
```
## 第5步：儲存文檔
將註解文件儲存到指定的輸出路徑。
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
通知使用者文件已成功註釋並儲存。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 Groupdocs.Annotation for .NET 為文件新增區域註解。透過遵循逐步指南，您可以透過有價值的註釋輕鬆增強文檔，從而改善協作和理解。
## 常見問題解答
### 我可以自訂區域註釋的外觀嗎？
是的，您可以自訂各個方面，例如背景顏色、不透明度、筆樣式等，以滿足您的喜好。
### Groupdocs.Annotation 與其他文件格式相容嗎？
是的，Groupdocs.Annotation 支援各種文件格式，包括 PDF、DOCX、PPTX 等。
### 我可以在同一個文件中新增多個註解嗎？
當然，您可以根據需要向同一個文件添加多個不同類型的註釋。
### Groupdocs.Annotation 是否提供跨平台相容性？
是的，Groupdocs.Annotation 與 .NET 框架相容，使其適用於 Windows、Linux 和 macOS 開發環境。
### 是否有可用於測試目的的試用版？
是的，您可以從以下位置存取免費試用版：[網站](https://releases.groupdocs.com/).