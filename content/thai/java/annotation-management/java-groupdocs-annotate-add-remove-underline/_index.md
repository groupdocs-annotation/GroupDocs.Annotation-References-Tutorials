---
categories:
- Java Development
date: '2026-03-24'
description: เรียนรู้วิธีสร้างไฟล์ PDF ด้วย Java อย่างสะอาด จัดการหน่วยความจำ PDF
  ของ Java และทำการอธิบาย (annotate) PDF ใน Java ด้วย GroupDocs.Annotation พร้อมตัวอย่างโค้ดเต็มและเคล็ดลับการแก้ปัญหา
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'สร้าง PDF ที่สะอาดด้วย Java: ขีดเส้นใต้คำอธิบายด้วย GroupDocs'
type: docs
url: /th/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# สร้าง Clean PDF Java: การใส่เส้นใต้ด้วย GroupDocs

หากคุณต้องการ **สร้าง Clean PDF Java** และเพิ่ม annotation ที่ทำงานร่วมกัน คุณมาถูกที่แล้ว คุณกำลังประสบปัญหาเรื่องการจัดการเอกสารและการทำงานร่วมกันในแอปพลิเคชัน Java ของคุณหรือไม่? คุณไม่ได้อยู่คนเดียว นักพัฒนาหลายคนเผชิญความท้าทายในการทำให้ฟีเจอร์ annotation ของเอกสารทำงานอย่างมั่นคงและรองรับหลายรูปแบบไฟล์

ในคู่มือนี้ คุณจะ **สร้าง Clean PDF Java** และเรียนรู้วิธี **annotate PDF in Java** ด้วย GroupDocs.Annotation เมื่อจบบทเรียนแล้ว คุณจะรู้วิธีเพิ่ม underline annotation พร้อมคอมเมนต์ การลบ annotation ที่มีอยู่ และการรวมฟีเจอร์เหล่านี้เข้าในโปรเจกต์ของคุณอย่างราบรื่น

**สิ่งที่คุณจะได้เรียนรู้ในคู่มือนี้:**
- การตั้งค่า GroupDocs.Annotation ในโปรเจกต์ Java ของคุณ (อย่างถูกต้อง)  
- การเพิ่ม underline annotation พร้อมคอมเมนต์และสไตล์ที่กำหนดเอง  
- การลบ annotation ทั้งหมดเพื่อสร้างเวอร์ชันเอกสารที่สะอาด  
- การแก้ไขปัญหาที่นักพัฒนามักเจอบ่อย  
- การเพิ่มประสิทธิภาพสำหรับแอปพลิเคชันในสภาพการผลิต  

ไม่ว่าคุณจะกำลังสร้างระบบตรวจสอบเอกสาร แพลตฟอร์มการศึกษา หรือเครื่องมือแก้ไขร่วมกัน คู่มือนี้มีตัวอย่างโค้ดที่ใช้งานได้จริงและผ่านการทดสอบแล้วให้คุณใช้ได้ทันที

## คำตอบสั้น
- **จะเพิ่ม underline annotation อย่างไร?** ใช้ `UnderlineAnnotation` และ `annotator.add()` แล้วบันทึกเอกสาร  
- **จะสร้าง Clean PDF Java อย่างไร?** โหลดไฟล์ที่มี annotation แล้วตั้งค่า `AnnotationType.NONE` ใน `SaveOptions` จากนั้นบันทึกเป็นไฟล์ใหม่  
- **ต้องใช้ไลบรารีอะไรบ้าง?** GroupDocs.Annotation v25.2 (หรือใหม่กว่า) พร้อม Maven repository  
- **ต้องมีลิขสิทธิ์สำหรับการผลิตหรือไม่?** ใช่ — ใส่ลิขสิทธิ์ GroupDocs ที่ถูกต้องเพื่อหลีกเลี่ยง watermark  
- **สามารถประมวลผลหลายเอกสารได้อย่างมีประสิทธิภาพหรือไม่?** ห่อ `Annotator` ทุกตัวในบล็อก `try‑with‑resources` แล้วทำการ dispose หลังจากแต่ละไฟล์เสร็จ  

