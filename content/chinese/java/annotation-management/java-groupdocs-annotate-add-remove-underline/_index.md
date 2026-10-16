---
date: '2026-10-16'
description: 了解如何在 Java 中保存不带批注的 PDF，掌握 Java PDF 内存管理，并使用 GroupDocs.Annotation 添加下划线批注。一步步指南。
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: 使用 GroupDocs 的 Java 文档批注
og_description: 了解如何在 Java 中保存不带批注的 PDF，掌握 Java PDF 内存管理，并使用 GroupDocs.Annotation
  添加下划线批注。一步步指南。
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: 如何使用 GroupDocs 在 Java 中保存不带批注的 PDF
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: 如何使用 GroupDocs 在 Java 中保存不带批注的 PDF
type: docs
url: /zh/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# 如何在 Java 中使用 GroupDocs 保存无批注的 PDF

如果您需要在仍然能够添加协作下划线注释的情况下 **保存 PDF 无批注**，那么您来对地方了。许多 Java 开发者在为最终分发保持文档的干净版本时会遇到困难，尤其是当同一文件用于迭代审阅时。在本教程中，您将学习如何生成干净的 PDF、有效管理内存，并使用 GroupDocs.Annotation 应用带有评论的下划线批注。完成后，您将了解完整的工作流——从加载 PDF 到生成无水印的最终副本——以及构建强大的 **java 文档审阅系统** 的最佳实践提示。

## 快速答案
- **如何添加下划线批注？** 使用 `UnderlineAnnotation` 与 `annotator.add()` 然后保存文档。  
- **如何保存 PDF 无批注？** 加载已批注的文件，在 `SaveOptions` 中设置 `AnnotationType.NONE`，然后保存为新副本。  
- **需要哪些库？** GroupDocs.Annotation v25.2（或更高版本）及其 Maven 仓库。  
- **生产环境是否需要许可证？** 是——应用有效的 GroupDocs 许可证以避免水印。  
- **我能高效处理多个文档吗？** 将每个 `Annotator` 包装在 try‑with‑resources 块中，并在每个文件处理后释放。

## 如何在 Java 中保存 PDF 无批注？

使用 `Annotator` 加载源 PDF，配置 `SaveOptions` 以排除所有批注类型，然后调用 `save()` 写入干净的副本。此操作不会修改原始文件，因此您既保留供审阅者使用的带批注版本，又保留用于分发的原始版本。该过程在底层使用流式处理，这意味着整个文档永远不会完全驻留在内存中——对大 PDF 至关重要。

## 什么是保存 PDF 无批注？

`save pdf without annotations` 指的是导出 PDF 文档时去除所有批注对象（高亮、评论、印章、下划线等）。生成的文件仅包含原始内容和布局，适用于法律归档、公开发布或存档存储。

## 为什么在 java 文档审阅系统中创建干净的 PDF 文件？

干净的版本会消除审阅者的标记、评论和高亮，使您拥有一份面向客户、监管机构或公开发布的精致文档。它还能平均将文件大小降低约 30%，并防止内部备注意外泄露——这对法律和合规工作流至关重要。GroupDocs.Annotation 可以一次性移除所有批注对象，支持最高 500 MB 的 PDF 而无需将整个文件加载到内存中。

## 前置条件和环境设置

### 开始前的要求

**开发环境要求**  
- Java Development Kit (JDK) 8 或更高（推荐 JDK 11+）  
- Maven 3.6+ 或 Gradle 6.0+ 用于依赖管理  
- IDE 如 IntelliJ IDEA、Eclipse 或带 Java 扩展的 VS Code  
- 至少 2 GB 可用 RAM（文档处理可能占用大量内存）

**知识前提**  
您应该熟悉基本的 Java 概念——对象初始化、方法调用和 Maven 依赖。拥有第三方库的使用经验将加快上手速度。

**测试文档**  
准备几份示例 PDF。基于文本的 PDF 效果最佳；扫描的图像可能需要在批注前进行 OCR。

### Maven 设置：将 GroupDocs 引入项目

在您的 `pom.xml` 中添加以下依赖。此步骤常让许多开发者在首次尝试时卡住，因为 group ID 和 artifact ID 必须完全匹配。

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**重要**：Version 25.2 是撰写时的最新稳定版本。请定期检查 GroupDocs 仓库，以获取包含错误修复和性能改进的更新版本。

### 许可证设置（不要跳过）

**用于开发/测试** – 从 GroupDocs 网站下载免费试用版。试用版包含所有功能，但会在处理的文档上添加水印。

**用于生产** – 购买许可证并在应用启动时应用。没有有效许可证，生产构建将受到限制并带有水印。

