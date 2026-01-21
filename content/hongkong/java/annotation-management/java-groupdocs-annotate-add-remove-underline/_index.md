---
categories:
- Java Development
date: '2025-12-21'
description: 學習如何使用 GroupDocs.Annotation 在 Java 中建立乾淨的 PDF 檔案並對 PDF 進行註釋，提供完整的程式碼範例與故障排除技巧。
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 使用 Java 建立乾淨 PDF - 使用 GroupDocs 添加底線註釋
type: docs
url: /zh-hant/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# 建立 Clean PDF Java：使用 GroupDocs 的底線註解

## 介紹

在 Java 應用程式中處理文件管理與協作時感到困擾嗎？你並不孤單。許多開發者都面臨在不同檔案格式間實作穩定文件註解功能的挑戰。

在本指南中，你將 **建立 clean PDF Java** 檔案，並學習如何使用 GroupDocs.Annotation **在 Java 中註解 PDF**。完成本教學後，你將清楚知道如何加入帶有評論的底線註解、移除既有註解，並將這些功能無縫整合到專案中。

**本指南將讓你掌握的內容：**
- 以正確方式在 Java 專案中設定 GroupDocs.Annotation  
- 使用自訂評論與樣式加入底線註解  
- 移除所有註解以產生 clean document 版本  
- 疑難排解開發者常見問題  
- 為正式環境優化效能  

無論你是建置文件審閱系統、教育平台，或是協作編輯工具，本教學都提供實用、經過測試的程式碼範例。

## 快速回答
- **如何加入底線註解？** 使用 `UnderlineAnnotation` 並呼叫 `annotator.add()` 後儲存文件。  
- **如何建立 clean PDF Java 檔案？** 載入已註解的檔案，在 `SaveOptions` 中設定 `AnnotationType.NONE`，再儲存為新副本。  
- **需要哪些函式庫？** GroupDocs.Annotation v25.2（或更新版本）以及其 Maven 套件庫。  
- **正式環境需要授權嗎？** 需要——套用有效的 GroupDocs 授權以避免浮水印。  
- **能否有效率地處理多個文件？** 在每個檔案使用 try‑with‑resources 包住 `Annotator`，處理完畢後釋放資源。

## 如何建立 clean PDF Java 檔案
建立 clean PDF Java 檔案即是產生一個 **不含任何註解** 的文件版本，同時保留原始內容。這在最終發佈、歸檔，或在審閱流程結束後需要分享「乾淨」副本時非常有用。

GroupDocs.Annotation 讓此操作變得簡單：載入已註解的檔案、將 `SaveOptions` 設定為排除所有註解類型，然後儲存結果。相關步驟稍後會在 **移除註解** 章節說明。

## 如何在 Java 中使用 GroupDocs 註解 PDF
GroupDocs.Annotation 提供功能豐富的 API，讓你 **在 Java 中註解 PDF**。它支援多種註解類型，包括高亮、印章與底線。本教學聚焦於底線註解，因為它常用於強調文字，同時支援串接評論。

## 前置條件與環境設定

### 開始前你需要的項目

**開發環境需求：**
- Java Development Kit (JDK) 8 或以上（建議 JDK 11+）  
- Maven 3.6+ 或 Gradle 6.0+ 以管理相依性  
- IntelliJ IDEA、Eclipse 或配備 Java 擴充功能的 VS Code 等 IDE  
- 至少 2 GB 可用記憶體（文件處理可能相當吃記憶體）

**知識前置條件：**
你應熟悉基本的 Java 概念——物件初始化、方法呼叫與 Maven 相依性。若有使用第三方函式庫的經驗，會更快上手。

**測試文件：**
準備幾份範例 PDF。文字型 PDF 效果最佳；掃描圖像可能需要先做 OCR 才能註解。

### Maven 設定：將 GroupDocs 加入專案

以下說明如何正確設定 Maven 專案（許多開發者第一次嘗試時常卡關）：

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

**重要提示：** 版本 25.2 為撰寫本文時的最新穩定版。請定期檢查 GroupDocs 套件庫，以取得更新的錯誤修正與效能改進。

### 授權設定（千萬別跳過）

**開發/測試用：**  
從 GroupDocs 官方網站下載免費試用版。試用版提供全部功能，但會在處理的文件上加上浮水印。

**正式環境用：**  
購買授權並在應用程式啟動時套用。未套用有效授權的正式建置會受到功能限制。

## 實作指南：加入底線註解

### 了解註解工作流程

在撰寫程式碼之前，先了解 **在 Java 中註解 PDF** 時的四步驟流程：

1. **文件載入** – `Annotator` 讀取檔案至記憶體。  
2. **註解建立** – 定義位置、樣式、評論等屬性。  
3. **註解套用** – 函式庫將註解注入 PDF 結構。  
4. **文件儲存** – 將修改後的檔案寫回磁碟，必要時保留原始檔。

此流程為非破壞性操作，除非你自行覆寫原檔，否則來源檔不會被改動。

### 步驟 1：初始化 Annotator 並載入文件

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**小技巧：** 開發階段使用絕對路徑可避免「找不到檔案」錯誤。正式環境建議從 classpath 或雲端儲存桶載入資源。

### 步驟 2：建立評論與回覆（協作部分）

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**實務應用：** 評審者可針對特定條款加入串接回覆，讓討論緊扣於該註解。

### 步驟 3：定義註解座標（確保位置正確）

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**座標系統說明：**  
- 點 1 與點 2 定義底線的上緣。  
- 點 3 與點 4 定義底線的下緣。  
- Y 軸差距（730 與 650）決定線條粗細。

