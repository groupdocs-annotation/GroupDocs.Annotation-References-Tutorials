---
categories:
- Java Development
date: '2025-12-21'
description: เรียนรู้วิธีสร้างไฟล์ PDF Java ที่สะอาดและทำการอธิบาย PDF ใน Java ด้วย
  GroupDocs.Annotation พร้อมตัวอย่างโค้ดเต็มและเคล็ดลับการแก้ปัญหา
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
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

# สร้างไฟล์ PDF Java ที่สะอาด: การทำขีดเส้นใต้ด้วย GroupDocs

## บทนำ

กำลังประสบปัญหาในการจัดการเอกสารและการทำงานร่วมกันในแอปพลิเคชัน Java ของคุณหรือไม่? คุณไม่ได้อยู่คนเดียว นักพัฒนาจำนวนมากเผชิญกับความท้าทายในการนำคุณลักษณะการทำหมายเหตุเอกสารที่แข็งแรงซึ่งทำงานได้อย่างเชื่อถือได้ในหลายรูปแบบไฟล์

ในคู่มือนี้ คุณจะ **สร้างไฟล์ PDF Java ที่สะอาด** และเรียนรู้วิธี **ทำหมายเหตุ PDF ใน Java** ด้วย GroupDocs.Annotation เมื่อจบการสอนนี้ คุณจะรู้วิธีเพิ่มขีดเส้นใต้พร้อมคอมเมนต์, ลบหมายเหตุที่มีอยู่, และรวมคุณลักษณะเหล่านี้เข้าไปในโครงการของคุณอย่างไร้รอยต่อ

**สิ่งที่คุณจะเชี่ยวชาญในคู่มือนี้:**
- ตั้งค่า GroupDocs.Annotation ในโครงการ Java ของคุณ (วิธีที่ถูกต้อง)  
- เพิ่มขีดเส้นใต้พร้อมคอมเมนต์และการจัดรูปแบบที่กำหนดเอง  
- ลบหมายเหตุทั้งหมดเพื่อสร้างเวอร์ชันเอกสารที่สะอาด  
- แก้ไขปัญหาที่พบบ่อยที่นักพัฒนาพบ  
- เพิ่มประสิทธิภาพการทำงานสำหรับแอปพลิเคชันในสภาพการผลิต  

ไม่ว่าคุณจะกำลังสร้างระบบตรวจสอบเอกสาร, แพลตฟอร์มการศึกษา, หรือเครื่องมือแก้ไขร่วมกัน คู่มือนี้มีตัวอย่างโค้ดที่ใช้งานได้จริงและผ่านการทดสอบเพื่อช่วยคุณ

## คำตอบอย่างรวดเร็ว
- **ฉันจะเพิ่มขีดเส้นใต้ได้อย่างไร?** ใช้ `UnderlineAnnotation` และ `annotator.add()` จากนั้นบันทึกเอกสาร.  
- **ฉันจะสร้างไฟล์ PDF Java ที่สะอาดได้อย่างไร?** โหลดไฟล์ที่มีหมายเหตุ, ตั้งค่า `AnnotationType.NONE` ใน `SaveOptions`, แล้วบันทึกเป็นสำเนาใหม่.  
- **ต้องใช้ไลบรารีอะไรบ้าง?** GroupDocs.Annotation v25.2 (หรือใหม่กว่า) และ Maven repository ของมัน.  
- **ต้องใช้ไลเซนส์สำหรับการผลิตหรือไม่?** ใช่—ใช้ไลเซนส์ GroupDocs ที่ถูกต้องเพื่อหลีกเลี่ยงลายน้ำ.  
- **ฉันสามารถประมวลผลหลายเอกสารได้อย่างมีประสิทธิภาพหรือไม่?** ห่อ `Annotator` แต่ละตัวในบล็อก try‑with‑resources และทำการ dispose หลังจากแต่ละไฟล์.

