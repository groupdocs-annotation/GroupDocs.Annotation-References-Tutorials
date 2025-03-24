---
title: 使用 .NET 中的儲存選項刪除註釋
linktitle: 使用 .NET 中的儲存選項刪除註釋
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation 從 PDF 和 .NET 中的其他文件中刪除註解。帶有程式碼範例的分步指南。
weight: 14
url: /zh-hant/net/removing-annotations/remove-annotations-using-save-options/
---

# 使用 .NET 中的儲存選項刪除註釋

## 介紹

GroupDocs.Annotation for .NET 是一個功能強大的工具，可讓開發人員輕鬆地將註解功能新增至他們的 .NET 應用程式。無論您是在文件管理系統、協作平台或涉及文件處理的任何其他應用程式上工作，GroupDocs.Annotation 都提供了一套全面的功能來無縫註釋 PDF 和其他文件格式。

## 先決條件

在深入使用 GroupDocs.Annotation for .NET 對文件進行註解之前，請確保符合以下先決條件：

### 1.安裝.NET的GroupDocs.Annotation

首先下載並安裝 GroupDocs.Annotation for .NET。您可以從以下位置下載最新版本[download page](https://releases.groupdocs.com/annotation/net/).

## 導入命名空間

要開始在 .NET 專案中使用 GroupDocs.Annotation，您需要匯入必要的命名空間。以下是您常用的命名空間：

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


現在，讓我們逐步了解使用 .NET 中的「儲存選項」功能從文件中刪除註解的過程：

## 第 1 步：定義輸出路徑

首先，定義儲存已刪除註解的文件的輸出路徑。您可以使用`Path.Combine`方法將目錄路徑與輸出檔名組合起來。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 第 2 步：初始化註釋器

接下來，初始化一個實例`Annotator`類，透過提供包含註釋的文檔的路徑。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    //註釋刪除程式碼將會放在這裡
}
```

## 步驟 3：儲存文件並刪除註釋

現在，使用`Save`的方法`Annotator`類與`SaveOptions`儲存已刪除註釋的文件。在裡面`SaveOptions`,設定`AnnotationTypes`財產給`AnnotationType.None`刪除所有註釋。

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## 步驟4：顯示成功訊息

最後，顯示一條成功訊息，表示文件已成功儲存並刪除了註釋。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

總之，GroupDocs.Annotation for .NET 簡化了從文件中刪除註解的過程。透過遵循上述逐步指南，開發人員可以將註解刪除功能無縫整合到他們的 .NET 應用程式中。

## 常見問題解答

### Q：GroupDocs.Annotation 是否可以刪除 PDF 以外的其他文件格式的註解？

答：GroupDocs.Annotation 支援多種文件格式，包括 PDF、Word、Excel 和 PowerPoint，可讓您從各種文件中刪除註解。

### Q：GroupDocs.Annotation 是否易於整合到現有的 .NET 專案中？

答：是的，GroupDocs.Annotation 提供了簡單的 API 和全面的文檔，使開發人員可以輕鬆地將註釋功能整合到他們的 .NET 應用程式中。

### Q：GroupDocs.Annotation 是否支援選擇性刪除註解？

答：是的，GroupDocs.Annotation 允許開發人員指定要刪除的註釋類型，從而使他們能夠靈活地管理文件中的註釋。

### Q：購買前可以免費試用 GroupDocs.Annotation 嗎？

答：是的，您可以從 GroupDocs.Annotation 下載免費試用版[發布頁面](https://releases.groupdocs.com/)在做出購買決定之前探索其功能。

### Q：在哪裡可以獲得 GroupDocs.Annotation 的支援？

答： 如需技術援助和社區支持，您可以訪問[GroupDocs.Annotation 論壇](https://forum.groupdocs.com/c/annotation/10).