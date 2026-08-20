---
categories:
- Java Development
date: '2026-05-16'
description: 學習如何使用 GroupDocs.Annotation 在 Java 中建立註解回覆。掌握 Java PDF 註解，提供實用範例、效能技巧與最佳實踐。
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Java PDF 註解教學
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Java PDF Annotation Library: 建立註解回覆（Java）'
type: docs
url: /zh-hant/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF 註解庫：建立註解回覆 Java

如果您需要為 PDF **create annotation reply java**（建立註解回覆 Java）——無論是構建合約審核平台、電子學習系統，或是大量處理管線——本指南將向您展示如何使用 GroupDocs.Annotation for Java 完成此操作。我們將逐步說明設定、波浪線註解的建立、回覆串接以及效能調校，讓您能在數天而非數週內交付可靠的解決方案。

## 快速解答
- **GroupDocs.Annotation 的主要目的為何？** 它允許在 Java 中以程式方式建立、修改和提取 PDF 註解。  
- **如何新增波浪線註解？** Instantiate `SquigglyAnnotation`，設定其幾何形狀與樣式，然後呼叫 `annotator.add(...)`。  
- **我可以為註解附加回覆嗎？** 可以——建立 `Reply` 物件，設定作者與文字，並將其關聯至父註解。  
- **生產環境需要授權嗎？** 絕對需要；若未使用有效授權，輸出檔案將會帶有浮水印。  
- **適合批次處理嗎？** 可以——使用 try‑with‑resources 開啟每個文件、進行註解，然後關閉，以保持低記憶體使用量。

## 為何 Java 開發者需要 PDF 註解庫

手動在 PDF 上標註既耗時又易出錯，尤其當您需要審閱數百份合約或考卷時。Java PDF 註解庫可自動化此工作，讓您直接在檔案中嵌入高亮、波浪線底線以及串接評論。最終產出的是可搜尋、可攜帶的文件，保留所有標註且不需額外的檢視器。

**本指南您將掌握的內容**
- 在 Maven 專案中安裝與授權 GroupDocs.Annotation  
- 建立類似原生 Word 底線的波浪線註解  
- 為任意註解新增串接回覆，以支援協作審閱  
- 在處理大型 PDF 時優化記憶體與 CPU 使用率  
- 在 Spring Boot、微服務或桌面應用程式中部署此解決方案  

無論您是構建法律文件審核系統、教育評分工具，或是自動化品質管控管線，以下技術都能為您提供可投入生產的基礎。

## 什麼是 create annotation reply java？

`create annotation reply java` 是使用 Java 將評論串 (Reply) 附加至現有 PDF 註解的程式化過程。回覆讓多位審閱者能在不離開文件的情況下討論特定標註，實現無縫、即時的協作。此功能將靜態 PDF 轉變為互動式討論平台，直接在檔案內保留上下文與稽核紀錄。

## 前置條件：準備開發環境

在深入程式碼之前，請確認您的開發工作站符合以下規格：
- **JDK** 8 或以上（建議使用 JDK 11 以上以獲得更佳的垃圾回收效能）  
- **Maven** 或 **Gradle** 用於相依管理（範例使用 Maven）  
- 支援 Maven 的 IDE（IntelliJ IDEA、Eclipse 或 VS Code）  
- 至少 **2 GB** 可用記憶體供 IDE 與測試執行使用  
- 用於實驗的範例 PDF 檔案（可使用任何 PDF 編輯器產生簡易 PDF）  

GroupDocs.Annotation 完全在程式內執行；不需要外部 PDF 檢視器或原生函式庫。

## 設定 GroupDocs.Annotation for Java

整合此函式庫僅需幾個步驟，但若忽略某些隱藏的陷阱，可能會導致執行時錯誤。

### Maven 相依設定

將儲存庫與相依項目加入您的 `pom.xml`。請將 `<repositories>` 元素 **放在** `<dependencies>` 之前，以確保 Maven 能解析此套件。

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
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

> **專業提示：** 請檢查 GroupDocs 發行頁面以取得最新版本。新版本通常包含對新興 PDF 標準的支援與效能改進。

### 授權設定（千萬別跳過！）

GroupDocs.Annotation 在生產環境使用時需要授權檔案。若未提供，所有產生的 PDF 都會帶有浮水印。

1. **免費試用** – 完整功能 30 天，適合評估。  
2. **臨時授權** – 適用於開發與內部測試。  
3. **正式授權** – 任何商業部署皆需使用。  

將 `GroupDocs.Annotation.lic` 檔案放置於 resources 資料夾，並於啟動時載入：

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **常見問題：** 若遺漏授權步驟，會導致 PDF 帶有浮水印且 API 呼叫靜默失敗。請務必在啟動流程的早期驗證授權。

