---
categories:
- Java Development
date: '2025-12-21'
description: GroupDocs.Annotation を使用して、クリーンな PDF Java ファイルの作成方法と Java で PDF に注釈を付ける方法を、完全なコード例とトラブルシューティングのヒントとともに学びましょう。
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'クリーンなPDFをJavaで作成: GroupDocsで下線アノテーション'
type: docs
url: /ja/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Clean PDF Java を作成する: GroupDocs で下線アノテーション

## Introduction

Java アプリケーションでのドキュメント管理やコラボレーションに苦労していますか？ あなたは一人ではありません。多くの開発者が、さまざまなファイル形式で確実に動作する堅牢なドキュメントアノテーション機能の実装に課題を抱えています。

このガイドでは **clean PDF Java** ファイルを作成し、GroupDocs.Annotation を使用して **annotate PDF in Java** する方法を学びます。チュートリアルの最後までに、コメント付きの下線アノテーションの追加方法、既存のアノテーションの削除方法、そしてこれらの機能をプロジェクトにシームレスに統合する方法が正確に分かります。

**このガイドで習得できること:**
- Java プロジェクトに GroupDocs.Annotation を正しく設定する方法  
- カスタムコメントとスタイリングを持つ下線アノテーションの追加  
- すべてのアノテーションを削除してクリーンなドキュメントバージョンを作成する方法  
- 開発者が直面しやすい一般的な問題のトラブルシューティング  
- 本番環境向けのパフォーマンス最適化  

ドキュメントレビューシステム、教育プラットフォーム、共同編集ツールのいずれを構築していても、実践的で検証済みのコード例がこのチュートリアルで網羅されています。

## Quick Answers
- **How do I add an underline annotation?** Use `UnderlineAnnotation` and `annotator.add()` then save the document.  
- **How can I create a clean PDF Java file?** Load the annotated file, set `AnnotationType.NONE` in `SaveOptions`, and save a new copy.  
- **What libraries are required?** GroupDocs.Annotation v25.2 (or newer) and its Maven repository.  
- **Do I need a license for production?** Yes—apply a valid GroupDocs license to avoid watermarks.  
- **Can I process multiple documents efficiently?** Wrap each `Annotator` in a try‑with‑resources block and dispose after each file.

## How to create clean PDF Java files
Creating a clean PDF Java file means generating a version of the document **without any annotations** while preserving the original content. This is useful for final distribution, archival, or when you need to share a “clean” copy after a review cycle.

GroupDocs.Annotation makes this straightforward: load the annotated file, configure `SaveOptions` to exclude all annotation types, and save the result. The steps are illustrated later in the **Removing Annotations** section.

## How to annotate PDF in Java using GroupDocs
GroupDocs.Annotation provides a rich API for **annotate PDF in Java**. It supports a wide range of annotation types, including highlights, stamps, and underlines. In this tutorial we focus on underline annotations because they are commonly used for emphasizing text while allowing threaded comments.

## Prerequisites and Environment Setup

### What You'll Need Before Starting

**Development Environment Requirements:**
- Java Development Kit (JDK) 8 or higher (JDK 11+ recommended)  
- Maven 3.6+ or Gradle 6.0+ for dependency management  
- IDE such as IntelliJ IDEA, Eclipse, or VS Code with Java extensions  
- At least 2 GB of available RAM (document processing can be memory‑intensive)

**Knowledge Prerequisites:**
You should be comfortable with basic Java concepts—object initialization, method calls, and Maven dependencies. Prior experience with third‑party libraries will speed up adoption.

**Testing Documents:**
Have a few sample PDFs ready. Text‑based PDFs work best; scanned images may require OCR before annotation.

### Maven Setup: Getting GroupDocs Into Your Project

Here's how to properly configure your Maven project (this trips up many developers on their first attempt):

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

**Important:** Version 25.2 is the latest stable release at the time of writing. Check the GroupDocs repository regularly for newer versions that include bug fixes and performance improvements.

### Licensing Setup (Don't Skip This)

**For Development/Testing:**  
Download the free trial from the GroupDocs website. The trial includes all features but adds a watermark to processed documents.

**For Production:**  
Purchase a license and apply it during application startup. Without a valid license, production builds will be limited.

## Implementation Guide: Adding Underline Annotations

### Understanding the Annotation Workflow

Before we dive into code, let’s walk through the four‑step workflow that occurs when you **annotate PDF in Java**:

1. **Document Loading** – `Annotator` reads the file into memory.  
2. **Annotation Creation** – Define properties such as position, style, and comments.  
3. **Annotation Application** – The library injects the annotation into the PDF’s structure.  
4. **Document Saving** – Persist the modified file, optionally preserving the original.

The process is non‑destructive; the source file remains untouched unless you overwrite it.

### Step 1: Initialize the Annotator and Load Your Document

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Pro Tip:** Use absolute paths while developing to avoid “file not found” errors. In production, consider loading resources from the classpath or a cloud storage bucket.

### Step 2: Creating Comments and Replies (The Collaborative Part)

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

