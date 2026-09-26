---
categories:
- Java Development
date: '2026-09-25'
description: 了解如何在 Java 中使用 try resources 与 GroupDocs.Annotation 保存特定的 PDF 页面。包括 Spring
  Boot 服务示例和性能技巧。
keywords:
- save specific pdf pages
- try with resources java
- remove unused pdf pages
- use try resources
lastmod: '2026-09-25'
linktitle: 保存特定页面 Java Annotation
og_description: 了解如何在 Java 中使用 try resources 与 GroupDocs.Annotation 保存特定的 PDF 页面。提供分步指南、性能技巧以及
  Spring Boot 集成。
og_image_alt: Guide to saving specific PDF pages in Java using GroupDocs.Annotation
  and try resources
og_title: 如何在 Java 中使用 try resources 保存特定的 PDF 页面
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to save specific pdf pages using try resources in Java with
    GroupDocs.Annotation. Includes Spring Boot service example and performance tips.
  headline: How to save specific pdf pages with try resources in Java
  type: TechArticle
- questions:
  - answer: Not with a single `SaveOptions` call. Run separate saves for each range
      and merge the results afterward.
    question: Can I save non‑consecutive pages (e.g., 1, 3, 7)?
  - answer: 'Yes—provide the password when constructing the `Annotator`: `new Annotator(inputFile,
      loadOptions.setPassword("your_password"))`.'
    question: Does this work with password‑protected documents?
  - answer: PDF, Microsoft Word, Excel, PowerPoint, and many others. See the [official
      documentation](https://docs.groupdocs.com/annotation/java/) for the full list.
    question: What file formats are supported?
  - answer: Absolutely—set `saveOptions.setAnnotationsOnly(true)` to create an annotation‑only
      file.
    question: Can I save just the annotations without the original content?
  - answer: Use `setLoadOnlyAnnotatedPages(true)`, process in chunks, and consider
      increasing the JVM heap size.
    question: How do I handle very large documents (1000+ pages)?
  type: FAQPage
tags:
- save specific pdf pages
- groupdocs
- java annotation
- document processing
- pdf manipulation
title: 如何在 Java 中使用 try resources 保存特定的 PDF 页面
type: docs
url: /zh/java/document-saving/groupdocs-annotation-java-save-specific-page-range/
weight: 1
---

# 如何在 Java 中从带注释的文档中保存特定 PDF 页面

当您需要从大型带注释的文件中**保存特定 pdf 页面**时，使用 Java 的 *try with resources* 模式结合 GroupDocs.Annotation 可以提供安全、内存高效的解决方案。本教程展示如何设置库、提取页面范围，并将逻辑集成到 Spring Boot 服务中——同时保持代码整洁并正确释放资源。

## 介绍

`Annotator` 是 GroupDocs.Annotation 中的主要类，用于加载文档并提供注释处理和保存的方法。  
在许多业务场景——法律合同、技术手册或研究论文——中，您通常只需要包含相关注释的少数页面。仅提取这些页面可将存储成本降低最高达 96 %，加快下游处理，并通过仅共享允许的章节帮助您保持合规。

**您将在本指南结束时掌握的内容：**  
- 安装和授权 GroupDocs.Annotation for Java  
- 使用 `try with resources` 安全保存页面范围  
- 以低内存开销处理大型 PDF  
- 将逻辑嵌入 Spring Boot 文档服务  
- 排查常见陷阱，如文件锁定和内存不足错误  

## 快速答案

- **“try with resources java” 是什么作用？** 它会自动关闭 `Annotator`，防止文件锁定和内存泄漏。  
- **哪个库处理页面范围保存？** `GroupDocs.Annotation` 提供带有 `setFirstPage`/`setLastPage` 的 `SaveOptions`。`SaveOptions` 允许您指定输出设置，如页面范围以及是否仅包含注释。  
- **我可以在 Spring Boot 服务中使用它吗？** 可以——请参阅 “Spring Boot 文档服务集成” 部分。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要完整许可证。  
- **对大型 PDF（1000+ 页）安全么？** 使用 load‑only‑annotated‑pages 并进行批处理以保持低内存使用。  

## 什么是保存特定 PDF 页面？

**保存特定 pdf 页面** 操作从源文档中提取定义的页面区间，同时保留这些页面上的所有注释。它会创建一个仅包含所选页面的更小 PDF，非常适合有针对性的共享或归档。

## 为什么在页面保存时使用 try resources？

使用 `try with resources` 可确保 `Annotator` 实例在代码块结束时立即被释放。这种确定性的清理可防止常见的 “文件被锁定” 异常，并使 JVM 的堆占用保持可预测——在并行处理数十个大型 PDF 时尤为重要。

## 前置条件和设置

### 您需要的条件

- **JDK 8+**（建议使用 JDK 11+）  
- **Maven** 或 **Gradle** 用于依赖管理  
- **GroupDocs.Annotation for Java** — 版本 25.2 或更高（支持 50 多种格式）  
- 对 Java I/O 和面向对象编程有基本了解  

### 为 Java 设置 GroupDocs.Annotation

#### Maven 配置

将依赖添加到您的 `pom.xml`（复制粘贴即可）：

```xml
<!-- ```xml
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
``` -->
```

#### Gradle 设置（如果您更喜欢 Gradle）

```groovy
// ```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/annotation/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```
```

### 获取许可证

先使用免费试用，然后根据需要切换到临时或正式许可证：

- **免费试用：** 适合测试和开发 – 从 [GroupDocs releases](https://releases.groupdocs.com/annotation/java/) 获取  
- **临时许可证：** 需要更多时间评估？获取 [临时许可证](https://purchase.groupdocs.com/temporary-license/)  
- **正式许可证：** 准备投入生产？[在此购买](https://purchase.groupdocs.com/buy)  

> **专业提示：** 试用版仅移除少数高级功能，已足以完成本教程并构建概念验证。

## try with resources 在 Java 中如何工作？

`try` `with` `resources` 会在代码块结束时自动调用实现了 `AutoCloseable` 接口的对象的 `close()` 方法。当您在此结构中包装 `Annotator` 实例时，库会释放文件句柄并清除内部缓冲区，无需额外代码，从而消除残留锁定的风险。

## 核心实现：保存特定页面范围

### `Annotator` 定义锚点

`Annotator` 是 GroupDocs.Annotation 用于加载、编辑和保存带注释文档的主要类。它提供访问注释、修改页面和导出结果的方法。

### 步骤 1：设置文件路径工具

创建一个小型助手，以一致方式构建输出路径：

```java
// ```java
import org.apache.commons.io.FilenameUtils;

