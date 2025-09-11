---
---
title: "Java Document Annotation Library - Add & Remove Underline Annotations"
linktitle: "Java Document Annotation with GroupDocs"
description: "Learn how to add and remove underline annotations in Java documents using GroupDocs.Annotation. Complete tutorial with code examples and troubleshooting tips."
date: "2025-01-02"
lastmod: "2025-01-02"
weight: 1
url: "/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
keywords: "java document annotation library, groupdocs annotation tutorial, add underline annotation java, java pdf annotation, how to annotate pdf documents in java"
categories: ["Java Development"]
tags: ["groupdocs", "document-annotation", "java-tutorial", "pdf-manipulation"]
---

# Java Document Annotation Library: Complete Guide to Adding and Removing Underline Annotations

## Introduction

Struggling with document management and collaboration in your Java applications? You're not alone. Many developers face the challenge of implementing robust document annotation features that work reliably across different file formats.

This comprehensive guide walks you through using GroupDocs.Annotation for Java - one of the most powerful document annotation libraries available. By the end of this tutorial, you'll know exactly how to add underline annotations with comments, remove existing annotations, and integrate these features seamlessly into your projects.

**What you'll master in this guide:**
- Setting up GroupDocs.Annotation in your Java project (the right way)
- Adding underline annotations with custom comments and styling
- Removing all annotations to create clean document versions  
- Troubleshooting common issues developers encounter
- Optimizing performance for production applications

Whether you're building a document review system, educational platform, or collaborative editing tool, this tutorial has you covered with practical, tested code examples.

## Why Choose GroupDocs for Java Document Annotation?

Before diving into the implementation, let's address why GroupDocs.Annotation stands out among Java document libraries:

**Comprehensive Format Support**: Unlike many alternatives, GroupDocs handles PDFs, Word documents, Excel spreadsheets, PowerPoint presentations, and more - all with a single API.

**Production-Ready Stability**: This isn't a lightweight library that breaks under pressure. It's designed for enterprise applications that need to process thousands of documents reliably.

**Rich Annotation Types**: Beyond basic underlining, you get access to highlights, stamps, watermarks, text replacements, and custom shapes - giving you flexibility for any use case.

## Prerequisites and Environment Setup

### What You'll Need Before Starting

**Development Environment Requirements:**
- Java Development Kit (JDK) 8 or higher (JDK 11+ recommended for better performance)
- Maven 3.6+ or Gradle 6.0+ for dependency management
- IDE like IntelliJ IDEA, Eclipse, or VS Code with Java extensions
- At least 2GB of available RAM (document processing can be memory-intensive)

**Knowledge Prerequisites:**
You should be comfortable with basic Java concepts like object initialization, method calls, and working with Maven dependencies. If you've worked with any third-party Java libraries before, you'll pick this up quickly.

**Testing Documents:**
Have a few sample PDFs ready for testing. The examples work best with text-based PDFs rather than scanned images.

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

**Important Note**: Version 25.2 is the latest stable release as of writing. Always check the GroupDocs repository for updates, as newer versions often include bug fixes and performance improvements.

### Licensing Setup (Don't Skip This)

For development and testing, you can start with GroupDocs' free trial. However, for production applications, you'll need a valid license. Here's how to handle both scenarios:

**For Development/Testing:**
Download the free trial from the GroupDocs website. The trial includes all features but adds a watermark to processed documents.

**For Production:**
Purchase a license and apply it in your application startup code. Without proper licensing, your production app will have limitations.

## Implementation Guide: Adding Underline Annotations

### Understanding the Annotation Workflow

Before jumping into code, let's understand what happens when you add an annotation:

1. **Document Loading**: The Annotator class loads your document into memory
2. **Annotation Creation**: You define the annotation properties (position, style, comments)
3. **Annotation Application**: The library applies the annotation to the document structure
4. **Document Saving**: The modified document is saved with embedded annotations

This process is designed to be non-destructive - your original document remains unchanged unless you explicitly overwrite it.

### Step 1: Initialize the Annotator and Load Your Document

The first step is creating an Annotator instance. This is where many developers encounter their first issue - file path problems.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Pro Tip**: Use absolute paths during development to avoid "file not found" errors. In production, consider using relative paths with proper resource management.

### Step 2: Creating Comments and Replies (The Collaborative Part)

One of GroupDocs' strengths is its support for threaded comments - just like you'd find in Google Docs or Microsoft Word online.

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

**Real-World Application**: In document review workflows, this threaded comment system lets multiple reviewers discuss specific sections without losing context.

