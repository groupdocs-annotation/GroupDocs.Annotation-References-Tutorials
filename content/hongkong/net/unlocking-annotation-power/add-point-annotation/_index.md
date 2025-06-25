---
"description": "了解如何使用 GroupDocs.Annotation for .NET 為 PDF 新增點註解。無縫整合的逐步指南。"
"linktitle": "在文件中新增點註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "在文件中新增點註釋"
"url": "/zh-hant/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# 在文件中新增點註釋

## 介紹
GroupDocs.Annotation for .NET 是一款功能強大的工具，可讓開發人員以程式設計方式為文件添加各種類型的註解。在本教學中，我們將重點放在如何使用 C# 在文件中新增點註解 (Point Annotation)。
## 先決條件
在開始之前，請確保您具備以下條件：
1. 對 C# 程式語言有基本的了解。
2. 您的系統上安裝了 Visual Studio。
3. 已安裝 GroupDocs.Annotation for .NET 程式庫。您可以從 [這裡](https://releases。groupdocs.com/annotation/net/).

## 導入必要的命名空間
首先，您需要將所需的命名空間匯入到您的 C# 專案中：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 步驟 1：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步驟中，我們定義註解文件的儲存輸出路徑。
## 步驟 2：初始化註解器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
在這裡，我們初始化 `Annotator` 具有輸入文檔的物件（“input.pdf”）。
## 步驟 3：建立點註釋
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
在此步驟中，我們建立一個 `PointAnnotation` 物件並指定其屬性，例如位置、訊息、頁碼和回覆。
## 步驟 4：新增註釋
```csharp
annotator.Add(point);
```
在這裡，我們將建立的點註釋新增到文件中。
## 步驟5：儲存文檔
```csharp
annotator.Save(outputPath);
```
最後我們將註解後的文檔儲存到指定的輸出路徑。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增點註解。借助這個強大的庫，您可以透過合併註釋功能來增強文件管理應用程式。
## 常見問題解答
### .NET 的 GroupDocs.Annotation 是否與所有文件格式相容？
是的，GroupDocs.Annotation for .NET 支援多種文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以自訂註釋的外觀嗎？
當然！ GroupDocs.Annotation for .NET 提供了豐富的選項，可自訂註解的外觀以滿足您的應用程式需求。
### GroupDocs.Annotation for .NET 有免費試用版嗎？
是的，您可以免費試用 [這裡](https://releases。groupdocs.com/).
### 如何獲得與 GroupDocs.Annotation for .NET 相關的任何問題或問題的支援？
您可以從 GroupDocs.Annotation 論壇獲得支持 [這裡](https://forum。groupdocs.com/c/annotation/10).
### 我可以獲得臨時許可證以用於測試嗎？
是的，你可以從 [這裡](https://purchase。groupdocs.com/temporary-license/).