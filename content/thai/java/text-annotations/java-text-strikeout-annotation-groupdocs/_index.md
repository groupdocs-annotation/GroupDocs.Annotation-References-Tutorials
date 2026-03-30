---
categories:
- Java Development
date: '2026-03-30'
description: เรียนรู้วิธีเพิ่มการทำเครื่องหมายขีดฆ่าใน Java ด้วย GroupDocs.Annotation
  คู่มือทีละขั้นตอนพร้อมตัวอย่างโค้ด เคล็ดลับการแก้ไขปัญหา และแนวทางปฏิบัติที่ดีที่สุดสำหรับการทำเครื่องหมายเอกสาร
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: เพิ่มการทำเครื่องหมายขีดฆ่าในบทแนะนำ Java ด้วย GroupDocs
type: docs
url: /th/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# เพิ่มการทำเครื่องหมายขีดฆ่าใน Java - คู่มือ GroupDocs ฉบับสมบูรณ์

เคยไหมที่คุณมองเอกสารแล้วคิดว่า “ฉันต้องขีดฆ่าข้อความนี้ แต่ฉันไม่สามารถหยิบปากกาสีแดงมาใช้ได้”? คุณไม่ได้เป็นคนเดียว ไม่ว่าคุณจะกำลังสร้างระบบตรวจสอบเอกสาร, สร้างกระบวนการแก้ไข, หรือเพียงต้องการทำเครื่องหมายข้อความเพื่อการลบในแอปพลิเคชัน Java ของคุณ, **add strikeout annotation java** เป็นทักษะที่จำเป็น ในบทแนะนำนี้เราจะพาคุณผ่านทุกอย่างที่คุณต้องรู้เพื่อทำการขีดฆ่าข้อความที่ทำงานได้จริงในสภาพแวดล้อมการผลิต

## คำตอบด่วน
- **ไลบรารีใดที่รองรับการทำเครื่องหมายขีดฆ่าใน Java?** GroupDocs.Annotation for Java  
- **คำสำคัญหลักที่ควรเน้นสำหรับ SEO คืออะไร?** add strikeout annotation java  
- **ฉันต้องการใบอนุญาตเพื่อรันโค้ดตัวอย่างหรือไม่?** การทดลองใช้ฟรีหรือใบอนุญาตชั่วคราวทำงานได้สำหรับการพัฒนา; จำเป็นต้องมีใบอนุญาตเต็มสำหรับการผลิต.  
- **ฉันสามารถใช้กับไฟล์ PDF, DOCX, และ PPTX ได้หรือไม่?** ใช่ – GroupDocs.Annotation รองรับรูปแบบเอกสารหลักทั้งหมด.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า (JDK 11+ แนะนำ).  

## add strikeout annotation java คืออะไร?
การทำเครื่องหมายขีดฆ่าเป็นการวาดเส้นผ่านข้อความที่เลือก, แสดงให้เห็นว่าคอนเทนต์ควรถูกลบหรือเพิกเฉย. เป็นวิธีที่ไม่ทำลายข้อมูลเพื่อเสนอการลบในขณะที่ยังคงรักษาข้อความต้นฉบับไว้เพื่อการตรวจสอบหรือการรีวิวร่วมกัน.

## ทำไมต้องใช้การทำเครื่องหมายขีดฆ่าในแอปพลิเคชัน Java?
- **กระบวนการตรวจสอบเอกสาร** – ผู้ตรวจสอบสามารถทำเครื่องหมายข้อความที่ไม่ต้องการโดยไม่ต้องแก้ไขแหล่งที่มา.  
- **การแก้ไขร่วมกัน** – สมาชิกทีมจะเห็นการลบที่เสนอทันที.  
- **กฎหมายและการปฏิบัติตาม** – รักษาร่องรอยการตรวจสอบที่ชัดเจนของการเปลี่ยนแปลง.  
- **การย้ายเนื้อหา** – ทำเครื่องหมายส่วนที่ล้าสมัยก่อนย้ายเนื้อหาระหว่างระบบ.  