public class FilePathConfiguration {
    public String getOutputFilePath(String inputFile) {
        return "YOUR_OUTPUT_DIRECTORY/SavingSpecificPageRange" + "." + FilenameUtils.getExtension(inputFile);
    }
}
```
```

将路径逻辑集中化，使以后更改目录变得容易，并保持代码可测试。

### 步骤 2：实现页面范围保存

以下代码片段展示了核心逻辑。它使用 `try with resources` 来保证清理：

```java
// ```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.export.SaveOptions;

public class SaveSpecificPageRange {
    public void run(String inputFile) {
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(2);  // Start from page 2
            saveOptions.setLastPage(4);   // End at page 4
            
            annotator.save(outputPath, saveOptions);
        }
    }
}
```
```

- `setFirstPage(2)` 和 `setLastPage(4)` 定义了一个**包含**范围（第 2‑4 页）。  
- 当代码块退出时，`Annotator` 会自动关闭，防止文件锁定问题。  

### 高级文件路径配置

在生产环境中，您可能需要动态命名：

```java
// ```java
public class FilePathConfiguration {
    private final String baseOutputDirectory;
    
    public FilePathConfiguration(String baseOutputDirectory) {
        this.baseOutputDirectory = baseOutputDirectory;
    }
    
    public String getInputFilePath(String filename) {
        return "YOUR_DOCUMENT_DIRECTORY/" + filename;
    }
    
