---
date: '2026-10-16'
description: Learn how to save PDF without annotations in Java, master java pdf memory
  management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
  guide.
images:
- /java/annotation-management/java-groupdocs-annotate-add-remove-underline/og-image.png
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Java Document Annotation with GroupDocs
og_description: Learn how to save PDF without annotations in Java, master java pdf
  memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
  guide.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: How to save PDF without annotations in Java using GroupDocs
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
title: How to save PDF without annotations in Java using GroupDocs
type: docs
url: /java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# How to save PDF without annotations in Java using GroupDocs

If you need to **save PDF without annotations** while still being able to add collaborative underline notes, you’re in the right place. Many Java developers struggle with keeping a clean version of a document for final distribution, especially when the same file is used for iterative reviews. In this tutorial you’ll learn how to generate a clean PDF, manage memory efficiently, and apply underline annotations with comments using GroupDocs.Annotation. By the end you’ll understand the complete workflow—from loading a PDF to producing a watermark‑free final copy—plus best‑practice tips for building a robust **java document review system**.

## Quick answers
- **How do I add an underline annotation?** Use `UnderlineAnnotation` with `annotator.add()` then save the document.  
- **How can I save PDF without annotations?** Load the annotated file, set `AnnotationType.NONE` in `SaveOptions`, and save a new copy.  
- **Which libraries are required?** GroupDocs.Annotation v25.2 (or newer) and its Maven repository.  
- **Do I need a license for production?** Yes—apply a valid GroupDocs license to avoid watermarks.  
- **Can I process multiple documents efficiently?** Wrap each `Annotator` in a try‑with‑resources block and dispose after each file.

## How do I save PDF without annotations in Java?

Load the source PDF with an `Annotator`, configure `SaveOptions` to exclude all annotation types, and call `save()` to write a clean copy. This operation does not modify the original file, so you retain both the annotated version for reviewers and a pristine version for distribution. The process uses streaming under the hood, meaning the entire document never fully resides in memory—crucial for large PDFs.

## What is save PDF without annotations?

`save pdf without annotations` refers to exporting a PDF document while stripping out every annotation object (highlights, comments, stamps, underlines, etc.). The resulting file contains only the original content and layout, making it suitable for legal filing, public release, or archival storage.

## Why create clean PDF files in a java document review system?

A clean version eliminates reviewer marks, comments, and highlights, giving you a polished document ready for clients, regulators, or public release. It also reduces file size by up to 30 % on average and prevents accidental disclosure of internal notes—critical for legal and compliance workflows. GroupDocs.Annotation can remove all annotation objects in a single pass, supporting PDFs up to 500 MB without loading the whole file into memory.

## Prerequisites and environment setup

### Requirements before starting

**Development environment requirements**  
- Java Development Kit (JDK) 8 or higher (JDK 11+ recommended)  
- Maven 3.6+ or Gradle 6.0+ for dependency management  
- IDE such as IntelliJ IDEA, Eclipse, or VS Code with Java extensions  
- At least 2 GB of available RAM (document processing can be memory‑intensive)

**Knowledge prerequisites**  
You should be comfortable with basic Java concepts—object initialization, method calls, and Maven dependencies. Prior experience with third‑party libraries will speed up adoption.

**Testing documents**  
Have a few sample PDFs ready. Text‑based PDFs work best; scanned images may require OCR before annotation.

### Maven setup: getting GroupDocs into your project

Add the following dependency to your `pom.xml`. This step trips up many developers on their first attempt because the group ID and artifact ID must match exactly.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Important:** Version 25.2 is the latest stable release at the time of writing. Check the GroupDocs repository regularly for newer versions that include bug fixes and performance improvements.

### Licensing setup (don’t skip this)

**For development/testing** – Download the free trial from the GroupDocs website. The trial includes all features but adds a watermark to processed documents.

**For production** – Purchase a license and apply it during application startup. Without a valid license, production builds will be limited and watermarked.

## Implementation guide: adding underline annotations

### Understanding the annotation workflow

Before we dive into code, let’s walk through the four‑step workflow that occurs when you **annotate PDF in Java**:

1. **Document loading** – `Annotator` reads the file into memory.  
2. **Annotation creation** – Define properties such as position, style, and comments.  
3. **Annotation application** – The library injects the annotation into the PDF’s structure.  
4. **Document saving** – Persist the modified file, optionally preserving the original.

The process is non‑destructive; the source file remains untouched unless you overwrite it.

### Step 1: initialize the annotator and load your document

`Annotator` is the main entry point in GroupDocs.Annotation for loading and modifying PDF documents. It abstracts file‑system handling, stream management, and native resource allocation.

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

**Pro tip:** Use absolute paths while developing to avoid “file not found” errors. In production, consider loading resources from the classpath or a cloud storage bucket.

### Step 2: creating comments and replies (the collaborative part)

`Comment` objects represent threaded discussion attached to an annotation. Each comment can have an author, a timestamp, and optional replies, enabling a full conversation around a specific markup.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Real‑world use:** Reviewers can discuss a specific clause by adding threaded replies, keeping the conversation tied to the exact annotation.

### Step 3: defining annotation coordinates (getting the position right)

`Point` defines a single coordinate in PDF space (measured in points, where 72 points = 1 inch). Four points are required for an underline: two for the start line and two for the end line.

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

**Coordinate system:**  
- Points 1 & 2 define the top edge of the underline.  
- Points 3 & 4 define the bottom edge.  
- The Y‑difference (730 vs 650) controls thickness.

### Step 4: creating and configuring the underline annotation

`UnderlineAnnotation` is the concrete class that represents an underline markup. It inherits from the base `Annotation` class and adds properties specific to underlines, such as line thickness and style.

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