## วิธีสร้าง Clean PDF Java
การสร้าง Clean PDF Java หมายถึงการสร้างเวอร์ชันของเอกสาร **โดยไม่มี annotation ใด ๆ** แต่ยังคงรักษาเนื้อหาเดิมไว้ ซึ่งเหมาะสำหรับการแจกจ่ายขั้นสุดท้าย การเก็บรักษา หรือเมื่อคุณต้องการแชร์สำเนา “สะอาด” หลังจากรอบการตรวจสอบ

GroupDocs.Annotation ทำให้ขั้นตอนนี้ง่ายดาย: โหลดไฟล์ที่มี annotation ตั้งค่า `SaveOptions` ให้ไม่รวม annotation ทั้งหมด แล้วบันทึกผลลัพธ์ ขั้นตอนเหล่านี้จะอธิบายต่อในส่วน **Removing Annotations**

## ทำไมต้องสร้าง Clean PDF Java?
เวอร์ชันที่สะอาดจะลบเครื่องหมายของผู้ตรวจสอบ คอมเมนต์ และไฮไลท์ ทำให้เอกสารดูเป็นมืออาชีพพร้อมส่งให้ลูกค้า หน่วยงานกำกับ หรือสาธารณะ อีกทั้งยังลดขนาดไฟล์และป้องกันการเปิดเผยบันทึกภายในโดยบังเอิญ — สิ่งสำคัญสำหรับกระบวนการทางกฎหมายและการปฏิบัติตามข้อกำหนด

## วิธี annotate PDF in Java ด้วย GroupDocs
GroupDocs.Annotation มี API ที่ครอบคลุมสำหรับ **annotate PDF in Java** รองรับประเภท annotation หลากหลาย รวมถึง highlight, stamp, และ underline ในบทเรียนนี้เราจะเน้นที่ underline annotation เนื่องจากมักใช้เพื่อเน้นข้อความพร้อมให้คอมเมนต์แบบเธรด

## ข้อกำหนดเบื้องต้นและการตั้งค่าสภาพแวดล้อม

### สิ่งที่คุณต้องเตรียมก่อนเริ่ม

**ความต้องการของสภาพแวดล้อมการพัฒนา:**
- Java Development Kit (JDK) 8 หรือสูงกว่า (แนะนำ JDK 11+)  
- Maven 3.6+ หรือ Gradle 6.0+ สำหรับจัดการ dependency  
- IDE เช่น IntelliJ IDEA, Eclipse หรือ VS Code พร้อมส่วนขยาย Java  
- RAM อย่างน้อย 2 GB (การประมวลผลเอกสารอาจใช้หน่วยความจำมาก)

**ความรู้พื้นฐานที่จำเป็น:**
คุณควรคุ้นเคยกับแนวคิดพื้นฐานของ Java — การสร้างอ็อบเจกต์ การเรียกเมธอด และการจัดการ Maven ประสบการณ์กับไลบรารีของบุคคลที่สามจะช่วยให้เริ่มต้นได้เร็วขึ้น

**เอกสารทดสอบ:**
เตรียม PDF ตัวอย่างหลายไฟล์ไว้ Text‑based PDFs ทำงานได้ดีที่สุด; ภาพสแกนอาจต้องใช้ OCR ก่อนทำ annotation

### การตั้งค่า Maven: นำ GroupDocs เข้าโปรเจกต์ของคุณ

นี่คือวิธีตั้งค่า Maven อย่างถูกต้อง (หลายคนมักทำผิดในครั้งแรก):

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

**สำคัญ:** เวอร์ชัน 25.2 เป็นรุ่นเสถียรล่าสุด ณ เวลาที่เขียนบทความ ตรวจสอบ repository ของ GroupDocs อย่างสม่ำเสมอเพื่ออัปเดตเวอร์ชันที่มีการแก้บั๊กและปรับปรุงประสิทธิภาพ

### การตั้งค่าลิขสิทธิ์ (ห้ามข้าม)

**สำหรับการพัฒนา/ทดสอบ:**  
ดาวน์โหลด trial ฟรีจากเว็บไซต์ GroupDocs trial มีฟีเจอร์ครบ แต่จะใส่ watermark ลงในเอกสารที่ประมวลผล

**สำหรับการผลิต:**  
ซื้อ license และใส่ในขั้นตอนเริ่มต้นของแอปพลิเคชัน หากไม่มี license ที่ถูกต้อง การสร้างในสภาพการผลิตจะถูกจำกัด

## คู่มือการทำงาน: การเพิ่ม Underline Annotation

