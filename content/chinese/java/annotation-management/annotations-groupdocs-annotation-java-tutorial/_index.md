---
date: '2025-12-17'
description: 了解如何使用 GroupDocs.Annotation for Java 保存带注释的 PDF 文件。本教程涵盖 Maven 依赖 GroupDocs、初始化
  Annotator Java、添加多个注释以及 Java 注释最佳实践。
keywords:
- GroupDocs.Annotation for Java
- Java document annotation
- Annotator initialization
title: 完整指南：如何使用 GroupDocs.Annotation for Java 保存带注释的 PDF
type: docs
url: /zh/java/annotation-management/annotations-groupdocs-annotation-java-tutorial/
weight: 1
---

# 使用 GroupDocs.Annotation for Java 保存带注释的 PDF

通过为 Java 应用程序添加文档注释功能，可以有效提升协作、合规性和用户体验。在本指南中，您将学习使用 GroupDocs.Annotation for Java **保存带注释的 PDF** 文件的方法，包括设置 Maven 依赖、添加多个注释以及遵循 Java 注释最佳实践。让我们逐步演示，以便您能够自信地将此功能集成到项目中。

## 快速答案
- **GroupDocs.Annotation 的主要目的是什么？**  
  在 Java 应用程序中以编程方式创建、编辑并 **保存带注释的 PDF** 文档。  
- **我需要哪个 Maven 构件？**  
  `com.groupdocs:groupdocs-annotation`（请参阅 *maven dependency groupdocs* 部分）。  
- **我可以一次添加多个注释吗？**  
  可以——您可以在一次操作中 **添加多个注释**。  
- **如何初始化标注器？**  
  使用教程中展示的 **initialize annotator java** 模式。  
- **关键的最佳实践提示是什么？**  
  请遵循 *annotation best practices java* 检查表，以进行内存管理和性能优化。

## 什么是“保存带注释的 PDF”？
保存带注释的 PDF 是指将所有可视化标记——高亮、评论、形状以及其他标注——持久化到 PDF 文件中，使任何打开文档的人都能看到这些更改。GroupDocs.Annotation 提供了一个简易的 API，以编程方式完成此任务。

## 为什么使用 GroupDocs.Annotation for Java？
- **跨平台支持** – 可在任何运行 Java 的操作系统上使用。  
- **丰富的注释类型** – 从简单的高亮到椭圆等复杂形状。  
- **无需外部 PDF 编辑器** – 所有操作均在您的 Java 代码中完成。  
- **企业级可扩展** – 适用于法律、教育和技术文档工作流。

## 前置条件
- **Java SDK**（JDK 8 或更高）已在您的机器上安装。  
- **Maven** 用于依赖管理。  
- IDE，例如 **IntelliJ IDEA** 或 **Eclipse**。  
- 基本的 Java 编程知识。  

### Maven 依赖 GroupDocs
将 GroupDocs 仓库和注释库添加到您的 `pom.xml`：

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

## 获取许可证
1. **免费试用：** 下载试用版以测试 GroupDocs.Annotation。  
2. **临时许可证：** 获取临时许可证，以在评估期间获得完整访问权限。  
3. **购买：** 获取正式许可证用于生产环境。

## 初始化 Annotator Java
第一步是使用您要处理的文档 **initialize annotator java**。以下是基本的初始化模式：

```java
import com.groupdocs.annotation.Annotator;

public class Feature1 {
    public void loadAnnotator(String fileName) {
        try (final Annotator annotator = new Annotator(fileName)) {
            // Ready to use!
        }
    }
}
```

### 功能 1：加载并初始化 Annotator
此功能演示了使用文档文件路径初始化 Annotator，为您的 Java 应用程序设置注释任务。

```java
import com.groupdocs.annotation.Annotator;

public class Feature1 {
    public void loadAnnotator(String fileName) {
        try (final Annotator annotator = new Annotator(fileName)) {
            // Annotator initialized and ready.
        }
    }
}
```

## 创建注释

### 功能 2：创建区域注释
区域注释允许您高亮矩形区域。请按照以下步骤创建：

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;

