---
"description": "了解如何使用 GroupDocs.Annotation for .NET 為文件新增折線註解。輕鬆增強協作和文件審閱流程。"
"linktitle": "在文件中新增折線註釋"
"second_title": "GroupDocs.Annotation .NET API"
"title": "在文件中新增折線註釋"
"url": "/zh-hant/net/unlocking-annotation-power/add-polyline-annotation/"
"weight": 18
---

# 在文件中新增折線註釋

## 介紹
GroupDocs.Annotation for .NET 是一款功能強大的工具，可讓開發人員以程式方式註解 PDF 和 Microsoft Office 文件。其功能之一是能夠為文件添加折線註釋，從而增強協作和文件審閱流程。
## 先決條件
在繼續本教學之前，請確保您已具備以下條件：
- 您的系統上安裝了 Visual Studio。
- C# 程式語言的基本知識。
- 已安裝 GroupDocs.Annotation for .NET 程式庫。您可以從 [這裡](https://releases。groupdocs.com/annotation/net/).

## 導入命名空間
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 步驟 1：定義輸出路徑
首先，定義註解文檔的儲存輸出路徑。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 步驟 2：初始化註解器
透過提供輸入文件名稱來初始化註釋者。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 步驟3：建立折線註解對象
建立折線註釋物件並設定其屬性，例如位置、訊息、不透明度、筆顏色、筆樣式和筆寬度。
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## 步驟 4：新增折線註釋
使用註釋器物件將折線註解新增至文件。
```csharp
annotator.Add(polyline);
```
## 步驟5：儲存文檔
將註解文件儲存到指定的輸出路徑。
```csharp
annotator.Save(outputPath);
```
## 步驟6：顯示成功訊息
顯示一條確認文件成功保存的訊息。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs.Annotation for .NET 在文件中新增折線註解。此功能增強了協作和文件審閱流程，使用戶能夠更輕鬆地有效地傳達回饋和建議。
## 常見問題解答
### .NET 的 GroupDocs.Annotation 是否與所有文件格式相容？
GroupDocs.Annotation for .NET 支援流行的文件格式，例如 PDF 和 Microsoft Office 格式，包括 Word、Excel 和 PowerPoint。
### 我可以自訂註釋的外觀嗎？
是的，您可以自訂註釋的各種屬性，例如顏色、不透明度、樣式和寬度，以滿足您的要求。
### GroupDocs.Annotation for .NET 是否提供免費試用？
是的，您可以透過造訪以下網址免費試用 GroupDocs.Annotation for .NET [此連結](https://releases。groupdocs.com/).
### 在哪裡可以找到 .NET 的 GroupDocs.Annotation 文件？
您可以找到 GroupDocs.Annotation for .NET 的文檔 [這裡](https://tutorials。groupdocs.com/annotation/net/).
### 如何獲得與 GroupDocs.Annotation for .NET 相關的任何問題或問題的支援？
您可以透過造訪 GroupDocs.Annotation 論壇獲得支持 [這裡](https://forum。groupdocs.com/c/annotation/10).