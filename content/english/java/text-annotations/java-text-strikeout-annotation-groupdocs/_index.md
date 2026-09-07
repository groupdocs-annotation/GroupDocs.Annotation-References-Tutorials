---
title: "Add Strikeout Annotation Java Tutorial with GroupDocs"
linktitle: "Add Strikeout Annotation Java Tutorial"
description: "Learn how to add strikeout annotation java using GroupDocs.Annotation. Step‑by‑step guide with code examples, troubleshooting tips, and best practices for document markup."
keywords: "Java strikeout annotation tutorial, GroupDocs annotation Java guide, text markup Java, document annotation Java, how to add strikeout annotation java"
date: "2026-03-30"
lastmod: "2026-03-30"
weight: 1
url: "/java/text-annotations/java-text-strikeout-annotation-groupdocs/"
categories: ["Java Development"]
tags: ["java-annotations", "groupdocs", "document-processing", "pdf-manipulation"]
type: docs
---
# Add Strikeout Annotation Java - Complete GroupDocs Guide

Ever found yourself staring at a document thinking, “I need to cross out this text, but I can’t just grab a red pen”? You’re not alone. Whether you’re building a document review system, creating an editing workflow, or just need to mark text for deletion in your Java application, **add strikeout annotation java** is an essential skill. In this tutorial we’ll walk through everything you need to know to implement text strikeout functionality that actually works in production.

## Quick Answers
- **What library supports strikeout annotations in Java?** GroupDocs.Annotation for Java  
- **Which primary keyword should I target for SEO?** add strikeout annotation java  
- **Do I need a license to run the sample code?** A free trial or temporary license works for development; a full license is required for production.  
- **Can I use this with PDF, DOCX, and PPTX files?** Yes – GroupDocs.Annotation supports all major document formats.  
- **What Java version is required?** JDK 8 or higher (JDK 11+ recommended).

## What is add strikeout annotation java?
A strikeout annotation draws a line through selected text, visually indicating that the content should be removed or ignored. It’s a non‑destructive way to suggest deletions while keeping the original text intact for audit trails or collaborative reviews.

## Why use strikeout annotations in Java applications?
- **Document review workflows** – reviewers can flag unwanted text without altering the source.  
- **Collaborative editing** – team members see suggested deletions instantly.  
- **Legal and compliance** – keep a clear audit trail of changes.  
- **Content migration** – mark obsolete sections before moving content between systems.  

## Prerequisites and Environment Setup
You’ll need the following before diving into code:

- **Java Development Kit (JDK)** 8+ (JDK 11+ recommended)  
- **Maven or Gradle** for dependency management  
- **IDE** – IntelliJ IDEA, Eclipse, or VS Code with Java extensions  
- **GroupDocs.Annotation library** – we’ll use version 25.2 in the examples  

*Nice to have:* basic knowledge of Java annotations and PDF handling.

## Setting Up GroupDocs.Annotation for Java

### Maven Configuration That Actually Works
Add the repository and dependency to your `pom.xml` exactly as shown:

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

### Getting Your License Sorted
GroupDocs offers several licensing options:

