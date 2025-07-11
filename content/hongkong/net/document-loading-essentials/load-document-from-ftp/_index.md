---
"description": "使用 GroupDocs.Annotation 增強您的 .NET 應用程序，實現無縫文件註釋。內含逐步教程。"
"linktitle": "從 FTP 載入文檔"
"second_title": "GroupDocs.Annotation .NET API"
"title": "從 FTP 載入文檔"
"url": "/zh-hant/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# 從 FTP 載入文檔

## 介紹
GroupDocs.Annotation for .NET 是一個多功能函式庫，旨在輕鬆實作 .NET 應用程式中的文件註解功能。無論您處理的是 PDF、Microsoft Office 文件、影像或其他格式，此程式庫都能提供統一的解決方案來新增註解（例如評論、高亮和形狀），從而增強協作和文件管理。
## 先決條件
在深入學習本教程之前，請確保您已滿足以下先決條件：
1. C# 知識：熟練 C# 程式語言對於理解和實作本教程中提供的程式碼範例至關重要。
2. GroupDocs.Annotation for .NET：確保從 [下載連結](https://releases.groupdocs.com/annotation/net/)依照安裝說明將程式庫成功整合到您的 .NET 專案中。
## 導入命名空間
為了利用 GroupDocs.Annotation 的 .NET 功能，您需要將所需的命名空間匯入到您的 C# 專案中。請遵循以下步驟：

在您的 C# 專案中，在程式碼檔案的開頭包含必要的命名空間：
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

現在，讓我們深入研究從 FTP 載入文件並使用 GroupDocs.Annotation for .NET 向其添加註解的過程。
## 步驟 1：定義輸出路徑
指定註解文檔的儲存輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟2：從FTP載入文檔
使用提供的檔案路徑從 FTP 伺服器檢索文件。
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // 註釋程式碼將在此處添加
}
```
## 步驟 3：新增註釋
定義並新增所需的註解（例如區域註解）到文件中。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## 步驟 4：儲存附註解的文檔
將註解文件儲存到指定的輸出路徑。
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## 步驟5：從FTP檢索文件
實作從 FTP 伺服器取得檔案的方法。
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## 步驟6：建立FTP請求
產生 FTP 請求來下載檔案。
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## 步驟 7：取得文件流
從 FTP 回應中檢索檔案流。
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## 結論
總而言之，GroupDocs.Annotation for .NET 使開發人員能夠將文件註釋功能無縫整合到他們的 .NET 應用程式中。按照本教程中概述的逐步指南，您可以有效地從 FTP 載入文件並輕鬆添加註釋，從而增強應用程式內的協作和文件管理。
## 常見問題解答
### .NET 的 GroupDocs.Annotation 是否與所有文件格式相容？
是的，GroupDocs.Annotation for .NET 支援多種文件格式，包括 PDF、Microsoft Office 文件、圖像等。
### 我可以自訂使用 GroupDocs.Annotation for .NET 新增的註解的外觀嗎？
當然，GroupDocs.Annotation for .NET 為註釋外觀提供了廣泛的自訂選項，包括顏色、樣式和形狀。
### GroupDocs.Annotation for .NET 是否提供雲端儲存服務的支援？
是的，GroupDocs.Annotation for .NET 與流行的雲端儲存服務無縫集成，讓您可以從 Dropbox、Google Drive 和 OneDrive 等服務載入和儲存文件。
### GroupDocs.Annotation for .NET 有試用版嗎？
是的，您可以透過下載免費試用版來探索 GroupDocs.Annotation for .NET 的功能 [發布頁面](https://releases。groupdocs.com/).
### 如何獲得 GroupDocs.Annotation for .NET 的技術協助或支援？
如需技術協助、故障排除或一般諮詢，您可以造訪 GroupDocs.Annotation for .NET [支援論壇](https://forum。groupdocs.com/c/annotation/10).