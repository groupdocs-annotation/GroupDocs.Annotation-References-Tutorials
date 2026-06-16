---
categories:
- Java Development
date: '2026-06-16'
description: 了解如何在 Java 中使用 GroupDocs.Annotation 為圖像及其他文件添加測量。完整教學包括程式碼範例、故障排除技巧與最佳實踐。
keywords:
- how to add measurement
- distance annotation Java
- measure image Java
- GroupDocs annotation tutorial
- Java document measurement
lastmod: '2026-06-16'
linktitle: Java Distance Annotations 指南
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  headline: 'Java Distance Annotation Tutorial: How to add measurement to image with
    GroupDocs'
  type: TechArticle
- description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  name: 'Java Distance Annotation Tutorial: How to add measurement to image with GroupDocs'
  steps:
  - name: Create Interactive Replies (Optional But Recommended)
    text: Replies let collaborators attach comments directly to a measurement, turning
      a simple ruler into a discussion thread. java import com.groupdocs.annotation.models.Reply;
      import java.util.ArrayList; import java.util.Calendar; Reply reply1 = new Reply();
      reply1.setComment("First comment"); reply1.setRe
  - name: Configure Your Distance Annotation
    text: The `DistanceAnnotation` class is GroupDocs.Annotation's top‑level object
      that represents a ruler measurement. You can customize its geometry, visual
      style, and attached message. `Rectangle` defines the annotation's bounding box
      on the page. `PenStyle` enumerates line styles such as solid, dash, and
  - name: Apply the Annotation and Save
    text: Once the annotation is ready, add it to the document and persist the changes.
      java annotator.add(distance); annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
      annotator.dispose(); **Important:** Always invoke `dispose()` after saving,
      especially when processing many documents in a batch job.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports PDFs, Word documents, PowerPoint presentations,
      Excel spreadsheets, and common image formats (PNG, JPEG, TIFF, BMP). The feature
      works consistently across all 50+ supported formats.
    question: What document formats support distance annotations?
  - answer: Absolutely! You have full control over pen color, line style (solid, dotted,
      dashed), line width, and opacity. You can also define custom end‑cap symbols
      for specialized engineering standards.
    question: Can I customize the appearance of measurement lines?
  - answer: The annotation itself displays the text you set in the `message` property.
      Perform any unit conversion (e.g., inches ↔ millimeters) in your Java code before
      assigning the message.
    question: How do I handle measurements in different units?
  - answer: Yes. In compatible viewers (GroupDocs.Viewer, Adobe Acrobat, or your own
      web viewer), users can click, drag, and edit the ruler. Replies and comments
      remain attached to the measurement for collaborative review.
    question: Can users interact with distance annotations after they're added?
  - answer: Adding up to several hundred annotations per document has a negligible
      impact (< 5 % CPU overhead). When you exceed 1,000 annotations, loading times
      may increase modestly, but the library remains stable and responsive.
    question: What's the performance impact of adding many annotations?
  type: FAQPage
tags:
- GroupDocs
- document-annotation
- Java-tutorial
- PDF-processing
title: Java Distance Annotation 教學：如何使用 GroupDocs 為圖像添加測量
type: docs
url: /zh-hant/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/
weight: 1
---

# Java 距離註釋教學：如何使用 GroupDocs 為圖像添加測量

在本完整指南中，您將學會 **如何為圖像、PDF 以及其他文件類型添加測量**，使用 GroupDocs.Annotation for Java。無論您是構建 CAD 檢視器、建築審查工具，或是技術文件平台，距離註釋都能為使用者提供清晰、互動的尺標。完成本教學後，您將擁有一個可投入生產的解決方案，能繪製精確測量、客製化外觀，並順利整合至現有的 Java 程式碼基礎。

## 如何在 Java 中為圖像添加測量？

使用 `Annotator` 載入目標文件，建立 `DistanceAnnotation`，設定其視覺屬性，將其加入指定頁面，最後儲存檔案。僅需四行程式碼，即可取得可在任何相容檢視器中由最終使用者編輯的完整尺標。此方法適用於 PDF、Word、PowerPoint、Excel 以及常見圖像格式如 PNG、JPEG、TIFF。

