---
categories:
- Java Development
date: '2026-09-25'
description: Learn how to save specific pdf pages using try resources in Java with
  GroupDocs.Annotation. Includes Spring Boot service example and performance tips.
images:
- /java/document-saving/groupdocs-annotation-java-save-specific-page-range/og-image.png
keywords:
- save specific pdf pages
- try with resources java
- remove unused pdf pages
- use try resources
lastmod: '2026-09-25'
linktitle: Save Specific Pages Java Annotation
og_description: Learn how to save specific pdf pages using try resources in Java with
  GroupDocs.Annotation. Step-by-step guide, performance tips, and Spring Boot integration.
og_image_alt: Guide to saving specific PDF pages in Java using GroupDocs.Annotation
  and try resources
og_title: How to save specific pdf pages with try resources in Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to save specific pdf pages using try resources in Java with
    GroupDocs.Annotation. Includes Spring Boot service example and performance tips.
  headline: How to save specific pdf pages with try resources in Java
  type: TechArticle
- questions:
  - answer: Not with a single `SaveOptions` call. Run separate saves for each range
      and merge the results afterward.
    question: Can I save non‑consecutive pages (e.g., 1, 3, 7)?
  - answer: 'Yes—provide the password when constructing the `Annotator`: `new Annotator(inputFile,
      loadOptions.setPassword("your_password"))`.'
    question: Does this work with password‑protected documents?
  - answer: PDF, Microsoft Word, Excel, PowerPoint, and many others. See the [official
      documentation](https://docs.groupdocs.com/annotation/java/) for the full list.
    question: What file formats are supported?
  - answer: Absolutely—set `saveOptions.setAnnotationsOnly(true)` to create an annotation‑only
      file.
    question: Can I save just the annotations without the original content?
  - answer: Use `setLoadOnlyAnnotatedPages(true)`, process in chunks, and consider
      increasing the JVM heap size.
    question: How do I handle very large documents (1000+ pages)?
  type: FAQPage
tags:
- save specific pdf pages
- groupdocs
- java annotation
- document processing
- pdf manipulation
title: How to save specific pdf pages with try resources in Java
type: docs
url: /java/document-saving/groupdocs-annotation-java-save-specific-page-range/
weight: 1
---

# How to save specific pdf pages from annotated documents in Java

When you need to **save specific pdf pages** from a large, annotated file, using Java’s *try with resources* pattern together with GroupDocs.Annotation gives you a safe, memory‑efficient solution. This tutorial shows you how to set up the library, extract a page range, and integrate the logic into a Spring Boot service—all while keeping your code clean and your resources properly released.

## Introduction

`Annotator` is the primary class in GroupDocs.Annotation that loads a document and provides methods for annotation handling and saving.  
In many business scenarios—legal contracts, technical manuals, or research papers—you often only need a handful of pages that contain the relevant annotations. Extracting just those pages reduces storage costs by up to 96 %, speeds up downstream processing, and helps you stay compliant by sharing only the permitted sections.

**What you’ll master by the end of this guide:**
- Installing and licensing GroupDocs.Annotation for Java  
- Using `try with resources` to safely save a page range  
- Handling large PDFs with low memory overhead  
- Embedding the logic in a Spring Boot document‑service  
- Troubleshooting common pitfalls such as locked files and out‑of‑memory errors  

## Quick answers
- **What does “try with resources java” do?** It automatically closes the `Annotator`, preventing file locks and memory leaks.  
- **Which library handles page‑range saving?** `GroupDocs.Annotation` provides `SaveOptions` with `setFirstPage`/`setLastPage`. `SaveOptions` lets you specify output settings such as page range and whether to include annotations only.  
- **Can I use this in a Spring Boot service?** Yes – see the “Spring Boot document service integration” section.  
- **Do I need a license?** A free trial works for development; a full license is required for production.  
- **Is it safe for large PDFs (1000+ pages)?** Use load‑only‑annotated‑pages and batch processing to keep memory usage low.  

## What is save specific pdf pages?
The **save specific pdf pages** operation extracts a defined page interval from a source document while preserving all annotations on those pages. It creates a new, smaller PDF that contains only the selected pages, which is ideal for targeted sharing or archival.

## Why use try resources for page saving?
Using `try with resources` guarantees that the `Annotator` instance is disposed as soon as the block ends. This deterministic cleanup prevents the common “file is locked” exception and keeps the JVM’s heap footprint predictable—especially important when processing dozens of large PDFs in parallel.

## Prerequisites and setup

### What you’ll need
- **JDK 8+** (JDK 11+ recommended)  
- **Maven** or **Gradle** for dependency management  
- **GroupDocs.Annotation for Java** — version 25.2 or later (supports 50+ formats)  
- Basic familiarity with Java I/O and OOP  

### Setting up GroupDocs.Annotation for Java

#### Maven configuration
Add the dependency to your `pom.xml` (copy‑paste is your friend here):

```xml
<!-- ```xml
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
``` -->
```

#### Gradle setup (if you prefer Gradle)
```groovy
// ```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/annotation/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```
```

### Getting your license sorted
Start with the free trial, then move to a temporary or full license as needed:

- **Free trial:** Perfect for testing and development – grab it from [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- **Temporary license:** Need more time to evaluate? Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)  
- **Full license:** Ready for production? [Purchase here](https://purchase.groupdocs.com/buy)  

> **Pro tip:** The trial version removes only a few advanced features, which is more than enough to follow this tutorial and build a proof of concept.

## How does try with resources work in Java?

`try` `with` `resources` automatically calls `close()` on any object that implements `AutoCloseable` at the end of the block. When you wrap an `Annotator` instance in this construct, the library releases file handles and clears internal buffers without any extra code, eliminating the risk of lingering locks.

## Core implementation: saving specific page ranges

### The `Annotator` definition anchor
`Annotator` is GroupDocs.Annotation’s primary class for loading, editing, and saving annotated documents. It provides methods to access annotations, modify pages, and export results.

### Step 1: set up file‑path utilities

Create a small helper that builds output paths consistently:

```java
// ```java
import org.apache.commons.io.FilenameUtils;