## 实施指南：添加下划线批注

### 理解批注工作流

在深入代码之前，让我们了解在 **使用 Java 批注 PDF** 时发生的四步工作流：

1. **文档加载** – `Annotator` 将文件读取到内存中。  
2. **批注创建** – 定义位置、样式和评论等属性。  
3. **批注应用** – 库将批注注入 PDF 的结构中。  
4. **文档保存** – 持久化修改后的文件，可选择保留原始文件。

该过程是非破坏性的；除非您覆盖，否则源文件保持不变。

### 步骤 1：初始化 annotator 并加载文档

`Annotator` 是 GroupDocs.Annotation 中用于加载和修改 PDF 文档的主要入口点。它抽象了文件系统处理、流管理和本机资源分配。

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

**技巧提示：** 在开发时使用绝对路径以避免 “file not found” 错误。生产环境中，考虑从 classpath 或云存储桶加载资源。

### 步骤 2：创建评论和回复（协作部分）

`Comment` 对象表示附加在批注上的线程式讨论。每条评论可以包含作者、时间戳和可选的回复，从而实现围绕特定标记的完整对话。

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**实际使用：** 审阅者可以通过添加线程式回复来讨论特定条款，使对话与确切的批注关联。

### 步骤 3：定义批注坐标（确保位置准确）

`Point` 定义了 PDF 空间中的单个坐标（以点为单位，72 点 = 1 英寸）。下划线需要四个点：两个用于起始线，两个用于结束线。

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

**坐标系统：**  
- 点 1 和 2 定义下划线的上边缘。  
- 点 3 和 4 定义下边缘。  
- Y 方向的差值（730 对 650）控制粗细。

### 步骤 4：创建并配置下划线批注

`UnderlineAnnotation` 是表示下划线标记的具体类。它继承自基类 `Annotation`，并添加了下划线特有的属性，如线条粗细和样式。

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

**颜色与不透明度提示：**  
- `FontColor` 使用 ARGB；`65535`（0x00FFFF）产生亮黄色。  
- 红色使用 `16711680`（0xFF0000）；蓝色使用 `255`（0x0000FF）。  
- 不透明度值在 0.5 到 0.8 之间可提供良好的可读性而不遮挡文字。

### 步骤 5：保存已批注的文档

`SaveOptions` 让您控制输出格式、是否嵌入批注以及元数据的处理方式。设置 `AnnotationType.NONE` 可指示库去除所有批注对象，这是 **保存 PDF 无批注** 的关键。

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

**内存管理：** 调用 `dispose()` 释放本机资源并防止内存泄漏——在批量处理大量文件时至关重要。

## 移除批注：创建干净的文档版本

有时您需要一个 **不含任何批注** 的 PDF 版本——例如交付最终批准的合同时。GroupDocs 让这变得简单。

### 理解批注移除选项

您可以：  
- 移除 **所有** 批注（最常见）  
- 移除特定类型（例如仅高亮）  
- 按作者或页面移除批注  

### 步骤式批注移除

**步骤 1：加载先前已批注的文档**

`Annotator` 再次充当加载器；它将读取仍包含批注对象的文件。

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**步骤 2：配置保存选项以获得干净输出**

`SaveOptions` 提供流式 API，以指定不应将任何批注类型写入输出文件。

```java
Annotator annotator = new Annotator(outputPath);
```

**步骤 3：保存干净版本**

使用配置好的选项调用 `save()`，会写入仅包含原始内容的 PDF。

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

这将生成一个 **干净的 PDF** 文件，不含批注对象，适合最终分发。

## 常见问题及解决方案

### 问题 1：“未找到文档” 错误

确保文件路径正确且应用具有读取权限。使用带绝对路径的 `Path.of()` 可消除大多数歧义。

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### 问题 2：批注出现在错误位置

PDF 坐标原点位于左下角。确认您的 Y 值向上递增，并考虑页面旋转。

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

### 问题 3：大文档的内存问题

GroupDocs.Annotation 对内容进行流式处理，永不将整个文件加载到堆内存中。但仍需调用 `dispose()`，并在文件大于 200 MB 时考虑增加 JVM 堆 (`-Xmx`)。

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 问题 4：生产环境的许可证问题

如果许可证文件缺失或路径不正确，库会回退到试用模式，在每页添加水印。将许可证文件放置在 classpath 可访问的位置，并在应用生命周期早期加载它。

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## 生产应用的性能最佳实践

### 内存管理策略

GroupDocs.Annotation 以流式方式处理 PDF，这使其能够在不将整个文档加载到内存的情况下处理高达 500 MB 的文件。不过仍需遵循以下指南：

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

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### 线程考虑事项