## 快速回答
- **在 Java 中為圖像添加測量的最簡單方法是什麼？** 使用 GroupDocs.Annotation 的 `DistanceAnnotation` 類別。  
- **支援哪些格式？** PDF、Word、PowerPoint、Excel，以及常見的圖像類型（PNG、JPEG、TIFF）。  
- **開發是否需要授權？** 測試可使用免費試用或臨時授權；正式上線需商業授權。  
- **我可以自訂尺標線的外觀嗎？** 可以——您可以設定顏色、樣式、寬度與透明度。  
- **如何避免記憶體泄漏？** 必須在使用完畢後釋放 `Annotator` 實例，或使用 try‑with‑resources。

## 什麼是距離註釋（以及為何需要它）？

距離註釋是顯示文件中兩點之間測量長度的互動視覺元素。它們如同可隨意放置、拖曳、即時編輯的數位尺標，為使用者提供即時視覺回饋，免除手動計算。

這些註釋為任何技術文件帶來 **視覺清晰度**、**互動回饋** 與 **專業外觀**。在建築圖紙、工程示意圖、醫學影像與房地產平面圖等需要精確尺寸的情境中，特別有價值。

## 文件測量最佳實踐

在開始編寫程式碼前，請記住以下驗證過的實踐：

1. **以零為起點的頁碼索引** – `pageNumber = 0` 代表第一頁，符合 GroupDocs.Annotation 的內部模型。  
2. **高對比度顏色** – 選擇在文件背景上突出的尺標顏色（例如深色圖紙上的亮黃色）。  
3. **透明度調整** – `0.7` 的透明度在可見度與底層細節之間取得平衡；對於關鍵測量可提升至 `1.0`。  
4. **將相關註釋分組** – 使用回覆或評論將討論圍繞特定測量組織起來。  
5. **及時釋放** – 必須呼叫 `annotator.dispose()` 或使用 try‑with‑resources 釋放原生記憶體，特別是處理大型檔案時。

## 前置條件：開始前需要的項目

### 開發環境需求
- **Java Development Kit (JDK)**：版本 8 或以上（建議使用 JDK 11+）。  
- **Maven 或 Gradle**：範例使用 Maven，但相同的相依性亦適用於 Gradle。  
- **IDE**：任何 Java IDE（IntelliJ IDEA、Eclipse、VS Code 等）皆可。

### 知識前提
您應該已熟悉以下內容：

- 核心 Java 概念（類別、物件、方法）。  
- 透過 Maven/Gradle 新增外部函式庫。  
- 基本的檔案 I/O 與路徑處理。

### 測試文件
- 一或多頁 PDF。  
- 用於點陣測試的 PNG/JPEG/TIFF 圖像。  
- 若想測試工程圖，可選擇 CAD 檔案。

## 為 Java 設定 GroupDocs.Annotation

整合 GroupDocs.Annotation 非常簡單。以下示範在專案中加入的 Maven 坐標。

### Maven 整合

將以下設定加入您的 `pom.xml` 檔案：

```xml
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
```

### 了解授權需求

GroupDocs.Annotation 提供三種授權模式：

1. **免費試用** – 適合評估；包含所有功能，僅有少量使用限制。  
2. **臨時授權** – 移除試用限制，可用於開發與測試。  
3. **商業授權** – 完整功能、正式上線使用，無限制。

先使用免費試用，待準備好正式上線時再升級。

### 基本初始化

`Annotator` 類別是所有註釋操作的入口。它會載入文件、提供編輯 API，並將結果寫回磁碟。

```java
```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with the input file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

**專業提示：** 將 `Annotator` 包在 try‑with‑resources 區塊中，或明確呼叫 `dispose()`，以避免原生記憶體泄漏。

## 步驟式實作指南

現在讓我們逐步說明完整、可投入生產的距離註釋工作流程。

### 步驟 1：建立互動回覆（可選但建議）

回覆讓協作者能直接在測量上附加評論，將簡單的尺標轉變為討論串。

```java
```java
import com.groupdocs.annotation.models.Reply;
import java.util.ArrayList;
import java.util.Calendar;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

**何時使用回覆：** 在多使用者審閱流程中，需要說明為何選擇某個尺寸或向團隊成員請求說明時。

### 步驟 2：設定距離註釋

`DistanceAnnotation` 類別是 GroupDocs.Annotation 的頂層物件，代表尺標測量。您可以自訂其幾何形狀、視覺樣式與附加訊息。

`Rectangle` 定義註釋在頁面上的邊界框。`PenStyle` 列舉線條樣式，如實線、虛線與點線。