    public String getOutputFilePath(String inputFile, String suffix) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_%s.%s", baseOutputDirectory, baseName, suffix, extension);
    }
}
```
```

现在输出文件的名称将类似于 `contract_pages_2-4.pdf`，清晰地表明提取了哪些页面。

## 常见陷阱及规避方法

### 陷阱 #1：页面索引混淆

**问题：** 假设页面编号从 0 开始。  
**解决方案：** GroupDocs.Annotation 的页面编号从 1 开始，与你在 PDF 查看器中看到的相同。

```java
// ```java
// Wrong - this tries to start from page 0 (doesn't exist)
saveOptions.setFirstPage(0);

// Right - this starts from the actual first page
saveOptions.setFirstPage(1);
```
```

### 陷阱 #2：资源泄漏

**问题：** 忘记关闭 `Annotator` 会导致文件被锁定。  
**解决方案：** 始终将 `Annotator` 包装在 `try with resources` 块中，或显式调用 `close()`。

```java
// ```java
// Good - automatic resource management
try (final Annotator annotator = new Annotator(inputFile)) {
    // your code here
} // automatically closes

// Also acceptable - manual closing
Annotator annotator = null;
try {
    annotator = new Annotator(inputFile);
    // your code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
```

### 陷阱 #3：无效的页面范围

**问题：** 指定的范围超出文档的页数。  
**解决方案：** 在保存前使用 `annotator.getDocumentInfo().getPagesCount()` 验证范围。

```java
// ```java
public void savePageRangeWithValidation(String inputFile, int firstPage, int lastPage) {
    try (final Annotator annotator = new Annotator(inputFile)) {
        // Get document info to check page count
        DocumentInfo documentInfo = annotator.getDocument().getDocumentInfo();
        int totalPages = documentInfo.getPageCount();
        
        // Validate range
        if (firstPage < 1 || firstPage > totalPages) {
            throw new IllegalArgumentException("First page out of range: " + firstPage);
        }
        if (lastPage < firstPage || lastPage > totalPages) {
            throw new IllegalArgumentException("Last page out of range: " + lastPage);
        }
        
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setFirstPage(firstPage);
        saveOptions.setLastPage(lastPage);
        
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        annotator.save(outputPath, saveOptions);
    }
}
```
```

## 性能优化技巧

### 大文档的内存管理

在处理 100 + 页的 PDF 时，启用仅加载带注释页面以保持堆内存低：

```java
// ```java
public class OptimizedPageRangeSaver {
    public void saveWithOptimization(String inputFile, int firstPage, int lastPage) {
        // Configure for lower memory usage
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadOnlyAnnotatedPages(true); // Only load pages with annotations
        
        try (final Annotator annotator = new Annotator(inputFile, loadOptions)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            // Optional: Enable compression for smaller output files
            saveOptions.setAnnotationsOnly(false); // Set to true if you only want annotations
            
            String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
            annotator.save(outputPath, saveOptions);
        }
    }
}
```
```

关键策略：
- `setLoadOnlyAnnotatedPages(true)` 通过仅加载包含注释的页面来降低内存使用。  
- `setAnnotationsOnly(true)` 创建仅存储注释层的轻量文件。  
- 使用固定线程池的批处理可避免耗尽系统资源。

### 批量处理多个文档

对于高吞吐场景，批量处理文件：

```java
// ```java
public class BatchPageRangeSaver {
    public void processBatch(List<String> inputFiles, int firstPage, int lastPage) {
        for (String inputFile : inputFiles) {
            try {
                savePageRangeWithValidation(inputFile, firstPage, lastPage);
                System.out.println("Successfully processed: " + inputFile);
            } catch (Exception e) {
                System.err.println("Failed to process " + inputFile + ": " + e.getMessage());
                // Log the error and continue with next file
            }
        }
    }
}
```
```

## 与流行框架的集成

### Spring Boot 文档服务集成

下面是一个最小化的 Spring Boot 服务，它接收 PDF，提取页面范围，并将新文件作为字节数组返回。

```java
// ```java
@Service
public class DocumentPageRangeService {
    
    @Value("${app.document.output-directory}")
    private String outputDirectory;
    
    public String savePageRange(String inputFile, int firstPage, int lastPage) {
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            String outputPath = generateOutputPath(inputFile, firstPage, lastPage);
            annotator.save(outputPath, saveOptions);
            
            return outputPath;
        } catch (Exception e) {
            throw new DocumentProcessingException("Failed to save page range", e);
        }
    }
    
    private String generateOutputPath(String inputFile, int firstPage, int lastPage) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_pages_%d-%d.%s", 
                            outputDirectory, baseName, firstPage, lastPage, extension);
    }
}
```
```

