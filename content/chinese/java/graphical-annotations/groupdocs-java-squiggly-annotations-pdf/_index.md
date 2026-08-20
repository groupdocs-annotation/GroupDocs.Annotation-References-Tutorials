---
categories:
- Java Development
date: '2026-05-16'
description: 了解如何使用 GroupDocs.Annotation 在 Java 中创建注释回复。通过实用示例、性能技巧和最佳实践，掌握 Java 中的
  PDF 注释。
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Java PDF Annotation 教程
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
title: Java PDF Annotation Library：创建注释回复 java
type: docs
url: /zh/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF 注释库：创建注释回复 java

如果您需要为 PDF **create annotation reply java**（创建注释回复 java）——无论是构建合同审查门户、电子学习系统，还是批量处理流水线——本指南将向您展示如何使用 GroupDocs.Annotation for Java 完成此操作。我们将逐步讲解设置、波浪线注释创建、回复线程以及性能调优，让您在几天而非几周内交付可靠的解决方案。

## 快速回答
- **GroupDocs.Annotation 的主要目的是什么？** 它能够在 Java 中以编程方式创建、修改和提取 PDF 注释。  
- **如何添加波浪线注释？** 实例化 `SquigglyAnnotation`，设置其几何形状和样式，然后调用 `annotator.add(...)`。  
- **我可以为注释附加回复吗？** 可以——创建 `Reply` 对象，设置作者和文本，并将其关联到父注释。  
- **生产环境需要许可证吗？** 绝对需要；没有有效许可证，输出的 PDF 将包含水印。  
- **它适合批量处理吗？** 适合——使用 try‑with‑resources 打开每个文档，进行注释后关闭，以保持低内存使用。

## 为什么 Java 开发者需要 PDF 注释库

手动在 PDF 上标记既耗时又容易出错，尤其是需要审阅数百份合同或试卷时。Java PDF 注释库可以自动化此工作，让您直接在文件中嵌入高亮、波浪线下划线和线程化评论。其结果是一个可搜索、可携带的文档，保留所有标记且无需额外的查看器。

**本指南您将掌握的内容**
- 在 Maven 项目中安装和授权 GroupDocs.Annotation  
- 构建类似原生 Word 下划线的波浪线注释  
- 为任意注释添加线程化回复，以实现协作审阅  
- 在处理大型 PDF 时优化内存和 CPU 使用  
- 在 Spring Boot、微服务或桌面应用中部署该解决方案  

无论您是在构建法律文档审查系统、教育评分工具，还是自动化质量控制流水线，以下技术都将为您提供可投入生产的基础。

## 什么是 create annotation reply java？

`create annotation reply java` 是使用 Java 将评论线程（Reply）附加到现有 PDF 注释的编程过程。回复允许多个审阅者在不离开文档的情况下讨论特定标记，实现无缝的现场协作。此功能将静态 PDF 转变为交互式讨论平台，直接在文件内保留上下文和审计轨迹。

## 前置条件：准备开发环境

在深入代码之前，请确认您的开发工作站满足以下规格：

- **JDK** 8 或更高（推荐使用 JDK 11 + 以获得更好的垃圾回收性能）  
- **Maven** 或 **Gradle** 用于依赖管理（示例使用 Maven）  
- 支持 Maven 的 IDE（IntelliJ IDEA、Eclipse 或 VS Code）  
- 至少 **2 GB** 空闲内存用于 IDE 和测试运行  
- 用于实验的示例 PDF 文件（您可以使用任何 PDF 编辑器生成简单的 PDF）  

GroupDocs.Annotation 完全在进程内运行；无需外部 PDF 查看器或本地库。

## 为 Java 设置 GroupDocs.Annotation

集成该库是一个几步的过程，但若遗漏某些隐藏的陷阱，可能导致运行时错误。

### Maven 依赖配置

将仓库和依赖添加到您的 `pom.xml` 中。将 `<repositories>` 元素 **放在** `<dependencies>` 之前，以确保 Maven 能解析该构件。

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

> **专业提示：** 检查 GroupDocs 发布页面以获取最新版本。新版本通常包括对新兴 PDF 标准的支持和性能改进。

### 许可证设置（不要跳过！）

GroupDocs.Annotation 在生产环境中需要许可证文件。没有它，生成的每个 PDF 都会带有水印。

1. **免费试用** – 完整功能 30 天，适合评估。  
2. **临时许可证** – 适用于开发和内部测试。  
3. **正式许可证** – 任何商业部署都需要。  

