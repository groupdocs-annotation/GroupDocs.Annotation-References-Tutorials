---
title: 生成不含註釋的預覽
linktitle: 生成不含註釋的預覽
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 將文件註解功能無縫整合到 .NET 應用程式中。
weight: 14
url: /zh-hant/net/advanced-usage/generate-preview-without-comments/
---
## 介紹
GroupDocs.Annotation for .NET 是一個功能強大的工具，可讓開發人員將註解功能無縫合併到他們的 .NET 應用程式中。無論您是在文件管理系統、協作平台或任何其他需要文件註釋功能的應用程式上工作，GroupDocs.Annotation 都提供了一套全面的工具來增強應用程式的功能。
## 先決條件
在深入使用 GroupDocs.Annotation for .NET 之前，請確保您已設定以下先決條件：
### 1.安裝.NET的GroupDocs.Annotation
首先，您需要下載並安裝 GroupDocs.Annotation for .NET。你可以找到下載鏈接[這裡](https://releases.groupdocs.com/annotation/net/)。請依照文件中提供的安裝說明進行操作，以順利完成設定程序。
### 2. 取得許可證
GroupDocs.Annotation for .NET 需要商業用途授權。您可以從以下位置取得許可證[這裡](https://purchase.groupdocs.com/buy)或選擇臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/)用於測試目的。
### 3.熟悉.NET框架
.NET Framework 和 C# 程式語言的基礎知識對於有效利用 GroupDocs.Annotation for .NET 至關重要。

## 導入命名空間
現在您已經設定了先決條件，讓我們將必要的命名空間匯入到您的 .NET 應用程式中。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

請依照下列逐步說明使用 GroupDocs.Annotation for .NET 產生不含註解的預覽：
## 第 1 步：初始化註釋器
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## 第 2 步：配置預覽選項
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## 步驟 3：指定預覽格式和頁碼
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## 第 4 步：停用評論渲染
```csharp
    previewOptions.RenderComments = false;
```
## 第 5 步：產生預覽
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
完成這些步驟後，您的 .NET 應用程式將能夠從文件產生指定頁面的預覽，而無需呈現註解。

## 結論
透過 GroupDocs.Annotation for .NET，將註解功能合併到 .NET 應用程式中從未如此簡單。透過遵循本教學中概述的步驟，您可以將文件註釋功能無縫整合到您的應用程式中，從而增強協作和文件管理。
## 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有文件格式相容？
GroupDocs.Annotation for .NET 支援多種文件格式，包括 PDF、DOCX、PPTX、XLSX 等。
### 我可以自訂使用 GroupDocs.Annotation for .NET 產生的註解的外觀嗎？
是的，GroupDocs.Annotation for .NET 提供了廣泛的自訂選項，可讓您自訂註解的外觀以滿足您的應用程式的需求。
### GroupDocs.Annotation for .NET 支援多用戶協作嗎？
是的，GroupDocs.Annotation for .NET 提供協作註解功能，使多個使用者能夠同時註解文件。
### GroupDocs.Annotation for .NET 是否提供技術支援？
是的，GroupDocs.Annotation for .NET 的技術支援可透過[支援論壇](https://forum.groupdocs.com/c/annotation/10).
### 可以在購買前免費試用 GroupDocs.Annotation for .NET 嗎？
是的，您可以透過下載免費試用版來探索 GroupDocs.Annotation for .NET 的功能[這裡](https://releases.groupdocs.com/).