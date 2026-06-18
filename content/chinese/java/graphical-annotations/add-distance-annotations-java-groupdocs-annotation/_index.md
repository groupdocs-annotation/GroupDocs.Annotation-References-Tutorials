---
categories:
- Java Development
date: '2026-06-16'
description: 了解如何在 Java 中使用 GroupDocs.Annotation 为图像及其他文档添加测量。完整教程包括代码示例、故障排除技巧和最佳实践。
keywords:
- how to add measurement
- distance annotation Java
- measure image Java
- GroupDocs annotation tutorial
- Java document measurement
lastmod: '2026-06-16'
linktitle: Java 距离注释指南
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
title: Java 距离注释教程：如何使用 GroupDocs 为图像添加测量
type: docs
url: /zh/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/
weight: 1
---

# Java 距离标注教程：如何使用 GroupDocs 为图像添加测量

在本综合指南中，您将了解如何使用 GroupDocs.Annotation for Java 为图像、PDF 和其他文档类型 **添加测量**。无论您是在构建 CAD 查看器、建筑审查工具，还是技术文档平台，距离标注都能为用户提供清晰、交互式的标尺。教程结束时，您将拥有一个可投入生产的解决方案，能够绘制精确测量、定制外观，并与现有的 Java 代码库平滑集成。

## 如何在 Java 中为图像添加测量？

使用 `Annotator` 加载目标文档，创建 `DistanceAnnotation`，配置其视觉属性，将其添加到指定页面，最后保存文件。仅用四行代码即可获得一个功能完整的标尺，终端用户可在任何兼容的查看器中编辑。此方法适用于 PDF、Word 文件、PowerPoint 幻灯片、Excel 表格以及常见图像格式，如 PNG、JPEG 和 TIFF。

## 快速答案
- **在 Java 中为图像添加测量的最简方法是什么？** 使用 GroupDocs.Annotation 的 `DistanceAnnotation` 类。  
- **支持哪些格式？** PDF、Word、PowerPoint、Excel，以及常见图像类型（PNG、JPEG、TIFF）。  
- **开发是否需要许可证？** 免费试用或临时许可证可用于测试；生产环境需商业许可证。  
- **我可以自定义标尺线的外观吗？** 可以——您可以设置颜色、样式、宽度和不透明度。  
- **如何避免内存泄漏？** 始终释放 `Annotator` 实例或使用 try‑with‑resources。

## 什么是距离标注（以及为什么需要它们）？

距离标注是交互式可视元素，显示文档中两点之间的测量长度。它们像数字标尺一样，可随意放置、拖动并实时编辑，为用户提供即时的可视化反馈，无需手动计算。

这些标注为任何技术文档带来 **可视化清晰度**、**交互式反馈** 和 **专业外观**。在建筑图纸、工程原理图、医学影像和房地产平面图等对精确尺寸要求高的场景中尤为有价值。

## 文档测量最佳实践

在编写代码之前，请牢记以下成熟实践：

1. **Zero‑based page indexing** – `pageNumber = 0` 表示第一页，符合 GroupDocs.Annotation 的内部模型。  
2. **High‑contrast colors** – 选择在文档背景上突出的标尺颜色（例如深色原理图上的亮黄色）。  
3. **Opacity tuning** – `0.7` 的不透明度在可见性和底层细节之间取得平衡；对关键测量可提升至 `1.0`。  
4. **Group related annotations** – 使用回复或评论将讨论围绕特定测量组织起来。  
5. **Dispose promptly** – 始终调用 `annotator.dispose()` 或使用 try‑with‑resources 释放本机内存，尤其在处理大文件时。

## 先决条件：开始之前您需要准备的内容

### 开发环境要求
- **Java Development Kit (JDK)**：版本 8 或更高（推荐 JDK 11+）。  
- **Maven 或 Gradle**：示例使用 Maven，Gradle 也可使用相同依赖。  
- **IDE**：任意 Java IDE（IntelliJ IDEA、Eclipse、VS Code 等）均可。

### 知识先决条件
您应已熟悉：
- 核心 Java 概念（类、对象、方法）。  
- 通过 Maven/Gradle 添加外部库。  
- 基本文件 I/O 与路径处理。

### 测试文档
准备一些示例文件：
- 一个或多个 PDF 页面。  
- 用于栅格测试的 PNG/JPEG/TIFF 图像。  
- 如需实验工程图纸，可选的 CAD 文件。

## 为 Java 设置 GroupDocs.Annotation

集成 GroupDocs.Annotation 非常简单。下面展示您需要在项目中添加的 Maven 坐标。

### Maven 集成

将以下配置添加到您的 `pom.xml` 文件中：

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

### 了解许可证要求

GroupDocs.Annotation 提供三种授权模式：

1. **Free Trial** – 适合评估，包含全部功能，仅有轻微使用限制。  
2. **Temporary License** – 去除试用限制，适用于开发和测试。  
3. **Commercial License** – 完全功能、生产就绪，无任何限制。

先使用免费试用，确认后再升级至商业许可证。

### 基本初始化

`Annotator` 类是所有标注操作的入口。它加载文档，提供编辑 API，并将结果写回磁盘。