public class FilePathConfiguration {
    public String getOutputFilePath(String inputFile) {
        return "YOUR_OUTPUT_DIRECTORY/SavingSpecificPageRange" + "." + FilenameUtils.getExtension(inputFile);
    }
}
```
```

Centralizing path logic makes it easy to change directories later and keeps your code testable.

### Step 2: implement page‑range saving

The following snippet shows the essential logic. It uses `try with resources` to guarantee cleanup:

```java
// ```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.export.SaveOptions;

public class SaveSpecificPageRange {
    public void run(String inputFile) {
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(2);  // Start from page 2
            saveOptions.setLastPage(4);   // End at page 4
            
            annotator.save(outputPath, saveOptions);
        }
    }
}
```
```

- `setFirstPage(2)` and `setLastPage(4)` define an **inclusive** range (pages 2‑4).  
- The `Annotator` is closed automatically when the block exits, preventing file‑lock issues.  

### Advanced file‑path configuration

For production you may want dynamic naming:

```java
// ```java
public class FilePathConfiguration {
    private final String baseOutputDirectory;
    
    public FilePathConfiguration(String baseOutputDirectory) {
        this.baseOutputDirectory = baseOutputDirectory;
    }
    
    public String getInputFilePath(String filename) {
        return "YOUR_DOCUMENT_DIRECTORY/" + filename;
    }
    
    public String getOutputFilePath(String inputFile, String suffix) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_%s.%s", baseOutputDirectory, baseName, suffix, extension);
    }
}
```
```

Now the output file will be named something like `contract_pages_2-4.pdf`, making it clear which pages were extracted.

## Common pitfalls and how to avoid them

### Pitfall #1: page‑index confusion
**Problem:** Assuming page numbers start at 0.  
**Solution:** Page numbering in GroupDocs.Annotation starts at 1, matching what users see in PDF viewers.

```java
// ```java
// Wrong - this tries to start from page 0 (doesn't exist)
saveOptions.setFirstPage(0);

// Right - this starts from the actual first page
saveOptions.setFirstPage(1);
```
```

### Pitfall #2: resource leaks
**Problem:** Forgetting to close `Annotator` leads to locked files.  
**Solution:** Always wrap the `Annotator` in a `try with resources` block or call `close()` explicitly.

```java
// ```java
// Good - automatic resource management
try (final Annotator annotator = new Annotator(inputFile)) {
    // your code here
} // automatically closes

