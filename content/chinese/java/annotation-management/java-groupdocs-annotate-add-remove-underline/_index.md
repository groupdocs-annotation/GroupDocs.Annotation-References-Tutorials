---
categories:
- Java Development
date: '2026-03-24'
description: 学习如何使用 GroupDocs.Annotation 在 Java 中创建干净的 PDF 文件、管理 Java PDF 内存以及对 PDF
  进行注释，提供完整的代码示例和故障排除技巧。
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 使用 GroupDocs 在 Java 中创建干净的 PDF：下划线批注
type: docs
url: /zh/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# 创建干净的 PDF Java：使用 GroupDocs 的下划线批注

如果您需要 **create clean PDF Java** 文件并添加协作批注，您来对地方了。 在 Java 应用程序中为文档管理和协作而苦恼吗？您并不孤单。许多开发者都面临实现可靠的文档批注功能的挑战，这些功能需要在不同文件格式下都能正常工作。

在本指南中，您将 **create clean PDF Java** 文件，并学习如何使用 GroupDocs.Annotation **annotate PDF in Java**。 完成本教程后，您将准确掌握如何添加带有评论的下划线批注、删除已有批注，并将这些功能无缝集成到您的项目中。

**本指南您将掌握的内容：**
- 在 Java 项目中正确设置 GroupDocs.Annotation（正确的方式）  
- 添加带有自定义评论和样式的下划线批注  
- 删除所有批注以创建干净的文档版本  
- 排查开发者常见问题  
- 为生产环境优化性能  

无论您是在构建文档审阅系统、教育平台，还是协作编辑工具，本教程都提供了实用且经过验证的代码示例。

## 快速答案
- **如何添加下划线批注？** 使用 `UnderlineAnnotation` 并调用 `annotator.add()`，随后保存文档。  
- **如何创建 clean PDF Java 文件？** 加载已批注的文件，在 `SaveOptions` 中设置 `AnnotationType.NONE`，然后保存为新副本。  
- **需要哪些库？** GroupDocs.Annotation v25.2（或更高）及其 Maven 仓库。  
- **生产环境是否需要许可证？** 是的——请应用有效的 GroupDocs 许可证以避免水印。  
- **能高效处理多个文档吗？** 将每个 `Annotator` 放在 try‑with‑resources 块中使用，使用后释放资源。

## 如何创建 clean PDF Java 文件
创建 clean PDF Java 文件意味着生成一个 **不包含任何批注** 的文档版本，同时保留原始内容。这在最终分发、归档或在审阅周期后需要共享“干净”副本时非常有用。

GroupDocs.Annotation 让这一步变得简单：加载已批注的文件，配置 `SaveOptions` 以排除所有批注类型，然后保存结果。具体步骤将在后面的 **删除批注** 部分演示。

## 为什么要创建 clean PDF Java 文件？
干净的版本会去除审阅者的标记、评论和高亮，使文档更加精致，适合交付给客户、监管机构或公开发布。它还能减小文件体积，防止内部备注意外泄露——这在法律和合规工作流中至关重要。

## 如何使用 GroupDocs 在 Java 中批注 PDF
GroupDocs.Annotation 为 **annotate PDF in Java** 提供了丰富的 API。它支持多种批注类型，包括高亮、印章和下划线。本教程聚焦于下划线批注，因为它常用于强调文本并支持线程化评论。

## 前置条件和环境搭建

### 开始前您需要准备的内容

**开发环境要求：**
- Java Development Kit (JDK) 8 或更高（推荐 JDK 11+）  
- Maven 3.6+ 或 Gradle 6.0+ 用于依赖管理  
- IntelliJ IDEA、Eclipse 或带有 Java 扩展的 VS Code 等 IDE  
- 至少 2 GB 可用内存（文档处理可能占用大量内存）

**知识前置条件：**
您应熟悉基本的 Java 概念——对象初始化、方法调用以及 Maven 依赖。拥有第三方库使用经验会加快上手速度。