## วิธีสร้างไฟล์ PDF Java ที่สะอาด
การสร้างไฟล์ PDF Java ที่สะอาดหมายถึงการสร้างเวอร์ชันของเอกสาร **โดยไม่มีหมายเหตุใด ๆ** พร้อมคงเนื้อหาต้นฉบับไว้ นี่มีประโยชน์สำหรับการแจกจ่ายขั้นสุดท้าย, การเก็บถาวร, หรือเมื่อคุณต้องการแชร์สำเนา “สะอาด” หลังจากรอบการตรวจสอบ

GroupDocs.Annotation ทำให้ขั้นตอนนี้ง่ายดาย: โหลดไฟล์ที่มีหมายเหตุ, ตั้งค่า `SaveOptions` เพื่อไม่รวมประเภทหมายเหตุใด ๆ, แล้วบันทึกผลลัพธ์ ขั้นตอนจะถูกอธิบายในส่วน **Removing Annotations** ต่อไป

## วิธีทำหมายเหตุ PDF ใน Java ด้วย GroupDocs
GroupDocs.Annotation มี API ที่ครอบคลุมสำหรับ **ทำหมายเหตุ PDF ใน Java** รองรับประเภทหมายเหตุหลากหลาย รวมถึงไฮไลท์, แสตมป์, และขีดเส้นใต้ ในบทเรียนนี้เราจะเน้นที่ขีดเส้นใต้เนื่องจากมักใช้เพื่อเน้นข้อความพร้อมให้คอมเมนต์แบบเธรด

## ข้อกำหนดเบื้องต้นและการตั้งค่าสภาพแวดล้อม

### สิ่งที่คุณต้องการก่อนเริ่ม

**Development Environment Requirements:**
- Java Development Kit (JDK) 8 หรือสูงกว่า (แนะนำ JDK 11+)
- Maven 3.6+ หรือ Gradle 6.0+ สำหรับการจัดการ dependencies
- IDE เช่น IntelliJ IDEA, Eclipse, หรือ VS Code พร้อมส่วนขยาย Java
- RAM ว่างอย่างน้อย 2 GB (การประมวลผลเอกสารอาจใช้หน่วยความจำมาก)

**Knowledge Prerequisites:**  
คุณควรคุ้นเคยกับแนวคิดพื้นฐานของ Java—การสร้างอ็อบเจ็กต์, การเรียกเมธอด, และ dependencies ของ Maven ประสบการณ์กับไลบรารีของบุคคลที่สามจะช่วยให้การนำไปใช้เร็วขึ้น

**Testing Documents:**  
เตรียมไฟล์ PDF ตัวอย่างหลายไฟล์ไว้ Text‑based PDFs ทำงานได้ดีที่สุด; ภาพสแกนอาจต้องใช้ OCR ก่อนทำหมายเหตุ

### การตั้งค่า Maven: นำ GroupDocs เข้าสู่โครงการของคุณ

นี่คือวิธีการกำหนดค่า Maven โปรเจกต์ของคุณอย่างถูกต้อง (หลายคนมักทำผิดในครั้งแรก):

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

**สำคัญ:** เวอร์ชัน 25.2 เป็นรุ่นเสถียรล่าสุดในขณะเขียนบทความ ตรวจสอบ Repository ของ GroupDocs อย่างสม่ำเสมอเพื่อหาเวอร์ชันใหม่ที่มีการแก้บั๊กและปรับปรุงประสิทธิภาพ

### การตั้งค่าไลเซนส์ (ห้ามข้ามขั้นตอนนี้)

**สำหรับการพัฒนา/ทดสอบ:**  
ดาวน์โหลดเวอร์ชันทดลองฟรีจากเว็บไซต์ GroupDocs เวอร์ชันทดลองมีคุณสมบัติครบ แต่จะใส่ลายน้ำในเอกสารที่ประมวลผล

**สำหรับการผลิต:**  
ซื้อไลเซนส์และนำไปใช้ในขั้นตอนเริ่มต้นของแอปพลิเคชัน หากไม่มีไลเซนส์ที่ถูกต้อง การสร้างในสภาพการผลิตจะถูกจำกัด

## คู่มือการดำเนินการ: การเพิ่มขีดเส้นใต้