### Step 3: Defining Annotation Coordinates (Getting the Position Right)

This is where precision matters. The coordinate system starts from the top-left corner of the page, with measurements in points.

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

**Understanding the Coordinate System**: 
- Point 1 and 2 define the top edge of your underline
- Point 3 and 4 define the bottom edge
- The difference between Y coordinates (730 vs 650) determines the underline thickness

### Step 4: Creating and Configuring the Underline Annotation

Now we bring everything together into a properly configured underline annotation:

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

**Color Configuration Notes**: 
- FontColor uses ARGB format (Alpha, Red, Green, Blue)
- 65535 represents bright yellow (0x00FFFF)
- For red, use 16711680 (0xFF0000)
- For blue, use 255 (0x0000FF)

**Opacity Best Practices**: Values between 0.5 and 0.8 work well for readability. Too low and the annotation becomes invisible; too high and it obscures the underlying text.

### Step 5: Saving Your Annotated Document

The final step is saving your work. Always specify a different output path to preserve your original document:

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management**: That `dispose()` call is crucial for preventing memory leaks, especially if you're processing multiple documents in a loop.

## Removing Annotations: Creating Clean Document Versions

Sometimes you need the original document without any annotations - perhaps for final distribution or archival purposes. Here's how to do that efficiently.

### Understanding Annotation Removal Options

GroupDocs gives you granular control over which annotations to remove:
- Remove all annotations (most common)
- Remove specific annotation types
- Remove annotations by author
- Remove annotations from specific pages

### Step-by-Step Annotation Removal

**Step 1: Load the Previously Annotated Document**

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 2: Configure Save Options for Clean Output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Step 3: Save the Clean Version**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

This approach is particularly useful in document approval workflows where you need both reviewed (with annotations) and final (clean) versions.

## Common Issues and Solutions

### Problem 1: "Document not found" Errors

**Symptoms**: FileNotFoundException when initializing the Annotator
**Common Causes**: 
- Incorrect file paths (especially on different operating systems)
- Missing file permissions
- File locked by another process

**Solution**:
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

### Problem 2: Annotations Appearing in Wrong Locations

**Symptoms**: Underlines appear far from the intended text
**Common Causes**: 
- Incorrect coordinate calculations
- Different page sizes than expected
- Zero-indexed vs one-indexed page numbering confusion

**Solution**:
Always test your coordinates with simple values first:
```java
// Start with a small rectangle in the top-left area for testing
Point point1 = new Point(10, 10);   // Top-left
Point point2 = new Point(100, 10);  // Top-right  
Point point3 = new Point(10, 30);   // Bottom-left
Point point4 = new Point(100, 30);  // Bottom-right
```

### Problem 3: Memory Issues with Large Documents

**Symptoms**: OutOfMemoryError or very slow processing
**Common Causes**: 
- Processing multiple large documents without proper cleanup
- Not disposing of Annotator instances
- Insufficient JVM heap space

**Solution**:
```java
// Increase JVM heap size when running your application
// -Xmx2g for 2GB heap space

// Always use try-with-resources or explicit disposal
try (Annotator annotator = new Annotator("document.pdf")) {
    // Your annotation code here
    annotator.save("output.pdf");
} // Automatically disposed here
```

### Problem 4: Licensing Issues in Production

**Symptoms**: Watermarks on documents, feature limitations
**Common Causes**: 
- Missing license file
- Expired license
- License not properly loaded at application startup

**Solution**: Implement proper license checking in your application startup:
```java
// Check license status at application start
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle appropriately for your application
}
```

## Performance Best Practices for Production Applications

### Memory Management Strategies

**Use Try-With-Resources**: Always wrap Annotator instances in try-with-resources blocks or explicitly call dispose():

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Automatic cleanup
```

**Batch Processing Approach**: When processing multiple documents, don't keep all Annotator instances in memory simultaneously:

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each document
}
```

### Threading Considerations

GroupDocs.Annotation is not thread-safe by default. If you're building a multi-threaded application:

**Don't Share Annotator Instances**: Create separate instances for each thread
**Synchronize File Access**: Use proper locking when multiple threads might access the same files
**Consider Connection Pooling**: For high-throughput applications, implement a pool of Annotator instances

### Caching Strategies

For applications that repeatedly annotate similar documents:

**Cache Annotation Templates**: Store commonly used annotation configurations
**Reuse Point Collections**: Pre-calculate common coordinate sets
**Template Documents**: Keep template documents in memory for faster processing

## Real-World Applications and Use Cases

### Document Review Systems

