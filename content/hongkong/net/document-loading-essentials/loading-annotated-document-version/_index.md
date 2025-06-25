---
"description": "了解如何使用 GroupDocs.Annotation for .NET 輕鬆載入已註解的文件版本。簡化協作和審核流程。"
"linktitle": "正在載入已載入的文件版本"
"second_title": "GroupDocs.Annotation .NET API"
"title": "正在載入已載入的文件版本"
"url": "/zh-hant/net/document-loading-essentials/loading-annotated-document-version/"
"weight": 16
---

# 正在載入已載入的文件版本

## 介紹
在當今的數位時代，文件註釋已成為各行各業協作、審核和回饋的重要工具。無論您是將註解功能整合到應用程式中的開發人員，還是希望利用這些功能的用戶，GroupDocs.Annotation for .NET 都能提供強大的解決方案。在本教學中，我們將深入探討使用 GroupDocs.Annotation for .NET 載入註解文件版本的流程。
## 先決條件
在開始之前，請確保您已滿足以下先決條件：
### 1. 安裝 GroupDocs.Annotation for .NET
您可以從 [發布頁面](https://releases.groupdocs.com/annotation/net/)依照提供的安裝說明在您的 .NET 環境中設定庫。
### 2. 取得附註釋的文檔
在本教程中，您需要一個包含註釋的文檔。請確保您擁有一個相容的文件格式（例如 PDF），其中包含要載入的註解。

## 導入命名空間
要啟動此過程，您需要將所需的命名空間匯入到專案中。這些命名空間提供對 GroupDocs.Annotation for .NET 功能的存取。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


現在我們已經介紹了先決條件和命名空間匯入，讓我們深入了解使用 GroupDocs.Annotation for .NET 載入已註解的文件版本的逐步過程。
## 步驟 1：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：指定載入選項
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## 步驟 3：初始化註解器
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## 步驟 4：檢索註釋
```csharp
var annotations = annotator.Get();
```
## 步驟 5：儲存已註記的文檔
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示確認訊息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Annotation for .NET 載入已註解的文件版本。透過遵循逐步指南並利用這個強大的程式庫的功能，您可以將文件註釋功能無縫整合到您的 .NET 應用程式中。
## 常見問題解答
### 我可以使用 GroupDocs.Annotation for .NET 註解各種格式的文件嗎？
是的，GroupDocs.Annotation 支援註解 PDF、DOCX、PPTX、XLSX 等格式的文件。
### GroupDocs.Annotation for .NET 有免費試用版嗎？
是的，您可以從 [這裡](https://releases。groupdocs.com/).
### 在哪裡可以找到 .NET 的 GroupDocs.Annotation 文件？
您可以參考詳細文檔 [這裡](https://tutorials。groupdocs.com/annotation/net/).
### 如何取得 GroupDocs.Annotation for .NET 的臨時授權？
您可以從 [此連結](https://purchase。groupdocs.com/temporary-license/).
### 我可以在哪裡尋求支援或詢問有關 GroupDocs.Annotation for .NET 的問題？
您可以造訪 GroupDocs.Annotation 論壇 [這裡](https://forum。groupdocs.com/c/annotation/10).