GroupDocs.Annotation 默认 **不是线程安全** 的。如果您的应用并发处理文档：

- **绝不要** 在多个线程之间共享 `Annotator` 实例。  
- **同步** 文件访问或使用锁机制。  
- 如果需要高吞吐量，可考虑使用 `Annotator` 对象的 **池**。

### 缓存策略

- 缓存经常使用的批注模板。  
- 对常用坐标集合复用 `Point` 集合。  
- 如果反复在同一基础文档上批注，保持一个 **模板 PDF** 在内存中。

## Java PDF 内存管理最佳实践

在处理大 PDF 或批量处理大量文件时，高效的内存使用至关重要。以下是一些实用建议：

- 对每个 `Annotator` 使用 **try‑with‑resources**，以确保释放。  
- 仅在需要时 **增加 JVM 堆** (`-Xmx`)；使用分析工具监控使用情况。  
- 尽可能 **顺序处理文档**，在每个文件后释放内存。  
- **避免多次加载相同的 PDF**；如果需要重复读取，请复用同一流。

应用这些实践有助于保持应用响应，并防止在大量批注工作负载下出现内存不足崩溃。

## 实际应用和使用案例

### 文档审阅系统

- **法律审查：** 下划线合同条款并添加风险评论。  
- **合规审计：** 高亮财务报表中的问题章节。  
- **学术同行评审：** 教授下划线需要澄清的段落。

### 教育平台

- **学生批注工具：** 让学习者在电子书中下划线关键概念。  
- **教师反馈：** 在提交的作业上直接提供内联评论。

### 质量保证工作流

- **技术文档审查：** 工程师下划线需要更新的章节。  
- **标准操作程序：** 安全员高亮关键步骤。

### 内容管理系统

- **编辑工作流：** 编辑下划线需要事实核查的文本。  
- **版本控制：** 跟踪文档修订中的批注历史。

## 专业实现的高级技巧

### 自定义批注样式

您可以通过设置自定义虚线模式、线帽和不透明度级别来扩展下划线的视觉外观。这在需要区分审阅者角色（例如法律与工程）时非常有用。

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

### 用于跟踪的批注元数据

每个批注都可以携带用户定义的元数据字典。存储 ID、时间戳或工作流状态，以便与外部跟踪系统集成。

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### 与用户管理系统集成

将 `Comment` 的 `author` 属性映射到您应用的用户 ID。这实现了基于角色的样式和审计轨迹生成。

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## 生产问题排查

### 性能监控

在生产环境中关注以下指标：  
- **堆使用情况** – 确保调用 `dispose()`。  
- **每个文档的处理时间** – 在 `annotator.save()` 前后记录时间戳。  
- **错误率** – 捕获异常并进行分类。

### 常见生产陷阱

- **文件锁定** – 确保在批注前关闭已上传的文件。  
- **并发编辑** – 实现乐观锁或版本检查。  
- **大文件（> 50 MB）** – 增加 JVM 超时并考虑使用流式 API。

### 错误处理最佳实践

将所有批注调用包装在 try‑catch 块中，记录完整堆栈跟踪，并抛出带有用户友好信息的自定义 `AnnotationException`。此模式简化调试并为 API 使用者提供清晰反馈。

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

## 常见问题

**Q: 如何在一次操作中批注多个文本区域？**  
A: 创建多个具有不同坐标的 `UnderlineAnnotation` 对象，并使用 `annotator.add()` 按顺序添加它们。

**Q: 我可以在 PDF 文档中的图像上批注吗？**  
A: 可以。使用相同的坐标系统，确保点位于图像边界内。

**Q: 除了 PDF，GroupDocs.Annotation 支持哪些文件格式？**  
A: Word（DOC/DOCX）、Excel（XLS/XLSX）、PowerPoint（PPT/PPTX）以及 JPEG、PNG、TIFF 等图像格式。

**Q: 如何处理超大文档而不耗尽内存？**  
A: 一次处理一个文档，增加 JVM 堆 (`-Xmx`)，并始终及时释放 `Annotator` 实例。

**Q: 能否从文档中提取已有的批注？**  
A: 可以。使用 `annotator.get()` 检索所有批注，然后根据需要按类型、作者或页面进行过滤。

---

**最后更新：** 2026-10-16  
**测试环境：** GroupDocs.Annotation 25.2  
**作者：** GroupDocs  

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

## 相关教程

- [使用 GroupDocs 创建干净的 PDF（Java）：下划线批注](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [编辑 PDF 批注（Java）- 完整的 GroupDocs 教程](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [使用 GroupDocs Annotation 为 PDF 添加批注（Java）](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)