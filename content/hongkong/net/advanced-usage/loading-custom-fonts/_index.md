---
title: 載入自訂字體
linktitle: 載入自訂字體
second_title: GroupDocs.Annotation .NET API
description: 了解如何在 GroupDocs.Annotation for .NET 中無縫載入自訂字體以增強文件註解。請按照我們的步驟輕鬆整合。
weight: 20
url: /zh-hant/net/advanced-usage/loading-custom-fonts/
---

# 載入自訂字體

## 介紹
GroupDocs.Annotation for .NET 是一個功能強大的程式庫，可讓開發人員輕鬆地將註解功能新增至其 .NET 應用程式。它提供的關鍵功能之一是能夠載入自訂字體，從而增強文件註釋的自訂和靈活性。
## 先決條件
在繼續學習本教程之前，請確保您符合以下先決條件：
1.  GroupDocs.Annotation for .NET Library：從下列位置下載並安裝程式庫[這裡](https://releases.groupdocs.com/annotation/net/).
2. .NET 開發環境：確保您已設定用於 .NET 開發的工作環境。
3. 存取自訂字體：準備要載入到應用程式中的自訂字體。

## 導入命名空間
在您的 .NET 專案中，匯入使用 GroupDocs.Annotation 所需的命名空間：
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 第 1 步：實例化註釋器對象
建立一個實例`Annotator`類，透過提供輸入 PDF 文件的路徑以及自訂字體目錄：
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    //您的進一步操作代碼將位於此處
}
```
## 第 2 步：配置預覽選項
定義預覽選項以指定如何產生文件預覽。您可以設定預覽格式、頁碼等選項：
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## 第 3 步：產生文件預覽
利用`GeneratePreview`的方法`Document`屬性來產生帶有自訂字體的預覽：
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## 第四步：顯示輸出路徑
最後，顯示一則訊息，指示已成功產生文件預覽以及輸出目錄路徑：
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## 結論
總之，在 GroupDocs.Annotation for .NET 中載入自訂字體可讓開發人員根據自己的要求靈活地自訂文件註解。透過遵循本教學中概述的步驟，您可以將自訂字體無縫整合到 .NET 應用程式中，並增強使用者的註釋體驗。
## 常見問題解答
### 我可以同時加載多種自訂字體嗎？
是的，實例化時可以指定多個字型目錄`Annotator`目的。
### 支援的字體類型有限制嗎？
GroupDocs.Annotation for .NET 支援多種字型類型，包括 TrueType (.ttf) 和 OpenType (.otf) 字型。
### 我可以在運行時動態更改載入的字體嗎？
是的，您可以根據需要動態修改字體目錄並重新載入文件註解。
### GroupDocs.Annotation 是否支援在輸出文件中嵌入字型？
是的，您可以在輸出文件中嵌入自訂字體，以確保跨不同平台的一致渲染。
### 有沒有辦法在應用程式中處理字體許可？
GroupDocs.Annotation 提供了管理字體授權的選項，包括用於評估目的的臨時許可。