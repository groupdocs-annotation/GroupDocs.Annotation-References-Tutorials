---
categories:
- Java Development
date: '2026-03-30'
description: 学习如何使用 GroupDocs.Annotation 在 Java 中添加删除线批注。分步指南，附代码示例、故障排除技巧及文档标注最佳实践。
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: 使用 GroupDocs 的 Java 教程：添加删除线批注
type: docs
url: /zh/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# 添加删除线注释 Java - 完整的 GroupDocs 指南

有没有遇到过盯着文档想：“我需要划掉这段文字，但我不能随便拿支红笔”？你并不孤单。无论是构建文档审阅系统、创建编辑工作流，还是仅仅在 Java 应用中标记待删除的文本，**add strikeout annotation java** 都是一项必备技能。在本教程中，我们将逐步讲解实现文本删除线功能的所有必要知识，确保在生产环境中真正可用。

## 快速答案
- **什么库支持 Java 中的删除线注释？** GroupDocs.Annotation for Java  
- **我应该针对哪个主要关键词进行 SEO？** add strikeout annotation java  
- **运行示例代码是否需要许可证？** 免费试用或临时许可证可用于开发；生产环境需要完整许可证。  
- **我可以将其用于 PDF、DOCX 和 PPTX 文件吗？** 是的 – GroupDocs.Annotation 支持所有主流文档格式。  
- **需要哪个 Java 版本？** JDK 8 或更高（建议使用 JDK 11+）。

## 什么是 add strikeout annotation java？
删除线注释在选定文本上绘制一条线，直观地表明该内容应被删除或忽略。这是一种非破坏性的方式来建议删除，同时保留原始文本以供审计追踪或协作审阅。

## 为什么在 Java 应用中使用删除线注释？
- **文档审阅工作流** – 审阅者可以标记不需要的文本，而不更改源文件。  
- **协作编辑** – 团队成员可以即时看到建议的删除。  
- **法律与合规** – 保持清晰的变更审计轨迹。  
- **内容迁移** – 在系统之间迁移内容之前标记过时的部分。

## 先决条件和环境设置
在编写代码之前，您需要准备以下内容：

- **Java Development Kit (JDK)** 8+（建议使用 JDK 11+）  
- **Maven 或 Gradle** 用于依赖管理  
- **IDE** – IntelliJ IDEA、Eclipse 或带有 Java 扩展的 VS Code  
- **GroupDocs.Annotation 库** – 示例中使用 25.2 版本  

*建议具备：* 基本的 Java 注解和 PDF 处理知识。

## 为 Java 设置 GroupDocs.Annotation

### 实际可用的 Maven 配置
将仓库和依赖添加到您的 `pom.xml`，完全按照以下示例：

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

### 获取许可证
GroupDocs 提供多种授权选项：

