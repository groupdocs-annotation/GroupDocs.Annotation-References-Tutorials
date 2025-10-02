---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation for Java 有效地在文件中建立、管理和儲存註解。本逐步指南涵蓋初始化、註釋類型和整合技巧。"
"title": "完整指南&#58;使用 GroupDocs.Annotation for Java 建立和管理註釋"
"url": "/zh-hant/java/annotation-management/annotations-groupdocs-annotation-java-tutorial/"
type: docs
"weight": 1
---

# 完整指南：使用 GroupDocs.Annotation for Java 建立和管理註釋

## 介紹

您是否希望透過添加強大的文件註釋功能來增強您的 Java 應用程式？無論您是需要突出顯示關鍵部分還是添加詳細的註釋，整合像 GroupDocs.Annotation 這樣的高效解決方案都可以簡化各行各業的工作流程。本教學將引導您使用 GroupDocs.Annotation for Java 輕鬆地在文件中載入、建立和儲存註解。

**您將學到什麼：**
- 如何使用文檔初始化註解器。
- 以程式設計方式建立區域和橢圓註釋。
- 在文件中新增多個註解。
- 儲存具有特定註釋類型的註釋文件。

讓我們從設定您的開發環境開始！

## 先決條件

在開始之前，請確保您的開發環境已正確配置：

- **所需庫：**
  - GroupDocs.Annotation for Java 版本 25.2
  - Maven 用於依賴管理

- **環境設定要求：**
  - 在您的機器上安裝 Java SDK。
  - 使用 IntelliJ IDEA 或 Eclipse 等 IDE 進行開發。

- **知識前提：**
  - 對 Java 程式設計有基本的了解。
  - 熟悉Maven建置工具。

## 為 Java 設定 GroupDocs.Annotation

若要使用 Maven 將 GroupDocs.Annotation 整合到您的專案中，請將以下配置新增至您的 `pom.xml`：

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

1. **免費試用：** 下載試用版測試 GroupDocs.Annotation。
2. **臨時執照：** 在評估期間取得臨時許可證以獲得完全存取權。
3. **購買：** 如果滿意，您可以購買完整許可證。

**基本初始化：**
若要初始化 Annotator，請透過提供文件的檔案路徑來建立實例：

```java
import com.groupdocs.annotation.Annotator;

public class Feature1 {
    public void loadAnnotator(String fileName) {
        try (final Annotator annotator = new Annotator(fileName)) {
            // 準備使用！
        }
    }
}
```

## 實施指南

### 功能 1：載入和初始化註解器

**概述：**
此功能示範如何使用文件文件路徑初始化註釋器，以及設定 Java 應用程式以執行註解任務。

#### 步驟 1：初始化註解器
建立一個實例 `Annotator` 提供檔案名稱。此步驟至關重要，因為它可以幫助您為文件做好進一步註釋的準備。

```java
import com.groupdocs.annotation.Annotator;

public class Feature1 {
    public void loadAnnotator(String fileName) {
        try (final Annotator annotator = new Annotator(fileName)) {
            // 註釋器已初始化並準備就緒。
        }
    }
}
```

### 功能 2：建立區域註釋

**概述：**
了解如何建立具有特定屬性（例如大小、顏色和頁碼）的區域註釋。

#### 步驟 1：建立新 `AreaAnnotation` 目的
首先實例化 `AreaAnnotation` 班級。

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;

public class Feature2 {
    public AreaAnnotation createAreaAnnotation() {
        AreaAnnotation area = new AreaAnnotation();
```

#### 步驟 2：設定矩形邊界
使用 `Rectangle` 目的。

```java
        area.setBox(new Rectangle(100, 100, 100, 100));
```

#### 步驟3：設定背景顏色
指定可見性的背景顏色。

```java
        area.setBackgroundColor(65535);
```

#### 步驟 4：指定頁碼
指示此註記將出現在文件的什麼位置。

```java
        area.setPageNumber(1);

        return area;
    }
}
```

### 功能 3：建立橢圓註釋

**概述：**
此功能專注於建立橢圓註釋，允許在文件中新增圓形或橢圓形註釋。

#### 步驟 1：建立新 `EllipseAnnotation` 目的
首先實例化 `EllipseAnnotation`。

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.EllipseAnnotation;

public class Feature3 {
    public EllipseAnnotation createEllipseAnnotation() {
        EllipseAnnotation ellipse = new EllipseAnnotation();
```

#### 步驟 2：定義矩形邊界
使用設定邊界尺寸 `Rectangle`。

```java
        ellipse.setBox(new Rectangle(100, 100, 100, 100));
```

#### 步驟3：設定背景顏色
選擇合適的背景顏色。

```java
        ellipse.setBackgroundColor(123456);
```

#### 步驟 4：標示頁碼
指定此註解的頁面。

```java
        ellipse.setPageNumber(2);

        return ellipse;
    }
}
```

### 功能 4：為 Annotator 新增註釋

**概述：**
了解如何使用 `Annotator` 實例。

#### 步驟 1：建立並新增註釋
建立註釋並將其新增至註釋者清單。

```java
import com.groupdocs.annotation.Annotator;
import java.util.ArrayList;
import java.util.List;
import com.groupdocs.annotation.models.AnnotationBase;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;
import com.groupdocs.annotation.models.annotationmodels.EllipseAnnotation;

public class Feature4 {
    public void addAnnotations(Annotator annotator) {
        AreaAnnotation area = new AreaAnnotation();
        area.setBox(new Rectangle(100, 100, 100, 100));
        area.setBackgroundColor(65535);
        area.setPageNumber(1);

        EllipseAnnotation ellipse = new EllipseAnnotation();
        ellipse.setBox(new Rectangle(100, 100, 100, 100));
        ellipse.setBackgroundColor(123456);
        ellipse.setPageNumber(2);

        List<AnnotationBase> annotations = new ArrayList<>();
        annotations.add(area);
        annotations.add(ellipse);

        annotator.add(annotations);
    }
}
```

### 功能5：儲存有特定註解的文檔

**概述：**
了解如何儲存已註解的文檔，指定應保留哪些註解類型。

#### 步驟1：指定輸出路徑
確定已儲存的文件所在的位置。

```java
public class Feature5 {
    public String getOutputPath(String fileName) {
        return "YOUR_OUTPUT_DIRECTORY" + "/filtered_output.pdf";
```

#### 步驟 2：儲存已註記的文件及其選項
配置儲存選項以僅包含所需的註解並執行儲存程序。

```java
    public void saveAnnotatedDocument(Annotator annotator, String outputPath) {
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setAnnotationTypes(AnnotationType.ELLIPSE);

        annotator.save(outputPath, saveOptions);
    }
}
```

## 實際應用

- **法律文件審查：** 突出顯示需要注意或修改的部分。
- **教育資源：** 為學習小組註釋教科書和論文。
- **技術手冊：** 在工程文件中標記重要註釋或說明。

整合可能性包括將註釋與專案管理工具連結以追蹤隨時間的變化。

## 性能考慮

為確保效能平穩運作：
- 限制大型文件的並發註釋數量。
- 透過在註解任務完成後釋放資源來管理記憶體使用情況。
- 實作 Java 記憶體管理的最佳實踐，例如使用 try-with-resources 來有效地處理 Annotator 實例。

## 結論

透過本指南，您學習如何使用 GroupDocs.Annotation 在 Java 中載入、建立和儲存註解。此功能增強了文件工作流程，讓您更輕鬆地突出顯示重要資訊、新增註解以及跨各種應用程式管理文件。