### ทำความเข้าใจกระบวนการทำหมายเหตุ

ก่อนที่เราจะลงลึกในโค้ด ให้เราดูกระบวนการสี่ขั้นตอนที่เกิดขึ้นเมื่อคุณ **ทำหมายเหตุ PDF ใน Java**:

1. **การโหลดเอกสาร** – `Annotator` อ่านไฟล์เข้าสู่หน่วยความจำ.  
2. **การสร้างหมายเหตุ** – กำหนดคุณสมบัติเช่น ตำแหน่ง, สไตล์, และคอมเมนต์.  
3. **การประยุกต์หมายเหตุ** – ไลบรารีแทรกหมายเหตุเข้าไปในโครงสร้างของ PDF.  
4. **การบันทึกเอกสาร** – บันทึกไฟล์ที่แก้ไข, สามารถเก็บไฟล์ต้นฉบับไว้ได้.

กระบวนการนี้ไม่ทำลายไฟล์ต้นฉบับ; ไฟล์ต้นทางจะไม่ถูกแก้ไข เว้นแต่คุณจะบันทึกทับ

### ขั้นตอนที่ 1: เริ่มต้น Annotator และโหลดเอกสารของคุณ

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**เคล็ดลับ:** ใช้เส้นทางแบบ absolute ระหว่างการพัฒนาเพื่อหลีกเลี่ยงข้อผิดพลาด “file not found”. ในการผลิต ควรโหลดทรัพยากรจาก classpath หรือ bucket ของคลาวด์

### ขั้นตอนที่ 2: สร้างคอมเมนต์และการตอบกลับ (ส่วนของการทำงานร่วมกัน)

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

**การใช้งานจริง:** ผู้ตรวจสอบสามารถอภิปรายข้อกำหนดเฉพาะโดยเพิ่มการตอบกลับแบบเธรด, ทำให้การสนทนาติดกับหมายเหตุที่ตรงกัน

### ขั้นตอนที่ 3: กำหนดพิกัดของหมายเหตุ (การตั้งตำแหน่งให้ถูกต้อง)

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
- จุด 1 และ 2 กำหนดขอบบนของขีดเส้นใต้.  
- จุด 3 และ 4 กำหนดขอบล่าง.  
- ความแตกต่างของค่า Y (730 vs 650) ควบคุมความหนา.

### ขั้นตอนที่ 4: สร้างและกำหนดค่าขีดเส้นใต้

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

**เคล็ดลับสีและความทึบ:**  
- `FontColor` ใช้ ARGB; `65535` (0x00FFFF) ให้สีเหลืองสว่าง.  
- สำหรับสีแดง ใช้ `16711680` (0xFF0000); สำหรับสีน้ำเงิน ใช้ `255` (0x0000FF).  
- ค่า Opacity ระหว่าง 0.5 และ 0.8 ให้ความอ่านที่ดีโดยไม่บังข้อความ.

### ขั้นตอนที่ 5: บันทึกเอกสารที่ทำหมายเหตุแล้ว

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**การจัดการหน่วยความจำ:** การเรียก `dispose()` ปล่อยทรัพยากรเนทีฟและป้องกันการรั่วไหลของหน่วยความจำ—สำคัญเมื่อประมวลผลไฟล์จำนวนมากเป็นชุด

## การลบหมายเหตุ: การสร้างเวอร์ชันเอกสารที่สะอาด

บางครั้งคุณต้องการเวอร์ชันของ PDF **โดยไม่มีหมายเหตุใด ๆ** — เช่น เมื่อส่งสัญญาที่ได้รับการอนุมัติขั้นสุดท้าย GroupDocs ทำให้เรื่องนี้ง่าย

### ทำความเข้าใจตัวเลือกการลบหมายเหตุ

คุณสามารถ:
- ลบ **ทั้งหมด** ของหมายเหตุ (เป็นที่นิยมที่สุด)  
- ลบประเภทเฉพาะ (เช่น ไฮไลท์เท่านั้น)  
- ลบหมายเหตุตามผู้เขียนหรือหน้าที่

