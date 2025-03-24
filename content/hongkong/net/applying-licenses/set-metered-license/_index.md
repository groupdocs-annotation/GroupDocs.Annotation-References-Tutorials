---
title: 設定計量許可證
linktitle: 設定計量許可證
second_title: GroupDocs.Annotation .NET API
description: 了解如何為 GroupDocs.Annotation .NET 設定計量許可證，以實現 .NET 應用程式中的資源使用和文件註解功能。
weight: 12
url: /zh-hant/net/applying-licenses/set-metered-license/
---

# 設定計量許可證

## 介紹
GroupDocs.Annotation for .NET 是一個功能強大的程式庫，可讓開發人員輕鬆地將文件註解功能新增至其 .NET 應用程式。無論您是建立文件管理系統、協作平台或任何涉及文件審查和標記的應用程序，GroupDocs.Annotation for .NET 都提供了一套全面的工具來簡化流程。
在本教學中，我們將深入研究為 GroupDocs.Annotation .NET 設定計量授權的過程。計量許可證允許您只需為您消耗的資源付費，使其成為適合任何規模專案的經濟高效的解決方案。透過執行下面概述的步驟，您將能夠將 GroupDocs.Annotation 無縫整合到您的 .NET 應用程式中，同時優化資源使用並保持預算控制。
## 先決條件
在深入學習本教程之前，請確保您符合以下先決條件：
1.  GroupDocs.Annotation for .NET 函式庫：從下列位置下載資料庫：[網站](https://releases.groupdocs.com/annotation/net/).
2. 存取 GroupDocs 帳戶：您需要一個 GroupDocs 帳戶來取得設定計量許可證所需的公鑰和私密金鑰。如果您還沒有帳戶，可以註冊免費試用[這裡](https://releases.groupdocs.com/).
3. 對 C# 和 .NET Framework 的基本了解：熟悉 C# 程式語言和 .NET Framework 將有助於實作本教學中概述的步驟。

## 導入命名空間
首先，請確保將必要的命名空間匯入到您的 C# 專案中。這些命名空間對於與 GroupDocs.Annotation 功能進行互動至關重要。
```csharp
using System;
```
## 步驟1：取得公鑰和私鑰
在設定計量許可證之前，您需要從 GroupDocs 帳戶儀表板取得公鑰和私鑰。
1. 登入您的 GroupDocs 帳戶。
2. 導航到許可證管理部分。
3. 複製 GroupDocs 提供的公鑰和私鑰。
## 第 2 步：設定計量許可證
獲得公鑰和私鑰後，您可以在 .NET 應用程式中設定計量許可證。
```csharp
string publicKey = "*****"; //將 ***** 替換為您的公鑰
string privateKey = "*****"; //將 ***** 替換為您的私鑰
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 結論
總之，為 GroupDocs.Annotation .NET 設定計量授權是一個簡單的過程，可確保文件註解專案的資源高效利用和成本效益。透過遵循本教學中概述的步驟，您可以將 GroupDocs.Annotation 無縫整合到 .NET 應用程式中，並增強文件協作和審查功能。
## 常見問題解答
### 我可以在商業專案中使用 GroupDocs.Annotation for .NET 嗎？
是的，GroupDocs.Annotation for .NET 可用於商業和非商業專案。但是，您需要根據您的專案要求取得適當的許可證。
### GroupDocs.Annotation for .NET 有沒有試用版？
是的，您可以存取 GroupDocs.Annotation for .NET 免費試用版[這個連結](https://releases.groupdocs.com/).
### 如何獲得 GroupDocs.Annotation for .NET 的技術支援？
您可以造訪 GroupDocs 論壇尋求技術支持[這裡](https://forum.groupdocs.com/c/annotation/10).
### 是否有可用的臨時許可證選項？
是的，您可以從 GroupDocs 取得臨時許可證以用於短期使用或評估目的。訪問[這個連結](https://purchase.groupdocs.com/temporary-license/)了解更多。
### 我可以根據我的專案需求自訂註釋功能嗎？
是的，GroupDocs.Annotation for .NET 提供了廣泛的自訂選項，可讓您自訂註解功能以滿足您的特定專案需求。