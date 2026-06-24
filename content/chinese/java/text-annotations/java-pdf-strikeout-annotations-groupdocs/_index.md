---
categories:
- Java PDF Processing
date: '2026-05-21'
description: 了解如何在 Java 中使用 GroupDocs 为 PDFs 添加 strikeout annotations。本 step‑by‑step
  教程覆盖 setup、code、troubleshooting 和 performance tips。
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF 文本 Strikeout 指南
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
title: 如何在 Java 中为 PDFs 添加 strikeout annotations – 完整的 GroupDocs 指南
type: docs
url: /zh/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# 如何在 Java 中为 PDF 添加删除线注释

是否曾经需要在 PDF 中以编程方式划掉文本？无论是构建文档审阅系统、创建编辑工作流，还是仅仅需要标记待删除的文本，**如何添加删除线** 注释都是一项实用技能，可节省时间并减少手动工作。在本全面指南中，您将了解使用 GroupDocs.Annotation for Java 实现删除线注释所需的全部内容，从项目设置到性能调优。

## 快速答案
- **第一步是什么？** 将 GroupDocs.Annotation Maven 依赖添加到您的 `pom.xml`。  
- **如何创建删除线？** 实例化 `Annotator`，使用点定义 `StrikeoutAnnotation`，设置颜色/不透明度，然后调用 `addAnnotation`。  
- **我可以添加评论吗？** 可以，将 `Comment` 对象附加到注释以实现协作。  
- **如果注释位置错误怎么办？** 调整坐标点；PDF 使用左下角为原点的坐标系。  
- **文档大小有上限吗？** GroupDocs 可以处理数百页的 PDF，而无需将整个文件加载到内存中。

## 什么是 PDF 注释中的 “如何添加删除线”？
短语 “如何添加删除线” 指的是使用注释 API 在 PDF 文档中以编程方式在选定文本上绘制横线的过程。在 Java 中，GroupDocs.Annotation 提供了专用的 `StrikeoutAnnotation` 类，用于处理删除线的渲染、样式和持久化。

## 为什么在 Java PDF 删除线中使用 GroupDocs？
GroupDocs.Annotation 支持 **50 多种输入和输出格式**——包括 PDF、DOCX、XLSX、PPTX、HTML 以及常见的图像类型——因此您不必局限于单一文件类型。它提供了高级 API，抽象了底层 PDF 结构，自动处理字体嵌入、页面渲染和注释持久化，使开发者能够专注于业务逻辑，而非 PDF 的内部细节。

## 前置条件和设置要求

### 必要条件
- **Java Development Kit (JDK)：** 8 版或更高（推荐使用 JDK 11+ 以获得最佳垃圾回收）。  
- **GroupDocs.Annotation for Java：** 通过 Maven 集成（见下方 Maven 代码片段）。  
- **IDE：** IntelliJ IDEA、Eclipse 或任何兼容 Java 的编辑器。

### Maven 依赖设置
将以下依赖块添加到您的 `pom.xml`：

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

**技巧提示：** 请始终在 GroupDocs 发布页面上确认最新版本；新版本会添加功能并修复可能影响注释渲染的错误。

### 获取许可证
GroupDocs.Annotation 需要有效许可证才能用于生产。您有三种选择：