- **免费试用** – 适合测试（无需信用卡）  
- **临时许可证** – 适用于开发和预发布环境  
- **完整许可证** – 生产使用必需；请参阅 [purchase page](https://purchase.groupdocs.com/buy)

> **专业提示：** 首先使用免费试用来探索 API，准备构建真实功能时再切换到临时许可证。

### 快速检查设置
运行以下最小程序以验证库是否正确加载：

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

如果控制台打印出成功信息且没有错误，您就可以开始添加删除线注释了。

## 如何添加删除线注释 java

以下是完整的、可用于生产的实现，分为清晰的步骤。

### 步骤 1 – 初始化 Annotator
创建指向源文档的 `Annotator` 实例：

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **原因说明：** 使用绝对路径或正确解析的相对路径可避免 “file not found” 异常。

### 步骤 2 – （可选）准备评论回复
添加回复可实现注释的协作：

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

当用户将鼠标悬停在删除线上时，会显示这些评论。

### 步骤 3 – 定义删除线区域
指定包围要划掉文本的矩形区域：

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **坐标提示：** 原点 (0,0) 位于页面左上角；X 向右增长，Y 向下增长。使用显示坐标的 PDF 查看器来微调这些数值。

### 步骤 4 – 配置删除线注释
设置外观、页码并附加评论：

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

*颜色说明：* `65535` 在整数 RGB 格式中对应黄色。更改该值可使用其他颜色。

### 步骤 5 – 应用注释并保存
将注释添加到文档并写入输出文件：

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### 步骤 6 – 清理资源（关键！）
始终释放 annotator 以释放本地资源：

```java
if (annotator != null) {
    annotator.dispose();
}
```

在生产环境中，将使用包装在 try‑with‑resources 块或 `try/finally` 结构中。

## 常见问题及解决方案
| 问题 | 症状 | 解决办法 |
|------|------|----------|
| **文件未找到** | `Annotator` 抛出异常 | 使用绝对路径，检查读取权限，确保没有其他进程锁定文件 |
| **坐标错误** | 删除线出现在预期文本之外 | 再次检查 PDF 查看器的坐标系统；相应调整点位 |
| **注释不可见** | 保存后没有可见的删除线 | 增加 `opacity`（例如 `0.9`），确认 `pageNumber`（从 0 开始），确保点位形成正确的矩形 |
| **OutOfMemoryError** | 在大 PDF 上应用崩溃 | 增加 JVM 堆内存 (`-Xmx2048m`)，批量处理文档，始终调用 `dispose()` |

## 生产环境的性能最佳实践

### 内存管理
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

### 批处理策略
当需要为数十或数百个文件添加注释时：

- 每批处理 10‑20 个文档。  
- 记录每个文件的成功/失败情况。  
- 为每个文档重新初始化 `Annotator`，以避免内存泄漏。  

### 缓存技巧
- 缓存经常使用的文档模板。  
- 为标准布局存储预先计算的坐标映射。  

## 真实场景用例

1. **文档审阅系统** – 编辑者在不更改原始合同的情况下建议删除。  
2. **法律修订** – 律师在保留原始措辞以供审计的同时跟踪条款删除。  
3. **学术同行评审** – 评审者标记待删除的章节并添加内联评论。  
4. **内容迁移** – 在 CMS 迁移期间，删除线突出显示需要替换的过时内容。  

## 高级自定义

### 自定义样式
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### 添加元数据
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## 故障排查清单
- ✅ 能手动打开源文件吗？  
- ✅ 类路径中是否存在所有 GroupDocs 依赖？  
- ✅ 点位是否形成有效的矩形？  
- ✅ 页码是否正确（从 0 开始）？  
- ✅ 堆内存是否足够？  
- ✅ 对输出文件夹是否有写入权限？  
- ✅ 文档格式是否受支持（PDF、DOCX、PPTX 等）？  

## 常见问题

**Q: 我可以在 Spring Boot 服务中使用 GroupDocs.Annotation 吗？**  
A: 可以。添加 Maven 依赖，注入创建 `Annotator` 的服务类，并使用 Spring 的 Bean 范围管理其生命周期。

**Q: 哪些文档格式支持删除线注释？**  
A: PDF、DOCX、PPTX 以及 GroupDocs.Annotation 支持的许多其他格式。PDF 提供最精确的坐标处理。

**Q: 如何处理页面尺寸各异的文档？**  
A: 通过 `annotator.getPageInfo(pageNumber)` 获取页面尺寸，并相应地缩放坐标。

**Q: 是否可以编辑或删除已有的删除线注释？**  
A: 完全可以。使用 `annotator.getAnnotations(pageNumber)` 获取，然后使用 `annotator.update(updatedAnnotation)` 或 `annotator.delete(annotationId)`。

**Q: 添加大量注释对性能有什么影响？**  
A: 添加数百个注释通常没有问题，但需监控内存使用。对于非常大的注释集合，考虑对视图进行分页或按需懒加载注释。

## 结论
您现在拥有使用 GroupDocs.Annotation 的完整、可用于生产的 **add strikeout annotation java** 指南。先从简单的检查示例开始，然后扩展到批处理、自定义样式和元数据丰富。请务必仔细测试坐标，负责任地管理资源，并为您的环境选择合适的授权模式。

准备好进一步探索了吗？查看其他注释类型——高亮、便签、图像、箭头和水印，以构建功能完整的文档协作套件。

---

**最后更新：** 2026-03-30  
**测试环境：** GroupDocs.Annotation 25.2 for Java  
**作者：** GroupDocs  

**其他资源**
- [GroupDocs 注释文档](https://docs.groupdocs.com/annotation/java/)
- [API 参考指南](https://reference.groupdocs.com/annotation/java/)
- [下载最新版本](https://releases.groupdocs.com/annotation/java/)
- [购买完整许可证](https://purchase.groupdocs.com/buy)
- [开始免费试用](https://releases.groupdocs.com/annotation/java/)
- [获取临时许可证](https://purchase.groupdocs.com/temporary-license/)
- [社区支持论坛](https://forum.groupdocs.com/c/annotation/)