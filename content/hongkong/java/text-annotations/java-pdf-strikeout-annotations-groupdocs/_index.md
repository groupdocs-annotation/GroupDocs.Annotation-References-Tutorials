---
categories:
- Java PDF Processing
date: '2026-05-21'
description: 了解如何使用 GroupDocs 在 Java 中為 PDF 添加刪除線註釋。本一步一步教學涵蓋設定、程式碼、故障排除及效能提示。
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF 文字刪除線指南
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: 如何在 Java 中為 PDF 添加刪除線註釋 – 完整 GroupDocs 指南
type: docs
url: /zh-hant/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# 如何在 Java 中為 PDF 添加刪除線批註

是否曾需要以程式方式在 PDF 中劃掉文字？無論您是構建文件審核系統、建立編輯工作流程，或只是需要標記要刪除的文字，**如何添加刪除線**批註在 Java 中是一項實用技能，可節省時間並減少手動工作。在本完整指南中，您將了解使用 GroupDocs.Annotation for Java 實作刪除線批註的所有必要資訊，從專案設定到效能調校。

## 快速解答
- **第一步是什麼？** 將 GroupDocs.Annotation 的 Maven 依賴加入您的 `pom.xml`。  
- **如何建立刪除線？** 實例化 `Annotator`，使用點定義 `StrikeoutAnnotation`，設定顏色/不透明度，然後呼叫 `addAnnotation`。  
- **我可以加入註解嗎？** 可以，將 `Comment` 物件附加到批註上以供協作。  
- **如果批註位置錯誤怎麼辦？** 調整座標點；PDF 使用左下角為原點的座標系統。  
- **文件大小有上限嗎？** GroupDocs 可處理數百頁的 PDF，且不會將整個檔案載入記憶體。

## PDF 批註中的「如何添加刪除線」是什麼？
「如何添加刪除線」指的是使用批註 API 以程式方式在 PDF 文件中選取的文字上畫一條線的過程。於 Java 中，GroupDocs.Annotation 提供專用的 `StrikeoutAnnotation` 類別，負責渲染、樣式設定與刪除線標記的持久化。

## 為何在 Java PDF 刪除線使用 GroupDocs？
GroupDocs.Annotation 支援 **50+ 輸入與輸出格式**——包括 PDF、DOCX、XLSX、PPTX、HTML 與常見影像類型——因此您不會被單一檔案類型所限制。它提供高階 API，抽象化低階 PDF 結構，自動處理字型嵌入、頁面渲染與批註持久化，讓開發者能專注於業務邏輯，而非 PDF 內部細節。

## 前置條件與設定需求

### 必要條件
- **Java 開發工具包 (JDK)：** 8 版或更新（建議使用 JDK 11+ 以獲得最佳垃圾回收）。  
- **GroupDocs.Annotation for Java：** 透過 Maven 整合（請參考下方的 Maven 片段）。  
- **IDE：** IntelliJ IDEA、Eclipse，或任何相容 Java 的編輯器。

### Maven 依賴設定
將以下依賴區塊加入您的 `pom.xml`：

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

**Pro Tip:** Always verify the latest version on the GroupDocs release page; newer releases add features and fix bugs that can affect annotation rendering.

### 取得授權設定
GroupDocs.Annotation 需要有效授權才能於正式環境使用。您有三種選擇：

