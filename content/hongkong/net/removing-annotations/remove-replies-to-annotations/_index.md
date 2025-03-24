---
title: 刪除 .NET 中註釋的回复
linktitle: 刪除 .NET 中註釋的回复
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 刪除 .NET 中註解的回應。帶有程式碼範例的分步指南。
weight: 15
url: /zh-hant/net/removing-annotations/remove-replies-to-annotations/
---

# 刪除 .NET 中註釋的回复

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Annotation 刪除 .NET 中註解的回應。 GroupDocs.Annotation 是一個功能強大的 .NET 程式庫，可讓開發人員輕鬆註解文件。無論是新增註解、突出顯示文字或新增圖章，GroupDocs.Annotation 都提供了一套全面的文件註釋工具。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
- C# 和 .NET 程式設計的基礎知識。
- Visual Studio 安裝在您的系統上。
- 安裝了 .NET 的 GroupDocs.Annotation。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/annotation/net/).
- 了解註釋在 GroupDocs.Annotation 中的工作原理。

## 導入命名空間
首先，您需要匯入必要的命名空間以存取 C# 程式碼中的 GroupDocs.Annotation 類別和方法。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## 第 1 步：載入文檔
使用以下命令載入包含註解和回覆的文檔`Annotator`班級。
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    //你的程式碼放在這裡
}
```
## 第2步：取得註釋集合
從文件中檢索註釋集合。
```csharp
List<AnnotationBase> annotations = annotator.Get();
```
## 第 3 步：刪除回复
刪除對註釋的回應。例如，讓我們按索引刪除第一個回應。
```csharp
annotations[0].Replies.RemoveAt(0);
```
## 第 4 步：儲存更改
儲存對註釋所做的變更。
```csharp
annotator.Update(annotations);
```
## 第5步：儲存文檔
將帶有修改後的註釋的文件儲存到所需位置。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```
## 第 6 步：顯示確認訊息
顯示一則訊息，確認文件已成功儲存。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation 刪除 .NET 中註解的回應。只需幾個簡單的步驟，您就可以有效率地操作文件中的註解。
## 常見問題解答
### 我可以一次刪除多個回應嗎？
是的，您可以透過迭代回應集合併一一刪除它們來刪除多個回應。
### GroupDocs.Annotation 是否支援 PDF 以外的其他文件格式？
是的，GroupDocs.Annotation 支援多種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 是否有試用版？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 如何取得 GroupDocs.Annotation 的臨時授權？
您可以從以下地址取得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 在哪裡可以找到 GroupDocs.Annotation 的協助和支援？
您可以造訪 GroupDocs.Annotation 論壇[這裡](https://forum.groupdocs.com/c/annotation/10)尋求幫助和支持。