---
"description": "了解如何使用 GroupDocs.Annotation 從 .NET 中的 PDF 和其他文件中刪除註解。包含程式碼範例的分步指南。"
"linktitle": "使用 .NET 中的儲存選項刪除註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "使用 .NET 中的儲存選項刪除註釋"
"url": "/zh-hant/net/removing-annotations/remove-annotations-using-save-options/"
"weight": 14
---

# 使用 .NET 中的儲存選項刪除註釋

## 介紹

GroupDocs.Annotation for .NET 是一款功能強大的工具，可協助開發人員輕鬆為其 .NET 應用程式新增註解功能。無論您是在使用文件管理系統、協作平台或任何其他涉及文件處理的應用程序，GroupDocs.Annotation 都能提供一套全面的功能，讓您無縫地註釋 PDF 和其他文件格式。

## 先決條件

在使用 GroupDocs.Annotation for .NET 註解文件之前，請確保您已符合以下先決條件：

### 1. 安裝 GroupDocs.Annotation for .NET

首先下載並安裝 GroupDocs.Annotation for .NET。您可以從 [下載頁面](https://releases。groupdocs.com/annotation/net/).

## 導入命名空間

要在 .NET 專案中開始使用 GroupDocs.Annotation，您需要匯入必要的命名空間。以下是您常用的命名空間：

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


現在，讓我們逐步介紹使用 .NET 中的「儲存選項」功能從文件中刪除註解的過程：

## 步驟 1：定義輸出路徑

首先，定義已刪除註解的文件的儲存路徑。您可以使用 `Path.Combine` 方法將目錄路徑與輸出檔名結合。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 步驟 2：初始化註解器

接下來，初始化一個實例 `Annotator` 類，透過提供包含註釋的文檔的路徑。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // 註釋刪除程式碼將會放在這裡
}
```

## 步驟 3：儲存文件並刪除註釋

現在，使用 `Save` 方法 `Annotator` 類以及 `SaveOptions` 儲存已刪除註釋的文件。在 `SaveOptions`,設定 `AnnotationTypes` 財產 `AnnotationType.None` 刪除所有註釋。

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## 步驟4：顯示成功訊息

最後，顯示一條成功訊息，表示文件已成功儲存並刪除了註釋。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

總而言之，GroupDocs.Annotation for .NET 簡化了從文件中刪除註解的過程。透過遵循上面概述的分步指南，開發人員可以將註釋刪除功能無縫整合到他們的 .NET 應用程式中。

## 常見問題解答

### Q：GroupDocs.Annotation 可以從 PDF 以外的其他文件格式中刪除註解嗎？

答：GroupDocs.Annotation 支援各種文件格式，包括 PDF、Word、Excel 和 PowerPoint，讓您可以從各種文件中刪除註解。

### Q：GroupDocs.Annotation 是否易於整合到現有的 .NET 專案中？

答：是的，GroupDocs.Annotation 提供了簡單的 API 和全面的文檔，使開發人員可以輕鬆地將註釋功能整合到他們的 .NET 應用程式中。

### Q：GroupDocs.Annotation 是否支援選擇性刪除註解？

答：是的，GroupDocs.Annotation 允許開發人員指定要刪除哪些類型的註釋，從而使他們能夠靈活地管理文件中的註釋。

### Q：我可以在購買前免費試用 GroupDocs.Annotation 嗎？

答：是的，您可以從 [發布頁面](https://releases.groupdocs.com/) 在做出購買決定之前探索其功能。

### Q：在哪裡可以獲得 GroupDocs.Annotation 的支援？

答：如需技術援助和社區支持，您可以訪問 [GroupDocs.Annotation 論壇](https://forum。groupdocs.com/c/annotation/10).