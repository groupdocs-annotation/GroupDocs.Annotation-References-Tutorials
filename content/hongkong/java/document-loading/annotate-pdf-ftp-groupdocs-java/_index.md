---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation for Java 直接從 FTP 伺服器為 PDF 文件新增註解。本逐步指南將協助您簡化文件處理工作流程。"
"title": "使用 GroupDocs.Annotation for Java 從 FTP 註解 PDF —— 完整指南"
"url": "/zh-hant/java/document-loading/annotate-pdf-ftp-groupdocs-java/"
type: docs
"weight": 1
---

# 使用 GroupDocs.Annotation for Java 從 FTP 註解 PDF：完整指南

## 介紹

您是否需要對儲存在 FTP 等遠端伺服器上的文件進行註解？企業和個人通常需要快速添加註釋或高亮顯示，而無需下載整個文件。使用合適的工具，這個過程可以有效率且簡化。本教學將引導您使用 GroupDocs.Annotation for Java，並在從 FTP 伺服器載入 PDF 檔案後直接對其進行註解。

**您將學到什麼：**
- 如何使用 Java 從 FTP 伺服器載入文件。
- 為您的文件新增註解（例如區域突出顯示）的步驟。
- 設定和最佳化 Java GroupDocs.Annotation 使用的最佳實務。

現在，讓我們開始吧！

## 先決條件

在開始之前，請確保您具備以下條件：

- **所需庫**：您需要 Apache Commons Net 來進行 FTP 操作，以及 GroupDocs.Annotation 來進行 Java 開發。請確保您的專案中已提供這些庫。
  
- **環境設定**：本教學假設您已基本了解 Java 開發環境。建議使用 Maven 或 Gradle 等工具來管理相依性。

- **知識前提**：熟悉 Java 程式設計、處理文件流和使用註解是有益的。

## 為 Java 設定 GroupDocs.Annotation

要開始使用 Java 版 GroupDocs.Annotation，您需要在專案中設定該程式庫。如果您使用的是 Maven，請新增以下配置：

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### 許可證獲取

GroupDocs 提供了不同的方式來取得許可證：
- **免費試用**：從免費試用開始探索 GroupDocs.Annotation 的功能。
- **臨時執照**：在評估期間取得臨時許可證以獲得完全存取權限。
- **購買**：考慮購買長期使用的許可證。

若要初始化並設定您的環境，請在您的 Maven 中新增上述依賴項 `pom.xml` 文件。此設定可確保您擁有開始註釋文件所需的所有元件。

## 實施指南

### 從 FTP 載入文檔

#### 概述
本節介紹如何使用 Java 的 Apache Commons Net 函式庫從 FTP 伺服器檢索文件。透過將檔案載入為 InputStream，我們可以將其直接傳遞給 GroupDocs.Annotation 進行處理。

#### 連接並檢索文件

```java
import org.apache.commons.net.ftp.FTPClient;
import java.io.IOException;
import java.io.InputStream;

public static InputStream getFileFromFtp(String server, String filePath) throws IOException {
    // 初始化 FTP 用戶端
    FTPClient client = new FTPClient();
    
    // 連接到 FTP 伺服器
    client.connect(server);
    
    // 檢索指定檔案作為輸入流
    InputStream inputStream = client.retrieveFileStream(filePath);
    
    // 中斷與 FTP 伺服器的連接
    client.disconnect();
    
    return inputStream;
}
```

**解釋**：此方法初始化一個 `FTPClient`，連接到您指定的 FTP 伺服器，檢索檔案作為 `InputStream`，然後斷開連線。確保處理異常，以實現強大的錯誤管理。

### 新增註釋

#### 概述
從 FTP 伺服器載入文件後，我們可以使用 GroupDocs.Annotation 的 Java API 新增註解。這裡我們重點介紹如何加入區域註解。

#### 註釋並保存

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;
import java.io.InputStream;

public static void addAnnotationAndSave(InputStream inputStream, String outputPath) {
    // 使用提供的InputStream初始化註解器
    final Annotator annotator = new Annotator(inputStream);
    
    // 建立新區域註釋
    AreaAnnotation area = new AreaAnnotation();
    
    // 設定註釋的位置和大小（座標 100,100，100x100）
    area.setBox(new Rectangle(100, 100, 100, 100));
    
    // 設定註釋的背景顏色
    area.setBackgroundColor(65535); // ARGB 格式的黃色
    
    // 將註釋新增至文檔
    annotator.add(area);
    
    // 將註解文件儲存到指定的輸出路徑
    annotator.save(outputPath);
    
    // 釋放註釋器使用的資源
    annotator.dispose();
}
```

**解釋**：此程式碼片段初始化一個 `Annotator` 物件與文件的 `InputStream`，建立黃色區域註釋，並儲存。 `Rectangle` 類別定義位置和大小，而 `AreaAnnotation` 管理註釋的細節。

#### 故障排除提示
- 確保正確的 FTP 憑證和權限以避免連線問題。
- 儲存已註解的文件時驗證文件路徑和存取權限。

## 實際應用

1. **法律文件註釋**：快速反白顯示 FTP 伺服器上儲存的合約中的關鍵術語或部分。
2. **文件審查流程**：透過直接從遠端儲存新增註解來促進協作文件審閱。
3. **自動報告分析**：使用腳本自動註解從 FTP 伺服器下載的報告，標記重要指標。

## 性能考慮

- **網路最佳化**：從 FTP 下載檔案時確保連線穩定，以避免中斷。
- **記憶體管理**：高效率處理流和資源，防止應用程式出現記憶體洩漏。處理 `Annotator` 物品使用後應立即丟棄。

## 結論

在本教學中，我們探索如何利用 GroupDocs.Annotation for Java 為從 FTP 伺服器下載的 PDF 新增註解。請依照下列步驟操作，您可以增強組織內的文件處理工作流程。接下來，嘗試將這些功能整合到更大的專案中，或探索 GroupDocs 支援的其他註釋類型。

**後續步驟**：嘗試不同的註釋並考慮自動化批次文件處理的整個過程。

## 常見問題部分

1. **我可以將 GroupDocs.Annotation 與其他雲端儲存服務一起使用嗎？**
   - 是的，您可以調整程式碼以適用於 AWS S3、Google Drive 或任何透過 API 提供檔案存取的服務。
2. **GroupDocs 支援哪些類型的註解？**
   - GroupDocs 支援各種註釋，包括文字、區域、點等。
3. **如何在 Java 中處理 FTP 伺服器連線錯誤？**
   - 圍繞 FTP 操作實施異常處理，以優雅地管理連線問題。
4. **此設定可以用於非 PDF 文件嗎？**
   - 是的，GroupDocs.Annotation 支援多種格式，包括 Word、Excel 和圖片。
5. **優化 FTP 文件載入時間的最佳方法是什麼？**
   - 考慮並行下載或對經常存取的檔案使用快取機制。

## 資源
- [文件](https://docs.groupdocs.com/annotation/java/)
- [API 參考](https://reference.groupdocs.com/annotation/java/)
- [下載](https://releases.groupdocs.com/annotation/java/)
- [購買](https://purchase.groupdocs.com/buy)
- [免費試用](https://releases.groupdocs.com/annotation/java/)
- [臨時執照](https://purchase.groupdocs.com/temporary-license/)
- [支援論壇](https://forum.groupdocs.com/c/annotation/) 

立即開始使用 GroupDocs.Annotation for Java 來簡化您的文件註解流程並提高工作效率！