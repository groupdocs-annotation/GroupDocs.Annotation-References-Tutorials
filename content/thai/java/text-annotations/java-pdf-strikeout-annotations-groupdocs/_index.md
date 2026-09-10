---
categories:
- Java PDF Processing
date: '2026-05-21'
description: เรียนรู้วิธีเพิ่ม strikeout annotations ใน PDFs ด้วย Java โดยใช้ GroupDocs.
  บทแนะนำขั้นตอนต่อขั้นตอนนี้ครอบคลุมการตั้งค่า, โค้ด, การแก้ไขปัญหา, และเคล็ดลับด้านประสิทธิภาพ.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: คู่มือ Java PDF Text Strikeout
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
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
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: วิธีเพิ่ม strikeout annotations ใน PDFs ด้วย Java – คู่มือครบวงจรของ GroupDocs
type: docs
url: /th/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# วิธีเพิ่มการทำเครื่องหมายขีดฆ่าใน PDF ด้วย Java

เคยต้องการขีดฆ่าข้อความใน PDF อย่างอัตโนมัติหรือไม่? ไม่ว่าคุณจะกำลังสร้างระบบตรวจทานเอกสาร, สร้างกระบวนการแก้ไข, หรือเพียงต้องการทำเครื่องหมายข้อความเพื่อการลบ, **how to add strikeout** annotations in Java เป็นทักษะที่เป็นประโยชน์ซึ่งช่วยประหยัดเวลาและลดความพยายามในการทำงานด้วยมือ. ในคู่มือฉบับครอบคลุมนี้คุณจะได้ค้นพบทุกอย่างที่ต้องรู้เพื่อทำการเพิ่มการทำเครื่องหมายขีดฆ่าโดยใช้ GroupDocs.Annotation for Java, ตั้งแต่การตั้งค่าโครงการจนถึงการปรับประสิทธิภาพ.

## คำตอบอย่างรวดเร็ว
- **ขั้นตอนแรกคืออะไร?** Add the GroupDocs.Annotation Maven dependency to your `pom.xml`.  
- **ฉันจะสร้าง strikeout อย่างไร?** Instantiate `Annotator`, define `StrikeoutAnnotation` with points, set color/opacity, then call `addAnnotation`.  
- **ฉันสามารถเพิ่มความคิดเห็นได้หรือไม่?** Yes, attach a `Comment` object to the annotation for collaboration.  
- **ถ้าการทำเครื่องหมายอยู่ผิดตำแหน่งจะทำอย่างไร?** Adjust the coordinate points; PDF uses a bottom‑left origin system.  
- **มีขีดจำกัดขนาดเอกสารหรือไม่?** GroupDocs processes multi‑hundred‑page PDFs without loading the entire file into memory.

## “how to add strikeout” คืออะไรใน PDF annotation?
วลี “how to add strikeout” หมายถึงกระบวนการวาดเส้นผ่านข้อความที่เลือกภายในเอกสาร PDF อย่างอัตโนมัติโดยใช้ API ของการทำเครื่องหมาย. ใน Java, GroupDocs.Annotation มีคลาส `StrikeoutAnnotation` เฉพาะที่จัดการการเรนเดอร์, การสไตลิ่ง, และการเก็บรักษาเครื่องหมายขีดฆ่า.

## ทำไมต้องใช้ GroupDocs สำหรับ Java PDF Strikeout?
GroupDocs.Annotation supports **50+ input and output formats**—including PDF, DOCX, XLSX, PPTX, HTML, and common image types—so you’re not locked into a single file type. It provides a high‑level API that abstracts the low‑level PDF structure, automatically handling font embedding, page rendering, and annotation persistence, which lets developers focus on business logic rather than PDF internals.

## ข้อกำหนดเบื้องต้นและการตั้งค่า

### ข้อกำหนดสำคัญ
- **Java Development Kit (JDK):** Version 8 or later (JDK 11+ recommended for optimal garbage‑collection).  
- **GroupDocs.Annotation for Java:** Integrated via Maven (see the Maven snippet below).  
- **IDE:** IntelliJ IDEA, Eclipse, or any Java‑compatible editor.

### การตั้งค่า Maven Dependencies
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