**Real‑World Use:** Reviewers can discuss a specific clause by adding threaded replies, keeping the conversation tied to the exact annotation.

### Step 3: Defining Annotation Coordinates (Getting the Position Right)

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

**Coordinate System:**  
- Points 1 & 2 define the top edge of the underline.  
- Points 3 & 4 define the bottom edge.  
- The Y‑difference (730 vs 650) controls thickness.

### Step 4: Creating and Configuring the Underline Annotation

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

**Color & Opacity Tips:**  
- `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow.  
- For red, use `16711680` (0xFF0000); for blue, `255` (0x0000FF).  
- Opacity values between 0.5 and 0.8 provide good readability without obscuring the text.

### Step 5: Saving Your Annotated Document

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management:** The `dispose()` call releases native resources and prevents memory leaks—critical when processing many files in a batch.

## Removing Annotations: Creating Clean Document Versions

Sometimes you need a version of the PDF **without any annotations**—for example, when delivering the final approved contract. GroupDocs makes this easy.

### Understanding Annotation Removal Options

You can:
- Remove **all** annotations (most common)  
- Remove specific types (e.g., only highlights)  
- Remove annotations by author or page  

### Step‑by‑Step Annotation Removal

**Step 1: Load the Previously Annotated Document**

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 2: Configure Save Options for a Clean Output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Step 3: Save the Clean Version**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

This produces a **clean PDF Java** file that contains no annotation objects, perfect for final distribution.

## Common Issues and Solutions

### Problem 1: “Document not found” Errors

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

### Problem 2: Annotations Appearing in Wrong Locations

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 3: Memory Issues with Large Documents

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problem 4: Licensing Issues in Production

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

## Performance Best Practices for Production Applications

### Memory Management Strategies

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

### Threading Considerations

GroupDocs.Annotation is **not thread‑safe** by default. If your application processes documents concurrently:

- **Never share** an `Annotator` instance across threads.  
- **Synchronize** file access or use a lock mechanism.  
- Consider a **pool** of `Annotator` objects if you need high throughput.

### Caching Strategies

- Cache frequently used annotation templates.  
- Reuse `Point` collections for common coordinate sets.  
- Keep a **template PDF** in memory if you repeatedly annotate the same base document.

## Real‑World Applications and Use Cases

### Document Review Systems

- **Legal Review:** Underline contract clauses and add comments about risk.  
- **Compliance Audits:** Highlight problematic sections in financial statements.  
- **Academic Peer Review:** Professors underline passages needing clarification.

### Educational Platforms

- **Student Annotation Tools:** Let learners underline key concepts in e‑books.  
- **Teacher Feedback:** Provide inline comments directly on submitted assignments.

### Quality Assurance Workflows

- **Technical Documentation Review:** Engineers underline sections that need updates.  
- **Standard Operating Procedures:** Safety officers highlight critical steps.

### Content Management Systems

- **Editorial Workflow:** Editors underline text that requires fact‑checking.  
- **Version Control:** Track annotation history across document revisions.

## Advanced Tips for Professional Implementation

### Custom Annotation Styles

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Annotation Metadata for Tracking

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integration with User Management Systems

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

## Troubleshooting Production Issues

### Performance Monitoring

Watch these metrics in production:
- **Heap usage** – ensure `dispose()` is called.  
- **Processing time per document** – log timestamps before/after `annotator.save()`.  
- **Error rate** – capture exceptions and categorize them.

### Common Production Gotchas

- **File locking** – ensure uploaded files are closed before annotation.  
- **Concurrent edits** – implement optimistic locking or version checks.  
- **Large files (> 50 MB)** – increase JVM timeout and consider streaming APIs.

### Error Handling Best Practices

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

## Conclusion

You now have everything needed to **create clean PDF Java** files and **annotate PDF in Java** with underline annotations using GroupDocs.Annotation. Remember to:

- Manage resources with try‑with‑resources or explicit `dispose()`.  
- Validate coordinates early to avoid misplaced underlines.  
- Implement robust error handling for production stability.  
- Leverage role‑based styling and metadata to fit your workflow.

Next steps? Try adding other annotation types—highlights, stamps, or text replacements—to build a full‑featured document review solution.

## Frequently Asked Questions

**Q: How do I annotate multiple areas of text in a single operation?**  
A: Create several `UnderlineAnnotation` objects with different coordinates and add them sequentially using `annotator.add()`.

**Q: Can I annotate images within PDF documents?**  
A: Yes. Use the same coordinate system, ensuring the points lie inside the image bounds.

**Q: What file formats besides PDF does GroupDocs.Annotation support?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats such as JPEG, PNG, TIFF.

**Q: How do I handle very large documents without running out of memory?**  
A: Process documents one at a time, increase the JVM heap (`-Xmx`), and always dispose of `Annotator` instances promptly.

**Q: Is it possible to extract existing annotations from a document?**  
A: Yes. Use `annotator.get()` to retrieve all annotations, then filter by type, author, or page as needed.

---

**Last Updated:** 2025-12-21  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs