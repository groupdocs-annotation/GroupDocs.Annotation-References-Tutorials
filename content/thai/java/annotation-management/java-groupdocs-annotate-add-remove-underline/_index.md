---
"date": "2025-05-06"
"description": "เรียนรู้วิธีเพิ่มและลบคำอธิบายขีดเส้นใต้ในเอกสาร Java โดยใช้ GroupDocs.Annotation ปรับปรุงการจัดการเอกสารของคุณด้วยคู่มือโดยละเอียดนี้"
"title": "เพิ่มและลบคำอธิบายขีดเส้นใต้ใน Java โดยใช้ GroupDocs คู่มือฉบับสมบูรณ์"
"url": "/th/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# วิธีการใช้ Java: เพิ่มและลบคำอธิบายขีดเส้นใต้ด้วย GroupDocs

## การแนะนำ

เพิ่มประสิทธิภาพระบบการจัดการเอกสารของคุณด้วยการเพิ่มหรือลบคำอธิบายประกอบด้วยโปรแกรมหรือไม่ บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับการใช้ไลบรารี GroupDocs.Annotation ที่ทรงพลังใน Java เพื่อเพิ่มคำอธิบายประกอบแบบขีดเส้นใต้และลบออกจากเอกสาร เช่น PDF

**สิ่งที่คุณจะได้เรียนรู้:**
- เริ่มต้นคลาส Annotator
- เพิ่มคำอธิบายขีดเส้นใต้พร้อมความคิดเห็นโดยใช้ GroupDocs.Annotation สำหรับ Java
- ลบคำอธิบายประกอบทั้งหมดออกจากเอกสาร
- กำหนดค่าสภาพแวดล้อมของคุณเพื่อใช้ GroupDocs.Annotation อย่างมีประสิทธิภาพ

มาสำรวจกันว่าฟังก์ชันเหล่านี้สามารถนำไปใช้ประโยชน์ในโครงการของคุณได้อย่างไร ตรวจสอบให้แน่ใจว่าคุณได้ครอบคลุมข้อกำหนดเบื้องต้นที่จำเป็นแล้วก่อนเริ่มต้น

## ข้อกำหนดเบื้องต้น

### ไลบรารีและการอ้างอิงที่จำเป็น
หากต้องการปฏิบัติตามบทช่วยสอนนี้อย่างมีประสิทธิผล ให้แน่ใจว่าคุณมี:
- **GroupDocs.Annotation สำหรับ Java**:ขอแนะนำเวอร์ชัน 25.2 ขึ้นไป
- **ชุดพัฒนา Java (JDK)**: ต้องมีเวอร์ชัน 8 ขึ้นไป

### ข้อกำหนดการตั้งค่าสภาพแวดล้อม
ตรวจสอบให้แน่ใจว่าสภาพแวดล้อมการพัฒนาของคุณมี IDE เช่น IntelliJ IDEA หรือ Eclipse และเครื่องมือสร้างเช่น Maven

### ข้อกำหนดเบื้องต้นของความรู้
ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม Java โดยเฉพาะการทำงานกับไลบรารีผ่าน Maven จะเป็นประโยชน์

## การตั้งค่า GroupDocs.Annotation สำหรับ Java

หากต้องการเริ่มใช้ GroupDocs.Annotation ในโปรเจ็กต์ Java ของคุณ ให้ทำตามขั้นตอนการตั้งค่าเหล่านี้:

**การกำหนดค่า Maven:**
เพิ่มการกำหนดค่าต่อไปนี้ลงในของคุณ `pom.xml` ไฟล์สำหรับดาวน์โหลดและรวม GroupDocs.Annotation

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

**การได้มาซึ่งใบอนุญาต:**
เริ่มต้นด้วยการดาวน์โหลดรุ่นทดลองใช้งานฟรีหรือรับใบอนุญาตชั่วคราวจาก GroupDocs เพื่อสำรวจความสามารถทั้งหมดของไลบรารีของพวกเขา หากต้องการใช้งานจริง จำเป็นต้องซื้อใบอนุญาต

## คู่มือการใช้งาน

### คุณลักษณะที่ 1: เริ่มต้น Annotator และเพิ่มคำอธิบายแบบขีดเส้นใต้

หัวข้อนี้จะแนะนำคุณเกี่ยวกับการเริ่มต้นใช้งาน `Annotator` ชั้นเรียนและการเพิ่มคำอธิบายขีดเส้นใต้ลงในเอกสารของคุณ

#### ภาพรวม
การเพิ่มคำอธิบายประกอบจะช่วยเน้นส่วนเฉพาะของเอกสาร ในที่นี้ เราจะเน้นที่การขีดเส้นใต้ข้อความด้วยคำอธิบายประกอบเพื่อให้ชัดเจนขึ้นหรือให้ข้อเสนอแนะ

#### การดำเนินการแบบทีละขั้นตอน

**1. เริ่มต้นใช้งาน Annotator**
สร้าง `Annotator` วัตถุและโหลดไฟล์ PDF ของคุณ