该服务使用构造函数注入 `AnnotatorFactory`，保持控制器简洁且易于测试。

## 实际应用和使用场景

### 法律文档处理

律所通常只需共享已审阅的条款。提取这些页面可降低泄露机密部分的风险。

```java
// ```java
public class LegalDocumentProcessor {
    public void extractEvidencePages(String caseFile, List<Integer> evidencePages) {
        // Group consecutive pages for efficient processing
        List<PageRange> ranges = groupConsecutivePages(evidencePages);
        
        for (PageRange range : ranges) {
            String outputFile = String.format("evidence_%d_%d-to-%d.pdf", 
                                            getCaseNumber(caseFile), range.start, range.end);
            savePageRange(caseFile, range.start, range.end, outputFile);
        }
    }
}
```
```

### 教育内容管理

教师可以仅提取学生在作业中需要的带注释章节，减少下载大小并提升专注度。

```java
// ```java
public class EducationalContentExtractor {
    public void createAssignmentPacket(String textbook, int chapterStart, int chapterEnd) {
        try (final Annotator annotator = new Annotator(textbook)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(chapterStart);
            saveOptions.setLastPage(chapterEnd);
            
            String assignmentFile = generateAssignmentFileName(textbook, chapterStart, chapterEnd);
            annotator.save(assignmentFile, saveOptions);
        }
    }
}
```
```

### 质量保证评审

质量保证团队可以隔离带有评审者评论的页面，从而加快迭代周期。

```java
// ```java
public class QAReviewExtractor {
    public void extractReviewedPages(String document) {
        try (final Annotator annotator = new Annotator(document)) {
            // Get pages with annotations
            List<Integer> annotatedPages = getAnnotatedPageNumbers(annotator);
            
            if (!annotatedPages.isEmpty()) {
                int firstPage = Collections.min(annotatedPages);
                int lastPage = Collections.max(annotatedPages);
                
                SaveOptions saveOptions = new SaveOptions();
                saveOptions.setFirstPage(firstPage);
                saveOptions.setLastPage(lastPage);
                
                String reviewFile = document.replace(".pdf", "_review_comments.pdf");
                annotator.save(reviewFile, saveOptions);
            }
        }
    }
}
```
```

## 最佳实践摘要

1. **验证页面号码** 在调用保存操作之前。  
2. **始终使用 `try with resources`** 以确保 `Annotator` 被关闭。  
3. **为大型 PDF 启用 `setLoadOnlyAnnotatedPages(true)`** 以保持内存使用受控。  
4. **在所有受支持的格式上进行测试**——GroupDocs.Annotation 支持超过 50 种输入和输出类型，包括 PDF、DOCX、XLSX、PPTX 和图像文件。  
5. **监控 JVM 堆** 并根据批处理作业的需要调整 `-Xmx`。  

## 常见问题排查

### 问题：“文件被锁定” 错误

**症状：** 在 `save()` 期间出现提及锁定文件的异常。  
**原因：**  
- 之前的 `Annotator` 实例未关闭。  
- 文件在其他应用程序中打开。  
- 文件系统权限不足。  

