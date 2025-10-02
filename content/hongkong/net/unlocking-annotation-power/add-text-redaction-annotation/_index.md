---
"description": "了解如何使用 GroupDocs.Annotation for .NET 在 PDF 文件中新增文字編輯註解。輕鬆保護敏感資訊。"
"linktitle": "為文件新增文字編輯註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "為文件新增文字編輯註釋"
"url": "/zh-hant/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# 為文件新增文字編輯註釋

## 介紹
在文件中加入文字編輯註解是安全管理敏感資訊的關鍵步驟。 GroupDocs.Annotation for .NET 提供了一個強大的解決方案，可以無縫實現這一點。在本教學中，我們將逐步指導您完成在文件中新增文字編輯註解的過程。
## 先決條件
在開始之前，請確保您已滿足以下先決條件：
1. GroupDocs.Annotation for .NET：確保您已安裝 GroupDocs.Annotation for .NET 程式庫。您可以從 [網站](https://releases。groupdocs.com/annotation/net/).
2. 開發環境：使用與 .NET 相容的 IDE（例如 Visual Studio）設定開發環境。

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
## 步驟 1：定義輸出路徑
定義要儲存帶有註解文檔的輸出路徑。確保該路徑可存取且可寫入。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：初始化註解器
使用輸入文檔路徑初始化註解器。替換 `"input.pdf"` 以及您的文件的路徑。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 註解程式碼將會放在這裡
}
```
## 步驟 3：建立文字編輯註釋
創建一個 `TextRedactionAnnotation` 具有所需屬性的對象，例如 `PageNumber`， `FontColor`， 和 `Points`根據您的要求自訂註釋。
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## 步驟 4：新增註解並儲存
使用註釋器將建立的註解新增至文件中，並將註解後的文件儲存到指定的輸出路徑。
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## 步驟5：檢查輸出
最後確認文件已成功儲存到指定的輸出路徑。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們示範如何使用 GroupDocs.Annotation for .NET 在文件中新增文字修訂註解的過程。完成這些步驟後，您現在可以安全地管理文件中的敏感資訊。
## 常見問題解答
### 我可以自訂文字編輯註釋的外觀嗎？
是的，您可以自訂各種屬性，例如字體顏色、填滿顏色和不透明度，以滿足您的要求。
### 購買前是否有試用版？
是的，您可以從 [網站](https://releases。groupdocs.com/).
### 如果我遇到任何問題，如何獲得支援？
您可以從 GroupDocs.Annotation 社群論壇獲得支持 [這裡](https://forum。groupdocs.com/c/annotation/10).
### 我是否需要臨時許可證來進行測試？
是的，你可以從 [購買頁面](https://purchase.groupdocs.com/temporary-license/) 用於測試。
### 我可以在單一文件中新增多個註解嗎？
當然，GroupDocs.Annotation 允許您為單一文件添加各種類型的註解和多個實例。