```java
```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with the input file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

**专业提示：** 将 `Annotator` 包裹在 try‑with‑resources 块中或显式调用 `dispose()`，以避免本机内存泄漏。

## 分步实现指南

下面我们将完整演示一个生产就绪的工作流，向文档添加距离标注。

### 步骤 1：创建交互式回复（可选但推荐）

回复让协作者可以直接在测量上附加评论，将简单的标尺转化为讨论线程。

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

**何时使用回复：** 在多用户审阅周期中，需要解释为何选择某个尺寸或向团队成员请求澄清时使用。

### 步骤 2：配置距离标注

`DistanceAnnotation` 类是 GroupDocs.Annotation 中表示标尺测量的顶层对象。您可以自定义其几何形状、视觉样式以及附加信息。

`Rectangle` 定义标注在页面上的边界框。`PenStyle` 枚举线条样式，如实线、虚线和点线。

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

**关键配置选项**  
- `setBox()` – 设置标注在页面上的边界矩形。  
- `setOpacity()` – 控制透明度（`0.0` = 完全透明，`1.0` = 完全不透明）。  
- `setPenColor()` – 测量线的 RGB 颜色。  
- `setPenStyle()` – 线条样式（`DOT`、`DASH`、`SOLID`）。  
- `setPenWidth()` – 线条粗细（单位：点）。

### 步骤 3：应用标注并保存

标注准备好后，将其添加到文档并持久化更改。

```java
```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```
```

**重要提示：** 保存后务必调用 `dispose()`，尤其在批量处理大量文档时。

## 完整工作示例

将所有步骤组合在一起，下面是一个完整的端到端示例，加载 PDF、添加距离标注并保存结果。

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

运行代码片段，在任何支持标注的 PDF 查看器中打开输出文件，即可看到一个功能完整的标尺，可供交互使用。

## 常见用例和实际应用

了解距离标注的优势，有助于您决定在产品中如何嵌入它们。

### 技术文档和手册
- 在装配指南中突出显示组件尺寸。  
- 在安装手册中展示间隙区域。  
- 为质量控制检查清单提供快速参考测量。

### 建筑和工程项目
- 在平面图上显示房间大小。  
- 标注结构构件间距。  
- 标记公用线路距离和安全间隙。

### 医学和科学应用
- 在放射影像中测量解剖结构。  
- 为显微切片添加比例尺。  
- 在研究报告中记录标本尺寸。

### 房地产和物业管理
- 可视化地块边界和产权线。  
- 为房源列表展示房间尺寸。  
- 标明停车位大小和景观测量。

## 常见问题排查

即使示例写得再好，也可能遇到问题。以下列出最常见的故障及解决方案。

### 问题：“文件未找到”或路径问题
**症状：** 创建 `Annotator` 时抛出异常。  
**解决方案：** 开发阶段使用绝对路径，确认文件存在，并确保进程拥有读取权限。

```java
```java
// Better path handling
String inputPath = new File("documents/input.pdf").getAbsolutePath();
final Annotator annotator = new Annotator(inputPath);
```
```

### 问题：标注不可见
**症状：** 代码运行无错误，但未出现标尺。  
**常见原因：** 页面索引错误（记得页面从 0 开始）、标注放置在可视画布之外，或不透明度设置过低。

**快速修复：**

```java
```java
distance.setPageNumber(0); // First page
distance.setOpacity(1.0);  // Fully opaque
distance.setBox(new Rectangle(50, 50, 200, 30)); // Visible position
```
```

### 问题：大文档的内存问题
**症状：** 出现 `OutOfMemoryError` 或在数百页文件上性能下降。  
**解决方案：**  
- 完成后立即释放每个 `Annotator` 实例。  
- 采用顺序处理而非一次性加载多个文档。  
- 对于超大输入，增加 JVM 堆内存（如 `-Xmx4g` 或更高）。

```java
```java
// Good practice - use try-with-resources
try (Annotator annotator = new Annotator("large-document.pdf")) {
    // Your annotation code here
} // Automatic disposal
```
```

### 问题：许可证相关错误
**症状：** 出现试用限制或许可证验证失败的警告。  
**解决方案：**  
- 确认许可证文件路径正确且可读。  
- 确保许可证版本与所使用的 GroupDocs.Annotation 库版本匹配。  
- 检查临时许可证是否已过期。

## 性能优化技巧

从原型进入生产时，请关注以下性能要点。

### 内存管理最佳实践
- **Always dispose**：优先使用 try‑with‑resources 或显式 `dispose()`。  
- **Batch operations**：在单个 `Annotator` 会话中批量执行标注修改，以降低开销。  
- **Profiling**：使用 Java 分析工具（VisualVM、YourKit）监控本机内存使用情况。

### 文件处理优化
- **Cache frequently accessed documents**：只读时可将文档缓存在内存。  
- **Prefer PDF**：相较高分辨率图像，PDF 渲染更快，且文件体积通常小 30‑40 %。  
- **Adjust image resolution**：除非需要更高保真度，否则将源图像下采样至最高 150 DPI。

### 并发处理注意事项
如果服务需要并行处理大量文件，请遵循以下规则：

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