### 步驟 4：建立並設定底線註解

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**顏色與透明度小技巧：**  
- `FontColor` 使用 ARGB；`65535`（0x00FFFF）會產生亮黃色。  
- 紅色使用 `16711680`（0xFF0000），藍色使用 `255`（0x0000FF）。  
- 透明度介於 0.5 至 0.8 之間，可在不遮蔽文字的前提下提供良好可讀性。

### 步驟 5：儲存已註解的文件

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**記憶體管理：** 呼叫 `dispose()` 會釋放原生資源，防止記憶體洩漏——在批次處理大量檔案時尤為重要。

## 移除註解：建立 Clean Document 版本

有時你需要一個 **不含任何註解** 的 PDF 版本，例如交付最終批准的合約。GroupDocs 讓此操作相當簡單。

### 了解註解移除選項

你可以：
- 移除 **全部** 註解（最常見）  
- 移除特定類型（例如僅移除高亮）  
- 依作者或頁碼移除註解  

### 步驟式註解移除

**步驟 1：載入先前已註解的文件**

```java
Annotator annotator = new Annotator(outputPath);
```

**步驟 2：設定 Clean 輸出的儲存選項**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**步驟 3：儲存 Clean 版本**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

如此即可產生 **clean PDF Java** 檔案，內部不含任何註解物件，適合最終發佈使用。

## 常見問題與解決方案

### 問題 1：「找不到文件」錯誤

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### 問題 2：註解出現在錯誤位置

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 問題 3：大型文件的記憶體問題

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### 問題 4：正式環境的授權問題

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## 正式環境效能最佳實踐

### 記憶體管理策略

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### 多執行緒考量

GroupDocs.Annotation 預設 **非執行緒安全**。若你的應用程式同時處理多筆文件：

- **千萬不要**在多個執行緒間共享同一個 `Annotator` 實例。  
- **同步**檔案存取或使用鎖定機制。  
- 若需高吞吐量，可考慮建立 **Annotator 物件池**。

### 快取策略

- 快取常用的註解範本。  
- 重複使用 `Point` 集合以減少座標建立開銷。  
- 若經常對同一基礎文件進行註解，可將 **範本 PDF** 常駐記憶體。

## 真實案例與應用場景

### 文件審閱系統

- **法律審查：** 底線標記合約條款並加入風險評論。  
- **合規稽核：** 高亮財務報表中問題段落。  
- **學術同行評審：** 教授底線需要說明的段落。

### 教育平台

- **學生註解工具：** 讓學習者在電子書中底線關鍵概念。  
- **教師回饋：** 直接在提交的作業上提供內嵌評論。

### 品質保證工作流程

- **技術文件審查：** 工程師底線需更新的章節。  
- **標準作業程序：** 安全主管標示關鍵步驟。

### 內容管理系統

- **編輯工作流：** 編輯者底線需要事實查證的文字。  
- **版本控制：** 追蹤不同文件修訂間的註解歷史。

## 專業實作進階技巧

### 自訂註解樣式

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### 註解中繼資料以便追蹤

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### 與使用者管理系統整合

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## 正式環境問題排除

### 效能監控

在正式環境留意以下指標：
- **Heap 使用量** – 確保呼叫 `dispose()`。  
- **每份文件的處理時間** – 在 `annotator.save()` 前後記錄時間戳。  
- **錯誤率** – 捕捉例外並分類。

### 常見正式環境陷阱

- **檔案鎖定** – 確保上傳的檔案在註解前已關閉。  
- **同時編輯** – 實作樂觀鎖或版本檢查。  
- **大型檔案（> 50 MB）** – 增加 JVM 超時設定，並考慮使用串流 API。

### 錯誤處理最佳實踐

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## 結論

現在你已掌握如何使用 GroupDocs.Annotation **建立 clean PDF Java** 檔案，並 **在 Java 中註解 PDF** 以底線註解為例。請記得：

- 以 try‑with‑resources 或明確的 `dispose()` 來管理資源。  
- 盡早驗證座標，避免底線位置錯位。  
- 為正式環境實作完整的錯誤處理機制，以提升穩定性。  
- 利用角色式樣式與中繼資料，讓工作流程更貼合需求。

接下來的步驟？嘗試加入其他註解類型——高亮、印章或文字取代，打造功能完整的文件審閱解決方案。

## 常見問答

**Q: 如何在一次操作中註解多個文字區域？**  
A: 建立多個 `UnderlineAnnotation` 物件，分別設定不同座標，然後依序使用 `annotator.add()` 加入。

**Q: 能否在 PDF 中的圖片上加入註解？**  
A: 能。使用相同的座標系統，只要確保座標點位於圖片範圍內即可。

**Q: 除了 PDF，GroupDocs.Annotation 支援哪些檔案格式？**  
A: 支援 Word（DOC/DOCX）、Excel（XLS/XLSX）、PowerPoint（PPT/PPTX）以及 JPEG、PNG、TIFF 等影像格式。

**Q: 如何處理超大型文件而不致記憶體不足？**  
A: 一次只處理一份文件，調整 JVM 堆疊大小（`-Xmx`），並確保及時呼叫 `dispose()` 釋放 `Annotator`。

**Q: 能否從文件中擷取已存在的註解？**  
A: 能。使用 `annotator.get()` 取得全部註解，然後依類型、作者或頁碼進行篩選。

---

**最後更新日期：** 2025-12-21  
**測試環境：** GroupDocs.Annotation 25.2  
**作者：** GroupDocs  

---