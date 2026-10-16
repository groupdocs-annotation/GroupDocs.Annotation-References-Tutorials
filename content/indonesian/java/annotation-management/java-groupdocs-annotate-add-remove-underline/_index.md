---
date: '2026-10-16'
description: Pelajari cara menyimpan PDF tanpa anotasi di Java, kuasai manajemen memori
  java pdf, dan tambahkan anotasi garis bawah dengan GroupDocs.Annotation. Panduan
  langkah demi langkah.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Anotasi Dokumen Java dengan GroupDocs
og_description: Pelajari cara menyimpan PDF tanpa anotasi di Java, kuasai manajemen
  memori java pdf, dan tambahkan anotasi garis bawah dengan GroupDocs.Annotation.
  Panduan langkah demi langkah.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Cara menyimpan PDF tanpa anotasi di Java menggunakan GroupDocs
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
title: Cara menyimpan PDF tanpa anotasi di Java menggunakan GroupDocs
type: docs
url: /id/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Cara menyimpan PDF tanpa anotasi di Java menggunakan GroupDocs

Jika Anda perlu **save PDF without annotations** sambil tetap dapat menambahkan catatan underline kolaboratif, Anda berada di tempat yang tepat. Banyak pengembang Java mengalami kesulitan menjaga versi bersih dokumen untuk distribusi akhir, terutama ketika file yang sama digunakan untuk tinjauan iteratif. Dalam tutorial ini Anda akan belajar cara menghasilkan PDF bersih, mengelola memori secara efisien, dan menerapkan anotasi underline dengan komentar menggunakan GroupDocs.Annotation. Pada akhir tutorial Anda akan memahami alur kerja lengkap—dari memuat PDF hingga menghasilkan salinan akhir tanpa watermark—serta tips praktik terbaik untuk membangun **java document review system** yang kuat.

## Jawaban Cepat
- **Bagaimana cara menambahkan anotasi underline?** Use `UnderlineAnnotation` with `annotator.add()` then save the document.  
- **Bagaimana cara menyimpan PDF tanpa anotasi?** Load the annotated file, set `AnnotationType.NONE` in `SaveOptions`, and save a new copy.  
- **Perpustakaan apa yang diperlukan?** GroupDocs.Annotation v25.2 (or newer) and its Maven repository.  
- **Apakah saya memerlukan lisensi untuk produksi?** Yes—apply a valid GroupDocs license to avoid watermarks.  
- **Bisakah saya memproses banyak dokumen secara efisien?** Wrap each `Annotator` in a try‑with‑resources block and dispose after each file.

## Bagaimana cara menyimpan PDF tanpa anotasi di Java?

Load the source PDF with an `Annotator`, configure `SaveOptions` to exclude all annotation types, and call `save()` to write a clean copy. This operation does not modify the original file, so you retain both the annotated version for reviewers and a pristine version for distribution. The process uses streaming under the hood, meaning the entire document never fully resides in memory—crucial for large PDFs.

## Apa itu menyimpan PDF tanpa anotasi?

`save pdf without annotations` refers to exporting a PDF document while stripping out every annotation object (highlights, comments, stamps, underlines, etc.). The resulting file contains only the original content and layout, making it suitable for legal filing, public release, or archival storage.

## Mengapa membuat file PDF bersih dalam sistem tinjauan dokumen java?

A clean version eliminates reviewer marks, comments, and highlights, giving you a polished document ready for clients, regulators, or public release. It also reduces file size by up to 30 % on average and prevents accidental disclosure of internal notes—critical for legal and compliance workflows. GroupDocs.Annotation can remove all annotation objects in a single pass, supporting PDFs up to 500 MB without loading the whole file into memory.

## Prasyarat dan penyiapan lingkungan

### Persyaratan sebelum memulai

**Development environment requirements**  
- Java Development Kit (JDK) 8 or higher (JDK 11+ recommended)  
- Maven 3.6+ or Gradle 6.0+ for dependency management  
- IDE such as IntelliJ IDEA, Eclipse, or VS Code with Java extensions  
- At least 2 GB of available RAM (document processing can be memory‑intensive)

**Knowledge prerequisites**  
You should be comfortable with basic Java concepts—object initialization, method calls, and Maven dependencies. Prior experience with third‑party libraries will speed up adoption.

**Testing documents**  
Have a few sample PDFs ready. Text‑based PDFs work best; scanned images may require OCR before annotation.

### Penyiapan Maven: menambahkan GroupDocs ke proyek Anda

Add the following dependency to your `pom.xml`. This step trips up many developers on their first attempt because the group ID and artifact ID must match exactly.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Important:** Version 25.2 is the latest stable release at the time of writing. Check the GroupDocs repository regularly for newer versions that include bug fixes and performance improvements.

### Penyiapan lisensi (jangan lewatkan ini)

**For development/testing** – Download the free trial from the GroupDocs website. The trial includes all features but adds a watermark to processed documents.

**For production** – Purchase a license and apply it during application startup. Without a valid license, production builds will be limited and watermarked.

## Panduan implementasi: menambahkan anotasi underline

### Memahami alur kerja anotasi

Before we dive into code, let’s walk through the four‑step workflow that occurs when you **annotate PDF in Java**:

1. **Document loading** – `Annotator` reads the file into memory.  
2. **Annotation creation** – Define properties such as position, style, and comments.  
3. **Annotation application** – The library injects the annotation into the PDF’s structure.  
4. **Document saving** – Persist the modified file, optionally preserving the original.

The process is non‑destructive; the source file remains untouched unless you overwrite it.

### Langkah 1: inisialisasi annotator dan muat dokumen Anda

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

