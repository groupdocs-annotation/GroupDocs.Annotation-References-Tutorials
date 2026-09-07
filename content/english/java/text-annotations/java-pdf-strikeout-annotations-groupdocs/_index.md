---
title: "How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide"
linktitle: "Java PDF Text Strikeout Guide"
description: "Learn how to add strikeout annotations to PDFs in Java using GroupDocs. This step‑by‑step tutorial covers setup, code, troubleshooting, and performance tips."
keywords:
  - how to add strikeout
  - java pdf strikeout
  - groupdocs annotation java
weight: 1
url: "/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/"
date: "2026-05-21"
lastmod: "2026-05-21"
categories: ["Java PDF Processing"]
tags: ["java-pdf", "annotations", "groupdocs", "document-processing"]
type: docs
schemas:
- type: TechArticle
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  dateModified: '2026-05-21'
  author: GroupDocs
- type: HowTo
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
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
- type: FAQPage
  questions:
  - question: Can I strikeout text across multiple lines?
    answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
  - question: What happens if I specify coordinates outside the page boundaries?
    answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
  - question: Can I remove strikeout annotations after adding them?
    answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
  - question: Is there a limit to how many annotations I can add to a single PDF?
    answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
  - question: How do I work with password‑protected PDFs?
    answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
---

# How to Add Strikeout Annotations to PDFs in Java

Ever needed to cross out text in a PDF programmatically? Whether you're building a document review system, creating an editing workflow, or just need to mark text for deletion, **how to add strikeout** annotations in Java is a practical skill that saves time and reduces manual effort. In this comprehensive guide you’ll discover everything you need to know to implement strikeout annotations with GroupDocs.Annotation for Java, from project setup to performance tuning.

## Quick Answers
- **What is the first step?** Add the GroupDocs.Annotation Maven dependency to your `pom.xml`.  
- **How do I create a strikeout?** Instantiate `Annotator`, define `StrikeoutAnnotation` with points, set color/opacity, then call `addAnnotation`.  
- **Can I add comments?** Yes, attach a `Comment` object to the annotation for collaboration.  
- **What if the annotation is misplaced?** Adjust the coordinate points; PDF uses a bottom‑left origin system.  
- **Is there a limit to document size?** GroupDocs processes multi‑hundred‑page PDFs without loading the entire file into memory.

## What is “how to add strikeout” in PDF annotation?
The phrase “how to add strikeout” refers to the process of programmatically drawing a line through selected text within a PDF document using an annotation API. In Java, GroupDocs.Annotation provides a dedicated `StrikeoutAnnotation` class that handles rendering, styling, and persistence of strikeout marks.

## Why Use GroupDocs for Java PDF Strikeout?
GroupDocs.Annotation supports **50+ input and output formats**—including PDF, DOCX, XLSX, PPTX, HTML, and common image types—so you’re not locked into a single file type. It provides a high‑level API that abstracts the low‑level PDF structure, automatically handling font embedding, page rendering, and annotation persistence, which lets developers focus on business logic rather than PDF internals.

## Prerequisites and Setup Requirements

### Essential Requirements
- **Java Development Kit (JDK):** Version 8 or later (JDK 11+ recommended for optimal garbage‑collection).
- **GroupDocs.Annotation for Java:** Integrated via Maven (see the Maven snippet below).
- **IDE:** IntelliJ IDEA, Eclipse, or any Java‑compatible editor.

### Maven Dependencies Setup
Add the following dependency block to your `pom.xml`:

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

**Pro Tip:** Always verify the latest version on the GroupDocs release page; newer releases add features and fix bugs that can affect annotation rendering.

### Getting Your License Sorted
GroupDocs.Annotation requires a valid license for production use. You have three options:

