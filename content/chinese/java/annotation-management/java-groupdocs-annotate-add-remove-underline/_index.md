---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation 在 Java 文档中添加和移除下划线注释。这份详细的指南将帮助您提升文档管理能力。"
"title": "使用 GroupDocs 在 Java 中添加和删除下划线注释的综合指南"
"url": "/zh/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# 如何实现 Java：使用 GroupDocs 添加和删除下划线注释

## 介绍

想要通过编程方式添加或删除注释来增强您的文档管理系统吗？本教程将指导您使用 Java 中强大的 GroupDocs.Annotation 库在 PDF 等文档中添加和删除下划线注释。

**您将学到什么：**
- 初始化注释器类。
- 使用 GroupDocs.Annotation for Java 添加带有注释的下划线注释。
- 从文档中删除所有注释。
- 配置您的环境以有效地使用 GroupDocs.Annotation。

让我们探索如何在您的项目中利用这些功能。开始之前，请确保您已满足必要的先决条件。

## 先决条件

### 所需的库和依赖项
为了有效地遵循本教程，请确保您已：
- **Java 版 GroupDocs.Annotation**：建议使用 25.2 或更高版本。
- **Java 开发工具包 (JDK)**：需要版本 8 或更高版本。

### 环境设置要求
确保您的开发环境包含 IntelliJ IDEA 或 Eclipse 等 IDE 和 Maven 等构建工具。

### 知识前提
对 Java 编程的基本了解，尤其是通过 Maven 使用库，将会很有帮助。

## 为 Java 设置 GroupDocs.Annotation

要开始在 Java 项目中使用 GroupDocs.Annotation，请按照以下设置步骤操作：

**Maven配置：**
将以下配置添加到您的 `pom.xml` 文件下载并集成 GroupDocs.Annotation。

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

**许可证获取：**
首先，请下载 GroupDocs 的免费试用版或获取临时许可证，以探索其库的全部功能。如需用于生产用途，则需要购买许可证。

## 实施指南

### 功能1：初始化注释器并添加下划线注释

本节将指导您初始化 `Annotator` 类并向您的文档添加下划线注释。

#### 概述
添加注释有助于突出显示文档的特定部分。在这里，我们重点关注带有注释的文本下划线，以便澄清或提供反馈。

#### 逐步实施

**1. 初始化注释器**
创建一个 `Annotator` 对象并加载您的 PDF 文件。

```java
import com.groupdocs.annotation.Annotator;

// 加载要注释的文档
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. 创建带有回复的评论**
定义与下划线注释相关的注释。

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

**3. 定义下划线注释点**
设置坐标以确定下划线出现的位置。

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

**4.创建并配置下划线注释**
创建下划线注释并设置其属性，如颜色、不透明度和注释。

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // ARGB 格式的黄色
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5.保存带注释的文档**
将更改保存到新文件。

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### 故障排除提示
- 确保所有点的坐标都在文档边界内。
- 验证 `outputPath` 目录存在并且可写。

### 功能 2：保存无注释的文档

本节介绍如何从先前注释的文档中删除所有注释。

#### 概述
您可能需要保存文档的干净版本（不带任何注释）以供共享或存档。

#### 逐步实施

**1. 使用带注释的文档初始化注释器**
加载具有现有注释的文档。

```java
Annotator annotator = new Annotator(outputPath);
```

**2. 配置保存选项以删除注释**
指定不应在输出文件中保存任何注释。

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. 保存不带注释的文档**
定义清理文档的路径并保存。

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## 实际应用

以下是这些功能可以发挥作用的一些实际场景：
1. **文件审查**：突出显示并评论合同或报告的某些部分以供审查。
2. **教育工具**：为学生在教科书上添加注释或更正。
3. **协作编辑**：在团队成员之间共享带注释的草稿以获得反馈。
4. **法律文件**：在讨论过程中划出法律文件中的关键条款。
5. **营销材料**：在分发小册子之前突出显示重要信息。

## 性能考虑
使用 GroupDocs.Annotation 时，请考虑以下技巧来优化性能：
- **内存管理**：妥善处置 `Annotator` 对象来释放资源。
- **批处理**：如果注释多个文档，请分批处理以有效管理系统负载。
- **资源分配**：确保您的环境具有足够的内存和处理能力来处理大文件。

## 结论
您已经学习了如何使用 GroupDocs.Annotation for Java 添加和移除下划线注释。本教程介绍了如何初始化 Annotator 类、如何配置带注释的注释以及如何保存不带注释的文档。 

为了进一步探索，请考虑将这些功能集成到您现有的文档管理系统中，或尝试 GroupDocs 提供的其他注释类型。

## 常见问题解答部分
1. **如何在一次运行中配置多个下划线注释？**
   - 创建多个 `UnderlineAnnotation` 对象并使用 `annotator.add()` 方法。
2. **我可以使用此库注释 PDF 中的图像吗？**
   - 是的，GroupDocs.Annotation 支持在 PDF 等文档中注释图像。
3. **GroupDocs.Annotation 支持哪些文件格式？**
   - 它支持各种文档格式，包括 PDF、Word、Excel 等。