**解决方案：** 确保每个 `Annotator` 都包装在 `try with resources` 块中，并验证操作系统层面的文件锁。

```java
// ```java
// Ensure proper cleanup
try (final Annotator annotator = new Annotator(inputFile)) {
    // ... your code ...
} // Automatically releases file handles

// Verify file accessibility before processing
File file = new File(inputFile);
if (!file.canRead()) {
    throw new IllegalArgumentException("Cannot read input file: " + inputFile);
}
if (!file.getParentFile().canWrite()) {
    throw new IllegalArgumentException("Cannot write to output directory");
}
```
```

### 问题：内存不足错误

**症状：** 处理大型 PDF 时出现 `OutOfMemoryError`。  
**解决方案：**  
1. 增加 JVM 堆内存（`-Xmx2g` 或更高）。  
2. 使用 `setLoadOnlyAnnotatedPages(true)` 和 `setAnnotationsOnly(true)`。  
3. 将文档分成更小的批次处理。

### 问题：注释未保留

**症状：** 输出文件缺少原始标记。  
**解决方案：** 不要误将 `setAnnotationsOnly(false)` 启用；保持默认设置以保留注释。

```java
// ```java
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationsOnly(false); // Keep both content and annotations
saveOptions.setFirstPage(firstPage);
saveOptions.setLastPage(lastPage);
```
```

## 常见问题

**Q: 我可以保存非连续页面（例如 1、3、7）吗？**  
A: 单次调用 `SaveOptions` 无法实现。需要对每个范围分别保存，然后再合并结果。

**Q: 这适用于受密码保护的文档吗？**  
A: 可以——在构造 `Annotator` 时提供密码，例如 `new Annotator(inputFile, loadOptions.setPassword("your_password"))`。

**Q: 支持哪些文件格式？**  
A: PDF、Microsoft Word、Excel、PowerPoint 等众多格式。完整列表请参阅 [official documentation](https://docs.groupdocs.com/annotation/java/)。

**Q: 我可以仅保存注释而不保留原始内容吗？**  
A: 完全可以——设置 `saveOptions.setAnnotationsOnly(true)` 可创建仅包含注释的文件。

**Q: 如何处理非常大的文档（1000+ 页）？**  
A: 使用 `setLoadOnlyAnnotatedPages(true)`，分块处理，并考虑增大 JVM 堆大小。

**Q: 有办法在保存前预览页面吗？**  
A: GroupDocs.Annotation 侧重于处理，但您可以通过 `annotator.getDocumentInfo()` 获取页数和注释位置，以决定要提取的范围。

## 其他资源

- 文档： [GroupDocs.Annotation for Java Docs](https://docs.groupdocs.com/annotation/java/)  
- 官方文档： [official documentation](https://docs.groupdocs.com/annotation/java/)  
- API 参考： [Complete API Documentation](https://reference.groupdocs.com/annotation/java/)  
- 下载： [Latest Releases](https://releases.groupdocs.com/annotation/java/)  
- GroupDocs 发布： [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- 许可证选项： [License Options](https://purchase.groupdocs.com/buy)  
- 在此购买： [Purchase here](https://purchase.groupdocs.com/buy)  
- 免费试用： [Try It Now](https://releases.groupdocs.com/annotation/java/)  
- 临时许可证： [Get Evaluation License](https://purchase.groupdocs.com/temporary-license/)  
- 支持： [Community Forum](https://forum.groupdocs.com/c/annotation/)  

---

**最后更新：** 2026-09-25  
**测试环境：** GroupDocs.Annotation 25.2 (Java)  
**作者：** GroupDocs

## 相关教程

- [使用 GroupDocs.Annotation 的 Java 减少 PDF 大小 – 完整指南](/annotation/java/document-saving/)
- [使用 GroupDocs Java 与 Azure Blob 保存带注释的 PDF](/annotation/java/document-loading/download-annotate-azure-blob-groupdocs-java/)
- [使用 GroupDocs.Annotation Java 加载受密码保护的 PDF](/annotation/java/advanced-features/)