将 `GroupDocs.Annotation.lic` 文件放置在 resources 文件夹中，并在启动时加载：

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **常见陷阱：** 忘记许可证步骤会导致 PDF 带水印且 API 调用静默失败。始终在启动例程的早期验证许可证。

## 完整实现指南：添加波浪线注释

下面是一步步的演示，展示如何在构建波浪线注释的同时 **create annotation reply java**。每一步都包含简要说明，让您了解每行代码背后的“原因”。

### 步骤 1：导入所有必需的类

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` 是所有文档级操作的入口点。  
- `Point` 表示页面上的坐标（X 和 Y 从左上角测量）。  
- `SquigglyAnnotation` 定义用于突出错误的波浪下划线。  
- `Reply` 存储附加到注释的线程化评论。  
- `SaveOptions` 让您控制输出格式和压缩。

### 步骤 2：创建并配置波浪线注释

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

SquigglyAnnotation 是用于在 PDF 中创建波浪下划线以突出错误的类。

- **坐标系**：点从左上角开始。上面的两个点绘制了一条从 (100, 200) 到 (300, 200) 的水平波浪线。  
- **不透明度** 0.7 表示注释 70% 不透明，使底层文本仍可阅读。

### 步骤 3：添加交互式回复（可选但强大）

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

Reply 是表示附加到注释的评论线程的类。

- 回复在注释上直接创建 **线程化讨论**，类似现代 PDF 审阅者的体验。  
- 每条回复存储作者信息和时间戳，您可以随后在 UI 中过滤或显示。

### 步骤 4：应用注释并保存文档

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- **try‑with‑resources** 结构会自动关闭 `Annotator`，释放文件句柄和本地缓冲区。  
- `save` 将修改后的 PDF 写入 `output.pdf`。  

> **内存提示：** `Annotator` 只加载您操作的页面。对于数百页的 PDF，此方法可将堆内存使用保持在典型服务器的 150 MB 以下。

## 高级配置选项

### 自定义注释外观

您可以微调视觉样式以匹配品牌指南：

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **边框宽度** 控制线条粗细（单位：点）。  
- **ARGB** 格式包含用于透明度的 Alpha 通道。

### 精确定位注释

在页面尺寸各异的 PDF 上获取正确坐标可能很棘手。请遵循以下系统化方法：

1. **在查看器中打开 PDF**（例如 Adobe Acrobat），记录目标区域的标尺数值。  
2. **将标尺数值转换为点**（1 点 = 1/72 英寸）。  
3. **使用 `annotator.getPageInfo(pageIndex)`** 获取页面宽高，然后计算相对位置。

## 常见问题及解决方案

### 问题：注释未显示

**最可能的原因**
- 点位于页面边界之外  
- 未加载许可证（水印隐藏注释）  
- 页面编号错误（API 中页面从零开始计数）  

**解决方案检查清单**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### 问题：大型文件性能差

将 500 页的 PDF 加载到内存中可能导致服务卡顿。可通过以下方式缓解：

- **一次处理一页**——打开文档，对单页进行注释，保存后再处理下一页。  
- **流式处理**——使用 `Annotator` 的流式 API，避免完整文档缓冲。  
- **缓存**——将经常访问的 PDF 存入快速缓存（如 Redis），对缓存副本进行注释。

### 问题：颜色值无效

GroupDocs 期望 **ARGB**（Alpha、Red、Green、Blue）而非普通 RGB。ARGB 值 `0xFFFF0000` 表示完全不透明的红色。如果提供 `0xFF0000`，库会错误解释，导致注释呈现为黑色。

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## 性能最佳实践

### 内存管理

在批处理作业中为数十个 PDF 添加注释时，请为每个文件使用独立的 try‑with‑resources 块：

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- 此模式确保在每次迭代后释放本地缓冲区，防止长时间运行的进程出现 **OutOfMemoryError**。

### 批处理优化

对于高吞吐量环境，考虑将并行流与有界线程池结合使用：

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **有界池** 防止线程爆炸，而并行流保持 CPU 核心忙碌。

### 文件大小考虑因素

大型 PDF（> 100 MB）可能降低性能。采用以下策略：

- **预压缩** 源 PDF（使用 Ghostscript 等工具）后再进行注释。  
- **仅注释所需页面**——跳过不需要标记的页面。  
- **拆分** 文档为逻辑章节（如每章），独立处理每个块。

## 实际应用案例

### 文档审查系统

律师事务所经常需要标记有问题的条款。波浪线注释结合线程化回复，使多位律师能够在不离开 PDF 的情况下讨论同一段落：

- **律师 A** 在条款下添加红色波浪线并写下 “表述模糊”。  
- **律师 B** 回复 “为 ‘重大违约’ 添加定义”。  
- 整个讨论保持嵌入式、可搜索且可审计。

### 与现有系统集成

GroupDocs.Annotation 与流行的 Java 框架无缝配合：

- **Spring Boot** ——暴露 REST 端点 `/api/annotate`，接受 PDF 多部件上传，添加注释并流式返回结果。  
- **JSF** ——将注释操作绑定到 UI 组件，实现网页视图中的即时标记。  
- **微服务** ——库体积小（< 15 MB），可使用 Docker 容器化并水平扩展。

### 工作流自动化

将注释与其他 GroupDocs 产品（如 GroupDocs.Signature）结合，构建端到端流水线：

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## 何时使用波浪线注释 vs. 替代方案

| 用例 | 推荐注释 |
|----------|------------------------|
| 标记拼写或语法错误 | **Squiggly** – 类似文字处理器的视觉提示 |
| 高亮重要章节且不暗示错误 | **Highlight** – 半透明覆盖层 |
| 提供详细反馈 | **Text** 或 **Comment** – 自由形式的注释框 |
| 批准或拒绝文档 | **Stamp** – “Approved” 或 “Rejected” 标记 |

## 结论

您现在拥有使用 GroupDocs.Annotation 的完整、可投入生产的 **create annotation reply java** 配方。通过掌握 API、处理许可证并应用上述性能技巧，您可以：

- 自动在数千个 PDF 上进行错误标记  
- 在文件内部实现协作式线程讨论  
- 即使处理大型文档也保持低内存使用  

**后续步骤**
1. 试验其他注释类型（高亮、印章、文本）。  
2. 构建接收 PDF、进行注释并返回结果的 REST 服务。  
3. 探索提取 API (`annotator.get()`) 以获取现有评论用于分析。  

程序化 PDF 注释的强大之处在于它能够用可重复、可审计的代码取代繁琐的手动标记。无论您是在构建细分的法律科技产品，还是通用的文档工作流引擎，本指南中的技术都为您提供了坚实的基础。

## 常见问题

**问：GroupDocs.Annotation 相比其他 Java PDF 库有什么优势？**  
答：GroupDocs.Annotation 专注于注释工作流，提供超过 30 种注释类型、线程化回复，并原生支持 50 多种文件格式，同时在 500 页 PDF 上的内存占用保持在 200 MB 以下。

**问：我可以在 Spring Boot 应用中使用此库吗？**  
答：完全可以。创建一个 `@RestController`，注入 `Annotator` 服务，处理 multipart 上传，并将注释后的 PDF 流式返回给客户端。记得为并发请求配置线程池。

**问：如何处理页面尺寸不同的文档？**  
答：通过 `annotator.getPageInfo(pageIndex)` 查询每页的尺寸，然后计算相对坐标（例如百分比），而不是硬编码点值。这样可确保注释在 A4、Letter 和自定义尺寸页面上正确显示。

**问：有没有办法提取 PDF 中已有的注释？**  
答：有。调用 `annotator.get()` 获取所有注释的集合，然后遍历读取作者、评论和几何等属性。这在迁移或分析场景中很有用。

**问：在多用户系统中处理注释权限的最佳做法是什么？**  
答：在应用层实现身份验证，将用户 ID 与每个 `Reply` 一起存储，并强制业务规则（例如，仅作者或管理员可编辑或删除回复）。API 本身不强制权限控制，提供了完全的灵活性。

**问：处理数百个 PDF 时如何优化内存使用？**  
答：对每个文档使用 try‑with‑resources，逐页处理，并考虑使用有界线程池限制并发内存消耗。使用 VisualVM 等工具监控 JVM 堆，可帮助微调 `-Xmx` 设置。

---

**最后更新：** 2026-05-16  
**测试环境：** GroupDocs.Annotation 25.2 for Java  
**作者：** GroupDocs  

**附加资源**

- [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)
- [Complete API Reference](https://reference.groupdocs.com/annotation/java/)

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

## 相关教程

- [Java PDF 注释库教程](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [删除注释回复 Java - 使用 GroupDocs.Annotation 按 ID 管理回复](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [编辑 PDF 注释 Java - 完整的 GroupDocs 教程](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)