**Color & opacity tips:**  
- `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow.  
- For red, use `16711680` (0xFF0000); for blue, `255` (0x0000FF).  
- Opacity values between 0.5 and 0.8 provide good readability without obscuring the text.

### Step 5: saving your annotated document

`SaveOptions` lets you control the output format, whether to embed annotations, and how to handle metadata. Setting `AnnotationType.NONE` instructs the library to strip all annotation objects, which is the key to **save PDF without annotations**.

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

**Memory management:** The `dispose()` call releases native resources and prevents memory leaks—critical when processing many files in a batch.

## Removing annotations: creating clean document versions

Sometimes you need a version of the PDF **without any annotations**—for example, when delivering the final approved contract. GroupDocs makes this easy.

### Understanding annotation removal options

You can:  
- Remove **all** annotations (most common)  
- Remove specific types (e.g., only highlights)  
- Remove annotations by author or page  

### Step‑by‑step annotation removal

**Step 1: load the previously annotated document**

`Annotator` again acts as the loader; it will read the file that still contains annotation objects.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Step 2: configure save options for a clean output**

`SaveOptions` provides a fluent API to specify that no annotation types should be written to the output file.

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 3: save the clean version**

Calling `save()` with the configured options writes a PDF that contains only the original content.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

This produces a **clean PDF** file that contains no annotation objects, perfect for final distribution.

## Common issues and solutions

### Problem 1: “Document not found” errors

Make sure the file path is correct and that the application has read permissions. Using `Path.of()` with absolute paths eliminates most ambiguities.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Problem 2: Annotations appearing in wrong locations

PDF coordinate origin is at the bottom‑left corner. Verify that your Y‑values increase upward and that you account for page rotation.

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

### Problem 3: Memory issues with large documents

GroupDocs.Annotation streams content and never loads the entire file into heap memory. However, you must still call `dispose()` and consider increasing the JVM heap (`-Xmx`) for files larger than 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 4: Licensing issues in production

If the license file is missing or the path is incorrect, the library falls back to trial mode, adding a watermark to every page. Place the license file in a location that is on the classpath and load it early in your application lifecycle.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Performance best practices for production applications

### Memory management strategies

GroupDocs.Annotation processes PDFs in a streaming fashion, which allows it to handle files up to 500 MB without loading the whole document into memory. Still, follow these guidelines:

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

### Threading considerations

GroupDocs.Annotation is **not thread‑safe** by default. If your application processes documents concurrently:

- **Never share** an `Annotator` instance across threads.  
- **Synchronize** file access or use a lock mechanism.  
- Consider a **pool** of `Annotator` objects if you need high throughput.

### Caching strategies

- Cache frequently used annotation templates.  
- Reuse `Point` collections for common coordinate sets.  
- Keep a **template PDF** in memory if you repeatedly annotate the same base document.

## Java PDF memory management best practices

Efficient memory use is essential when handling large PDFs or processing many files in a batch. Here are a few practical recommendations:

- **Use try‑with‑resources** for every `Annotator` to guarantee disposal.  
- **Increase the JVM heap** (`-Xmx`) only as needed; monitor usage with profiling tools.  
- **Process documents sequentially** when possible, freeing memory after each file.  
- **Avoid loading the same PDF multiple times**; reuse the same stream if you need to read it repeatedly.

Applying these practices helps keep your application responsive and prevents out‑of‑memory crashes during heavy annotation workloads.

## Real‑world applications and use cases

### Document review systems

- **Legal review:** Underline contract clauses and add comments about risk.  
- **Compliance audits:** Highlight problematic sections in financial statements.  
- **Academic peer review:** Professors underline passages needing clarification.

### Educational platforms

- **Student annotation tools:** Let learners underline key concepts in e‑books.  
- **Teacher feedback:** Provide inline comments directly on submitted assignments.

### Quality assurance workflows

- **Technical documentation review:** Engineers underline sections that need updates.  
- **Standard operating procedures:** Safety officers highlight critical steps.

### Content management systems

- **Editorial workflow:** Editors underline text that requires fact‑checking.  
- **Version control:** Track annotation history across document revisions.

## Advanced tips for professional implementation

### Custom annotation styles

You can extend the visual appearance of an underline by setting custom dash patterns, line caps, and opacity levels. This is useful when you need to differentiate reviewer roles (e.g., legal vs. engineering).

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

### Annotation metadata for tracking

Every annotation can carry a user‑defined metadata dictionary. Store IDs, timestamps, or workflow state to integrate with external tracking systems.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integration with user‑management systems

Map the `author` property of a `Comment` to your application's user IDs. This enables role‑based styling and audit‑trail generation.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Troubleshooting production issues

### Performance monitoring

Watch these metrics in production:  
- **Heap usage** – ensure `dispose()` is called.  
- **Processing time per document** – log timestamps before/after `annotator.save()`.  
- **Error rate** – capture exceptions and categorize them.

### Common production gotchas

- **File locking** – ensure uploaded files are closed before annotation.  
- **Concurrent edits** – implement optimistic locking or version checks.  
- **Large files (> 50 MB)** – increase JVM timeout and consider streaming APIs.

### Error handling best practices

Wrap all annotation calls in try‑catch blocks, log the full stack trace, and re‑throw a custom `AnnotationException` with a user‑friendly message. This pattern simplifies debugging and provides clear feedback to API consumers.

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

## Frequently asked questions

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

**Last Updated:** 2026-10-16  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs  

---

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

## Related Tutorials

- [Create Clean PDF Java: Underline Annotations with GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annotate Pdfs Groupdocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)