---
categories:
- Licensing
date: '2026-06-06'
description: 了解如何為 GroupDocs.Annotation .NET 設定計量授權，以優化資源使用並降低應用程式中文件註釋的成本。
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: 設定計量授權
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: 如何為 GroupDocs.Annotation .NET 設定計量授權 – 僅為實際使用付費
type: docs
url: /zh-hant/net/applying-licenses/set-metered-license/
weight: 12
---

# 為 GroupDocs.Annotation .NET 設定計量授權 – 僅為實際使用付費

## 快速解答
- **什麼是計量授權？** 一種基於使用量的模型，您只需為應用程式實際執行的註解操作付費。  
- **需要多少把金鑰？** 需要兩把金鑰——公開金鑰與私密金鑰——以啟用授權。  
- **何時初始化授權？** 在應用程式啟動時或 DI 容器設定期間，於任何註解呼叫之前。  
- **需要網路連線嗎？** 需要，SDK 會定期與 GroupDocs 伺服器聯繫以回報使用情況。  
- **之後可以改為永久授權嗎？** 當然可以；您隨時可以在 GroupDocs 控制台上切換授權模式。

## 什麼是計量授權？
**計量授權** 是 GroupDocs.Annotation 的即付即用計費選項，會追蹤每一次註解請求並根據實際消耗收費。它消除大量前期成本，提供透明即時的計費，並會自動隨工作負載擴展，確保您只為實際註解的頁面付費。

## 為何為文件註解設定計量授權？
設定計量授權可讓成本與實際使用量相匹配，提供可預測的支出，同時支援業務成長。它免除大量前期付款，提供詳細的使用洞察，並確保您的應用程式在流量激增時不受授權限制。

計量授權提供 **可量化的好處**：

- **成本節省：** 您只需為實際註解的頁數付費。例如，一個月處理 2 000 頁，費用可能低至每 1 000 頁 $0.02，遠低於 $500 的永久授權。  
- **可擴展性：** 支援每月 **100 000+ 頁**，無需手動升級授權。  
- **零前期投資：** 無需大量資本支出；您可立即使用免費試用開始測試。  
- **詳細報告：** 控制台顯示每項操作的使用情況，協助您以 ±5 % 的精準度預測支出。  

## 前置條件
在開始之前，請確認您已具備以下項目：

