---
categories:
- Java Development
date: '2026-03-30'
description: 學習如何使用 GroupDocs.Annotation 在 Java 中新增刪除線註解。逐步指南，附程式碼範例、故障排除技巧及文件標註的最佳實踐。
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: 使用 GroupDocs 的 Java 教學：新增刪除線註解
type: docs
url: /zh-hant/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# 新增刪除線註釋 Java - 完整 GroupDocs 指南

有沒有曾經盯著文件看，心想「我需要把這段文字劃掉，但又不能直接拿支紅筆」？你並不孤單。無論你是在構建文件審閱系統、建立編輯工作流程，或只是需要在 Java 應用程式中標記要刪除的文字，**add strikeout annotation java** 都是必備技能。在本教學中，我們將逐步說明在生產環境中實作文字刪除線功能所需的全部知識。

## 快速答案
- **哪個程式庫支援 Java 中的刪除線註釋？** GroupDocs.Annotation for Java  
- **我應該針對哪個主要關鍵字進行 SEO？** add strikeout annotation java  
- **執行範例程式碼是否需要授權？** 免費試用或臨時授權可用於開發；正式環境需要完整授權。  
- **我可以在 PDF、DOCX 與 PPTX 檔案上使用嗎？** 可以 — GroupDocs.Annotation 支援所有主要文件格式。  
- **需要哪個 Java 版本？** JDK 8 or higher (JDK 11+ recommended).  

## 什麼是 add strikeout annotation java？
刪除線註釋會在選取的文字上畫一條線，以視覺方式表示該內容應被移除或忽略。這是一種非破壞性的方式，能在保留原始文字以供稽核或協作審閱的同時，提出刪除建議。

## 為何在 Java 應用程式中使用刪除線註釋？
- **文件審閱工作流程** – 審閱者可標記不需要的文字而不改變原始檔案。  
- **協作編輯** – 團隊成員可即時看到建議的刪除。  
- **法律與合規** – 保持變更的清晰稽核紀錄。  
- **內容遷移** – 在將內容搬移至不同系統前標記過時的段落。  

## 前置條件與環境設定
在開始編寫程式碼之前，你需要以下項目：

- **Java Development Kit (JDK)** 8+ (建議使用 JDK 11+)  
- **Maven 或 Gradle** 用於相依性管理  
- **IDE** – IntelliJ IDEA、Eclipse 或帶有 Java 擴充功能的 VS Code  
- **GroupDocs.Annotation library** – 範例中將使用 25.2 版  

*建議具備:* 基本的 Java 註釋與 PDF 處理知識。

## 設定 GroupDocs.Annotation for Java

### 真正可行的 Maven 設定
將以下儲存庫與相依性加入你的 `pom.xml`，完全照以下示範：

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

### 取得授權設定
GroupDocs 提供多種授權選項：