public class Feature2 {
    public AreaAnnotation createAreaAnnotation() {
        AreaAnnotation area = new AreaAnnotation();
```
```java
        area.setBox(new Rectangle(100, 100, 100, 100));
```
```java
        area.setBackgroundColor(65535);
```
```java
        area.setPageNumber(1);

        return area;
    }
}
```

### 功能 3：创建椭圆注释
椭圆注释非常适合圆形或椭圆形的高亮。

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.EllipseAnnotation;

public class Feature3 {
    public EllipseAnnotation createEllipseAnnotation() {
        EllipseAnnotation ellipse = new EllipseAnnotation();
```
```java
        ellipse.setBox(new Rectangle(100, 100, 100, 100));
```
```java
        ellipse.setBackgroundColor(123456);
```
```java
        ellipse.setPageNumber(2);

        return ellipse;
    }
}
```

## 添加多个注释
您可以在一次调用中 **添加多个注释**，这可以提升性能并保持代码整洁。

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

## 保存文档 – 如何保存带注释的 PDF
现在注释已完成，您将 **保存带注释的 PDF**，仅包含所需的注释类型。

```java
public class Feature5 {
    public String getOutputPath(String fileName) {
        return "YOUR_OUTPUT_DIRECTORY" + "/filtered_output.pdf";
```
```java
    public void saveAnnotatedDocument(Annotator annotator, String outputPath) {
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setAnnotationTypes(AnnotationType.ELLIPSE);

        annotator.save(outputPath, saveOptions);
    }
}
```

## 注释最佳实践 Java
- **使用 try‑with‑resources** 自动关闭 `Annotator` 并释放内存。  
- **批量添加注释**（如 Feature 4 所示）以减少 I/O 开销。  
- **在 `SaveOptions` 中仅指定所需的注释类型**，以保持文件大小较小。  
- **保存后从内存中释放大型文档**，以避免内存泄漏。  

## 实际应用
- **法律文档审查：** 高亮条款并为律师添加评论。  
- **教育资源：** 为学习小组标注教科书。  
- **技术手册：** 在工程图纸上添加注释和警告。  

## 性能考虑因素
- 限制在超大 PDF 上的并发注释。  
- 使用推荐的 **annotation best practices java** 来高效管理内存。  
- 如果发现性能下降，请使用 Java Flight Recorder 对应用进行分析。  

## 常见问题及解决方案

| 问题 | 解决方案 |
|------|----------|
| **OutOfMemoryError** 在加载大型 PDF 时 | 以流式模式加载文档或增大 JVM 堆大小。 |
| 保存后注释未显示 | 确保 `SaveOptions` 包含正确的 `AnnotationType`。 |
| 许可证错误 | 验证试用或永久许可证文件是否被正确引用。 |

## 常见问答

**问：我可以在形状之外添加文本评论吗？**  
答：可以，GroupDocs.Annotation 支持 `TextAnnotation` 和 `CommentAnnotation` 类型——只需实例化相应的模型并将其添加到列表中。

**问：是否可以编辑已有的注释？**  
答：当然可以。通过注释 ID 获取注释，修改其属性，然后调用 `annotator.update(updatedAnnotation)`。

**问：如何删除不再需要的注释？**  
答：使用 `annotator.delete(annotationId)` 删除特定注释，或使用 `annotator.clear(pageNumber)` 清除页面上的所有注释。

**问：该库是否支持受密码保护的 PDF？**  
答：支持。在构造 `Annotator` 实例时提供密码，例如 `new Annotator(filePath, password)`。

**问：需要哪个版本的 Java？**  
答：该库兼容 Java 8 及以上版本；我们建议使用最新的 LTS 版本以获得最佳性能。

## 结论
现在，您已经拥有使用 GroupDocs.Annotation for Java **保存带注释的 PDF** 文件的完整端到端解决方案。通过遵循上述步骤——设置 Maven 依赖、初始化标注器、创建并添加多个注释以及应用注释最佳实践，您可以为任何 Java 应用程序注入强大的文档标记功能。

---

**最后更新：** 2025-12-17  
**测试环境：** GroupDocs.Annotation 25.2  
**作者：** GroupDocs