## ความต้องการเบื้องต้นและการตั้งค่าสภาพแวดล้อม
คุณจะต้องมีสิ่งต่อไปนี้ก่อนเริ่มเขียนโค้ด:
- **Java Development Kit (JDK)** 8+ (JDK 11+ แนะนำ)  
- **Maven หรือ Gradle** สำหรับการจัดการ dependencies  
- **IDE** – IntelliJ IDEA, Eclipse, หรือ VS Code พร้อมส่วนขยาย Java  
- **GroupDocs.Annotation library** – เราจะใช้เวอร์ชัน 25.2 ในตัวอย่าง  

*Nice to have:* ความรู้พื้นฐานเกี่ยวกับ Java annotations และการจัดการ PDF.

## การตั้งค่า GroupDocs.Annotation สำหรับ Java

### การกำหนดค่า Maven ที่ใช้งานได้จริง
เพิ่ม repository และ dependency ลงใน `pom.xml` ของคุณตามที่แสดง:

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

### การจัดการใบอนุญาตของคุณ
GroupDocs มีตัวเลือกใบอนุญาตหลายแบบ:
- **Free trial** – เหมาะสำหรับการทดสอบ (ไม่ต้องใช้บัตรเครดิต)  
- **Temporary license** – เหมาะสำหรับการพัฒนาและสเตจ  
- **Full license** – จำเป็นสำหรับการใช้งานในสภาพแวดล้อมการผลิต; ดูที่ [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** เริ่มต้นด้วยการทดลองใช้ฟรีเพื่อสำรวจ API, จากนั้นเปลี่ยนเป็นใบอนุญาตชั่วคราวเมื่อคุณพร้อมสร้างฟีเจอร์ในโลกจริง.

### การตั้งค่าการตรวจสอบความถูกต้องอย่างรวดเร็ว
รันโปรแกรมขั้นต่ำนี้เพื่อยืนยันว่าไลบรารีโหลดอย่างถูกต้อง:

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

หากคอนโซลพิมพ์ข้อความสำเร็จโดยไม่มีข้อผิดพลาด, คุณพร้อมที่จะเพิ่มการทำเครื่องหมายขีดฆ่าแล้ว.

## วิธีเพิ่มการทำเครื่องหมายขีดฆ่าใน Java

ด้านล่างเป็นการนำไปใช้ที่สมบูรณ์และพร้อมสำหรับการผลิต แบ่งเป็นขั้นตอนที่ชัดเจน.

### ขั้นตอนที่ 1 – เริ่มต้น Annotator
สร้างอินสแตนซ์ `Annotator` ที่ชี้ไปยังเอกสารต้นฉบับ:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Why this matters:** การใช้เส้นทางแบบ absolute หรือ relative ที่แก้ไขอย่างถูกต้องจะป้องกันข้อยกเว้น “file not found”.

### ขั้นตอนที่ 2 – (Optional) เตรียมการตอบกลับคอมเมนต์
การเพิ่มการตอบกลับทำให้ annotation มีความร่วมมือ:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

คอมเมนต์เหล่านี้จะแสดงเมื่อผู้ใช้ชี้เมาส์เหนือการขีดฆ่า.

### ขั้นตอนที่ 3 – กำหนดพื้นที่ขีดฆ่า
ระบุสี่เหลี่ยมที่ล้อมรอบข้อความที่คุณต้องการขีดฆ่า:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Coordinate tip:** จุดกำเนิด (0,0) อยู่ที่มุมบนซ้ายของหน้า; X เพิ่มไปทางขวา, Y เพิ่มลงล่าง. ใช้ PDF viewer ที่แสดงพิกัดเพื่อปรับค่าตามต้องการ.

### ขั้นตอนที่ 4 – กำหนดค่าการทำเครื่องหมายขีดฆ่า
ตั้งค่าลักษณะ, หมายเลขหน้า, และแนบคอมเมนต์:

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

*Color note:* `65535` ตรงกับสีเหลืองในรูปแบบ integer RGB. เปลี่ยนค่าดังกล่าวเพื่อใช้สีอื่น.

### ขั้นตอนที่ 5 – ใช้ Annotation และบันทึก
เพิ่ม annotation ลงในเอกสารและเขียนไฟล์ผลลัพธ์:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### ขั้นตอนที่ 6 – ทำความสะอาดทรัพยากร (สำคัญ!)
ควรทำการ dispose annotator เสมอเพื่อปลดปล่อยทรัพยากร native:

```java
if (annotator != null) {
    annotator.dispose();
}
```

ในสภาพแวดล้อมการผลิต, ควรห่อการใช้งานในบล็อก try‑with‑resources หรือโครงสร้าง `try/finally`.

## ปัญหาทั่วไปและวิธีแก้ไข

| ปัญหา | อาการ | วิธีแก้ |
|---------|---------|-----|
| **ไฟล์ไม่พบ** | `Annotator` ขว้างข้อยกเว้น | ใช้เส้นทางแบบ absolute, ตรวจสอบสิทธิ์การอ่าน, ตรวจสอบว่าไม่มีโปรเซสอื่นล็อกไฟล์ |
| **พิกัดผิด** | ขีดฆ่าแสดงห่างจากข้อความที่ต้องการ | ตรวจสอบระบบพิกัดของ PDF viewer อีกครั้ง; ปรับจุดตามความเหมาะสม |
| **Annotation ไม่แสดง** | ไม่มีขีดฆ่าที่มองเห็นได้หลังบันทึก | เพิ่ม `opacity` (เช่น `0.9`), ตรวจสอบ `pageNumber` (เริ่มจาก 0), ตรวจสอบว่าจุดสร้างสี่เหลี่ยมที่ถูกต้อง |
| **OutOfMemoryError** | แอปพลิเคชันพังเมื่อทำงานกับ PDF ขนาดใหญ่ | เพิ่มขนาด heap ของ JVM (`-Xmx2048m`), ประมวลผลเอกสารเป็นชุด, เรียก `dispose()` เสมอ |

## แนวปฏิบัติที่ดีที่สุดด้านประสิทธิภาพสำหรับการผลิต

### การจัดการหน่วยความจำ
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

### กลยุทธ์การประมวลผลเป็นชุด
เมื่อคุณต้องทำ annotation ให้กับหลายสิบหรือหลายร้อยไฟล์:
- ประมวลผลเอกสาร 10‑20 ไฟล์ต่อชุด.  
- บันทึกผลสำเร็จ/ความล้มเหลวสำหรับแต่ละไฟล์.  
- เริ่มต้น `Annotator` ใหม่สำหรับแต่ละเอกสารเพื่อหลีกเลี่ยงการรั่วของหน่วยความจำ.  

### เคล็ดลับการแคช
- แคชเทมเพลตเอกสารที่ใช้บ่อย.  
- เก็บแผนที่พิกัดที่คำนวณล่วงหน้าสำหรับเลเอาต์มาตรฐาน.  

## กรณีการใช้งานจริง

1. **Document Review Systems** – ผู้ตรวจสอบเสนอการลบโดยไม่แก้ไขสัญญาต้นฉบับ.  
2. **Legal Amendments** – ทนายความติดตามการลบข้อกำหนดในขณะที่รักษาข้อความต้นฉบับเพื่อการตรวจสอบ.  
3. **Academic Peer Review** – ผู้รีวิวทำเครื่องหมายส่วนที่ต้องลบและเพิ่มคอมเมนต์ในบรรทัด.  
4. **Content Migration** – ในระหว่างการย้าย CMS, การขีดฆ่าเน้นข้อความที่ล้าสมัยที่ต้องการเปลี่ยน.  

## การปรับแต่งขั้นสูง

### การสไตล์แบบกำหนดเอง
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### การเพิ่ม Metadata
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## รายการตรวจสอบการแก้ไขปัญหา
- ✅ คุณสามารถเปิดไฟล์ต้นฉบับด้วยตนเองได้หรือไม่?  
- ✅ dependencies ของ GroupDocs ทั้งหมดอยู่ใน classpath หรือไม่?  
- ✅ จุดเหล่านั้นสร้างสี่เหลี่ยมที่ถูกต้องหรือไม่?  
- ✅ หมายเลขหน้าถูกต้องหรือไม่ (เริ่มจาก 0)?  
- ✅ มีหน่วยความจำ heap เพียงพอหรือไม่?  
- ✅ คุณมีสิทธิ์เขียนในโฟลเดอร์ผลลัพธ์หรือไม่?  
- ✅ รูปแบบเอกสารได้รับการสนับสนุนหรือไม่ (PDF, DOCX, PPTX, ฯลฯ)?  

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้ GroupDocs.Annotation ภายในบริการ Spring Boot ได้หรือไม่?**  
A: ใช่. เพิ่ม dependency ของ Maven, ฉีด (inject) คลาสบริการที่สร้าง `Annotator`, และจัดการวงจรชีวิตของมันด้วย bean scopes ของ Spring.

**Q: รูปแบบเอกสารใดบ้างที่รองรับการทำเครื่องหมายขีดฆ่า?**  
A: PDF, DOCX, PPTX, และรูปแบบอื่น ๆ มากมายที่ GroupDocs.Annotation รองรับ. PDF ให้การจัดการพิกัดที่แม่นยำที่สุด.

**Q: ฉันจะจัดการกับเอกสารที่มีขนาดหน้าต่าง ๆ อย่างไร?**  
A: ดึงขนาดหน้าผ่าน `annotator.getPageInfo(pageNumber)` แล้วสเกลพิกัดของคุณตามนั้น.

**Q: สามารถแก้ไขหรือทำลายการทำเครื่องหมายขีดฆ่าที่มีอยู่ได้หรือไม่?**  
A: แน่นอน. ใช้ `annotator.getAnnotations(pageNumber)` เพื่อดึง, จากนั้นใช้ `annotator.update(updatedAnnotation)` หรือ `annotator.delete(annotationId)`.

**Q: ผลกระทบต่อประสิทธิภาพของการเพิ่ม annotation จำนวนมากคืออะไร?**  
A: การเพิ่มหลายร้อย annotation โดยทั่วไปไม่มีปัญหา, แต่ควรตรวจสอบการใช้หน่วยความจำ. สำหรับชุด annotation ขนาดใหญ่มาก, ควรพิจารณาแบ่งหน้า view หรือโหลด annotation แบบ lazy‑loading ตามความต้องการ.

## สรุป
คุณมีคู่มือที่สมบูรณ์และพร้อมสำหรับการผลิตเพื่อ **add strikeout annotation java** ด้วย GroupDocs.Annotation แล้ว. เริ่มต้นด้วยตัวอย่างการตรวจสอบความถูกต้องอย่างง่าย, จากนั้นขยายเป็นการประมวลผลเป็นชุด, การสไตล์แบบกำหนดเอง, และการเพิ่ม metadata. จำไว้ว่าต้องทดสอบพิกัดอย่างละเอียด, จัดการทรัพยากรอย่างรับผิดชอบ, และเลือกโมเดลใบอนุญาตที่เหมาะสมสำหรับสภาพแวดล้อมของคุณ.

พร้อมสำรวจเพิ่มเติมหรือยัง? ตรวจสอบประเภท annotation อื่น ๆ — highlight, note, image, arrow, และ watermark — เพื่อสร้างชุดการทำงานร่วมกันของเอกสารที่ครบวงจร.

---

**อัปเดตล่าสุด:** 2026-03-30  
**ทดสอบด้วย:** GroupDocs.Annotation 25.2 for Java  
**ผู้เขียน:** GroupDocs  

**แหล่งข้อมูลเพิ่มเติม**
- [เอกสาร GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [คู่มืออ้างอิง API](https://reference.groupdocs.com/annotation/java/)
- [ดาวน์โหลดเวอร์ชันล่าสุด](https://releases.groupdocs.com/annotation/java/)
- [ซื้อใบอนุญาตเต็ม](https://purchase.groupdocs.com/buy)
- [เริ่มทดลองใช้ฟรี](https://releases.groupdocs.com/annotation/java/)
- [รับใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)
- [ฟอรั่มสนับสนุนชุมชน](https://forum.groupdocs.com/c/annotation/)