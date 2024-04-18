---
title: 載入已註解的文檔版本
linktitle: 載入已註解的文檔版本
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 輕鬆載入已註解的文件版本。簡化協作和審核流程。
type: docs
weight: 16
url: /zh-hant/net/document-loading-essentials/loading-annotated-document-version/
---
## 介紹
在現今的數位時代，文件註釋已成為各行業協作、審閱和回饋的重要工具。無論您是將註釋功能整合到應用程式中的開發人員還是希望利用這些功能的用戶，GroupDocs.Annotation for .NET 都提供了強大的解決方案。在本教學中，我們將深入研究使用 GroupDocs.Annotation for .NET 載入已註解的文件版本的過程。
## 先決條件
在我們開始之前，請確保您具備以下先決條件：
### 1.安裝.NET的GroupDocs.Annotation
您可以從以下位置下載必要的文件[發布頁面](https://releases.groupdocs.com/annotation/net/)。依照提供的安裝說明在 .NET 環境中設定庫。
### 2. 取得附註釋的文檔
對於本教程，您將需要帶有註釋的文檔。確保您擁有包含要載入的註解的相容文件格式（例如 PDF）。

## 導入命名空間
要啟動流程，您需要將所需的命名空間匯入到您的專案中。這些命名空間提供對 GroupDocs.Annotation for .NET 功能的存取。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


現在我們已經介紹了先決條件和命名空間導入，接下來讓我們深入了解使用 GroupDocs.Annotation for .NET 載入已註解的文件版本的逐步過程。
## 第 1 步：定義輸出路徑
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 第 2 步：指定載入選項
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## 第 3 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## 第 4 步：檢索註釋
```csharp
var annotations = annotator.Get();
```
## 第 5 步：儲存附註解的文檔
```csharp
annotator.Save(outputPath);
```
## 第 6 步：顯示確認訊息
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Annotation for .NET 載入已註解的文件版本。透過遵循逐步指南並利用這個強大庫的功能，您可以將文件註釋功能無縫整合到您的 .NET 應用程式中。
## 常見問題解答
### 我可以使用 GroupDocs.Annotation for .NET 對各種格式的文件進行註解嗎？
是的，GroupDocs.Annotation 支援對 PDF、DOCX、PPTX、XLSX 等格式的文件進行註解。
### GroupDocs.Annotation for .NET 是否有免費試用版？
是的，您可以從以下位置存取免費試用版：[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到 GroupDocs.Annotation for .NET 的文件？
您可以參考詳細文檔[這裡](https://reference.groupdocs.com/annotation/net/).
### 如何取得 GroupDocs.Annotation for .NET 的臨時授權？
您可以從以下位置取得臨時許可證[這個連結](https://purchase.groupdocs.com/temporary-license/).
### 我可以在哪裡尋求有關 GroupDocs.Annotation for .NET 的支援或提出問題？
您可以造訪 GroupDocs.Annotation 論壇[這裡](https://forum.groupdocs.com/c/annotation/10).