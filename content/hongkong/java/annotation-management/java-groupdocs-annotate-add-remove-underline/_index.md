---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation 在 Java 文件中新增和移除底線註解。這份詳細的指南將幫助您提昇文件管理能力。"
"title": "使用 GroupDocs 在 Java 中新增和刪除下劃線註解的綜合指南"
"url": "/zh-hant/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# 如何實作 Java：使用 GroupDocs 新增和刪除底線註釋

## 介紹

想要透過程式設計方式新增或刪除註解來增強您的文件管理系統嗎？本教學將指導您使用 Java 中強大的 GroupDocs.Annotation 程式庫在 PDF 等文件中新增和刪除底線註解。

**您將學到什麼：**
- 初始化註解器類別。
- 使用 GroupDocs.Annotation for Java 新增帶有註解的底線註解。
- 從文件中刪除所有註釋。
- 配置您的環境以有效地使用 GroupDocs.Annotation。

讓我們探索如何在您的專案中利用這些功能。在開始之前，請確保您已滿足必要的先決條件。

## 先決條件

### 所需的庫和依賴項
為了有效地遵循本教程，請確保您已：
- **Java 版 GroupDocs.Annotation**：建議使用 25.2 或更高版本。
- **Java 開發工具包 (JDK)**：需要版本 8 或更高版本。

### 環境設定要求
確保您的開發環境包含 IntelliJ IDEA 或 Eclipse 等 IDE 和 Maven 等建置工具。

### 知識前提
對 Java 程式設計的基本了解，尤其是透過 Maven 使用函式庫，將會很有幫助。

## 為 Java 設定 GroupDocs.Annotation

若要開始在 Java 專案中使用 GroupDocs.Annotation，請依照下列設定步驟操作：

**Maven配置：**
將以下配置新增至您的 `pom.xml` 檔案下載並整合 GroupDocs.Annotation。

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

**許可證取得：**
首先，請下載 GroupDocs 的免費試用版或取得臨時許可證，以探索其庫的全部功能。如需用於生產用途，則需要購買許可證。

## 實施指南

### 功能1：初始化註釋器並新增底線註釋

本節將指導您初始化 `Annotator` 類別並在您的文件中添加下劃線註釋。

#### 概述
新增註解有助於突出顯示文件的特定部分。在這裡，我們將重點放在帶有註釋的文字下劃線，以便澄清或提供回饋。

#### 逐步實施

**1. 初始化註解器**
創建一個 `Annotator` 對象並加載您的 PDF 文件。

```java
import com.groupdocs.annotation.Annotator;

// 載入要註解的文檔
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. 建立帶有回應的評論**
定義與底線註解相關的註解。

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

**3. 定義底線註解點**
設定座標以確定下劃線出現的位置。

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

**4.建立並配置底線註釋**
建立下劃線註釋並設定其屬性，如顏色、不透明度和註釋。

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // ARGB 格式的黃色
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5.保存附註解的文檔**
將變更儲存到新文件。

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### 故障排除提示
- 確保所有點的座標都在文件邊界內。
- 驗證 `outputPath` 目錄存在並且可寫入。

### 功能 2：儲存無註解的文檔

本節介紹如何從先前註釋的文檔中刪除所有註釋。

#### 概述
您可能需要儲存文件的乾淨版本（不含任何註解）以供共用或存檔。

#### 逐步實施

**1. 使用附註解的文件初始化註解器**
載入具有現有註解的文檔。

```java
Annotator annotator = new Annotator(outputPath);
```

**2. 配置儲存選項以刪除註釋**
指定不應在輸出檔中儲存任何註解。

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. 儲存不含註解的文檔**
定義清理文檔的路徑並儲存。

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## 實際應用

以下是這些功能可以發揮作用的一些實際場景：
1. **文件審查**：突出顯示並評論合約或報告的某些部分以供審查。
2. **教育工具**：為學生在教科書上添加註釋或更正。
3. **協作編輯**：在團隊成員之間共享註釋的草稿以獲得回饋。
4. **法律文件**：在討論過程中劃出法律文件中的關鍵條款。
5. **行銷資料**：在分發小冊子之前突出顯示重要資訊。

## 性能考慮
使用 GroupDocs.Annotation 時，請考慮以下技巧來優化效能：
- **記憶體管理**：妥善處置 `Annotator` 對象來釋放資源。
- **批次處理**：如果註釋多個文檔，請分批處理以有效管理系統負載。
- **資源分配**：確保您的環境具有足夠的記憶體和處理能力來處理大檔案。

## 結論
您已經學習如何使用 GroupDocs.Annotation for Java 新增和移除底線註解。本教學介紹如何初始化 Annotator 類別、如何配置註解的註解以及如何儲存不含註解的文件。 

為了進一步探索，請考慮將這些功能整合到您現有的文件管理系統中，或嘗試 GroupDocs 提供的其他註解類型。

## 常見問題部分
1. **如何在一次運行中配置多個下劃線註解？**
   - 創建多個 `UnderlineAnnotation` 物件並使用 `annotator.add()` 方法。
2. **我可以使用此庫註釋 PDF 中的圖像嗎？**
   - 是的，GroupDocs.Annotation 支援在 PDF 等文件中註釋影像。
3. **GroupDocs.Annotation 支援哪些檔案格式？**
   - 它支援各種文件格式，包括 PDF、Word、Excel 等。