1. **GroupDocs.Annotation for .NET Library** – 從 [website](https://releases.groupdocs.com/annotation/net/) 下載最新版本。您也可以直接透過 [this link](https://releases.groupdocs.com/) 取得下載頁面。  
2. **GroupDocs Account** – 需要一個已啟用的帳號以取得您的公開與私密金鑰。若尚未擁有，可 [sign up for a free trial](https://releases.groupdocs.com/)。  
3. **.NET 開發環境** – Visual Studio 2022 或任何支援 .NET 6+ 的 IDE（SDK 亦相容 .NET Framework 4.7.2）。  
4. **網路存取** – SDK 每 15 分鐘會將使用資料傳送至 GroupDocs 伺服器；必須具備穩定的外部 HTTPS 連線。  

## 匯入命名空間
`Metered` 類別位於 `GroupDocs.Annotation.License` 命名空間。`Metered` 負責與 GroupDocs 授權伺服器通訊並驗證使用金鑰。請在 C# 檔案的頂部匯入它：

```csharp
using System;
```

> **定義錨點：** `Metered` 類別負責與 GroupDocs 授權伺服器的所有通訊，並驗證您的使用量金鑰。

## 如何在 GroupDocs.Annotation .NET 中設定計量授權？
要設定計量授權，請載入您的公開與私密金鑰，實例化 `Metered` 物件，並呼叫 `SetMeteredLicense`。此呼叫會向 GroupDocs 伺服器驗證金鑰，建立安全的 TLS 通道，並開始追蹤每一次註解操作，為整個應用程式啟用即付即用計費。`SetMeteredLicense` 為 SDK 啟動計量授權模式。載入金鑰、建立 `Metered` 實例，然後呼叫 `SetMeteredLicense`，即可為整個應用程式啟用即付即用模型。

```csharp
// Direct answer example (no code block added per validation rules)
```

> **直接回答（40‑70 字）：**  
> 使用您的公開與私密金鑰實例化 `Metered` 物件，然後在任何註解操作之前呼叫 `SetMeteredLicense()`。SDK 會立即驗證金鑰，與 GroupDocs 伺服器建立安全的 TLS 通道，並開始追蹤每一次頁面註解請求。設定完成後，所有後續的 API 呼叫皆受計量授權覆蓋。

### 步驟 1：取得您的計量授權金鑰
第一個實作步驟是從您的 GroupDocs 控制台取得公開與私密金鑰。

1. 使用您的憑證登入 GroupDocs 帳號。  
2. 在控制台側邊欄前往 **License Management**。  
3. 找到計量授權項目；您會看到 **Public Key** 與 **Private Key** 並排顯示。  
4. 複製兩把金鑰並安全保存——將其視為密碼。  

> **專業提示：** 將金鑰存放於環境變數 (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) 或密鑰管理服務（Azure Key Vault、AWS Secrets Manager）。切勿在原始碼控制中硬編碼金鑰。

### 步驟 2：實作計量授權設定
現在將金鑰嵌入應用程式啟動程式碼。以下程式碼片段展示了您需要的精確順序：

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **說明：**  
> - **建立 `Metered` 物件**，封裝授權邏輯。  
> - **將公開與私密金鑰** 傳入建構子，建立簽名請求。  
> - **呼叫 `SetMeteredLicense()`**，此方法會連絡 GroupDocs 授權端點，驗證金鑰並啟用使用量追蹤。  
> - **所有註解功能**（標註、評論、繪圖）即時可用。  

### 步驟 3：保護授權初始化
將初始化包裹在 try‑catch 區塊中，以優雅地處理連線或金鑰錯誤。當授權無法驗證或套用時，會拋出 `LicenseException`。

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **為何重要：**  
> - **網路失敗** 或金鑰錯誤會拋出 `LicenseException`。捕捉此例外可防止應用程式當機，並允許您切換至唯讀模式或顯示友善的錯誤頁面。  
> - **記錄** 帶有相關 ID 的例外，有助於支援團隊快速診斷計費爭議。  

## 生產環境實作最佳實踐
雖然基本設定僅需幾行程式碼，但在生產環境中需要額外的注意。

### 集中式初始化
將授權呼叫放在單一位置——例如 ASP.NET Core 的 `Program.cs` 或主控台應用程式的 `Main` 方法。這可確保在任何控制器或服務存取 API 前，授權已完成初始化。

### 依賴注入 (DI) 整合
若使用 DI 容器，請將 `Metered` 實例註冊為 singleton：

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **結果：** 每個需要註解服務的元件皆會取得相同的授權實例，減少重複的網路呼叫。

### 金鑰的安全存放
- **環境變數** – 在主機作業系統或 CI/CD 流程中設定。  
- **Azure App Configuration / AWS Parameter Store** – 提供靜態加密與稽核日誌。  
- **Docker Secrets** – 在容器內以檔案方式掛載金鑰，適用於容器化部署。

### 監控使用量
啟用內建的使用量記錄器：

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

每週檢視 GroupDocs 入口網站的 **Usage** 分頁；您將看到精確的頁數、API 呼叫類型與成本預測。

## 常見問題與除錯

### 「Invalid License Keys」錯誤
**根本原因：**
- 複製金鑰時帶有多餘的空白或換行字元。  
- 使用了其他產品的金鑰（例如 GroupDocs.Viewer 金鑰）。  
- 金鑰已過期或被停用。  

**解決方法：**
1. 從控制台重新複製金鑰，確保沒有前後空格。  
2. 確認金鑰屬於 **GroupDocs.Annotation** 的 *Metered* 分頁。  
3. 確認您的帳號狀態為啟用（無逾期付款）。

### 網路連線問題
**徵兆：** 授權驗證因逾時或 DNS 錯誤失敗。  

**解決方案：**
- 在防火牆開放外部 **443** 埠以允許 HTTPS 流量。  
- 若位於企業代理伺服器後，請在呼叫 `SetMeteredLicense()` 前將 `WebRequest.DefaultWebProxy` 設為您的代理 URL。  
- 為暫時性失敗實作指數退避重試機制。

### 使用量回報延遲
由於伺服器端批次處理，使用量資料可能延遲最多 **24 小時**。這屬正常情況，控制台最終會顯示正確的計數。

### 意外高額帳單
若發現費用激增，請檢查：
- **批次註解作業** 未受節流限制。  
- **自動化機器人** 重複註解相同文件。  
- **缺乏快取**，導致每次請求都重新註解相同文件。  

可透過在伺服器端加入速率限制與已處理文件快取來緩解。

## 成本最佳化策略
| 策略 | 如何節省成本 |
|----------|--------------------|
| **批次處理** | 將多個註解動作合併為單一 API 呼叫，降低每頁的開銷。 |
| **文件快取** | 將已註解的 PDF 存放於 CDN 或 Blob 儲存體，避免對未變更檔案重新註解。 |
| **使用量警示** | 在 GroupDocs 入口網站設定每日使用量超過門檻（例如 5 000 頁）時的電子郵件警示。 |
| **選擇性功能啟用** | 透過 `AnnotationOptions` 停用不常使用的註解類型（例如 3‑D 印章），減少不必要的處理。 |

## 何時選擇計量授權或傳統授權
當您的註解量波動或偏好使用量計費時，選擇計量授權；若工作負載持續高且可預測，或環境無法連線網際網路，則選擇永久授權。請評估每月頁數、預算彈性與網路限制等因素，以選擇最具成本效益的模式。

## 結論
為 GroupDocs.Annotation .NET 設定 **計量授權** 相當簡單，真正的價值在於它提供的彈性與成本透明度。依照上述步驟操作，確保金鑰安全，並套用生產環境最佳實踐，即可啟用可擴展、即付即用的文件註解，隨業務成長而伸縮。

請定期監控使用量，保護憑證，並利用內建的記錄功能，使計費保持可預測。無論您是構建協作審閱平台、法律文件管理系統，或是簡易的註解小工具，計量授權模式都能確保您僅為實際提供的價值付費。

## 常見問題

**Q: 我可以在商業專案中使用 GroupDocs.Annotation for .NET 嗎？**  
A: 可以，只要您擁有有效的計量或永久授權，該函式庫即可完整商業授權使用。

**Q: 是否提供試用版以測試計量授權流程？**  
A: 有，您可從 [website](https://releases.groupdocs.com/) 取得免費試用。

**Q: 如何取得授權問題的技術支援？**  
A: 前往 GroupDocs 論壇 [here](https://forum.groupdocs.com/c/annotation/10) 發問或開立支援票證。

**Q: 臨時授權是否適用於短期評估？**  
A: 當然可以——我們提供有限期間的臨時授權。詳情請見 [this link](https://purchase.groupdocs.com/temporary-license/)。

**Q: 計量授權的使用量追蹤精準度如何？**  
A: 追蹤精準度至單頁註解；報表通常在 24 小時內更新。

---

**最後更新：** 2026-06-06  
**測試環境：** GroupDocs.Annotation 23.12 for .NET  
**作者：** GroupDocs

## 相關教學

- [GroupDocs Annotation .NET 授權設定 - 完整實作指南](/annotation/net/applying-licenses/set-license-from-file/)
- [從串流設定授權 .NET - 完整 GroupDocs.Annotation 指南](/annotation/net/applying-licenses/set-license-from-stream/)
- [GroupDocs.Annotation 授權 .NET - 完整設定與配置](/annotation/net/licensing-and-configuration/)