- 每个线程必须实例化自己的 `Annotator`。  
- 使用有界线程池，防止耗尽系统资源。  
- 在负载下监控 CPU 与堆内存使用情况，必要时水平扩展。

## 高级配置选项

掌握基础后，可探索以下高级功能，以进一步微调标注。

### 自定义样式选项

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

您可以定义自定义 `Pen` 对象、应用渐变填充，甚至在标尺线两端嵌入 SVG 标记。

### 动态定位

```java
```java
// Calculate position based based on document dimensions or content
Rectangle dynamicBox = calculateOptimalPosition(documentWidth, documentHeight);
distance.setBox(dynamicBox);
```
```

利用相对页面坐标，使标注在文档缩放或旋转时自动重新定位。

### 条件标注

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

仅在满足特定条件时创建距离标注（例如组件超出公差阈值时）。

## 与其他系统的集成

距离标注并非孤立存在，它们可以自然地融入更广泛的文档管理生态。

### 数据库集成

`AnnotationRecord` 是用于将标注元数据持久化到数据库的自定义数据模型。

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

将标注元数据（作者、时间戳、测量值）存入关系型数据库，以便报告和搜索。

### Web 应用集成

`DistanceAnnotationRequest` 是从客户端传递标注参数到服务器的 DTO。

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

提供 REST 端点，接受文件并根据 JSON 负载添加距离标注，返回标注后的文档。

### 云存储集成

```java
```java
// Download from cloud, process, upload result
byte[] documentBytes = cloudStorageService.download(documentPath);
// Process with GroupDocs.Annotation
byte[] annotatedDocument = processAnnotations(documentBytes);
cloudStorageService.upload(outputPath, annotatedDocument);
```
```

直接使用 AWS S3、Azure Blob Storage 或 Google Cloud Storage 的 SDK 读取/写入文件，然后将流传递给 `Annotator`。

## 常见问题

**Q: 哪些文档格式支持距离标注？**  
A: GroupDocs.Annotation 支持 PDF、Word 文档、PowerPoint 演示文稿、Excel 电子表格以及常见图像格式（PNG、JPEG、TIFF、BMP）。该功能在所有 50 多种受支持的格式上表现一致。

**Q: 我可以自定义测量线的外观吗？**  
A: 完全可以！您可以自由控制笔颜色、线条样式（实线、点线、虚线）、线宽和不透明度。还可以为特定工程标准定义自定义端帽符号。

**Q: 如何处理不同单位的测量？**  
A: 标注本身显示您在 `message` 属性中设置的文本。请在将值赋给 `message` 前，在 Java 代码中完成单位换算（例如英寸 ↔ 毫米）。

**Q: 添加标注后用户还能交互吗？**  
A: 可以。在兼容的查看器（GroupDocs.Viewer、Adobe Acrobat 或自定义网页查看器）中，用户可以点击、拖动并编辑标尺。回复和评论会保持附着在测量上，便于协作审阅。

**Q: 添加大量标注对性能有何影响？**  
A: 每个文档添加数百个标注对 CPU 影响微乎其微（< 5 %），对性能几乎没有影响。超过 1,000 个标注时，加载时间可能略有增加，但库仍保持稳定和响应迅速。

## 结论与后续步骤

现在，您已经掌握了使用 GroupDocs.Annotation 在 Java 中 **为图像和其他文档添加测量** 的完整、可投入生产的路线图。通过距离标注，您可以将静态图纸转化为交互式、数据丰富的资产，从而提升协作效率、降低错误率。

**关键要点**  
- 距离标注在 50 多种文件格式上提供精确、可视化的测量。  
- 实现简洁：加载、配置、添加、保存。  
- 对中等规模文档性能稳健；对大文件请遵循内存管理建议。  
- 数据库、REST、云等集成点让标注可嵌入任何工作流。

### 推荐的后续步骤
1. **Prototype**：克隆完整示例，在自己的 PDF 或图像上运行，确认标尺如预期出现。  
2. **Explore other annotation types**：高亮、文本和印章标注可与距离测量相辅相成。  
3. **Build a UI**：设计拖拽界面，让终端用户直接在浏览器或桌面客户端中放置标尺。  
4. **Plan for scale**：若预期有成千上万并发用户，实施线程池策略并按性能章节所述监控堆内存使用情况。

---

**Last Updated:** 2026-06-16  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**Related Resources:**  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Comprehensive API documentation  
- [API Reference](https://reference.groupdocs.com/annotation/java/) - Detailed method and class references  
- [Download Page](https://releases.groupdocs.com/annotation/java/) - Latest versions and release notes  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Community support and discussions  
- [Purchase Options](https://purchase.groupdocs.com/buy) - Commercial licensing information  
- [Free Trial](https://releases.groupdocs.com/annotation/java/) - Try before you buy  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/) - Extended evaluation license

## 相关教程

- [How to add arrow to pdf with Java – Complete Tutorial & Best Practices](/annotation/java/graphical-annotations/add-arrow-annotations-java-groupdocs/)  
- [Java PDF Image Annotation - Complete GroupDocs Tutorial](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)  
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)