```java
import com.groupdocs.annotation.Annotator;

// โหลดเอกสารที่คุณต้องการใส่คำอธิบาย
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. สร้างความคิดเห็นพร้อมคำตอบ**
กำหนดความคิดเห็นที่เกี่ยวข้องกับคำอธิบายขีดเส้นใต้

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

**3. กำหนดจุดสำหรับคำอธิบายแบบขีดเส้นใต้**
ตั้งค่าพิกัดเพื่อกำหนดว่าควรขีดเส้นใต้ปรากฏที่ใด

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

**4. สร้างและกำหนดค่าคำอธิบายขีดเส้นใต้**
สร้างคำอธิบายขีดเส้นใต้และตั้งค่าคุณสมบัติ เช่น สี ความทึบ และความคิดเห็น

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // สีเหลืองในรูปแบบ ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. บันทึกเอกสารที่มีคำอธิบายประกอบ**
บันทึกการเปลี่ยนแปลงของคุณลงในไฟล์ใหม่

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบให้แน่ใจว่าพิกัดทั้งหมดสำหรับจุดอยู่ภายในขอบเขตเอกสาร
- ตรวจสอบว่า `outputPath` มีไดเร็กทอรีอยู่และสามารถเขียนได้

### คุณสมบัติที่ 2: บันทึกเอกสารโดยไม่ต้องมีคำอธิบายประกอบ

หัวข้อนี้จะกล่าวถึงวิธีการลบคำอธิบายประกอบทั้งหมดจากเอกสารที่มีคำอธิบายประกอบไว้ก่อนหน้านี้

#### ภาพรวม
คุณอาจจำเป็นต้องบันทึกเอกสารในรูปแบบใหม่โดยไม่มีคำอธิบายประกอบเพื่อจุดประสงค์ในการแชร์หรือการเก็บถาวร

#### การดำเนินการแบบทีละขั้นตอน

**1. เริ่มต้น Annotator ด้วยเอกสารที่มีคำอธิบายประกอบ**
โหลดเอกสารที่มีคำอธิบายประกอบอยู่แล้ว

```java
Annotator annotator = new Annotator(outputPath);
```

**2. กำหนดค่าตัวเลือกการบันทึกเพื่อลบคำอธิบายประกอบ**
ระบุว่าไม่ควรบันทึกคำอธิบายประกอบในไฟล์เอาต์พุต

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. บันทึกเอกสารโดยไม่ต้องมีคำอธิบายประกอบ**
กำหนดเส้นทางสำหรับเอกสารที่ทำความสะอาดแล้วและบันทึกไว้

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## การประยุกต์ใช้งานจริง

ต่อไปนี้คือสถานการณ์จริงบางสถานการณ์ที่คุณลักษณะเหล่านี้อาจเป็นประโยชน์ได้:
1. **การตรวจสอบเอกสาร**:การเน้นข้อความและการแสดงความคิดเห็นในส่วนต่างๆ ของสัญญาหรือรายงานเพื่อการตรวจสอบ
2. **เครื่องมือทางการศึกษา**:การใส่หมายเหตุในตำราเรียนหรือแก้ไขให้นักเรียนทราบ
3. **การแก้ไขแบบร่วมมือกัน**:การแบ่งปันแบบร่างพร้อมคำอธิบายระหว่างสมาชิกในทีมเพื่อรับคำติชม
4. **เอกสารทางกฎหมาย**:การขีดเส้นใต้ประเด็นสำคัญในเอกสารทางกฎหมายระหว่างการหารือ
5. **สื่อการตลาด**:การเน้นข้อมูลที่สำคัญในโบรชัวร์ก่อนการจัดจำหน่าย

## การพิจารณาประสิทธิภาพ
เมื่อทำงานกับ GroupDocs.Annotation โปรดพิจารณาเคล็ดลับเหล่านี้เพื่อเพิ่มประสิทธิภาพการทำงาน:
- **การจัดการหน่วยความจำ**: กำจัดอย่างถูกวิธี `Annotator` วัตถุเพื่อปลดปล่อยทรัพยากร
- **การประมวลผลแบบแบตช์**:หากต้องการใส่คำอธิบายประกอบเอกสารหลายฉบับ ให้ประมวลผลเป็นชุดๆ เพื่อจัดการภาระระบบอย่างมีประสิทธิภาพ
- **การจัดสรรทรัพยากร**: ตรวจสอบให้แน่ใจว่าสภาพแวดล้อมของคุณมีหน่วยความจำและพลังการประมวลผลเพียงพอสำหรับการจัดการไฟล์ขนาดใหญ่

## บทสรุป
คุณได้เรียนรู้วิธีการเพิ่มและลบคำอธิบายประกอบแบบขีดเส้นใต้โดยใช้ GroupDocs.Annotation สำหรับ Java แล้ว บทช่วยสอนนี้ครอบคลุมถึงการเริ่มต้นคลาส Annotator การกำหนดค่าคำอธิบายประกอบด้วยคำอธิบายประกอบ และการบันทึกเอกสารโดยไม่ต้องใช้คำอธิบายประกอบใดๆ 

หากต้องการสำรวจเพิ่มเติม โปรดพิจารณาการรวมคุณลักษณะเหล่านี้เข้าในระบบการจัดการเอกสารที่มีอยู่ของคุณ หรือทดลองใช้ประเภทคำอธิบายประกอบอื่น ๆ ที่ GroupDocs จัดทำไว้ให้

## ส่วนคำถามที่พบบ่อย
1. **ฉันจะกำหนดค่าคำอธิบายขีดเส้นใต้หลายรายการในครั้งเดียวได้อย่างไร**
   - สร้างหลาย ๆ `UnderlineAnnotation` วัตถุและเพิ่มพวกมันตามลำดับโดยใช้ `annotator.add()` วิธี.
2. **ฉันสามารถใส่คำอธิบายประกอบภาพในไฟล์ PDF โดยใช้ไลบรารีนี้ได้หรือไม่**
   - ใช่ GroupDocs.Annotation รองรับการใส่คำอธิบายภาพในเอกสารเช่น PDF
3. **GroupDocs.Annotation รองรับรูปแบบไฟล์อะไรบ้าง**
   - รองรับรูปแบบเอกสารต่างๆ รวมถึง PDF, Word, Excel และอื่นๆ อีกมากมาย