### ขั้นตอนการลบหมายเหตุแบบทีละขั้นตอน

**ขั้นตอน 1: โหลดไฟล์ที่เคยทำหมายเหตุแล้ว**

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

**ขั้นตอน 3: บันทึกเวอร์ชันที่สะอาด**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

นี่จะสร้างไฟล์ **PDF Java ที่สะอาด** ที่ไม่มีวัตถุหมายเหตุใด ๆ เหมาะสำหรับการแจกจ่ายขั้นสุดท้าย

## ปัญหาทั่วไปและวิธีแก้

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

### ปัญหา 2: หมายเหตุปรากฏในตำแหน่งผิด

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

### ปัญหา 4: ปัญหาไลเซนส์ในสภาพการผลิต

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

## แนวทางปฏิบัติที่ดีที่สุดสำหรับประสิทธิภาพในแอปพลิเคชันการผลิต

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

GroupDocs.Annotation **ไม่ปลอดภัยต่อการทำงานหลายเธรด** โดยค่าเริ่มต้น หากแอปพลิเคชันของคุณประมวลผลเอกสารพร้อมกัน:

- **ห้ามแชร์** อินสแตนซ์ `Annotator` ข้ามเธรด.  
- **ซิงโครไนซ์** การเข้าถึงไฟล์หรือใช้กลไกล็อก.  
- พิจารณา **pool** ของอ็อบเจ็กต์ `Annotator` หากต้องการ throughput สูง.

### กลยุทธ์การแคช

- แคชเทมเพลตหมายเหตุที่ใช้บ่อย.  
- นำ `Point` collections มาใช้ซ้ำสำหรับชุดพิกัดทั่วไป.  
- เก็บ **PDF เทมเพลต** ในหน่วยความจำหากคุณทำหมายเหตุซ้ำบนเอกสารฐานเดียวกัน.

## การใช้งานจริงและกรณีศึกษา

### ระบบตรวจสอบเอกสาร

- **การตรวจสอบทางกฎหมาย:** ขีดเส้นใต้ข้อสัญญาและเพิ่มคอมเมนต์เกี่ยวกับความเสี่ยง.  
- **การตรวจสอบการปฏิบัติตาม:** ไฮไลท์ส่วนที่มีปัญหาในงบการเงิน.  
- **การตรวจสอบทางวิชาการ:** อาจารย์ขีดเส้นใต้ข้อความที่ต้องการคำอธิบายเพิ่มเติม.

### แพลตฟอร์มการศึกษา

- **เครื่องมือทำหมายเหตุของนักเรียน:** ให้นักเรียนขีดเส้นใต้แนวคิดสำคัญใน e‑books.  
- **ฟีดแบ็กของครู:** ให้คอมเมนต์แบบอินไลน์โดยตรงบนงานที่ส่ง.

### กระบวนการประกันคุณภาพ

- **การตรวจสอบเอกสารเทคนิค:** วิศวกรขีดเส้นใต้ส่วนที่ต้องอัปเดต.  
- **ขั้นตอนการปฏิบัติงานมาตรฐาน:** เจ้าหน้าที่ความปลอดภัยไฮไลท์ขั้นตอนสำคัญ.

### ระบบจัดการเนื้อหา

- **กระบวนการบรรณาธิการ:** บรรณาธิการขีดเส้นใต้ข้อความที่ต้องตรวจสอบความถูกต้อง.  
- **การควบคุมเวอร์ชัน:** ติดตามประวัติหมายเหตุระหว่างการแก้ไขเอกสาร.

## เคล็ดลับขั้นสูงสำหรับการนำไปใช้ระดับมืออาชีพ

### สไตล์หมายเหตุแบบกำหนดเอง

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### เมทาดาต้าของหมายเหตุสำหรับการติดตาม

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

## การแก้ไขปัญหาในสภาพการผลิต

### การตรวจสอบประสิทธิภาพ