### การจัดการใบอนุญาตของคุณ
GroupDocs.Annotation requires a valid license for production use. You have three options:

- **ทดลองใช้ฟรี:** Download from [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)
- **Temporary License:** Request a development key at [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Full License:** Purchase for production at [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

The trial adds a subtle watermark, so plan your testing accordingly.

## คู่มือการทำงานแบบขั้นตอนต่อขั้นตอน

### ทำความเข้าใจส่วนประกอบหลัก
The following definitions give you a quick mental model:

- **Annotator:** The primary API object that loads a PDF and exposes annotation methods.  
- **StrikeoutAnnotation:** Represents the visual strikeout line and its styling options.  
- **Point:** A coordinate pair (X, Y) that tells the library where the line starts and ends.  
- **Comment:** Optional text attached to an annotation for collaboration.

### ขั้นตอนที่ 1: การตั้งค่าเส้นทางไฟล์
Define the locations of your source PDF and the destination file. Incorrect paths are a common source of “File Not Found” errors.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Ensure the output directory exists and is writable; GroupDocs will not auto‑create missing folders.

### ขั้นตอนที่ 2: เริ่มต้น Annotator
Create an `Annotator` instance that loads the PDF into memory.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** The library parses the PDF structure, builds an internal representation, and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this step may take a few seconds.

### ขั้นตอนที่ 3: การเพิ่มความคิดเห็น (ไม่บังคับแต่แนะนำ)
`Comment` is a class that represents a textual note attached to an annotation, allowing collaborators to explain the reason for the strikeout.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Use comments to explain why text is being removed—this is especially useful in legal or editorial review workflows.

### ขั้นตอนที่ 4: กำหนดพิกัดการทำเครื่องหมาย
`Point` objects store X‑Y coordinate pairs that define the exact location of an annotation on a PDF page.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF coordinates start at the bottom‑left corner (0,0). The example creates a horizontal line from (80,730) to (240,730) on the target page.

**Finding the Right Coordinates:** Many developers create a helper that converts percentages of page width/height into absolute points, making the code resilient to different page sizes.

### ขั้นตอนที่ 5: สร้าง Strikeout Annotation
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

### ขั้นตอนที่ 6: ใช้ Annotation
`addAnnotation` is a method of the `Annotator` that registers the prepared annotation with the document so it will be rendered and saved.

```java
annotator.add(strikeout);
```

### ขั้นตอนที่ 7: บันทึกและทำความสะอาด
`dispose()` releases native resources held by the `Annotator` instance, preventing memory leaks after processing is complete.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Calling `dispose()` frees native resources and prevents memory leaks when processing batches of PDFs.

## ปัญหาทั่วไปและวิธีแก้ไข

### ปัญหา 1: ข้อผิดพลาด “File Not Found”
**Symptoms:** Exception thrown during `Annotator` construction.  
**Solution:** Verify both input and output paths, and confirm the application has read/write permissions.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### ปัญหา 2: Strikeout ปรากฏในตำแหน่งผิด
**Symptoms:** The line does not line up with the intended text.  
**Solution:** Remember that PDF Y‑coordinates increase upward. Use a visual debugging tool or print the page dimensions to fine‑tune the points.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### ปัญหา 3: Annotation ไม่แสดง
**Symptoms:** No strikeout shows up after saving.  
**Possible Causes & Fixes:**
- **Opacity too low:** Temporarily set opacity to `1.0` to verify visibility.  
- **Color blending:** Use a high‑contrast color like red (`255`).  
- **Incorrect page index:** Page numbers are zero‑based; ensure you target the correct page.

### ปัญหา 4: ปัญหา Memory กับไฟล์ขนาดใหญ่
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

## การใช้งานจริงและกรณีศึกษา

### การตรวจสอบเอกสารทางกฎหมาย
Law firms annotate contracts with strikeouts to indicate deleted clauses while preserving an audit trail.

### การแก้ไขเอกสารวิชาการ
Professors use strikeouts to suggest removals during peer review, keeping the original text visible for context.

### ระบบจัดการเนื้อหา
Publishing platforms automatically flag policy‑violating sections with strikeouts before manual moderation.

### การควบคุมเวอร์ชันสำหรับเอกสาร
Enterprises treat strikeout annotations as “deletion markers” in a document‑centric version‑control workflow, similar to code diffs.

## เคล็ดลับการปรับประสิทธิภาพ

### กลยุทธ์การประมวลผลเป็นชุด
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

### แนวทางปฏิบัติที่ดีที่สุดสำหรับการจัดการ Memory
- Call `dispose()` on every `Annotator`.  
- Limit concurrent document loads to avoid heap pressure.  
- Monitor JVM memory usage with tools like VisualVM.

### การแคชพิกัด
If you apply the same annotation layout across multiple files, cache the `Point` objects to avoid recomputation.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## ตัวเลือกการปรับแต่งขั้นสูง

### การเลือกสีแบบไดนามิก
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

### Strikeout หลายบรรทัด
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

## รายการตรวจสอบการแก้ไขปัญหา
1. **File Permissions:** Verify read/write access.  
2. **Library Version:** Ensure you’re using a supported GroupDocs.Annotation release.  
3. **License Status:** Confirm the license file is correctly referenced.  
4. **PDF Compatibility:** Check that the PDF is not corrupted and is within supported size limits.  
5. **Coordinate Validation:** Ensure all points lie inside page bounds.  
6. **Heap Space:** Increase JVM `-Xmx` if processing very large files.

## คำถามที่พบบ่อย

**Q: Can I strikeout text across multiple lines?**  
**A:** Yes. Create several `Point` objects that trace the desired path; the annotation will follow the supplied polyline.

**Q: What happens if I specify coordinates outside the page boundaries?**  
**A:** The annotation will be clipped and may become invisible. Always validate coordinates against the page’s width and height.

**Q: Can I remove strikeout annotations after adding them?**  
**A:** Absolutely. Use the `removeAnnotation` method with the annotation’s ID or filter by type to delete them programmatically.

**Q: Is there a limit to how many annotations I can add to a single PDF?**  
**A:** GroupDocs does not impose a hard cap, but performance may degrade after thousands of annotations. Consider pagination or summarizing annotations for very large sets.

**Q: How do I work with password‑protected PDFs?**  
**A:** Pass the password to the `Annotator` constructor. The library will decrypt the document in memory before applying any annotations.

**Q: How can I handle PDFs with different page sizes and orientations?**  
**A:** Retrieve each page’s dimensions via `annotator.getPageInfo(pageNumber)` and calculate coordinates relative to those dimensions to ensure consistent placement.

## สรุป
You now have a complete, production‑ready solution for **how to add strikeout** annotations to PDFs in Java using GroupDocs.Annotation. By mastering file‑path handling, coordinate calculation, and resource management, you can embed this capability into document review tools, content pipelines, or any Java‑based application that needs precise visual feedback.

**Next Steps**
1. Clone the example project and run it against a sample PDF.  
2. Experiment with different colors, opacities, and comment texts.  
3. Integrate the annotation workflow into your existing document‑processing service.  
4. Explore related annotation types—highlights, sticky notes, and shape annotations—to broaden your PDF manipulation toolkit.

Ready for more? Dive into the official documentation for deeper API insights.

## แหล่งข้อมูลเพิ่มเติม

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - เอกสารทั่วไปสำหรับไลบรารี GroupDocs  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - อ้างอิง API อย่างครบถ้วน  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - รายละเอียดเมธอดโดยละเอียด  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - รักษาไลบรารีให้เป็นเวอร์ชันล่าสุด  
- [Purchase License](https://purchase.groupdocs.com/buy) - การจัดการใบอนุญาตสำหรับการผลิต  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - ทดลองใช้ก่อนซื้อ  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - การทดสอบสำหรับการพัฒนา  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - ชุมชนช่วยเหลือและการสนับสนุนจากทีมงาน  

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Annotation 23.12 for Java  
**Author:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [เพิ่มการทำเครื่องหมาย PDF ด้วย Java – คู่มือครบถ้วนของ GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Tutorial การทำเครื่องหมาย PDF ด้วย Java - คู่มือเต็มสำหรับการไฮไลท์ PDF](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [วิธีเพิ่มลูกศรใน PDF ด้วย Java – คู่มือเต็มของ GroupDocs](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)