- **Free trial** – perfect for testing (no credit card required)  
- **Temporary license** – ideal for development and staging  
- **Full license** – required for production use; see the [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** Start with the free trial to explore the API, then switch to a temporary license when you’re ready to build a real‑world feature.

### Quick Sanity Check Setup
Run this minimal program to verify that the library loads correctly:

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

If the console prints the success message without errors, you’re ready to add strikeout annotations.

## How to add strikeout annotation java

Below is a complete, production‑ready implementation broken into clear steps.

### Step 1 – Initialize the Annotator
Create an `Annotator` instance that points to the source document:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Why this matters:** Using an absolute or correctly resolved relative path prevents “file not found” exceptions.

### Step 2 – (Optional) Prepare Comment Replies
Adding replies makes the annotation collaborative:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

These comments appear when a user hovers over the strikeout.

### Step 3 – Define the Strikeout Area
Specify the rectangle that encloses the text you want to cross out:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Coordinate tip:** Origin (0,0) is the top‑left corner of the page; X grows right, Y grows down. Use a PDF viewer that shows coordinates to fine‑tune these values.

### Step 4 – Configure the Strikeout Annotation
Set appearance, page number, and attach the comments:

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

*Color note:* `65535` corresponds to yellow in integer RGB format. Change the value to use other colors.

### Step 5 – Apply the Annotation and Save
Add the annotation to the document and write the output file:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Step 6 – Clean Up Resources (Critical!)
Always dispose of the annotator to free native resources:

```java
if (annotator != null) {
    annotator.dispose();
}
```

In production, wrap the usage in a try‑with‑resources block or a `try/finally` construct.

## Common Issues and How to Fix Them

| Problem | Symptom | Fix |
|---------|---------|-----|
| **File Not Found** | `Annotator` throws an exception | Use absolute paths, verify read permissions, ensure no other process locks the file |
| **Wrong Coordinates** | Strikeout appears away from the intended text | Double‑check the PDF viewer’s coordinate system; adjust points accordingly |
| **Annotation Invisible** | No visible strikeout after saving | Increase `opacity` (e.g., `0.9`), verify `pageNumber` (0‑based), ensure points form a proper rectangle |
| **OutOfMemoryError** | Application crashes on large PDFs | Increase JVM heap (`-Xmx2048m`), process documents in batches, always call `dispose()` |

## Performance Best Practices for Production

### Memory Management
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

### Batch Processing Strategy
When you need to annotate dozens or hundreds of files:

- Process 10‑20 documents per batch.  
- Log success/failure for each file.  
- Re‑initialize the `Annotator` for each document to avoid memory leaks.  

### Caching Tips
- Cache frequently used document templates.  
- Store pre‑calculated coordinate maps for standard layouts.  

## Real‑World Use Cases

1. **Document Review Systems** – Editors suggest deletions without altering the original contract.  
2. **Legal Amendments** – Lawyers track clause removals while preserving the original wording for audit.  
3. **Academic Peer Review** – Reviewers mark sections for removal and add inline comments.  
4. **Content Migration** – During CMS migrations, strikeouts highlight outdated copy that needs replacement.  

## Advanced Customization

### Custom Styling
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Adding Metadata
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Troubleshooting Checklist
- ✅ Can you open the source file manually?  
- ✅ Are all GroupDocs dependencies present in the classpath?  
- ✅ Do the points form a valid rectangle?  
- ✅ Is the page number correct (0‑based)?  
- ✅ Is there enough heap memory?  
- ✅ Do you have write permission for the output folder?  
- ✅ Is the document format supported (PDF, DOCX, PPTX, etc.)?  

## Frequently Asked Questions

**Q: Can I use GroupDocs.Annotation inside a Spring Boot service?**  
A: Yes. Add the Maven dependency, inject a service class that creates the `Annotator`, and manage its lifecycle with Spring’s bean scopes.

**Q: Which document formats support strikeout annotations?**  
A: PDF, DOCX, PPTX, and many other formats supported by GroupDocs.Annotation. PDF offers the most precise coordinate handling.

**Q: How do I handle documents with varying page sizes?**  
A: Retrieve the page dimensions via `annotator.getPageInfo(pageNumber)` and scale your coordinates accordingly.

**Q: Is it possible to edit or delete an existing strikeout annotation?**  
A: Absolutely. Use `annotator.getAnnotations(pageNumber)` to fetch, then `annotator.update(updatedAnnotation)` or `annotator.delete(annotationId)`.

**Q: What is the performance impact of adding many annotations?**  
A: Adding hundreds of annotations is generally fine, but monitor memory usage. For very large annotation sets, consider paginating the view or lazy‑loading annotations on demand.

## Conclusion
You now have a complete, production‑ready guide to **add strikeout annotation java** using GroupDocs.Annotation. Start with the simple sanity‑check example, then scale up to batch processing, custom styling, and metadata enrichment. Remember to test coordinates carefully, manage resources responsibly, and choose the right licensing model for your environment.

Ready to explore more? Check out other annotation types—highlight, note, image, arrow, and watermark—to build a full‑featured document collaboration suite.

---

**Last Updated:** 2026-03-30  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**Additional Resources**

- [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/java/)
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)
- [Purchase Full License](https://purchase.groupdocs.com/buy)
- [Start Free Trial](https://releases.groupdocs.com/annotation/java/)
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/)

---