## 完整實作指南：新增波浪線註解

以下為逐步說明，展示如何在建立波浪線註解的同時 **create annotation reply java**。每一步皆附有簡要說明，讓您了解每行程式碼背後的「原因」。

### 步驟 1：匯入所有必要類別

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` 是所有文件層級操作的入口點。  
- `Point` 代表頁面上的座標（X 與 Y 以左上角為原點測量）。  
- `SquigglyAnnotation` 定義用於標示錯誤的波浪底線。  
- `Reply` 儲存附加於註解的串接評論。  
- `SaveOptions` 讓您控制輸出格式與壓縮方式。

### 步驟 2：建立與設定波浪線註解

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation 是用於在 PDF 中建立波浪底線以突顯錯誤的類別。

- **座標系統**：點的起點為左上角。上述兩個點繪製一條從 (100, 200) 到 (300, 200) 的水平波浪線。  
- **不透明度** 0.7 表示註解的透明度為 70%，讓底層文字仍可閱讀。

### 步驟 3：新增互動回覆（可選但功能強大）

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

Reply 是代表附加於註解的評論串的類別。

- 回覆在註解上直接建立 **串接討論**，類似現代 PDF 評閱者的使用體驗。  
- 每則回覆儲存作者資訊與時間戳記，您可稍後於 UI 中過濾或顯示。

### 步驟 4：套用註解並儲存文件

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- **try‑with‑resources** 結構會自動關閉 `Annotator`，釋放檔案句柄與原生緩衝區。  
- `save` 將修改後的 PDF 寫入 `output.pdf`。

> **記憶體說明：** `Annotator` 僅載入您操作的頁面。對於數百頁的 PDF，此方式可將堆積使用量控制在典型伺服器的 150 MB 以下。

## 進階設定選項

### 自訂註解外觀

您可以微調視覺樣式以符合品牌指南：

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **邊框寬度** 控制線條粗細（以點為單位）。  
- **ARGB** 格式包含透明度通道。

### 精確定位註解

在頁面尺寸各異的 PDF 上取得正確座標可能相當棘手。請遵循以下系統化步驟：

1. **在檢視器中開啟 PDF**（例如 Adobe Acrobat），並記錄目標區域的尺規數值。  
2. **將尺規數值轉換** 為點（1 點 = 1/72 英吋）。  
3. **使用 `annotator.getPageInfo(pageIndex)`** 取得頁面寬高，然後計算相對位置。

## 常見問題與解決方案

### 問題：註解未顯示

**最常見的原因**
- 點位於頁面邊界之外  
- 未載入授權（浮水印隱藏註解）  
- 頁碼錯誤（API 中頁碼從零開始）

**解決方案檢查清單**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### 問題：大型檔案效能不佳

將 500 頁的 PDF 載入記憶體可能導致服務卡頓。可透過以下方式緩解：

- **一次處理單頁**——開啟文件、在單一頁面上註解、儲存，然後再處理下一頁。  
- **串流**——使用 `Annotator` 的串流 API，避免完整文件緩衝。  
- **快取**——將常用 PDF 存於高速快取（如 Redis），在快取副本上進行註解。

### 問題：顏色值無效

GroupDocs 期待 **ARGB**（Alpha、Red、Green、Blue）而非純粹的 RGB。ARGB 值 `0xFFFF0000` 代表完全不透明的紅色。若提供 `0xFF0000`，函式庫會錯誤解讀，導致註解呈現為黑色。

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## 效能最佳實踐

### 記憶體管理

在批次作業中為數十個 PDF 加註時，請將每個檔案包在各自的 try‑with‑resources 區塊中：

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- 此模式確保每次迭代後釋放原生緩衝區，防止長時間執行時出現 **OutOfMemoryError**。

### 批次處理最佳化

對於高吞吐量環境，建議使用平行串流結合受限執行緒池：

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **受限執行緒池** 可避免執行緒激增，而平行串流則能充分利用 CPU 核心。

### 檔案大小考量

大型 PDF（> 100 MB）可能降低效能。可採取以下策略：

- **預先壓縮** 原始 PDF（使用 Ghostscript 等工具）再進行註解。  
- **僅註解必要頁面**——跳過不需標註的頁面。  
- **分割** 文件為邏輯段落（如每章），分別處理每個區塊。

## 真實案例應用

### 文件審核系統

法律事務所常需標示有問題的條款。波浪線註解結合串接回覆，使多位律師能在不離開 PDF 的情況下討論同一段落：

- **律師 A** 在條款下方加上紅色波浪線並寫下「措辭模糊」。  
- **律師 B** 回覆「為 ‘重大違約’ 加上定義」。  
- 整個討論皆嵌入於文件中，可搜尋且具稽核性。

### 與既有系統整合

GroupDocs.Annotation 可順利與流行的 Java 框架整合：

- **Spring Boot** – 暴露 REST 端點 `/api/annotate`，接受 PDF 多部件上傳、加入註解，並串流回傳結果。  
- **JSF** – 將註解操作綁定至 UI 元件，以即時在網頁檢視中標註。  
- **微服務** – 函式庫體積小（< 15 MB），可使用 Docker 容器化並水平擴展。

### 工作流程自動化

將註解與其他 GroupDocs 產品（如 GroupDocs.Signature）結合，構建端對端的工作流程管線：

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## 何時使用波浪線註解 vs. 其他選項

| 使用情境 | 推薦註解類型 |
|----------|------------------------|
| 標示拼寫或文法錯誤 | **Squiggly** – 類似文字處理器的視覺提示 |
| 突顯重要段落且不暗示錯誤 | **Highlight** – 半透明覆蓋層 |
| 提供詳細回饋 | **Text** 或 **Comment** – 自由格式的備註框 |
| 核准或拒絕文件 | **Stamp** – 「Approved」或「Rejected」標章 |

## 結論

您現在已掌握使用 GroupDocs.Annotation 的完整、可投入生產的 **create annotation reply java** 範例。透過精通 API、處理授權，以及套用上述效能技巧，您可以：
- 自動在數千份 PDF 上標記錯誤  
- 在檔案內部啟用協作式、串接的討論  
- 即使處理大型文件，也能保持低記憶體使用量  

**接下來的步驟**
1. 嘗試其他註解類型（高亮、印章、文字）。  
2. 建立接收 PDF、進行註解並回傳結果的 REST 服務。  
3. 探索提取 API（`annotator.get()`），以取得現有評論進行分析。  

程式化 PDF 註解的威力在於能以可重複、可稽核的程式碼取代繁瑣的手動標註。無論您是打造特定領域的法律科技產品，或是一般用途的文件工作流引擎，本指南中的技術皆為您提供堅實的基礎，持續前進。

## 常見問答

**Q: GroupDocs.Annotation 相較於其他 Java PDF 函式庫有何優勢？**  
A: GroupDocs.Annotation 專注於註解工作流程，提供超過 30 種註解類型、串接回覆，且原生支援 50+ 檔案格式，同時在 500 頁 PDF 上的記憶體佔用保持在 200 MB 以下。

**Q: 可以在 Spring Boot 應用程式中使用此函式庫嗎？**  
A: 當然可以。建立一個 `@RestController`，注入 `Annotator` 服務，處理多部件上傳，並將註解後的 PDF 串流回客戶端。記得為同時請求配置執行緒池。

**Q: 如何處理頁面尺寸不同的文件？**  
A: 透過 `annotator.getPageInfo(pageIndex)` 取得每頁的尺寸，並計算相對座標（例如百分比），而非硬編碼點值。這可確保註解在 A4、Letter 以及自訂尺寸的頁面上正確顯示。

**Q: 有方法從 PDF 中提取現有註解嗎？**  
A: 有。呼叫 `annotator.get()` 取得所有註解的集合，然後遍歷以讀取作者、評論、幾何等屬性。此功能在遷移或分析情境中相當有用。

**Q: 在多使用者系統中處理註解權限的最佳做法是什麼？**  
A: 在應用層實作驗證，將使用者 ID 與每個 `Reply` 一起儲存，並依據業務規則執行權限控制（例如僅作者或管理員可編輯或刪除回覆）。API 本身不強制權限，提供完整彈性。

**Q: 處理數百份 PDF 時，如何最佳化記憶體使用？**  
A: 為每個文件使用 try‑with‑resources，逐頁處理，並考慮使用受限執行緒池以限制同時記憶體消耗。使用 VisualVM 等工具監控 JVM 堆積，可微調 `-Xmx` 設定。

---

**最後更新：** 2026-05-16  
**測試版本：** GroupDocs.Annotation 25.2 for Java  
**作者：** GroupDocs  

**其他資源**
- [GroupDocs.Annotation for Java 文件說明](https://docs.groupdocs.com/annotation/java/)
- [完整 API 參考](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

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

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## 相關教學

- [Java PDF 註解庫教學](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [移除註解回覆 Java - 使用 GroupDocs.Annotation 依 ID 管理回覆](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [編輯 PDF 註解 Java - 完整 GroupDocs 教學](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)