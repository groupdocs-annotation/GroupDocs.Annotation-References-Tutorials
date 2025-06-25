---
"date": "2025-05-06"
"description": "了解如何使用強大的 GroupDocs.Annotation for .NET 程式庫透過自訂版本金鑰註解和儲存 PDF，確保每個文件迭代都是唯一可識別的。"
"title": "使用 GroupDocs.Annotation 在 .NET 中儲存帶有自訂版本金鑰的註釋的 PDF"
"url": "/zh-hant/net/document-saving/annotate-pdf-custom-version-key-groupdocs-net/"
"weight": 1
---

# 使用 GroupDocs.Annotation 在 .NET 中儲存帶有自訂版本金鑰的註釋的 PDF

## 介紹
在當今的數位世界中，管理文件版本對於確保協作專案的準確性和可追溯性至關重要。如何有效率地管理和註釋文檔，同時確保每個版本都具有唯一可識別性？本教學將指導您使用自訂版本金鑰保存已註釋的 PDF 文件。 **適用於 .NET 的 GroupDocs.Annotation** 庫。透過利用這個強大的工具，您可以簡化工作流程並增強文件管理實務。

在本文中，我們將探討如何實作文件註釋，並使用特定的版本鍵來儲存註釋，以確保每次迭代都可追溯且獨一無二。您將學習以下內容：
- 如何使用 **適用於 .NET 的 GroupDocs.Annotation** 註釋 PDF 文件。
- 使用自訂鍵儲存註解版本的文件的技術。
- 現實場景中的實際應用。

在開始實現此功能之前，讓我們深入了解先決條件。

## 先決條件
要學習本教程，您需要：

### 所需的庫和版本
- **GroupDocs.註釋** 庫（版本 25.4.0 或更高版本）
- 您的機器上設定了 .NET Framework 或 .NET Core 環境

### 環境設定要求
確保您的開發環境配備以下設備：
- Visual Studio 或支援 C# 的類似 IDE
- 準備註釋的 PDF 文件儲存在可存取的目錄中

### 知識前提
熟悉基本的 C# 程式設計概念並了解 .NET 環境將大有裨益。具備文件處理庫的使用經驗也會有所幫助，但並非強制要求。

## 為 .NET 設定 GroupDocs.Annotation
首先，我們需要設定 **GroupDocs.註釋** 項目中的庫。安裝此套件的主要方法有兩種：

### NuGet 套件管理器控制台
在 NuGet 套件管理器控制台中執行以下命令：
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### .NET CLI
或者，您可以使用 .NET 命令列介面 (CLI)：
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