- **免費試用：** 從 [GroupDocs 下載](https://releases.groupdocs.com/annotation/java/) 下載。  
- **臨時授權：** 在 [GroupDocs 臨時授權](https://purchase.groupdocs.com/temporary-license/) 申請開發金鑰。  
- **正式授權：** 前往 [GroupDocs 授權購買頁面](https://purchase.groupdocs.com/buy) 購買。

試用版會加入淡淡的浮水印，請依此規劃測試。

## 步驟式實作指南

### 了解核心元件
以下定義提供快速的概念模型：

- **Annotator：** 主要的 API 物件，用於載入 PDF 並提供批註方法。  
- **StrikeoutAnnotation：** 代表視覺上的刪除線及其樣式選項。  
- **Point：** 座標對 (X, Y)，告訴函式庫線條的起始與結束位置。  
- **Comment：** 可選的文字，附加於批註以供協作。

### 步驟 1：設定檔案路徑
定義來源 PDF 與目標檔案的位置。錯誤的路徑是「找不到檔案」錯誤的常見原因。

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Ensure the output directory exists and is writable; GroupDocs will not auto‑create missing folders.

### 步驟 2：初始化 Annotator
建立一個 `Annotator` 實例，將 PDF 載入記憶體。

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** The library parses the PDF structure, builds an internal representation, and prepares a page‑wise annotation canvas. For multi‑hundred-page files this step may take a few seconds.

### 步驟 3：加入註解（可選但建議）
`Comment` 是一個類別，代表附加於批註的文字說明，讓協作者說明刪除線的原因。

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Use comments to explain why text is being removed—this is especially useful in legal or editorial review workflows.

### 步驟 4：定義批註座標
`Point` 物件儲存 X‑Y 座標對，定義批註在 PDF 頁面上的精確位置。

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF coordinates start at the bottom‑left corner (0,0). The example creates a horizontal line from (80,730) to (240,730) on the target page.

**Finding the Right Coordinates:** Many developers create a helper that converts percentages of page width/height into absolute points, making the code resilient to different page sizes.

### 步驟 5：建立刪除線批註
`StrikeoutAnnotation` 封裝視覺線條、顏色與不透明度等樣式屬性，以及任何相關的元資料。

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright yellow). Use an online converter if you need brand‑specific shades.

**Opacity Recommendation:** An opacity of `0.7` (70 %) offers a clear visual cue while keeping the underlying text legible.

### 步驟 6：套用批註
`addAnnotation` 是 `Annotator` 的方法，用於將已準備好的批註註冊至文件，使其在儲存時被渲染。

```java
annotator.add(strikeout);
```

### 步驟 7：儲存與清理
`dispose()` 釋放 `Annotator` 實例所持有的原生資源，防止處理完成後發生記憶體洩漏。

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Calling `dispose()` frees native resources and prevents memory leaks when processing batches of PDFs.

## 常見問題與解決方式

### 問題 1：「找不到檔案」錯誤
**Symptoms:** Exception thrown during `Annotator` construction.  
**Solution:** Verify both input and output paths, and confirm the application has read/write permissions.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### 問題 2：刪除線出現在錯誤位置
**Symptoms:** The line does not line up with the intended text.  
**Solution:** Remember that PDF Y‑coordinates increase upward. Use a visual debugging tool or print the page dimensions to fine‑tune the points.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### 問題 3：批註未顯示
**Symptoms:** No strikeout shows up after saving.  
**Possible Causes & Fixes:**
- **不透明度過低：** 暫時將不透明度設為 `1.0` 以驗證可見性。  
- **顏色混合：** 使用高對比度的顏色，例如紅色 (`255`)。  
- **頁碼錯誤：** 頁碼從零開始；確保目標頁面正確。

### 問題 4：大型檔案的記憶體問題
**Symptoms:** `OutOfMemoryError` or sluggish performance.  
**Solutions:**  
- Process documents in smaller batches.  
- Use the streaming API if available.  
- Always invoke `dispose()` after each document.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## 真實案例與使用情境

### 法律文件審查
Law firms annotate contracts with strikeouts to indicate deleted clauses while preserving an audit trail.

### 學術論文編輯
Professors use strikeouts to suggest removals during peer review, keeping the original text visible for context.

### 內容管理系統
Publishing platforms automatically flag policy‑violating sections with strikeouts before manual moderation.

### 文件版本控制
Enterprises treat strikeout annotations as “deletion markers” in a document‑centric version‑control workflow, similar to code diffs.

## 效能最佳化技巧

### 批次處理策略
When handling many PDFs, reuse a single `Annotator` instance where possible and process files in parallel threads.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### 記憶體管理最佳實踐
- 對每個 `Annotator` 呼叫 `dispose()`。  
- 限制同時載入的文件數量，以免堆積壓力。  
- 使用 VisualVM 等工具監控 JVM 記憶體使用情況。

### 座標快取
If you apply the same annotation layout across multiple files, cache the `Point` objects to avoid recomputation.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## 進階客製化選項

### 動態顏色選擇
Choose colors at runtime based on business rules (e.g., red for critical deletions, yellow for tentative ones).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### 多行刪除線
Create a series of `Point` pairs to draw a zig‑zag line that crosses several lines of text.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## 疑難排解清單
1. **檔案權限：** 確認讀寫存取權限。  
2. **函式庫版本：** 確保使用受支援的 GroupDocs.Annotation 版本。  
3. **授權狀態：** 確認授權檔案已正確引用。  
4. **PDF 相容性：** 檢查 PDF 是否未損毀且在支援的大小範圍內。  
5. **座標驗證：** 確保所有點位於頁面範圍內。  
6. **堆積空間：** 若處理極大檔案，請增加 JVM `-Xmx` 設定。

## 常見問答

**Q: 我可以在多行文字上劃刪除線嗎？**  
A: 可以。建立多個 `Point` 物件以描繪所需路徑，批註會依照提供的折線繪製。

**Q: 若指定的座標超出頁面邊界會發生什麼事？**  
A: 批註會被裁切，可能變得不可見。請務必根據頁面的寬高驗證座標。

**Q: 我可以在加入後移除刪除線批註嗎？**  
A: 當然可以。使用 `removeAnnotation` 方法搭配批註 ID，或依類型過濾後程式化刪除。

**Q: 單一 PDF 能加入多少批註才算合理？**  
A: GroupDocs 沒有硬性上限，但當批註數量達到數千時效能可能下降。對於極大量的批註，建議分頁或彙總。

**Q: 如何處理受密碼保護的 PDF？**  
A: 在 `Annotator` 建構子中傳入密碼。函式庫會在記憶體中解密文件，然後再套用批註。

**Q: 如何因應不同頁面尺寸與方向的 PDF？**  
A: 透過 `annotator.getPageInfo(pageNumber)` 取得每頁尺寸，並依此計算相對座標，以確保放置一致。

## 結論
您現在已掌握使用 GroupDocs.Annotation 在 Java 中為 PDF 添加 **如何添加刪除線** 批註的完整、可投入生產的解決方案。透過熟悉檔案路徑處理、座標計算與資源管理，您可以將此功能嵌入文件審核工具、內容管線或任何需要精確視覺回饋的 Java 應用程式。

**下一步**
1. 複製範例專案並對樣本 PDF 執行。  
2. 嘗試不同的顏色、不透明度與註解文字。  
3. 將批註工作流程整合至現有的文件處理服務。  
4. 探索相關的批註類型——標記、便利貼與圖形批註，以擴充 PDF 操作工具箱。

Ready for more? Dive into the official documentation for deeper API insights.

## 其他資源

- [GroupDocs 文件](https://docs.groupdocs.com/annotation/java/) - GroupDocs 函式庫的一般文件  
- [GroupDocs.Annotation 文件](https://docs.groupdocs.com/annotation/java/) - 完整的 API 參考  
- [API 參考指南](https://reference.groupdocs.com/annotation/java/) - 方法逐一說明  
- [下載最新版本](https://releases.groupdocs.com/annotation/java/) - 保持函式庫為最新  
- [購買授權](https://purchase.groupdocs.com/buy) - 生產環境授權  
- [免費試用下載](https://releases.groupdocs.com/annotation/java/) - 購買前先評估  
- [臨時授權申請](https://purchase.groupdocs.com/temporary-license/) - 開發測試  
- [支援論壇](https://forum.groupdocs.com/c/annotation/) - 社群協助與官方支援  

---

**最後更新：** 2026-05-21  
**測試環境：** GroupDocs.Annotation 23.12 for Java  
**作者：** GroupDocs

## 相關教學

- [新增 PDF 批註 Java – 完整 GroupDocs 指南](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF 批註教學 - 完整標註 PDF 指南](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [如何在 Java 為 PDF 添加箭頭 – 完整 GroupDocs 教程](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)