ตรวจสอบเมตริกเหล่านี้ในสภาพการผลิต:
- **การใช้ Heap** – ตรวจสอบว่าได้เรียก `dispose()` แล้ว.  
- **เวลาในการประมวลผลต่อเอกสาร** – บันทึก timestamp ก่อนและหลัง `annotator.save()`.  
- **อัตราข้อผิดพลาด** – เก็บ exception และจัดประเภท.

### ปัญหาที่พบบ่อยในสภาพการผลิต

- **การล็อกไฟล์** – ตรวจสอบว่าไฟล์ที่อัปโหลดถูกปิดก่อนทำหมายเหตุ.  
- **การแก้ไขพร้อมกัน** – ใช้ optimistic locking หรือการตรวจสอบเวอร์ชัน.  
- **ไฟล์ขนาดใหญ่ (> 50 MB)** – เพิ่ม timeout ของ JVM และพิจารณา API แบบสตรีม.

### แนวทางปฏิบัติที่ดีที่สุดสำหรับการจัดการข้อผิดพลาด

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

ตอนนี้คุณมีทุกอย่างที่จำเป็นเพื่อ **สร้างไฟล์ PDF Java ที่สะอาด** และ **ทำหมายเหตุ PDF ใน Java** ด้วยขีดเส้นใต้โดยใช้ GroupDocs.Annotation จำไว้ว่า:

- จัดการทรัพยากรด้วย try‑with‑resources หรือเรียก `dispose()` อย่างชัดเจน.  
- ตรวจสอบพิกัดตั้งแต่แรกเพื่อหลีกเลี่ยงขีดเส้นใต้ที่ผิดตำแหน่ง.  
- ใช้การจัดการข้อผิดพลาดที่แข็งแรงเพื่อความเสถียรในการผลิต.  
- ใช้สไตล์ตามบทบาทและเมทาดาต้าให้สอดคล้องกับกระบวนการทำงานของคุณ.

ขั้นตอนต่อไป? ลองเพิ่มประเภทหมายเหตุอื่น ๆ — ไฮไลท์, แสตมป์, หรือการแทนที่ข้อความ — เพื่อสร้างโซลูชันการตรวจสอบเอกสารที่ครบถ้วน

## คำถามที่พบบ่อย

**ถาม: ฉันจะทำหมายเหตุหลายส่วนของข้อความในหนึ่งการดำเนินการได้อย่างไร?**  
**ตอบ:** สร้างอ็อบเจ็กต์ `UnderlineAnnotation` หลายตัวโดยใช้พิกัดต่างกันและเพิ่มเข้าไปต่อเนื่องด้วย `annotator.add()`.

**ถาม: ฉันสามารถทำหมายเหตุบนรูปภาพภายในเอกสาร PDF ได้หรือไม่?**  
**ตอบ:** ได้ ใช้ระบบพิกัดเดียวกัน โดยต้องแน่ใจว่าจุดอยู่ภายในขอบเขตของรูปภาพ.

**ถาม: GroupDocs.Annotation รองรับรูปแบบไฟล์ใดบ้างนอกจาก PDF?**  
**ตอบ:** Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) และรูปภาพเช่น JPEG, PNG, TIFF.

**ถาม: ฉันจะจัดการกับเอกสารขนาดใหญ่มากโดยไม่เกิดการหมดหน่วยความจำได้อย่างไร?**  
**ตอบ:** ประมวลผลเอกสารทีละไฟล์, เพิ่มขนาด heap ของ JVM (`-Xmx`), และทำการ dispose อินสแตนซ์ `Annotator` อย่างทันท่วงที.

**ถาม: สามารถดึงหมายเหตุที่มีอยู่จากเอกสารได้หรือไม่?**  
**ตอบ:** ได้ ใช้ `annotator.get()` เพื่อดึงหมายเหตุทั้งหมด, แล้วกรองตามประเภท, ผู้เขียน, หรือหน้า ตามต้องการ.

**อัปเดตล่าสุด:** 2025-12-21  
**ทดสอบด้วย:** GroupDocs.Annotation 25.2  
**ผู้เขียน:** GroupDocs