- **Free trial** – 適合測試（不需信用卡）  
- **Temporary license** – 適用於開發與測試環境  
- **Full license** – 正式環境必須使用；請參閱 [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** 從免費試用開始探索 API，當你準備好開發實際功能時，再切換至臨時授權。

### 快速驗證設定
執行以下最小程式以驗證程式庫正確載入：

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

如果主控台印出成功訊息且沒有錯誤，即表示你已準備好新增刪除線註釋。

## 如何 add strikeout annotation java

以下是一個完整、可投入生產的實作範例，已分成明確的步驟。

### 步驟 1 – 初始化 Annotator
建立指向來源文件的 `Annotator` 實例：

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **為什麼重要：** 使用絕對路徑或正確解析的相對路徑可避免「找不到檔案」例外。

### 步驟 2 – （可選）準備回覆評論
加入回覆可使註釋具備協作功能：

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

當使用者將滑鼠懸停於刪除線上時，會顯示這些評論。

### 步驟 3 – 定義刪除線區域
指定包住欲劃除文字的矩形區域：

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **座標提示：** 原點 (0,0) 位於頁面的左上角；X 向右遞增，Y 向下遞增。請使用能顯示座標的 PDF 檢視器以微調這些數值。

### 步驟 4 – 設定刪除線註釋
設定外觀、頁碼，並附加評論：

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*顏色說明：* `65535` 代表整數 RGB 格式的黃色。變更此值即可使用其他顏色。

### 步驟 5 – 套用註釋並儲存
將註釋加入文件並寫入輸出檔案：

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### 步驟 6 – 清理資源（關鍵！）
務必釋放 annotator，以釋放本機資源：

```java
if (annotator != null) {
    annotator.dispose();
}
```

在正式環境中，請將使用方式包在 try‑with‑resources 區塊或 `try/finally` 結構中。

## 常見問題與解決方法

| 問題 | 徵狀 | 解決方案 |
|---------|---------|-----|
| **找不到檔案** | `Annotator` 拋出例外 | 使用絕對路徑，確認讀取權限，確保沒有其他程序鎖定檔案 |
| **座標錯誤** | 刪除線出現在預期文字之外 | 再次確認 PDF 檢視器的座標系統；依需求調整座標點 |
| **註釋不可見** | 儲存後未看到刪除線 | 提升 `opacity`（例如 `0.9`），確認 `pageNumber`（從 0 起算），確保座標點形成正確的矩形 |
| **記憶體不足錯誤** | 在大型 PDF 上程式崩潰 | 增加 JVM 堆積大小（`-Xmx2048m`），批次處理文件，並始終呼叫 `dispose()` |

## 生產環境效能最佳實踐

### 記憶體管理
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### 批次處理策略
當需要為數十或數百個檔案加註時：

- 每批次處理 10‑20 份文件。  
- 為每個檔案記錄成功或失敗。  
- 為每個文件重新初始化 `Annotator`，以避免記憶體洩漏。  

### 快取技巧
- 快取常用的文件範本。  
- 儲存標準版面之預先計算座標對映表。  

## 真實案例應用

1. **Document Review Systems** – 編輯者可在不改動原始合約的情況下建議刪除。  
2. **Legal Amendments** – 律師在保留原始文字以供稽核的同時，追蹤條款刪除。  
3. **Academic Peer Review** – 評審者標記需刪除的段落並加入行內評論。  
4. **Content Migration** – 在 CMS 遷移期間，刪除線可突顯需要取代的過時內容。  

## 進階自訂

### 自訂樣式
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### 新增中繼資料
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## 疑難排解清單
- ✅ 你能手動開啟來源檔案嗎？  
- ✅ 所有 GroupDocs 相依性是否已在 classpath 中？  
- ✅ 座標點是否形成有效的矩形？  
- ✅ 頁碼是否正確（0 起算）？  
- ✅ 記憶體堆積是否足夠？  
- ✅ 你是否對輸出資料夾具有寫入權限？  
- ✅ 文件格式是否受支援（PDF、DOCX、PPTX 等）？  

## 常見問與答

**Q: 我可以在 Spring Boot 服務中使用 GroupDocs.Annotation 嗎？**  
A: 可以。加入 Maven 相依性，注入建立 `Annotator` 的服務類別，並使用 Spring 的 Bean 範圍管理其生命週期。

**Q: 哪些文件格式支援刪除線註釋？**  
A: PDF、DOCX、PPTX 以及 GroupDocs.Annotation 支援的其他多種格式。PDF 提供最精確的座標處理。

**Q: 如何處理頁面尺寸不同的文件？**  
A: 透過 `annotator.getPageInfo(pageNumber)` 取得頁面尺寸，並相應地縮放座標。

**Q: 是否可以編輯或刪除已存在的刪除線註釋？**  
A: 當然可以。使用 `annotator.getAnnotations(pageNumber)` 取得，然後使用 `annotator.update(updatedAnnotation)` 或 `annotator.delete(annotationId)`。

**Q: 大量新增註釋對效能有何影響？**  
A: 新增數百筆註釋通常沒問題，但需監控記憶體使用。對於非常大的註釋集合，建議分頁顯示或按需延遲載入註釋。

## 結論
現在你已擁有使用 GroupDocs.Annotation 進行 **add strikeout annotation java** 的完整、生產就緒指南。先從簡單的驗證範例開始，然後擴展至批次處理、自訂樣式與中繼資料豐富。請務必仔細測試座標、負責任地管理資源，並為你的環境選擇合適的授權模式。

想探索更多嗎？請查看其他註釋類型——突出顯示、備註、圖片、箭頭與浮水印，以打造完整的文件協作套件。

---

**最後更新：** 2026-03-30  
**測試環境：** GroupDocs.Annotation 25.2 for Java  
**作者：** GroupDocs  

**其他資源**
- [GroupDocs Annotation 文件說明](https://docs.groupdocs.com/annotation/java/)
- [API 參考指南](https://reference.groupdocs.com/annotation/java/)
- [下載最新版本](https://releases.groupdocs.com/annotation/java/)
- [購買完整授權](https://purchase.groupdocs.com/buy)
- [開始免費試用](https://releases.groupdocs.com/annotation/java/)
- [取得臨時授權](https://purchase.groupdocs.com/temporary-license/)
- [社群支援論壇](https://forum.groupdocs.com/c/annotation/)