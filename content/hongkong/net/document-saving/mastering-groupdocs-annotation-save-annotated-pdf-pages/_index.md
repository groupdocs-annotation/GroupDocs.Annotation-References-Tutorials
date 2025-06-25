---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation for .NET 有效率地僅儲存 PDF 中註解的頁面。本指南詳盡，助您增強文件管理與協作。"
"title": "如何使用 GroupDocs.Annotation for .NET 將已註解的頁面儲存為 PDF"
"url": "/zh-hant/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# 如何使用 GroupDocs.Annotation for .NET 將已註解的頁面儲存為 PDF

## 介紹

還在為保存 PDF 文件中帶註釋的特定頁面而苦惱嗎？本指南將示範如何使用 GroupDocs.Annotation for .NET 有效率地實現這一目標。利用註釋功能，您可以專注於相關內容，從而簡化文件管理並增強協作。

在本教程中，您將學習：
- 使用 GroupDocs.Annotation 設定您的開發環境
- 新增各種類型的註釋
- 有效地保存註釋的頁面

準備好開始了嗎？讓我們確保您一切就緒。

### 先決條件

在開始之前，請確保您已具備以下條件：
- **.NET 框架** （4.6 或更高版本）或 **.NET Core/5+**
- 像 Visual Studio 這樣的程式碼編輯器
- C# 和 .NET 專案設定的基礎知識

## 為 .NET 設定 GroupDocs.Annotation

要開始使用 GroupDocs.Annotation，請透過 NuGet 安裝它。

**NuGet 套件管理器控制台**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### 許可證獲取

GroupDocs 提供免費試用，方便使用者全面探索其軟體。如需長期使用，請購買許可證或申請臨時許可證：
- **免費試用**：在初始階段探索不受限制的功能。
- **臨時執照**：在生產中暫時使用 GroupDocs.Annotation。
- **購買**：使用商業許可證來保障您的長期需求。

安裝後，如下初始化庫：

```csharp
using GroupDocs.Annotation;

// 載入和註釋文檔的基本設置
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## 實施指南

### 新增註釋

#### 概述

註釋有助於突出顯示文件中的重要區域。讓我們來探索如何添加 `AreaAnnotation` 和一個 `EllipseAnnotation`。

**步驟 1：建立區域註釋**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// 定義區域註釋
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置和大小
    BackgroundColor = 65535,                // 高亮的 ARGB 顏色值
    PageNumber = 1                          // 具體頁碼
};
```

這 `AreaAnnotation` 突出顯示文件中的矩形區域。自訂其位置（`Box`）和背景顏色。

**步驟 2：建立橢圓註釋**

```csharp
// 定義橢圓註釋
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置和大小
    BackgroundColor = 123456,                // 高亮的 ARGB 顏色值
    PageNumber = 1                           // 具體頁碼
};
```

這 `EllipseAnnotation` 允許在文件上繪製橢圓形。使用 `Box` 財產。

**步驟 3：新增註釋**

```csharp
// 在 Annotator 實例中新增註釋
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

使用 `Add` 方法，包括多種類型的註釋。此步驟同時新增了 `AreaAnnotation` 和 `EllipseAnnotation`。

### 僅儲存附註解的頁面

#### 概述

若要僅儲存包含註解的頁面，請相應地配置儲存選項。

**步驟 4：儲存附註解的頁面**

```csharp
using GroupDocs.Annotation.Options;

// 設定儲存選項以僅包含帶註釋的頁面
annotator.Save("path/to/output/document.pdf\