```java
```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30)); // Set the annotation's position and size
distance.setCreatedOn(Calendar.getInstance().getTime()); 
distance.setMessage("This is a distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0); 
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.DOT);
distance.setPenWidth((byte) 3);

distance.setReplies(replies); // Attach replies
```
```

**主要設定選項**  
- `setBox()` – 設定註釋在頁面上的邊界矩形。  
- `setOpacity()` – 控制透明度（`0.0` = 完全透明，`1.0` = 完全不透明）。  
- `setPenColor()` – 測量線的 RGB 顏色。  
- `setPenStyle()` – 線條樣式（`DOT`、`DASH`、`SOLID`）。  
- `setPenWidth()` – 線條的粗細（點數）。

### 步驟 3：套用註釋並儲存

註釋設定完成後，將其加入文件並保存變更。

```java
```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```
```

**重要提示：** 儲存後務必呼叫 `dispose()`，特別是在批次處理多個文件時。

## 完整範例程式

以下為完整的端對端範例，載入 PDF、加入距離註釋，並儲存結果。

```java
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;
import java.util.ArrayList;
import java.util.Calendar;

public class DistanceAnnotationExample {
    public static void main(String[] args) {
        try (Annotator annotator = new Annotator("input.pdf")) {
            // Create replies for the annotation
            ArrayList<Reply> replies = new ArrayList<>();
            Reply reply = new Reply();
            reply.setComment("Measurement verified by engineering team");
            reply.setRepliedOn(Calendar.getInstance().getTime());
            replies.add(reply);

            // Configure the distance annotation
            DistanceAnnotation distance = new DistanceAnnotation();
            distance.setBox(new Rectangle(100, 100, 300, 50));
            distance.setCreatedOn(Calendar.getInstance().getTime());
            distance.setMessage("Wall length: 12 feet");
            distance.setOpacity(0.8);
            distance.setPageNumber(0);
            distance.setPenColor(0xFF0000); // Red color
            distance.setPenStyle(PenStyle.SOLID);
            distance.setPenWidth((byte) 2);
            distance.setReplies(replies);

            // Add and save
            annotator.add(distance);
            annotator.save("output_with_distance_annotation.pdf");
            
            System.out.println("Distance annotation added successfully!");
        } catch (Exception e) {
            System.err.println("Error adding distance annotation: " + e.getMessage());
        }
    }
}
```
```

執行程式碼，使用任何支援註釋的 PDF 檢視器開啟輸出檔，即可看到可互動的完整尺標。

## 常見使用情境與實務應用

了解距離註釋的優勢，有助於決定如何在產品中嵌入它們。

### 技術文件與手冊
- 在組裝指南中突顯元件尺寸。  
- 在安裝手冊中顯示間隙區域。  
- 為品質檢查清單提供快速參考測量。

### 建築與工程專案
- 在平面圖上顯示房間大小。  
- 標示結構元件間距。  
- 標註管線距離與安全間距。

### 醫學與科學應用
- 在放射影像中測量解剖結構。  
- 在顯微鏡切片上加入比例尺。  
- 在研究報告中記錄樣本尺寸。

### 房地產與物業管理
- 視覺化地塊邊界與產權線。  
- 在房源資訊中顯示房間尺寸。  
- 標示停車位大小與景觀測量。

## 常見問題排除

即使範例寫得很好，仍可能遇到問題。以下列出最常見的問題與解決方式。

### 問題：「找不到檔案」或路徑問題
**症狀：** 建立 `Annotator` 時拋出例外。**解決方案：** 開發期間使用絕對路徑，確認檔案存在，且程式具有讀取權限。

```java
```java
// Better path handling
String inputPath = new File("documents/input.pdf").getAbsolutePath();
final Annotator annotator = new Annotator(inputPath);
```
```

### 問題：註釋未顯示
**症狀：** 程式執行無錯誤，但未看到尺標。**常見原因：** 頁碼錯誤（頁碼從 0 開始）、註釋放置在可視畫布外，或透明度設定過低。

**快速修正：**

```java
```java
distance.setPageNumber(0); // First page
distance.setOpacity(1.0);  // Fully opaque
distance.setBox(new Rectangle(50, 50, 200, 30)); // Visible position
```
```

### 問題：大型文件的記憶體問題
**症狀：** `OutOfMemoryError` 或在數百頁文件上效能緩慢。**解決方案：**
- 在完成後立即釋放每個 `Annotator` 實例。  
- 依序處理文件，而非一次載入全部。  
- 對於極大檔案，提升 JVM 堆積大小（如 `-Xmx4g` 或更高）。

```java
```java
// Good practice - use try-with-resources
try (Annotator annotator = new Annotator("large-document.pdf")) {
    // Your annotation code here
} // Automatic disposal
```
```

### 問題：授權相關錯誤
**症狀：** 出現關於試用限制或授權驗證失敗的警告。**解決方案：**
- 確認授權檔案路徑正確且檔案可讀取。  
- 確保授權版本與您使用的 GroupDocs.Annotation 函式庫版本相符。  
- 確認臨時授權尚未過期。

## 效能優化技巧

從原型轉為正式環境時，請留意以下效能考量。

### 記憶體管理最佳實踐
- **始終釋放**：優先使用 try‑with‑resources 或明確呼叫 `dispose()`。  
- **批次操作**：在單一 `Annotator` 會話中一次處理多筆註釋變更，以減少開銷。  
- **效能分析**：使用 Java 效能分析工具（VisualVM、YourKit）監控原生記憶體使用情況。

### 檔案處理最佳化
- **快取**：對於唯讀的常用文件，可在記憶體中快取。  
- **優先使用 PDF** 而非高解析度圖像，以加快渲染速度；相同視覺內容的 PDF 通常小 30‑40%。  
- **調整影像解析度**：除非需要更高保真度，否則將來源圖像縮小至最高 150 DPI。

### 並行處理考量
若服務同時處理多個檔案，請遵循以下規則：

```java
```java
// Example of efficient batch processing
public void processMultipleDocuments(List<String> filePaths) {
    for (String path : filePaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Add multiple annotations per document
            addDistanceAnnotation(annotator, config1);
            addDistanceAnnotation(annotator, config2);
            // Save once with all annotations
            annotator.save(getOutputPath(path));
        }
    }
}
```
```

- 每個執行緒必須自行建立 `Annotator` 實例。  
- 使用受限的執行緒池，以免耗盡系統資源。  
- 在負載下監控 CPU 與堆積使用情況；必要時水平擴展。

## 進階設定選項

掌握基礎後，可探索以下進階功能，以微調註釋。

### 自訂樣式選項

```java
```java
// Advanced pen styling
distance.setPenStyle(PenStyle.DASH_DOT);
distance.setPenWidth((byte) 4);
distance.setPenColor(0x00FF00); // Hex color codes work too

// Custom opacity for different emphasis levels
distance.setOpacity(0.6); // Subtle background measurements
// vs
distance.setOpacity(1.0); // Prominent foreground measurements
```
```

您可以定義自訂的 `Pen` 物件、套用漸層填色，甚至在尺標線端點嵌入 SVG 標記。

### 動態定位

```java
```java
// Calculate position based on document dimensions or content
Rectangle dynamicBox = calculateOptimalPosition(documentWidth, documentHeight);
distance.setBox(dynamicBox);
```
```

利用相對於頁面的座標，使註釋在文件縮放或旋轉時自動重新定位。

### 條件式註釋

```java
```java
// Add annotations based on document content or user preferences
if (document.getType() == DocumentType.ARCHITECTURAL_PLAN) {
    distance.setMessage("Room dimension");
    distance.setPenStyle(PenStyle.SOLID);
} else if (document.getType() == DocumentType.ENGINEERING_DRAWING) {
    distance.setMessage("Component spacing");
    distance.setPenStyle(PenStyle.DOT);
}
```
```

加入條件判斷，僅在滿足特定條件時（例如元件超過容差門檻）才建立距離註釋。

## 與其他系統整合

距離註釋並非孤立存在，它自然融入更廣泛的文件管理生態系統。

### 資料庫整合

`AnnotationRecord` 是用於在資料庫中持久化註釋中繼資料的自訂資料模型。

```java
```java
// Save annotation details to database
AnnotationRecord record = new AnnotationRecord();
record.setDocumentId(documentId);
record.setAnnotationType("distance");
record.setMeasurement(distance.getMessage());
record.setCreatedDate(distance.getCreatedOn());
```
```

將註釋中繼資料（作者、時間戳記、測量值）存入關聯式資料庫，以供報表與搜尋使用。

### 網頁應用程式整合

`DistanceAnnotationRequest` 是從客戶端傳遞至伺服器的 DTO，承載註釋參數。

```java
```java
@PostMapping("/documents/{id}/annotations/distance")
public ResponseEntity<String> addDistanceAnnotation(
    @PathVariable String id,
    @RequestBody DistanceAnnotationRequest request) {
    // Process the annotation request
    // Return success/failure response
}
```
```

提供一個 REST 端點，接受檔案、根據 JSON 載荷加入距離註釋，並回傳已註釋的文件。

### 雲端儲存整合

```java
```java
// Download from cloud, process, upload result
byte[] documentBytes = cloudStorageService.download(documentPath);
// Process with GroupDocs.Annotation
byte[] annotatedDocument = processAnnotations(documentBytes);
cloudStorageService.upload(outputPath, annotatedDocument);
```
```

使用相應的 SDK，直接從 AWS S3、Azure Blob Storage 或 Google Cloud Storage 讀寫檔案，然後將串流傳遞給 `Annotator`。

## 常見問答

**問：哪些文件格式支援距離註釋？**  
**答：** GroupDocs.Annotation 支援 PDF、Word 文件、PowerPoint 簡報、Excel 試算表以及常見圖像格式（PNG、JPEG、TIFF、BMP）。此功能在所有 50 多種支援格式中皆表現一致。

**問：我可以自訂測量線的外觀嗎？**  
**答：** 當然可以！您可完全控制筆刷顏色、線條樣式（實線、點線、虛線）、線寬與透明度，亦可為特定工程標準定義自訂端點符號。

**問：如何處理不同單位的測量？**  
**答：** 註釋會顯示您在 `message` 屬性中設定的文字。請在 Java 程式碼中先完成單位換算（例如英吋 ↔ 毫米），再將結果寫入 `message`。

**問：使用者在加入距離註釋後能互動嗎？**  
**答：** 可以。在相容的檢視器（如 GroupDocs.Viewer、Adobe Acrobat 或自訂的 Web 檢視器）中，使用者可點擊、拖曳與編輯尺標。回覆與評論會持續附著於測量，供協作審閱。

**問：加入大量註釋對效能有何影響？**  
**答：** 每份文件加入數百筆註釋的效能影響可忽略不計（CPU 開銷 < 5 %）。若超過 1,000 筆，載入時間可能略為增加，但函式庫仍保持穩定與回應迅速。

## 結論與後續步驟

您現在已掌握完整、可投入生產的 **如何在 Java 中為圖像與其他文件添加測量** 路線圖。透過距離註釋，您可將靜態圖紙轉換為互動且富含資料的資產，提升協作並降低錯誤。

**重點摘要**
- 距離註釋在 50 多種文件格式中提供精確、可視的測量。  
- 實作簡潔：載入、設定、加入、儲存。  
- 對中等大小文件效能穩健；對大型檔案請遵循記憶體管理建議。  
- 整合點（資料庫、REST、雲端）讓您可將註釋嵌入任何工作流程。

### 推薦後續步驟
1. **原型開發**：複製完整範例，對自己的 PDF 或圖像執行，確認尺標如預期顯示。  
2. **探索其他註釋類型**：標註、文字與印章註釋可與距離測量互補。  
3. **建立使用者介面**：設計拖放介面，讓最終使用者能直接在瀏覽器或桌面客戶端放置尺標。  
4. **規劃擴充**：若預期有數千名同時使用者，請實作執行緒池策略，並依效能章節所述監控堆積使用情況。

---

**最後更新：** 2026-06-16  
**測試環境：** GroupDocs.Annotation 25.2 for Java  
**作者：** GroupDocs  

**相關資源：**
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - 完整的 API 文件  
- [API Reference](https://reference.groupdocs.com/annotation/java/) - 詳細的方法與類別參考  
- [Download Page](https://releases.groupdocs.com/annotation/java/) - 最新版本與發行說明  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - 社群支援與討論  
- [Purchase Options](https://purchase.groupdocs.com/buy) - 商業授權資訊  
- [Free Trial](https://releases.groupdocs.com/annotation/java/) - 試用版  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/) - 延長評估授權  

## 相關教學
- [如何使用 Java 為 PDF 添加箭頭 – 完整教學與最佳實踐](/annotation/java/graphical-annotations/add-arrow-annotations-java-groupdocs/)  
- [Java PDF 圖像註釋 – 完整 GroupDocs 教學](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)  
- [編輯 PDF 註釋 Java – 完整 GroupDocs 教學](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)