### ทำความเข้าใจ Workflow ของ Annotation

ก่อนจะลงมือเขียนโค้ด เรามาดู workflow สี่ขั้นตอนที่เกิดขึ้นเมื่อคุณ **annotate PDF in Java**:

1. **Document Loading** – `Annotator` อ่านไฟล์เข้าสู่หน่วยความจำ  
2. **Annotation Creation** – กำหนดคุณสมบัติต่าง ๆ เช่น ตำแหน่ง สไตล์ และคอมเมนต์  
3. **Annotation Application** – ไลบรารีแทรก annotation ลงในโครงสร้าง PDF  
4. **Document Saving** – บันทึกไฟล์ที่แก้ไขแล้ว โดยอาจเก็บไฟล์ต้นฉบับไว้

กระบวนการนี้ไม่ทำลายไฟล์ต้นฉบับ; ไฟล์เดิมจะไม่ถูกเปลี่ยนแปลงหากคุณไม่ได้บันทึกทับ

### ขั้นตอนที่ 1: เริ่มต้น Annotator และโหลดเอกสารของคุณ

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**เคล็ดลับ:** ใช้ path แบบ absolute ระหว่างพัฒนาเพื่อหลีกเลี่ยงข้อผิดพลาด “file not found” ในสภาพการผลิต ควรโหลดทรัพยากรจาก classpath หรือคลังเก็บบนคลาวด์

### ขั้นตอนที่ 2: สร้างคอมเมนต์และ Reply (ส่วนของการทำงานร่วมกัน)

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

**การใช้งานจริง:** ผู้ตรวจสอบสามารถสนทนารอบข้อกำหนดเฉพาะโดยเพิ่ม reply แบบเธรด ทำให้การสนทนาติดอยู่กับ annotation นั้น ๆ

### ขั้นตอนที่ 3: กำหนดพิกัดของ Annotation (ตำแหน่งที่แม่นยำ)

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

**ระบบพิกัด:**  
- จุด 1 และ 2 กำหนดขอบบนของเส้นใต้  
- จุด 3 และ 4 กำหนดขอบล่าง  
- ความแตกต่างของค่า Y (730 vs 650) ควบคุมความหนา

### ขั้นตอนที่ 4: สร้างและตั้งค่า Underline Annotation

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

**เคล็ดลับเรื่องสีและความโปร่งใส:**  
- `FontColor` ใช้ ARGB; ค่า `65535` (0x00FFFF) ให้สีเหลืองสดใส  
- สำหรับสีแดงใช้ `16711680` (0xFF0000); สีน้ำเงินใช้ `255` (0x0000FF)  
- ค่า Opacity ระหว่าง 0.5 และ 0.8 ให้ความอ่านง่ายโดยไม่บังข้อความ

### ขั้นตอนที่ 5: บันทึกเอกสารที่มี Annotation

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**การจัดการหน่วยความจำ:** การเรียก `dispose()` ปล่อยทรัพยากรเนทีฟและป้องกัน memory leak — สิ่งสำคัญเมื่อประมวลผลไฟล์จำนวนมากเป็น batch

## การลบ Annotation: สร้างเวอร์ชันเอกสารที่สะอาด

บางครั้งคุณต้องการ PDF **โดยไม่มี annotation ใด ๆ** เช่น เมื่อส่งสัญญาที่ได้รับการอนุมัติขั้นสุดท้าย GroupDocs ทำให้ขั้นตอนนี้ง่ายดาย

### ทำความเข้าใจตัวเลือกการลบ Annotation

คุณสามารถ:
- ลบ **ทั้งหมด** (เป็นวิธีที่นิยมที่สุด)  
- ลบเฉพาะประเภทบางอย่าง (เช่น highlight เท่านั้น)  
- ลบตามผู้เขียนหรือหน้าที่ระบุ  

### ขั้นตอนการลบ Annotation ทีละขั้นตอน

**ขั้นตอน 1: โหลดเอกสารที่เคยมี Annotation**

```java
Annotator annotator = new Annotator(outputPath);
```

**ขั้นตอน 2: ตั้งค่า Save Options สำหรับผลลัพธ์ที่สะอาด**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**ขั้นตอน 3: บันทึกเวอร์ชันสะอาด**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

