---
title: 取得文件上的所有版本金鑰
linktitle: 取得文件上的所有版本金鑰
second_title: GroupDocs.Annotation .NET API
description: 了解如何使用 GroupDocs.Annotation for .NET 擷取文件上的所有版本金鑰。透過此綜合功能增強您的文件管理能力。
weight: 16
url: /zh-hant/net/advanced-usage/get-all-version-keys-document/
---

# 取得文件上的所有版本金鑰

## 介紹
在當今快節奏的數位世界中，有效的文件管理對於企業和個人都至關重要。無論您是在專案上進行協作、審查合約還是只是組織文件，擁有正確的工具都可以發揮重要作用。 GroupDocs.Annotation for .NET 提供了在 .NET 應用程式中註解和操作文件的全面解決方案。在本教學中，我們將探討如何利用 GroupDocs.Annotation for .NET 擷取文件上的所有版本金鑰。
## 先決條件
在我們深入學習本教程之前，請確保您符合以下先決條件：
### 1.安裝.NET的GroupDocs.Annotation
首先，您需要下載並安裝 GroupDocs.Annotation for .NET。您可以從以下位置取得最新版本[下載連結](https://releases.groupdocs.com/annotation/net/).
### 2. 取得API憑證
確保您擁有必要的 API 憑證來存取 GroupDocs.Annotation for .NET 功能。

## 導入必要的命名空間
在繼續之前，請確保將所需的命名空間匯入到您的專案中：
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

讓我們將獲取文件上所有版本金鑰的過程分解為簡單的步驟：
## 第 1 步：初始化註釋器對象
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    //代碼放在這裡
}
```
初始化`Annotator`物件包含您要使用的文件的路徑。
## 第 2 步：檢索版本金鑰
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
呼叫`GetVersionsList()`方法上的`Annotator`物件來檢索與文件關聯的所有版本金鑰。此方法傳回版本密鑰清單。

## 結論
GroupDocs.Annotation for .NET 簡化了 .NET 應用程式中的文件註解和操作任務。透過學習本教學課程，您已了解如何使用 GroupDocs.Annotation for .NET 擷取文件上的所有版本金鑰。將此功能合併到您的專案中以增強文件管理功能。
## 常見問題解答
### GroupDocs.Annotation for .NET 是否與所有文件格式相容？
GroupDocs.Annotation for .NET 支援多種文件格式，包括 PDF、DOCX、XLSX、PPTX 等。
### 可以在購買前試用 GroupDocs.Annotation for .NET 嗎？
是的，您可以透過造訪可用的免費試用版來探索 GroupDocs.Annotation for .NET 的功能[這裡](https://releases.groupdocs.com/).
### 如何獲得對 GroupDocs.Annotation for .NET 的支援？
您可以透過支援論壇尋求協助並與社群互動[這裡](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET 是否有可用的臨時授權？
是的，臨時許可證可用於評估目的。您可以從以下位置取得一份[這裡](https://purchase.groupdocs.com/temporary-license/).
### 哪裡可以購買 GroupDocs.Annotation for .NET？
您可以從網站購買 GroupDocs.Annotation for .NET[這裡](https://purchase.groupdocs.com/buy).