// Also acceptable - manual closing
Annotator annotator = null;
try {
    annotator = new Annotator(inputFile);
    // your code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
```

### Pitfall #3: invalid page ranges
**Problem:** Specifying a range that exceeds the document’s page count.  
**Solution:** Validate the range against `annotator.getDocumentInfo().getPagesCount()` before saving.

```java
// ```java
public void savePageRangeWithValidation(String inputFile, int firstPage, int lastPage) {
    try (final Annotator annotator = new Annotator(inputFile)) {
        // Get document info to check page count
        DocumentInfo documentInfo = annotator.getDocument().getDocumentInfo();
        int totalPages = documentInfo.getPageCount();
        
        // Validate range
        if (firstPage < 1 || firstPage > totalPages) {
            throw new IllegalArgumentException("First page out of range: " + firstPage);
        }
        if (lastPage < firstPage || lastPage > totalPages) {
            throw new IllegalArgumentException("Last page out of range: " + lastPage);
        }
        
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setFirstPage(firstPage);
        saveOptions.setLastPage(lastPage);
        
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        annotator.save(outputPath, saveOptions);
    }
}
```
```

## Performance optimization tips

### Memory management for large documents
When processing PDFs with 100 + pages, enable loading‑only‑annotated pages to keep the heap low:

```java
// ```java
public class OptimizedPageRangeSaver {
    public void saveWithOptimization(String inputFile, int firstPage, int lastPage) {
        // Configure for lower memory usage
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadOnlyAnnotatedPages(true); // Only load pages with annotations
        
        try (final Annotator annotator = new Annotator(inputFile, loadOptions)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            // Optional: Enable compression for smaller output files
            saveOptions.setAnnotationsOnly(false); // Set to true if you only want annotations
            
            String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
            annotator.save(outputPath, saveOptions);
        }
    }
}
```
```

Key strategies:
- `setLoadOnlyAnnotatedPages(true)` reduces memory usage by loading only pages that contain annotations.  
- `setAnnotationsOnly(true)` creates a lightweight file that stores just the annotation layer.  
- Batch processing with a fixed thread pool avoids exhausting system resources.

### Batch processing multiple documents
For high‑throughput scenarios, process files in batches:

```java
// ```java
public class BatchPageRangeSaver {
    public void processBatch(List<String> inputFiles, int firstPage, int lastPage) {
        for (String inputFile : inputFiles) {
            try {
                savePageRangeWithValidation(inputFile, firstPage, lastPage);
                System.out.println("Successfully processed: " + inputFile);
            } catch (Exception e) {
                System.err.println("Failed to process " + inputFile + ": " + e.getMessage());
                // Log the error and continue with next file
            }
        }
    }
}
```
```

## Integration with popular frameworks

### Spring Boot document service integration
Below is a minimal Spring Boot service that receives a PDF, extracts a page range, and returns the new file as a byte array.

```java
// ```java
@Service
public class DocumentPageRangeService {
    
    @Value("${app.document.output-directory}")
    private String outputDirectory;
    
    public String savePageRange(String inputFile, int firstPage, int lastPage) {
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            String outputPath = generateOutputPath(inputFile, firstPage, lastPage);
            annotator.save(outputPath, saveOptions);
            
            return outputPath;
        } catch (Exception e) {
            throw new DocumentProcessingException("Failed to save page range", e);
        }
    }
    
    private String generateOutputPath(String inputFile, int firstPage, int lastPage) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_pages_%d-%d.%s", 
                            outputDirectory, baseName, firstPage, lastPage, extension);
    }
}
```
```

The service uses constructor injection for the `AnnotatorFactory`, keeping the controller thin and testable.

## Practical applications and use cases

### Legal document processing
Law firms often need to share only the clauses that have been reviewed. Extracting those pages reduces the risk of exposing confidential sections.

```java
// ```java
public class LegalDocumentProcessor {
    public void extractEvidencePages(String caseFile, List<Integer> evidencePages) {
        // Group consecutive pages for efficient processing
        List<PageRange> ranges = groupConsecutivePages(evidencePages);
        
        for (PageRange range : ranges) {
            String outputFile = String.format("evidence_%d_%d-to-%d.pdf", 
                                            getCaseNumber(caseFile), range.start, range.end);
            savePageRange(caseFile, range.start, range.end, outputFile);
        }
    }
}
```
```

### Educational content management
Teachers can pull out only the annotated chapters students need for an assignment, cutting down on download size and improving focus.

```java
// ```java
public class EducationalContentExtractor {
    public void createAssignmentPacket(String textbook, int chapterStart, int chapterEnd) {
        try (final Annotator annotator = new Annotator(textbook)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(chapterStart);
            saveOptions.setLastPage(chapterEnd);
            
            String assignmentFile = generateAssignmentFileName(textbook, chapterStart, chapterEnd);
            annotator.save(assignmentFile, saveOptions);
        }
    }
}
```
```

### Quality‑assurance reviews
QA teams can isolate pages with reviewer comments, enabling faster iteration cycles.

```java
// ```java
public class QAReviewExtractor {
    public void extractReviewedPages(String document) {
        try (final Annotator annotator = new Annotator(document)) {
            // Get pages with annotations
            List<Integer> annotatedPages = getAnnotatedPageNumbers(annotator);
            
            if (!annotatedPages.isEmpty()) {
                int firstPage = Collections.min(annotatedPages);
                int lastPage = Collections.max(annotatedPages);
                
                SaveOptions saveOptions = new SaveOptions();
                saveOptions.setFirstPage(firstPage);
                saveOptions.setLastPage(lastPage);
                
                String reviewFile = document.replace(".pdf", "_review_comments.pdf");
                annotator.save(reviewFile, saveOptions);
            }
        }
    }
}
```
```

