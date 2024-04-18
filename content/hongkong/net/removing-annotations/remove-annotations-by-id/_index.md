---
title: 按 ID 刪除註釋
linktitle: 按 ID 刪除註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 按 ID 刪除註解。有效率簡化您的文件工作流程。
type: docs
weight: 11
url: /zh-hant/net/removing-annotations/remove-annotations-by-id/
---
## 介紹
在本教學中，我們將引導您完成使用 GroupDocs.Annotation for .NET 按下 ID 刪除註解的過程。註釋可能會使您的文件變得混亂，選擇性地刪除它們可以簡化您的工作流程。我們將逐步指導您，確保您清楚了解每個階段。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
1.  GroupDocs.Annotation for .NET：確保您已安裝 GroupDocs.Annotation for .NET 程式庫。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/annotation/net/).
2. 存取已註解的文件：使用 GroupDocs.Annotation 註解文件。如果您沒有，您可以按照我們先前的教學課程來註解文件。
3. C# 基礎知識：需要熟悉 C# 程式語言才能理解程式碼範例。

## 導入命名空間
在開始編碼之前，讓我們先導入必要的名稱空間：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```

## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
我們定義儲存已刪除註解的文件的輸出路徑。
## 第 2 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
在這裡，我們初始化`Annotator`帶有註釋的 PDF 文件路徑的物件。
## 第 3 步：刪除註釋
```csharp
annotator.Remove(0);
```
我們透過指定 ID 來刪除註釋。在這個例子中，我們刪除帶有ID的註釋`0`。您可以更換`0`以及您要刪除的註釋的 ID。
## 第 4 步：儲存文檔
```csharp
annotator.Save(outputPath);
```
刪除註解後，我們將修改後的文件儲存到先前指定的輸出路徑中。
## 步驟5：顯示成功訊息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
最後，我們顯示一條成功訊息以及保存修改後的文件的路徑。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 按下 ID 刪除註解。此功能透過選擇性地刪除註釋來幫助更有效地管理帶有註釋的文件。
## 常見問題解答
### 我可以一次刪除多個註解嗎？
是的，您可以透過在`Remove`方法。
### 有沒有辦法撤銷註解的刪除？
不可以，一旦刪除註釋，就無法撤銷。請確保在刪除註釋之前備份您的文件。
### 我可以從 PDF 以外的文件中刪除註釋嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 DOCX、XLSX、PPTX 等。
### 可刪除的註釋數量是否有限制？
不，只要正確指定註釋 ID，您就可以從文件中刪除任意數量的註釋。
### 如果我遇到任何問題，可以獲得技術支援嗎？
是的，您可以從 GroupDocs.Annotation 論壇獲得技術支持[這裡](https://forum.groupdocs.com/c/annotation/10).