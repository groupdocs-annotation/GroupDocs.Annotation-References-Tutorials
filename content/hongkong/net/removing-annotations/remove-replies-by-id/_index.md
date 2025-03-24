---
title: 在 .NET 中按 ID 刪除回复
linktitle: 在 .NET 中按 ID 刪除回复
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 在 .NET 中按 ID 刪除回應。按照我們的逐步教學進行高效率的文件註解管理。
weight: 16
url: /zh-hant/net/removing-annotations/remove-replies-by-id/
---
## 介紹
在 .NET 開發領域，管理文件中的註釋的能力對於各種應用程式至關重要。無論您使用的是 PDF、Word 文件還是其他格式，以程式設計方式操作註釋的能力都將開啟一個充滿可能性的世界。 GroupDocs.Annotation 是處理 .NET 中註解的強大工具之一。
## 先決條件
在深入了解使用 GroupDocs.Annotation 在 .NET 中按 ID 刪除回應的教學課程之前，請確保您具備以下先決條件：
### 1.GroupDocs.Annotation安裝
首先，您需要安裝 GroupDocs.Annotation for .NET。您可以從以下位置下載該程式庫[這裡](https://releases.groupdocs.com/annotation/net/)並按照文件中提供的安裝說明進行操作[這裡](https://tutorials.groupdocs.com/annotation/net/).
### 2. 對 C# 和 .NET 的基本了解
要理解本教程中的範例，需要熟悉 C# 程式語言和 .NET 框架。
### 3. 附回覆的註釋文檔
準備一份包含註解和回覆的文件。該文件將作為刪除過程的輸入。

## 導入命名空間
在您的 .NET 專案中，匯入必要的命名空間以存取 GroupDocs.Annotation 功能。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
指定刪除回覆後要儲存修改文件的路徑。
## 第 2 步：載入文件和註釋
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    List<AnnotationBase> annotations = annotator.Get();
```
使用以下命令載入包含註解和回覆的文檔`Annotator`類別並檢索註釋集合。
## 步驟 3：按 ID 刪除回复
```csharp
annotations[0].Replies.RemoveAll(x => x.Id == 4);
```
根據回复 ID 識別要刪除的回复，並將其從相應註釋的回复集合中刪除。
## 第 4 步：儲存更改
```csharp
annotator.Update(annotations);
annotator.Save(outputPath);
```
使用刪除的回覆更新註釋，並將修改後的文件儲存到指定的輸出路徑。
## 第5步：確認成功
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
顯示確認訊息，表示文件已成功儲存並刪除了回覆。

## 結論
總之，GroupDocs.Annotation for .NET 為管理文件中的註解提供了一個簡單的解決方案。透過遵循本教程中概述的步驟，您可以輕鬆地按 ID 刪除回复，從而使您能夠輕鬆有效地根據您的特定要求定製文件註釋。
## 常見問題解答
### GroupDocs.Annotation 可以與 PDF 以外的其他文件格式一起使用嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否有免費試用版？
是的，您可以免費試用[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到對 GroupDocs.Annotation 的支援？
您可以尋求支持並參與社區[這裡](https://forum.groupdocs.com/c/annotation/10).
### 如何取得 GroupDocs.Annotation 的臨時授權？
您可以獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 哪裡可以購買 GroupDocs.Annotation for .NET？
您可以購買 GroupDocs.Annotation[這裡](https://purchase.groupdocs.com/buy).