**测试文档：**
准备几份示例 PDF。基于文本的 PDF 效果最佳；扫描的图像可能需要先进行 OCR 才能批注。

### Maven 设置：将 GroupDocs 引入项目

下面展示了正确配置 Maven 项目的方式（许多开发者第一次尝试时会踩坑）：

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

**重要提示：** 版本 25.2 是撰写本文时的最新稳定版。请定期检查 GroupDocs 仓库，以获取包含 bug 修复和性能改进的更新版本。

### 许可证设置（不可跳过）

**开发/测试阶段：**  
从 GroupDocs 官网下载免费试用版。试用版包含全部功能，但会在处理后的文档上添加水印。

**生产环境：**  
购买许可证并在应用启动时进行应用。没有有效许可证，生产构建将受到限制。

## 实现指南：添加下划线批注

### 理解批注工作流

在深入代码之前，让我们先了解在 **annotate PDF in Java** 时发生的四步工作流：

1. **文档加载** – `Annotator` 将文件读取到内存。  
2. **批注创建** – 定义位置、样式和评论等属性。  
3. **批注应用** – 库将批注注入 PDF 结构。  
4. **文档保存** – 持久化修改后的文件，可选择保留原始文件。

该过程是非破坏性的，除非您主动覆盖，否则源文件保持不变。

### 步骤 1：初始化 Annotator 并加载文档

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**小贴士：** 开发阶段使用绝对路径可避免 “文件未找到” 错误。生产环境建议从类路径或云存储桶加载资源。

### 步骤 2：创建评论和回复（协作部分）

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

**真实场景：** 审阅者可以通过添加线程化回复来讨论特定条款，保持对话与对应批注绑定。

### 步骤 3：定义批注坐标（确保位置准确）

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

**坐标系统说明：**  
- 点 1 和 2 定义下划线的上边缘。  
- 点 3 和 4 定义下划线的下边缘。  
- Y 方向的差值（730 vs 650）控制线条粗细。

### 步骤 4：创建并配置下划线批注

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

**颜色与透明度技巧：**  
- `FontColor` 使用 ARGB；`65535`（0x00FFFF）呈现亮黄色。  
- 红色使用 `16711680`（0xFF0000）；蓝色使用 `255`（0x0000FF）。  
- 透明度在 0.5 到 0.8 之间可在不遮挡文字的前提下提供良好可读性。

### 步骤 5：保存已批注的文档

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**内存管理：** `dispose()` 调用会释放本地资源，防止内存泄漏——在批量处理大量文件时尤为关键。

## 删除批注：创建干净的文档版本

有时您需要一个 **不含任何批注** 的 PDF 版本，例如交付最终批准的合同。GroupDocs 提供了简便的实现方式。

### 理解批注删除选项

您可以：
- 删除 **所有** 批注（最常用）  
- 删除特定类型的批注（例如仅删除高亮）  
- 按作者或页面删除批注  

### 步骤式批注删除

**步骤 1：加载已批注的文档**

```java
Annotator annotator = new Annotator(outputPath);
```

**步骤 2：为干净输出配置保存选项**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**步骤 3：保存干净版本**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

这样即可生成一个 **clean PDF Java** 文件，内部不包含任何批注对象，适合最终分发。

## 常见问题及解决方案

### 问题 1：“未找到文档” 错误

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

### 问题 2：批注出现在错误位置

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 问题 3：大文档的内存问题

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### 问题 4：生产环境的授权问题

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

## 生产应用的性能最佳实践

### 内存管理策略

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

### 线程考虑

GroupDocs.Annotation 默认 **非线程安全**。如果您的应用并发处理文档：

- **绝不要**在多个线程之间共享 `Annotator` 实例。  
- **同步**文件访问或使用锁机制。  
- 如需高吞吐量，可考虑维护一个 `Annotator` 对象池。