In legal firms and corporate environments, document review is critical. Here's how underline annotations fit:

**Contract Review**: Lawyers underline key clauses while adding comments about potential issues
**Compliance Auditing**: Auditors highlight problematic sections in financial reports
**Academic Paper Review**: Professors underline areas needing clarification in student papers

**Implementation Tip**: Consider color-coding annotations by reviewer role (red for legal issues, yellow for clarification needed, green for approved sections).

### Educational Platforms

**Student Annotation Tools**: Let students underline important passages in digital textbooks
**Teacher Feedback Systems**: Instructors can highlight areas needing improvement in submitted assignments
**Collaborative Study Groups**: Multiple students can annotate the same document with threaded discussions

### Quality Assurance Workflows

**Documentation Review**: Technical writers underline sections needing updates
**Standard Operating Procedures**: Safety inspectors highlight critical steps in procedure documents
**Training Materials**: Subject matter experts mark areas requiring additional explanation

### Content Management Systems

**Editorial Workflows**: Editors underline text requiring fact-checking or revision
**Approval Processes**: Managers highlight sections needing stakeholder review
**Version Control**: Track changes and decisions through annotation history

## Advanced Tips for Professional Implementation

### Custom Annotation Styles

While our example uses basic yellow underlining, you can create sophisticated annotation styles:

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED"); // Clear messaging
```

### Annotation Metadata for Tracking

Add metadata to annotations for better organization:

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integration with User Management Systems

In enterprise applications, integrate annotations with your user management:

```java
// Get current user from your authentication system
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role-based annotation styles
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Troubleshooting Production Issues

### Performance Monitoring

Monitor these metrics in production:
- **Memory Usage**: Watch for memory leaks from undisposed Annotator instances
- **Processing Time**: Track how long annotation operations take
- **Error Rates**: Monitor failed annotation attempts

### Common Production Gotchas

**File Locking Issues**: In web applications, ensure uploaded files are properly unlocked before processing
**Concurrent Access**: Multiple users trying to annotate the same document can cause conflicts
**Large File Handling**: Documents over 50MB may require special handling and increased timeout values

### Error Handling Best Practices

Implement comprehensive error handling:

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

You now have everything needed to implement robust document annotation features in your Java applications. From basic underline annotations to complex collaborative review systems, GroupDocs.Annotation provides the foundation for professional document management solutions.

**Key Takeaways:**
- Always use proper resource management with try-with-resources or explicit disposal
- Test coordinate calculations thoroughly before deploying to production
- Implement comprehensive error handling for robust applications
- Consider user roles and workflows when designing annotation features
- Monitor performance metrics in production environments

The examples in this guide provide a solid foundation, but don't stop here. Explore other annotation types like highlights, stamps, and text replacements to build even more powerful document collaboration tools.

**Next Steps**: Try implementing a simple document review workflow in your application using these techniques. Start with basic underlining, then gradually add features like role-based styling and threaded comments as your requirements evolve.

## Frequently Asked Questions

### How do I annotate multiple areas of text in a single operation?
Create multiple `UnderlineAnnotation` objects and add them sequentially using the `annotator.add()` method. Each annotation can have different coordinates, colors, and comments.

### Can I annotate images within PDF documents?
Yes, GroupDocs.Annotation supports annotating images embedded in PDFs. Use the same coordinate system, but ensure your coordinates fall within the image boundaries.

### What file formats besides PDF does GroupDocs.Annotation support?
The library supports Word documents (DOC, DOCX), Excel spreadsheets (XLS, XLSX), PowerPoint presentations (PPT, PPTX), and various image formats (JPEG, PNG, TIFF).

### How do I handle very large documents without running out of memory?
Process large documents in smaller chunks, always dispose of Annotator instances properly, and consider increasing your JVM heap size with the `-Xmx` parameter.

### Is it possible to extract existing annotations from a document?
Yes, use the `get()` method of the Annotator class to retrieve all existing annotations, then filter them by type or other properties as needed.

### Can I customize the appearance of underline annotations beyond color and opacity?
You can adjust font size, add custom messages, set creation timestamps, and define reply threads. For more advanced styling, consider using different annotation types or combining multiple annotations.

### How do I handle concurrent users annotating the same document?
Implement file locking mechanisms in your application, use version control strategies, or consider real-time collaborative features with conflict resolution algorithms.

### What's the performance impact of adding many annotations to a single document?
Performance scales roughly linearly with the number of annotations. For documents with hundreds of annotations, consider pagination or lazy loading strategies in your user interface.