- **免费试用：** 从 [GroupDocs 下载](https://releases.groupdocs.com/annotation/java/) 下载  
- **临时许可证：** 在 [GroupDocs 临时许可证](https://purchase.groupdocs.com/temporary-license/) 请求开发密钥  
- **正式许可证：** 在 [GroupDocs 购买页面](https://purchase.groupdocs.com/buy) 购买用于生产的许可证  

试用版会添加淡淡的水印，请相应地安排测试。

## 步骤实现指南

### 理解核心组件
以下定义帮助您快速建立概念模型：

- **Annotator：** 加载 PDF 并提供注释方法的主要 API 对象。  
- **StrikeoutAnnotation：** 表示可视的删除线及其样式选项。  
- **Point：** 坐标对 (X, Y)，告诉库线条的起始和结束位置。  
- **Comment：** 可选的附加到注释上的文本，用于协作。

### 步骤 1：设置文件路径
定义源 PDF 和目标文件的位置。路径错误是导致 “File Not Found” 错误的常见原因。

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**常见错误提示：** 确保输出目录存在且可写；GroupDocs 不会自动创建缺失的文件夹。

### 步骤 2：初始化 Annotator
创建一个 `Annotator` 实例，将 PDF 加载到内存中。

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**这里发生了什么？** 库解析 PDF 结构，构建内部表示，并准备逐页的注释画布。对于数百页的文件，此步骤可能需要几秒钟。

### 步骤 3：添加评论（可选但推荐）
`Comment` 是一个类，表示附加到注释上的文本备注，允许协作者解释删除线的原因。

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**实际技巧：** 使用评论解释为何删除文本——这在法律或编辑审阅工作流中尤为有用。

### 步骤 4：定义注释坐标
`Point` 对象存储 X‑Y 坐标对，定义注释在 PDF 页面上的精确位置。

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**坐标系说明：** PDF 坐标以左下角 (0,0) 为起点。示例在目标页上创建了一条从 (80,730) 到 (240,730) 的水平线。

**寻找正确坐标：** 许多开发者会编写辅助函数，将页面宽高的百分比转换为绝对点数，使代码能够适应不同页面尺寸。

### 步骤 5：创建删除线注释
`StrikeoutAnnotation` 封装了可视线条、颜色和不透明度等样式属性，以及用于删除线标记的任何关联元数据。

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

**颜色值：** `fontColor` 使用十进制 RGB 值（例如，亮黄色为 65535）。如果需要品牌特定的色调，可使用在线转换器。

**不透明度建议：** `0.7`（70 %）的不透明度提供清晰的视觉提示，同时保持底层文本可读。

### 步骤 6：应用注释
`addAnnotation` 是 `Annotator` 的方法，用于将准备好的注释注册到文档中，以便渲染并保存。

```java
annotator.add(strikeout);
```

### 步骤 7：保存并清理
`dispose()` 可释放 `Annotator` 实例持有的本地资源，防止处理完成后出现内存泄漏。

```java
annotator.save(outputPath);
annotator.dispose();
```

**内存管理提示：** 调用 `dispose()` 可释放本地资源，防止在批量处理 PDF 时出现内存泄漏。

## 常见问题及解决方法

### 问题 1：“File Not Found” 错误
**症状：** 在 `Annotator` 构造期间抛出异常。  
**解决方案：** 验证输入输出路径，并确认应用具有读写权限。

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### 问题 2：删除线出现在错误位置
**症状：** 线条未与预期文本对齐。  
**解决方案：** 记住 PDF 的 Y 坐标向上递增。使用可视化调试工具或打印页面尺寸以微调坐标点。

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### 问题 3：注释不可见
**症状：** 保存后未出现删除线。  
**可能原因与解决办法：**
- **不透明度太低：** 暂时将不透明度设为 `1.0` 以验证可见性。  
- **颜色混合：** 使用高对比度颜色，如红色 (`255`)。  
- **页面索引错误：** 页面编号从零开始；确保定位到正确的页面。

### 问题 4：大文件的内存问题
**症状：** `OutOfMemoryError` 或性能迟缓。  
**解决方案：**  
- 将文档分批处理。  
- 如有可用，使用流式 API。  
- 始终在每个文档处理后调用 `dispose()`。

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## 实际应用场景和用例

### 法律文档审阅
律师事务所在合同中使用删除线标注已删除的条款，同时保留审计轨迹。

### 学术论文编辑
教授在同行评审期间使用删除线建议删除内容，同时保留原始文本以提供上下文。

### 内容管理系统
出版平台在人工审核前会自动使用删除线标记违反政策的段落。

### 文档版本控制
企业在以文档为中心的版本控制工作流中，将删除线注释视为 “删除标记”，类似于代码差异。

## 性能优化技巧

### 批量处理策略
处理大量 PDF 时，尽可能复用单个 `Annotator` 实例，并在并行线程中处理文件。

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### 内存管理最佳实践
- 对每个 `Annotator` 调用 `dispose()`。  
- 限制并发文档加载数量，以避免堆内存压力。  
- 使用 VisualVM 等工具监控 JVM 内存使用情况。

### 坐标缓存
如果在多个文件中使用相同的注释布局，缓存 `Point` 对象以避免重新计算。

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## 高级自定义选项

### 动态颜色选择
根据业务规则在运行时选择颜色（例如，关键删除使用红色，暂定删除使用黄色）。

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

### 多行删除线
创建一系列 `Point` 对，以绘制穿过多行文本的锯齿线。

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## 故障排查清单
1. **文件权限：** 验证读写访问权限。  
2. **库版本：** 确保使用受支持的 GroupDocs.Annotation 版本。  
3. **许可证状态：** 确认许可证文件已正确引用。  
4. **PDF 兼容性：** 检查 PDF 是否未损坏且在支持的大小范围内。  
5. **坐标验证：** 确保所有点位于页面边界内。  
6. **堆空间：** 如处理超大文件，请增加 JVM `-Xmx` 参数。

## 常见问答

**问：我可以跨多行添加删除线吗？**  
**答：** 可以。创建多个 `Point` 对象来描绘所需路径，注释会沿着提供的折线绘制。

**问：如果指定的坐标超出页面边界会怎样？**  
**答：** 注释会被裁剪，可能不可见。请始终根据页面宽高验证坐标。

**问：添加后我可以删除删除线注释吗？**  
**答：** 当然可以。使用 `removeAnnotation` 方法并提供注释的 ID，或按类型过滤来程序化删除。

**问：单个 PDF 能添加的注释数量有限制吗？**  
**答：** GroupDocs 没有硬性上限，但在成千上万的注释后性能可能下降。对于非常大的集合，考虑分页或汇总注释。

**问：如何处理受密码保护的 PDF？**  
**答：** 将密码传递给 `Annotator` 构造函数。库会在内存中解密文档后再应用注释。

**问：如何处理页面尺寸和方向不同的 PDF？**  
**答：** 通过 `annotator.getPageInfo(pageNumber)` 获取每页尺寸，并相对于这些尺寸计算坐标，以确保位置一致。

## 结论
现在，您已经拥有使用 GroupDocs.Annotation 在 Java 中为 PDF 添加 **删除线** 注释的完整、可投入生产的解决方案。通过掌握文件路径处理、坐标计算和资源管理，您可以将此功能嵌入文档审阅工具、内容流水线或任何需要精确视觉反馈的 Java 应用程序中。

**后续步骤**
1. 克隆示例项目并在示例 PDF 上运行。  
2. 尝试不同的颜色、不透明度和评论文本。  
3. 将注释工作流集成到现有的文档处理服务中。  
4. 探索相关的注释类型——高亮、便签和形状注释，以扩展您的 PDF 操作工具箱。

想了解更多？深入官方文档，获取更深入的 API 见解。

## 附加资源
- [GroupDocs 文档](https://docs.groupdocs.com/annotation/java/) - GroupDocs 库的一般文档  
- [GroupDocs.Annotation 文档](https://docs.groupdocs.com/annotation/java/) - 完整的 API 参考  
- [API 参考指南](https://reference.groupdocs.com/annotation/java/) - 方法逐一的详细说明  
- [下载最新版本](https://releases.groupdocs.com/annotation/java/) - 保持库为最新版本  
- [购买许可证](https://purchase.groupdocs.com/buy) - 生产就绪的许可证  
- [免费试用下载](https://releases.groupdocs.com/annotation/java/) - 购买前评估  
- [临时许可证请求](https://purchase.groupdocs.com/temporary-license/) - 开发测试  
- [支持论坛](https://forum.groupdocs.com/c/annotation/) - 社区帮助和官方支持  

**最后更新：** 2026-05-21  
**测试环境：** GroupDocs.Annotation 23.12 for Java  
**作者：** GroupDocs

## 相关教程
- [在 Java 中添加 PDF 注释 – 完整 GroupDocs 指南](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF 注释教程 - 完整的 PDF 高亮指南](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [如何在 Java 中为 PDF 添加箭头 – 完整 GroupDocs 教程](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)