### 缓存策略

- 缓存常用的批注模板。  
- 对常用坐标集合复用 `Point` 集合。  
- 若频繁对同一基准文档进行批注，可将 **模板 PDF** 常驻内存。

## Java PDF 内存管理技巧
在处理大型 PDF 或批量处理时，高效的内存使用至关重要。以下是一些实用建议：

- 对每个 `Annotator` 使用 try‑with‑resources，确保及时释放。  
- 仅在必要时增加 JVM 堆大小（`-Xmx`），并使用分析工具监控使用情况。  
- 如可能，顺序处理文档，在每个文件处理完后释放内存。  
- 避免多次加载同一 PDF；若需重复读取，可复用同一流。

遵循这些做法可保持应用响应迅速，防止在高负载批注工作时出现内存溢出。

## 实际应用场景与案例

### 文档审阅系统

- **法律审阅：** 下划线合同条款并添加风险评论。  
- **合规审计：** 高亮财务报表中的问题段落。  
- **学术同行评审：** 教授下划线需要澄清的段落。

### 教育平台

- **学生批注工具：** 让学习者在电子书中下划线关键概念。  
- **教师反馈：** 直接在提交的作业上提供行内评论。

### 质量保证工作流

- **技术文档审阅：** 工程师下划线需要更新的章节。  
- **标准操作程序：** 安全员突出关键步骤。

### 内容管理系统

- **编辑工作流：** 编辑下划线需事实核查的文本。  
- **版本控制：** 跨文档修订追踪批注历史。

## 专业实现的高级技巧

### 自定义批注样式

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### 用于追踪的批注元数据

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### 与用户管理系统集成

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

## 生产问题排查

### 性能监控

在生产环境关注以下指标：
- **堆内存使用** – 确保已调用 `dispose()`。  
- **每份文档的处理时间** – 在 `annotator.save()` 前后记录时间戳。  
- **错误率** – 捕获异常并进行分类。

### 常见生产陷阱

- **文件锁定** – 确保上传的文件在批注前已关闭。  
- **并发编辑** – 实现乐观锁或版本检查。  
- **大文件（> 50 MB）** – 增加 JVM 超时并考虑使用流式 API。

### 错误处理最佳实践

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

## 结论

现在，您已经掌握了使用 GroupDocs.Annotation **create clean PDF Java** 文件并 **annotate PDF in Java** 的下划线批注全部要点。请记住：

- 使用 try‑with‑resources 或显式 `dispose()` 管理资源。  
- 及早验证坐标，避免下划线位置错误。  
- 为生产环境实现健壮的错误处理。  
- 利用基于角色的样式和元数据来匹配您的工作流。

下一步？尝试添加其他批注类型——高亮、印章或文字替换，构建完整的文档审阅解决方案。

## 常见问答

**Q: 如何在一次操作中批注多个文本区域？**  
A: 创建多个 `UnderlineAnnotation` 对象，分别设置不同坐标，然后使用 `annotator.add()` 依次添加。

**Q: 能在 PDF 文档中的图像上进行批注吗？**  
A: 能。使用相同的坐标系统，确保点位落在图像边界内。

**Q: 除了 PDF，GroupDocs.Annotation 还支持哪些文件格式？**  
A: 支持 Word（DOC/DOCX）、Excel（XLS/XLSX）、PowerPoint（PPT/PPTX）以及 JPEG、PNG、TIFF 等图像格式。

**Q: 如何处理超大文档而不出现内存不足？**  
A: 一次只处理一份文档，必要时增大 JVM 堆（`-Xmx`），并及时 `dispose()` `Annotator` 实例。

**Q: 能提取文档中已有的批注吗？**  
A: 能。使用 `annotator.get()` 获取所有批注，然后可按类型、作者或页面进行过滤。

---

**最后更新：** 2026-03-24  
**测试环境：** GroupDocs.Annotation 25.2  
**作者：** GroupDocs