ผลลัพธ์คือ **Clean PDF Java** ที่ไม่มีวัตถุ annotation ใด ๆ เหมาะสำหรับการแจกจ่ายขั้นสุดท้าย

## ปัญหาที่พบบ่อยและวิธีแก้

### ปัญหา 1: ข้อผิดพลาด “Document not found”

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

### ปัญหา 2: Annotation ปรากฏในตำแหน่งผิด

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### ปัญหา 3: ปัญหาหน่วยความจำกับเอกสารขนาดใหญ่

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### ปัญหา 4: ปัญหาลิขสิทธิ์ในสภาพการผลิต

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

## แนวทางปฏิบัติที่ดีที่สุดสำหรับประสิทธิภาพใน Production

### กลยุทธ์การจัดการหน่วยความจำ

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

### พิจารณาการทำงานหลายเธรด

GroupDocs.Annotation **ไม่ปลอดภัยต่อหลายเธรด** โดยค่าเริ่มต้น หากแอปของคุณประมวลผลเอกสารพร้อมกัน:

- **ห้ามแชร์** อินสแตนซ์ `Annotator` ข้ามเธรด  
- **ซิงโครไนซ์** การเข้าถึงไฟล์หรือใช้กลไก lock  
- พิจารณา **pool** ของอ็อบเจกต์ `Annotator` หากต้องการ throughput สูง

### กลยุทธ์การแคช

- แคชเทมเพลต annotation ที่ใช้บ่อย  
- รีใช้คอลเลกชัน `Point` สำหรับพิกัดที่ใช้ซ้ำบ่อย  
- เก็บ **template PDF** ไว้ในหน่วยความจำหากต้อง annotate เอกสารฐานเดียวกันหลายครั้ง

## เคล็ดลับการจัดการหน่วยความจำสำหรับ Java PDF
การใช้หน่วยความจำอย่างมีประสิทธิภาพเป็นสิ่งจำเป็นเมื่อจัดการ PDF ขนาดใหญ่หรือประมวลผลหลายไฟล์เป็น batch คำแนะนำที่ใช้งานได้จริง:

- **ใช้ try‑with‑resources** สำหรับทุก `Annotator` เพื่อรับประกันการ dispose  
- **เพิ่ม heap ของ JVM** (`-Xmx`) ตามความจำเป็น; ตรวจสอบการใช้ด้วยเครื่องมือ profiling  
- **ประมวลผลไฟล์ต่อเนื่อง** เมื่อทำได้, ปล่อยหน่วยความจำหลังจากแต่ละไฟล์เสร็จ  
- **หลีกเลี่ยงการโหลด PDF เดียวกันหลายครั้ง**; ใช้ stream เดียวกันหากต้องอ่านซ้ำ

การปฏิบัติตามแนวทางเหล่านี้ช่วยให้แอปของคุณตอบสนองได้ดีและป้องกันการ crash จาก out‑of‑memory ในงาน annotation หนัก ๆ

## การใช้งานจริงและกรณีศึกษา

### ระบบตรวจสอบเอกสาร

- **การตรวจสอบกฎหมาย:** ใต้เส้นข้อสัญญาและเพิ่มคอมเมนต์เกี่ยวกับความเสี่ยง  
- **การตรวจสอบการปฏิบัติตาม:** ไฮไลท์ส่วนที่เป็นปัญหาในงบการเงิน  
- **การตรวจสอบวิชาการ:** อาจารย์ใส่เส้นใต้ข้อความที่ต้องการคำอธิบายเพิ่มเติม

### แพลตฟอร์มการศึกษา

- **เครื่องมือ Annotation ของนักเรียน:** ให้นักเรียนใส่เส้นใต้แนวคิดสำคัญใน e‑book  
- **ฟีดแบ็คของครู:** ให้คอมเมนต์แบบอินไลน์บนงานที่ส่ง

### กระบวนการประกันคุณภาพ

- **การตรวจสอบเอกสารเทคนิค:** วิศวกรใส่เส้นใต้ส่วนที่ต้องอัปเดต  
- **ขั้นตอนการปฏิบัติงานมาตรฐาน:** เจ้าหน้าที่ความปลอดภัยไฮไลท์ขั้นตอนสำคัญ

### ระบบจัดการเนื้อหา (CMS)