## Best practices summary
1. **Validate page numbers** before invoking the save operation.  
2. **Always use `try with resources`** to guarantee that `Annotator` is closed.  
3. **Enable `setLoadOnlyAnnotatedPages(true)`** for large PDFs to keep memory usage under control.  
4. **Test across supported formats**—GroupDocs.Annotation handles over 50 input and output types, including PDF, DOCX, XLSX, PPTX, and image files.  
5. **Monitor JVM heap** and adjust `-Xmx` as needed for batch jobs.  

## Troubleshooting common issues

### Issue: “File is locked” error
**Symptoms:** An exception mentioning a locked file appears during `save()`.  
**Causes:**  
- A previous `Annotator` instance wasn’t closed.  
- The file is open in another application.  
- Insufficient file‑system permissions.  

**Solution:** Ensure every `Annotator` is wrapped in `try with resources` and verify OS‑level file locks.

```java
// ```java
// Ensure proper cleanup
try (final Annotator annotator = new Annotator(inputFile)) {
    // ... your code ...
} // Automatically releases file handles

// Verify file accessibility before processing
File file = new File(inputFile);
if (!file.canRead()) {
    throw new IllegalArgumentException("Cannot read input file: " + inputFile);
}
if (!file.getParentFile().canWrite()) {
    throw new IllegalArgumentException("Cannot write to output directory");
}
```
```

### Issue: Out‑of‑memory errors
**Symptoms:** `OutOfMemoryError` when processing large PDFs.  
**Solutions:**  
1. Increase JVM heap (`-Xmx2g` or higher).  
2. Use `setLoadOnlyAnnotatedPages(true)` and `setAnnotationsOnly(true)`.  
3. Process documents in smaller batches.

### Issue: Annotations not preserved
**Symptoms:** Output file lacks the original markup.  
**Solution:** Do not enable `setAnnotationsOnly(false)` inadvertently; keep the default to retain annotations.

```java
// ```java
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationsOnly(false); // Keep both content and annotations
saveOptions.setFirstPage(firstPage);
saveOptions.setLastPage(lastPage);
```
```

## Frequently asked questions

**Q: Can I save non‑consecutive pages (e.g., 1, 3, 7)?**  
A: Not with a single `SaveOptions` call. Run separate saves for each range and merge the results afterward.

**Q: Does this work with password‑protected documents?**  
A: Yes—provide the password when constructing the `Annotator`: `new Annotator(inputFile, loadOptions.setPassword("your_password"))`.

**Q: What file formats are supported?**  
A: PDF, Microsoft Word, Excel, PowerPoint, and many others. See the [official documentation](https://docs.groupdocs.com/annotation/java/) for the full list.

**Q: Can I save just the annotations without the original content?**  
A: Absolutely—set `saveOptions.setAnnotationsOnly(true)` to create an annotation‑only file.

**Q: How do I handle very large documents (1000+ pages)?**  
A: Use `setLoadOnlyAnnotatedPages(true)`, process in chunks, and consider increasing the JVM heap size.

**Q: Is there a way to preview pages before saving?**  
A: GroupDocs.Annotation focuses on processing, but you can retrieve page count and annotation locations via `annotator.getDocumentInfo()` to decide which ranges to extract.

## Additional resources

- Documentation: [GroupDocs.Annotation for Java Docs](https://docs.groupdocs.com/annotation/java/)  
- Official documentation: [official documentation](https://docs.groupdocs.com/annotation/java/)  
- API reference: [Complete API Documentation](https://reference.groupdocs.com/annotation/java/)  
- Download: [Latest Releases](https://releases.groupdocs.com/annotation/java/)  
- GroupDocs releases: [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- License options: [License Options](https://purchase.groupdocs.com/buy)  
- Purchase here: [Purchase here](https://purchase.groupdocs.com/buy)  
- Free trial: [Try It Now](https://releases.groupdocs.com/annotation/java/)  
- Temporary license: [Get Evaluation License](https://purchase.groupdocs.com/temporary-license/)  
- Support: [Community Forum](https://forum.groupdocs.com/c/annotation/)  

---

**Last Updated:** 2026-09-25  
**Tested With:** GroupDocs.Annotation 25.2 (Java)  
**Author:** GroupDocs

## Related Tutorials

- [Reduce PDF Size Java with GroupDocs.Annotation – Complete Guide](/annotation/java/document-saving/)
- [Save Annotated PDF using GroupDocs Java & Azure Blob](/annotation/java/document-loading/download-annotate-azure-blob-groupdocs-java/)
- [Load Password Protected PDF with GroupDocs.Annotation Java](/annotation/java/advanced-features/)