- **Free Trial:** Download from [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)
- **Temporary License:** Request a development key at [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Full License:** Purchase for production at [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

The trial adds a subtle watermark, so plan your testing accordingly.

## Step‑by‑Step Implementation Guide

### Understanding the Core Components
The following definitions give you a quick mental model:

- **Annotator:** The primary API object that loads a PDF and exposes annotation methods.  
- **StrikeoutAnnotation:** Represents the visual strikeout line and its styling options.  
- **Point:** A coordinate pair (X, Y) that tells the library where the line starts and ends.  
- **Comment:** Optional text attached to an annotation for collaboration.

### Step 1: Setting Up File Paths
Define the locations of your source PDF and the destination file. Incorrect paths are a common source of “File Not Found” errors.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Ensure the output directory exists and is writable; GroupDocs will not auto‑create missing folders.

### Step 2: Initialize the Annotator
Create an `Annotator` instance that loads the PDF into memory.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** The library parses the PDF structure, builds an internal representation, and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this step may take a few seconds.

### Step 3: Adding Comments (Optional but Recommended)
`Comment` is a class that represents a textual note attached to an annotation, allowing collaborators to explain the reason for the strikeout.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Use comments to explain why text is being removed—this is especially useful in legal or editorial review workflows.

### Step 4: Defining Annotation Coordinates
`Point` objects store X‑Y coordinate pairs that define the exact location of an annotation on a PDF page.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF coordinates start at the bottom‑left corner (0,0). The example creates a horizontal line from (80,730) to (240,730) on the target page.

**Finding the Right Coordinates:** Many developers create a helper that converts percentages of page width/height into absolute points, making the code resilient to different page sizes.

### Step 5: Creating the Strikeout Annotation
`StrikeoutAnnotation` encapsulates the visual line, its style properties such as color and opacity, and any associated metadata for a strikeout mark.

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

**Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright yellow). Use an online converter if you need brand‑specific shades.

**Opacity Recommendation:** An opacity of `0.7` (70 %) offers a clear visual cue while keeping the underlying text legible.

### Step 6: Apply the Annotation
`addAnnotation` is a method of the `Annotator` that registers the prepared annotation with the document so it will be rendered and saved.

```java
annotator.add(strikeout);
```

### Step 7: Save and Clean Up
`dispose()` releases native resources held by the `Annotator` instance, preventing memory leaks after processing is complete.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Calling `dispose()` frees native resources and prevents memory leaks when processing batches of PDFs.

## Common Issues and How to Fix Them

### Issue 1: “File Not Found” Errors
**Symptoms:** Exception thrown during `Annotator` construction.  
**Solution:** Verify both input and output paths, and confirm the application has read/write permissions.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Issue 2: Strikeout Appears in the Wrong Location
**Symptoms:** The line does not line up with the intended text.  
**Solution:** Remember that PDF Y‑coordinates increase upward. Use a visual debugging tool or print the page dimensions to fine‑tune the points.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Issue 3: Annotation Not Visible
**Symptoms:** No strikeout shows up after saving.  
**Possible Causes & Fixes:**
- **Opacity too low:** Temporarily set opacity to `1.0` to verify visibility.  
- **Color blending:** Use a high‑contrast color like red (`255`).  
- **Incorrect page index:** Page numbers are zero‑based; ensure you target the correct page.

### Issue 4: Memory Problems with Large Files
**Symptoms:** `OutOfMemoryError` or sluggish performance.  
**Solutions:**  
- Process documents in smaller batches.  
- Use the streaming API if available.  
- Always invoke `dispose()` after each document.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Real‑World Applications and Use Cases

### Legal Document Review
Law firms annotate contracts with strikeouts to indicate deleted clauses while preserving an audit trail.

### Academic Paper Editing
Professors use strikeouts to suggest removals during peer review, keeping the original text visible for context.

### Content Management Systems
Publishing platforms automatically flag policy‑violating sections with strikeouts before manual moderation.

### Version Control for Documents
Enterprises treat strikeout annotations as “deletion markers” in a document‑centric version‑control workflow, similar to code diffs.

## Performance Optimization Tips

### Batch Processing Strategy
When handling many PDFs, reuse a single `Annotator` instance where possible and process files in parallel threads.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Memory Management Best Practices
- Call `dispose()` on every `Annotator`.  
- Limit concurrent document loads to avoid heap pressure.  
- Monitor JVM memory usage with tools like VisualVM.

### Coordinate Caching
If you apply the same annotation layout across multiple files, cache the `Point` objects to avoid recomputation.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Advanced Customization Options

### Dynamic Color Selection
Choose colors at runtime based on business rules (e.g., red for critical deletions, yellow for tentative ones).

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

### Multi‑Line Strikeouts
Create a series of `Point` pairs to draw a zig‑zag line that crosses several lines of text.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Troubleshooting Checklist
1. **File Permissions:** Verify read/write access.  
2. **Library Version:** Ensure you’re using a supported GroupDocs.Annotation release.  
3. **License Status:** Confirm the license file is correctly referenced.  
4. **PDF Compatibility:** Check that the PDF is not corrupted and is within supported size limits.  
5. **Coordinate Validation:** Ensure all points lie inside page bounds.  
6. **Heap Space:** Increase JVM `-Xmx` if processing very large files.

## Frequently Asked Questions

**Q: Can I strikeout text across multiple lines?**  
A: Yes. Create several `Point` objects that trace the desired path; the annotation will follow the supplied polyline.

**Q: What happens if I specify coordinates outside the page boundaries?**  
A: The annotation will be clipped and may become invisible. Always validate coordinates against the page’s width and height.

**Q: Can I remove strikeout annotations after adding them?**  
A: Absolutely. Use the `removeAnnotation` method with the annotation’s ID or filter by type to delete them programmatically.

**Q: Is there a limit to how many annotations I can add to a single PDF?**  
A: GroupDocs does not impose a hard cap, but performance may degrade after thousands of annotations. Consider pagination or summarizing annotations for very large sets.

**Q: How do I work with password‑protected PDFs?**  
A: Pass the password to the `Annotator` constructor. The library will decrypt the document in memory before applying any annotations.

**Q: How can I handle PDFs with different page sizes and orientations?**  
A: Retrieve each page’s dimensions via `annotator.getPageInfo(pageNumber)` and calculate coordinates relative to those dimensions to ensure consistent placement.

## Conclusion
You now have a complete, production‑ready solution for **how to add strikeout** annotations to PDFs in Java using GroupDocs.Annotation. By mastering file‑path handling, coordinate calculation, and resource management, you can embed this capability into document review tools, content pipelines, or any Java‑based application that needs precise visual feedback.

**Next Steps**
1. Clone the example project and run it against a sample PDF.  
2. Experiment with different colors, opacities, and comment texts.  
3. Integrate the annotation workflow into your existing document‑processing service.  
4. Explore related annotation types—highlights, sticky notes, and shape annotations—to broaden your PDF manipulation toolkit.

Ready for more? Dive into the official documentation for deeper API insights.

## Additional Resources

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - General documentation for GroupDocs libraries
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Complete API reference  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Method‑by‑method details  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Keep your library up‑to‑date  
- [Purchase License](https://purchase.groupdocs.com/buy) - Production‑ready licensing  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Evaluate before buying  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Development testing  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Community help and official support  

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Annotation 23.12 for Java  
**Author:** GroupDocs

## Related Tutorials

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)
