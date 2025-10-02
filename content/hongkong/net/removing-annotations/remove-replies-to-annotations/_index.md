---
"description": "了解如何使用 GroupDocs.Annotation 在 .NET 中刪除註解回覆。包含程式碼範例的分步指南。"
"linktitle": "在 .NET 中刪除對註釋的回复"
"second_title": "GroupDocs.Annotation .NET API"
"title": "在 .NET 中刪除對註釋的回复"
"url": "/zh-hant/net/removing-annotations/remove-replies-to-annotations/"
type: docs
"weight": 15
---

# 在 .NET 中刪除對註釋的回复

## 介紹
在本教學中，我們將探索如何使用 GroupDocs.Annotation 在 .NET 中刪除註解的回應。 GroupDocs.Annotation 是一個功能強大的 .NET 程式庫，可協助開發人員輕鬆註解文件。無論是新增註解、突出顯示文字或新增圖章，GroupDocs.Annotation 都提供了一套全面的文件註釋工具。
## 先決條件
在開始之前，請確保您符合以下先決條件：
- 具有 C# 和 .NET 程式設計的基本知識。
- 您的系統上安裝了 Visual Studio。
- 已安裝 GroupDocs.Annotation for .NET。您可以從 [這裡](https://releases。groupdocs.com/annotation/net/).
- 了解 GroupDocs.Annotation 中註釋的工作方式。

## 導入命名空間
首先，您需要匯入必要的命名空間來存取 C# 程式碼中的 GroupDocs.Annotation 類別和方法。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## 步驟 1：載入文檔
使用 `Annotator` 班級。
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    // 您的程式碼在此處
}
```
## 步驟2：取得註釋集合
從文件中檢索註釋集合。
```csharp
List<AnnotationBase> annotations = annotator.Get();
```
## 步驟 3：刪除回复
移除註釋的回覆。例如，我們來移除按索引排序的第一個回應。
```csharp
annotations[0].Replies.RemoveAt(0);
```
## 步驟 4：儲存更改
儲存對註釋所做的變更。
```csharp
annotator.Update(annotations);
```
## 步驟5：儲存文檔
將修改後的註解的文件儲存到所需位置。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```
## 步驟6：顯示確認
顯示一則訊息，確認文件已成功儲存。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation 在 .NET 中刪除註解的回應。只需幾個簡單的步驟，您就可以有效率地操作文件中的註解。
## 常見問題解答
### 我可以一次刪除多個回應嗎？
是的，您可以透過遍歷回覆集合並逐一刪除它們來刪除多個回應。
### GroupDocs.Annotation 除了支援 PDF 之外還支援其他文件格式嗎？
是的，GroupDocs.Annotation 支援多種文件格式，包括 Word、Excel、PowerPoint 等。
### GroupDocs.Annotation 有試用版嗎？
是的，您可以從下載免費試用版 [這裡](https://releases。groupdocs.com/).
### 如何取得 GroupDocs.Annotation 的臨時授權？
您可以從 [這裡](https://purchase。groupdocs.com/temporary-license/).
### 在哪裡可以找到有關 GroupDocs.Annotation 的協助和支援？
您可以造訪 GroupDocs.Annotation 論壇 [這裡](https://forum.groupdocs.com/c/annotation/10) 尋求幫助和支持。