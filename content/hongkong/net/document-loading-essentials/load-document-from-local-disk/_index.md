---
title: 從本機磁碟載入文檔
linktitle: 從本機磁碟載入文檔
second_title: GroupDocs.Annotation .NET API
description: 使用 GroupDocs.Annotation for .NET 釋放文件註解的強大功能。將註釋功能無縫整合到您的 .NET 應用程式中。
type: docs
weight: 13
url: /zh-hant/net/document-loading-essentials/load-document-from-local-disk/
---
## 介紹
使用 GroupDocs.Annotation for .NET 釋放文件註解的潛力從未如此簡單。這個強大的工具使開發人員能夠將強大的註釋功能無縫整合到他們的 .NET 應用程式中。在這份綜合指南中，我們將引導您逐步完成利用 GroupDocs.Annotation for .NET 來註解文件的流程。無論您是經驗豐富的開發人員還是新手，本教學都將為您提供增強文件協作和簡化工作流程的知識。
## 先決條件
在深入研究使用 GroupDocs.Annotation for .NET 進行文件註解之前，請確保您具備以下先決條件：
1. C# 基礎知識：熟悉 C# 程式語言基礎至關重要。
2. 安裝 GroupDocs.Annotation for .NET：從下列位置下載並安裝 GroupDocs.Annotation for .NET[這裡](https://releases.groupdocs.com/annotation/net/).
3. 開發環境：使用 Visual Studio 或任何相容的 IDE 設定開發環境。

## 導入命名空間
若要開始使用 GroupDocs.Annotation for .NET 註解文檔，請將必要的命名空間匯入到您的專案中：
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 步驟1：從本機磁碟載入文檔
首先，您需要從本機磁碟載入文件。使用以下程式碼片段：
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 第2步：定義註解區域
接下來，定義註解區域。在此範例中，我們將建立一個 AreaAnnotation：
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## 步驟 3：儲存附註解的文檔
對文件進行註釋後，將其與註釋一起儲存：
```csharp
    annotator.Save(outputPath);
}
```
## 步驟4：顯示成功訊息
最後，顯示一條成功訊息以及輸出路徑：
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
總之，GroupDocs.Annotation for .NET 提供了一個強大的解決方案，將文件註解功能整合到 .NET 應用程式中。透過遵循此逐步指南，您可以輕鬆地為文件添加註釋並增強專案中的協作。
## 常見問題解答
### 可以在購買前試用 GroupDocs.Annotation for .NET 嗎？
是的，您可以從以下位置下載免費試用版[這裡](https://releases.groupdocs.com/).
### 在哪裡可以找到 GroupDocs.Annotation for .NET 的文件？
您可以存取文檔[這裡](https://reference.groupdocs.com/annotation/net/).
### 如何取得 GroupDocs.Annotation for .NET 的臨時授權？
您可以從以下地址取得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).
### 是否支援 GroupDocs.Annotation for .NET？
是的，您可以在 GroupDocs 論壇上找到支持[這裡](https://forum.groupdocs.com/c/annotation/10).
### 哪裡可以購買 GroupDocs.Annotation for .NET？
您可以購買 GroupDocs.Annotation for .NET[這裡](https://purchase.groupdocs.com/buy).