#### 許可證取得步驟
1. **免費試用**：您可以從下載免費試用版 [GroupDocs 發布](https://releases.groupdocs.com/annotation/net/) 測試圖書館的功能。
2. **臨時執照**：如果您需要更廣泛的測試，請透過以下方式取得臨時許可證 [GroupDocs 臨時許可證頁面](https://purchase。groupdocs.com/temporary-license/).
3. **購買**：如需長期使用，請直接從 [GroupDocs 購買頁面](https://purchase。groupdocs.com/buy).

#### 使用 C# 進行基本初始化和設置
要開始使用 GroupDocs.Annotation for .NET 註解您的文檔，請先初始化一個 `Annotator` 帶有文檔路徑的實例：
```csharp
using GroupDocs.Annotation;
// 定義輸入和輸出目錄的常數
const string INPUT_PDF = "YOUR_DOCUMENT_DIRECTORY/document.pdf";
const string OUTPUT_PATH = Path.Combine("YOUR_OUTPUT_DIRECTORY", "result.pdf");

using (Annotator annotator = new Annotator(INPUT_PDF))
{
    // 進一步的註釋步驟將在此處添加
}
```
這為新增註解和使用自訂版本金鑰保存文件奠定了基礎。

## 實施指南
### 新增註釋
#### 概述
在本節中，我們將示範如何使用兩種類型的註解來註解 PDF 文件： `AreaAnnotation` 和 `EllipseAnnotation`這些將有助於突出顯示文件中的特定區域。

#### 步驟 1：初始化註解器
首先創建一個 `Annotator` 類別與輸入 PDF 的路徑：
```csharp
using (Annotator annotator = new Annotator(INPUT_PDF))
{
    // 註釋步驟如下
}
```
這 `Annotator` 物件允許您有效地管理和應用註釋。

#### 步驟 2：建立 AreaAnnotation 對象
定義區域註解的屬性，包括其位置和顏色：
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 定義位置（x，y）和大小（寬度，高度）
    BackgroundColor = 65535,                // 設定背景顏色的 ARGB 格式
    PageNumber = 1                          // 指定要註解的頁碼
};
```

#### 步驟3：建立EllipseAnnotation對象
類似地，使用所需的屬性設定橢圓註釋：
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 定義位置（x，y）和大小（寬度，高度）
    BackgroundColor = 123456,                // 設定背景顏色的 ARGB 格式
    PageNumber = 1                          // 指定要註解的頁碼
};
```

#### 步驟 4：新增註釋
將兩個註釋添加到您的 `Annotator` 實例：
```csharp
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```
此步驟將您的自訂註解註冊到文件中。

#### 步驟 5：使用自訂版本金鑰儲存已註解的文檔
最後，儲存註解文件並使用 `SaveOptions` 班級：
```csharp
annotator.Save(OUTPUT_PATH, new SaveOptions { Version = "SECOND" });
```
這 `Version` 財產 `SaveOptions` 允許您為文件的每個版本指派一個有意義的標識符。

### 故障排除提示
- 確保輸入和輸出目錄的路徑正確。
- 在繼續註解之前，請透過 NuGet 或 CLI 驗證 GroupDocs.Annotation 的安裝。
- 如果遇到權限問題，請檢查您環境中的檔案存取權限。

## 實際應用
GroupDocs.Annotation 功能多樣，可整合到各種實際場景中：
1. **法律文件審查**：註釋合約以突顯審查過程中需要注意的條款。
2. **學術回饋**：透過在 PDF 中添加註釋或更正來對學生提交的內容提供回饋。
3. **設計協作**：使用註釋進行協作設計評審，標記設計變更的文件。

整合可能性擴展到 .NET 系統和框架，增強了企業應用程式中的文件處理能力。

## 性能考慮
使用 GroupDocs.Annotation 時，請考慮以下效能最佳化提示：
- 透過處理以下操作來優化記憶體使用 `Annotator` 使用後的情況。
- 有效管理資源分配，以順利處理大型文件。
- 應用 .NET 記憶體管理的最佳實踐，確保應用程式的穩定性和回應能力。

## 結論
您已成功學習如何使用 **適用於 .NET 的 GroupDocs.Annotation** 並使用自訂版本密鑰儲存。此功能可確保每個註釋的版本都具有唯一可識別性，從而顯著改善您的文件管理工作流程。

接下來的步驟是探索 GroupDocs.Annotation 的更多功能或將此功能整合到更大的應用程式中。

## 常見問題部分
1. **什麼是適用於 .NET 的 GroupDocs.Annotation？**
   - 一個在 .NET 應用程式中以程式設計方式註解文件的函式庫，提供一系列註解類型和自訂選項。
2. **如何為文件新增多個註解？**
   - 使用 `Add` 方法 `Annotator` 帶有註釋物件清單的實例。
3. **我可以使用不同的標識符保存註解版本嗎？**
   - 是的，透過在 `SaveOptions`。
4. **可以使用 GroupDocs.Annotation 註解哪些類型的文件？**
   - 它支援各種文件格式，如 PDF、Word 文件和圖像。
5. **如何取得 GroupDocs.Annotation 的授權？**
   - 透過以下方式取得許可證 [GroupDocs 購買頁面](https://purchase。groupdocs.com).