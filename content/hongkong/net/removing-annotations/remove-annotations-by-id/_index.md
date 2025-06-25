---
"description": "了解如何使用 GroupDocs.Annotation for .NET 透過 ID 刪除註解。有效率簡化您的文件工作流程。"
"linktitle": "透過 ID 刪除註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "透過 ID 刪除註釋"
"url": "/zh-hant/net/removing-annotations/remove-annotations-by-id/"
"weight": 11
---

# 透過 ID 刪除註釋

## 介紹
在本教學中，我們將引導您完成使用 GroupDocs.Annotation for .NET 透過 ID 刪除註解的過程。註釋可能會使您的文件變得雜亂，而選擇性地刪除註釋可以簡化您的工作流程。我們將逐步指導您，確保您清楚地理解每個階段。
## 先決條件
在深入學習本教程之前，請確保您符合以下先決條件：
1. GroupDocs.Annotation for .NET：請確保您已安裝 GroupDocs.Annotation for .NET 程式庫。您可以從此處下載 [這裡](https://releases。groupdocs.com/annotation/net/).
2. 存取已註解的文件：使用 GroupDocs.Annotation 註解文件。如果您還沒有註釋，可以參考我們先前的教學課程來為文件新增註釋。
3. C# 基礎知識：需要熟悉 C# 程式語言才能理解程式碼範例。

## 導入命名空間
在開始編碼之前，讓我們先導入必要的命名空間：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```

## 步驟 1：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
我們定義已刪除註解的文件的儲存路徑。
## 步驟 2：初始化註解器
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
在這裡，我們初始化 `Annotator` 帶有註釋 PDF 文件路徑的物件。
## 步驟 3：刪除註釋
```csharp
annotator.Remove(0);
```
我們透過指定註釋的 ID 來刪除註釋。在本例中，我們刪除了 ID 為 `0`。您可以替換 `0` 使用您想要刪除的註釋的 ID。
## 步驟4：儲存文檔
```csharp
annotator.Save(outputPath);
```
刪除註解後，我們將修改後的文件儲存到先前指定的輸出路徑。
## 步驟5：顯示成功訊息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
最後，我們顯示一條成功訊息以及保存修改後的文件的路徑。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 透過 ID 刪除註解。此功能有助於透過選擇性刪除註釋來更有效地管理帶有註釋的文件。
## 常見問題解答
### 我可以一次刪除多個註解嗎？
是的，您可以透過在 `Remove` 方法。
### 有沒有辦法撤銷註解的刪除？
不可以，註解一旦刪除，將無法撤銷。刪除註釋前，請務必備份您的文件。
### 我可以從 PDF 以外的文件中刪除註釋嗎？
是的，GroupDocs.Annotation 支援各種文件格式，包括 DOCX、XLSX、PPTX 等。
### 可刪除的註釋數量是否有限制？
不，只要您正確指定註釋的 ID，您就可以從文件中刪除任意數量的註釋。
### 如果我遇到任何問題，可以獲得技術支援嗎？
是的，您可以從 GroupDocs.Annotation 論壇獲得技術支持 [這裡](https://forum。groupdocs.com/c/annotation/10).