- **เวิร์กโฟลว์บรรณาธิการ:** บรรณาธิการใส่เส้นใต้ข้อความที่ต้องตรวจสอบข้อเท็จจริง  
- **การควบคุมเวอร์ชัน:** ติดตามประวัติ annotation ข้ามการปรับปรุงเอกสาร

## เคล็ดลับขั้นสูงสำหรับการใช้งานระดับมืออาชีพ

### สไตล์ Annotation แบบกำหนดเอง

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Metadata ของ Annotation สำหรับการติดตาม

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### การรวมกับระบบจัดการผู้ใช้

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

## การแก้ไขปัญหาใน Production

### การตรวจสอบประสิทธิภาพ

ตรวจสอบเมตริกเหล่านี้ใน Production:
- **การใช้ Heap** – ตรวจสอบให้แน่ใจว่าเรียก `dispose()` แล้ว  
- **เวลาในการประมวลผลต่อเอกสาร** – บันทึก timestamp ก่อน/หลัง `annotator.save()`  
- **อัตราเกิดข้อผิดพลาด** – เก็บ exception และจัดหมวดหมู่

### ปัญหาที่พบบ่อยใน Production

- **File locking** – ตรวจสอบให้ไฟล์ที่อัปโหลดถูกปิดก่อนทำ annotation  
- **การแก้ไขพร้อมกัน** – ใช้ optimistic locking หรือเช็คเวอร์ชัน  
- **ไฟล์ขนาดใหญ่ (> 50 MB)** – เพิ่ม timeout ของ JVM และพิจารณา API แบบ streaming

### แนวทางการจัดการข้อผิดพลาดที่ดีที่สุด

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

## สรุป

ตอนนี้คุณมีทุกอย่างที่จำเป็นเพื่อ **สร้าง Clean PDF Java** และ **annotate PDF in Java** ด้วย underline annotation ผ่าน GroupDocs.Annotation จำไว้ว่า:

- จัดการทรัพยากรด้วย try‑with‑resources หรือเรียก `dispose()` อย่างชัดเจน  
- ตรวจสอบพิกัดล่วงหน้าเพื่อหลีกเลี่ยงเส้นใต้ที่วางผิดตำแหน่ง  
- ใช้การจัดการข้อผิดพลาดที่แข็งแรงสำหรับความเสถียรใน Production  
- ใช้สไตล์และ metadata ตามบทบาทเพื่อให้สอดคล้องกับเวิร์กโฟลว์ของคุณ  

ขั้นตอนต่อไป? ลองเพิ่มประเภท annotation อื่น ๆ — highlight, stamp, หรือการแทนที่ข้อความ — เพื่อสร้างโซลูชันการตรวจสอบเอกสารที่ครบวงจร

## คำถามที่พบบ่อย

**ถาม: จะทำ annotation หลายส่วนของข้อความในครั้งเดียวอย่างไร?**  
ตอบ: สร้างหลายอ็อบเจกต์ `UnderlineAnnotation` ที่มีพิกัดต่างกัน แล้วเพิ่มลงใน `annotator.add()` ทีละอัน

**ถาม: สามารถ annotate รูปภาพภายใน PDF ได้หรือไม่?**  
ตอบ: ได้ ใช้ระบบพิกัดเดียวกัน ตรวจสอบให้จุดอยู่ภายในขอบเขตของรูปภาพ

**ถาม: GroupDocs.Annotation รองรับไฟล์ฟอร์แมตอื่น ๆ นอกจาก PDF หรือไม่?**  
ตอบ: รองรับ Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) และรูปภาพเช่น JPEG, PNG, TIFF

**ถาม: จะจัดการกับเอกสารขนาดใหญ่อย่างไรโดยไม่ให้หน่วยความจำหมด?**  
ตอบ: ประมวลผลไฟล์ทีละไฟล์, เพิ่ม heap ของ JVM (`-Xmx`), และทำการ dispose `Annotator` ทันทีหลังใช้งาน

**ถาม: สามารถดึง annotation ที่มีอยู่จากเอกสารได้หรือไม่?**  
ตอบ: ได้ ใช้ `annotator.get()` เพื่อดึง annotation ทั้งหมด แล้วกรองตามประเภท, ผู้เขียน, หรือหน้าได้ตามต้องการ

---

**อัปเดตล่าสุด:** 2026-03-24  
**ทดสอบกับ:** GroupDocs.Annotation 25.2  
**ผู้เขียน:** GroupDocs