---
title: 在文件中新增點註釋
linktitle: 在文件中新增點註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 將點註釋新增至 PDF。無縫整合的逐步指南。
type: docs
weight: 17
url: /zh-hant/net/unlocking-annotation-power/add-point-annotation/
---
## 介紹
GroupDocs.Annotation for .NET 是一個功能強大的工具，可讓開發人員以程式設計方式為文件添加各種類型的註解。在本教程中，我們將重點介紹如何使用 C# 將點註釋新增至文件。
## 先決條件
在我們開始之前，請確保您具備以下條件：
1. 對 C# 程式語言有基本了解。
2. Visual Studio 安裝在您的系統上。
3. 安裝了 .NET 函式庫的 GroupDocs.Annotation。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/annotation/net/).

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
## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
在此步驟中，我們定義保存已註解的文件的輸出路徑。
## 第 2 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
在這裡，我們初始化`Annotator`物件與輸入文檔（“input.pdf”）。
## 第 3 步：建立點註釋
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
在這一步中，我們創建一個`PointAnnotation`物件並指定其屬性，例如位置、訊息、頁碼和回覆。
## 第四步：新增註釋
```csharp
annotator.Add(point);
```
在這裡，我們將建立的點註釋新增到文件中。
## 第5步：儲存文檔
```csharp
annotator.Save(outputPath);
```
最後，我們將註解文檔儲存到指定的輸出路徑。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 將點註解新增至文件中。借助這個強大的庫，您可以透過合併註釋功能來增強文件管理應用程式。
## 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有文件格式相容？
是的，GroupDocs.Annotation for .NET 支援多種文件格式，包括 PDF、Microsoft Word、Excel、PowerPoint 等。
### 我可以自訂註釋的外觀嗎？
絕對地！ GroupDocs.Annotation for .NET 提供了廣泛的選項來自訂註解的外觀以滿足您的應用程式的需求。
### GroupDocs.Annotation for .NET 是否有免費試用版？
是的，您可以免費試用[這裡](https://releases.groupdocs.com/).
### 對於與 GroupDocs.Annotation for .NET 相關的任何問題或查詢，如何獲得支援？
您可以從 GroupDocs.Annotation 論壇獲得支持[這裡](https://forum.groupdocs.com/c/annotation/10).
### 我可以獲得用於測試目的的臨時許可證嗎？
是的，您可以從以下地址獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).