### Langkah 2: membuat komentar dan balasan (bagian kolaboratif)

`Comment` objects represent threaded discussion attached to an annotation. Each comment can have an author, a timestamp, and optional replies, enabling a full conversation around a specific markup.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Real‑world use:** Reviewers can discuss a specific clause by adding threaded replies, keeping the conversation tied to the exact annotation.

### Langkah 3: mendefinisikan koordinat anotasi (menentukan posisi yang tepat)

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

### Langkah 4: membuat dan mengkonfigurasi anotasi underline

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

### Langkah 5: menyimpan dokumen beranotasi Anda

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

## Menghapus anotasi: membuat versi dokumen bersih

Sometimes you need a version of the PDF **without any annotations**—for example, when delivering the final approved contract. GroupDocs makes this easy.

### Memahami opsi penghapusan anotasi

You can:  
- Remove **all** annotations (most common)  
- Remove specific types (e.g., only highlights)  
- Remove annotations by author or page  

### Penghapusan anotasi langkah demi langkah

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

## Masalah umum dan solusi

### Masalah 1: kesalahan “Document not found”

Make sure the file path is correct and that the application has read permissions. Using `Path.of()` with absolute paths eliminates most ambiguities.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Masalah 2: Anotasi muncul di lokasi yang salah

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

### Masalah 3: Masalah memori dengan dokumen besar

GroupDocs.Annotation streams content and never loads the entire file into heap memory. However, you must still call `dispose()` and consider increasing the JVM heap (`-Xmx`) for files larger than 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Masalah 4: Masalah lisensi di produksi

If the license file is missing or the path is incorrect, the library falls back to trial mode, adding a watermark to every page. Place the license file in a location that is on the classpath and load it early in your application lifecycle.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Praktik terbaik kinerja untuk aplikasi produksi

### Strategi manajemen memori

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

### Pertimbangan threading

GroupDocs.Annotation is **not thread‑safe** by default. If your application processes documents concurrently:

- **Never share** an `Annotator` instance across threads.  
- **Synchronize** file access or use a lock mechanism.  
- Consider a **pool** of `Annotator` objects if you need high throughput.

### Strategi caching

- Cache frequently used annotation templates.  
- Reuse `Point` collections for common coordinate sets.  
- Keep a **template PDF** in memory if you repeatedly annotate the same base document.

## Praktik terbaik manajemen memori PDF Java

Efficient memory use is essential when handling large PDFs or processing many files in a batch. Here are a few practical recommendations:

- **Use try‑with‑resources** for every `Annotator` to guarantee disposal.  
- **Increase the JVM heap** (`-Xmx`) only as needed; monitor usage with profiling tools.  
- **Process documents sequentially** when possible, freeing memory after each file.  
- **Avoid loading the same PDF multiple times**; reuse the same stream if you need to read it repeatedly.

Applying these practices helps keep your application responsive and prevents out‑of‑memory crashes during heavy annotation workloads.

## Aplikasi dunia nyata dan kasus penggunaan

### Sistem tinjauan dokumen

- **Legal review:** Underline contract clauses and add comments about risk.  
- **Compliance audits:** Highlight problematic sections in financial statements.  
- **Academic peer review:** Professors underline passages needing clarification.

### Platform pendidikan

- **Student annotation tools:** Let learners underline key concepts in e‑books.  
- **Teacher feedback:** Provide inline comments directly on submitted assignments.

### Alur kerja jaminan kualitas

- **Technical documentation review:** Engineers underline sections that need updates.  
- **Standard operating procedures:** Safety officers highlight critical steps.

### Sistem manajemen konten

- **Editorial workflow:** Editors underline text that requires fact‑checking.  
- **Version control:** Track annotation history across document revisions.

## Tips lanjutan untuk implementasi profesional

### Gaya anotasi khusus

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

### Metadata anotasi untuk pelacakan

Every annotation can carry a user‑defined metadata dictionary. Store IDs, timestamps, or workflow state to integrate with external tracking systems.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integrasi dengan sistem manajemen pengguna

Map the `author` property of a `Comment` to your application's user IDs. This enables role‑based styling and audit‑trail generation.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Memecahkan masalah produksi

### Pemantauan kinerja

Watch these metrics in production:  
- **Heap usage** – ensure `dispose()` is called.  
- **Processing time per document** – log timestamps before/after `annotator.save()`.  
- **Error rate** – capture exceptions and categorize them.

### Kendala produksi umum

- **File locking** – ensure uploaded files are closed before annotation.  
- **Concurrent edits** – implement optimistic locking or version checks.  
- **Large files (> 50 MB)** – increase JVM timeout and consider streaming APIs.

### Praktik terbaik penanganan error

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

## Pertanyaan yang sering diajukan

**Q: Bagaimana cara menandai beberapa area teks dalam satu operasi?**  
A: Create several `UnderlineAnnotation` objects with different coordinates and add them sequentially using `annotator.add()`.

**Q: Apakah saya dapat menandai gambar dalam dokumen PDF?**  
A: Yes. Use the same coordinate system, ensuring the points lie inside the image bounds.

**Q: Format file apa saja selain PDF yang didukung oleh GroupDocs.Annotation?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), dan format gambar seperti JPEG, PNG, TIFF.

**Q: Bagaimana cara menangani dokumen sangat besar tanpa kehabisan memori?**  
A: Process documents one at a time, increase the JVM heap (`-Xmx`), and always dispose of `Annotator` instances promptly.

**Q: Apakah memungkinkan mengekstrak anotasi yang sudah ada dari sebuah dokumen?**  
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

## Tutorial Terkait

- [Create Clean PDF Java: Underline Annotations with GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annotate Pdfs Groupdocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)