---
categories:
- Java Development
date: '2026-11-01'
description: เรียนรู้วิธีบันทึกหน้าที่เลือกจาก PDF ด้วย GroupDocs.Annotation ใน Java
  โดยใช้การบันทึกเอกสารด้วย Spring Boot, การบีบอัด PDF สูงสุด, และการจัดเวอร์ชันเพื่อประสิทธิภาพที่ดีที่สุด
keywords:
- save selected pdf pages
- flatten pdf annotations
- maximum pdf compression
- how to compress pdf
- reduce pdf size java
- spring boot document saving
lastmod: '2026-11-01'
linktitle: บทเรียนการบันทึกเอกสาร
og_description: บันทึกหน้าที่เลือกจาก PDF ด้วย GroupDocs.Annotation สำหรับ Java คู่มือนี้แสดงการบันทึกเอกสารด้วย
  Spring Boot, การบีบอัด PDF สูงสุด, และเทคนิคการจัดเวอร์ชันเพื่อลดขนาดไฟล์และปรับปรุงประสิทธิภาพ
og_image_alt: 'Developer guide: Save selected PDF pages with GroupDocs.Annotation
  in Java'
og_title: บันทึกหน้าที่เลือกจาก PDF ด้วย GroupDocs.Annotation สำหรับ Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-01'
  description: Learn how to save selected pdf pages with GroupDocs.Annotation in Java,
    using spring boot document saving, maximum pdf compression, and versioning for
    optimal performance.
  headline: Save selected pdf pages with GroupDocs.Annotation for Java
  type: TechArticle
- description: Learn how to save selected pdf pages with GroupDocs.Annotation in Java,
    using spring boot document saving, maximum pdf compression, and versioning for
    optimal performance.
  name: Save selected pdf pages with GroupDocs.Annotation for Java
  steps:
  - name: Initialize the Annotation API
    text: '`AnnotationApi` is the primary entry point for all annotation operations
      in GroupDocs.Annotation. You obtain it by creating an `AnnotationApi` instance
      with your license key.'
  - name: Define the page range
    text: Specify the exact pages you want to keep. For example, pages 1‑5 and 10‑12
      cover the most‑relevant sections in a legal contract.
  - name: Configure save options
    text: '`SaveOptions` lets you set compression level, output format, and whether
      to flatten annotations. Setting `compressionLevel` to `Maximum` often yields
      the biggest size drop.'
  - name: Execute the save operation
    text: Call the `save` method with the source document, the configured `SaveOptions`,
      and an output stream. The API writes only the selected pages, applying compression
      on the fly.
  - name: Clean up resources
    text: After saving, invoke `close()` on the document object to release file handles
      and help the garbage collector reclaim memory.
  type: HowTo
- questions:
  - answer: Inject the `AnnotationApi` bean, configure `SaveOptions` with the desired
      page range, and expose a `@PostMapping` that triggers the save asynchronously.
    question: How do I enable page range saving java in a Spring Boot service?
  - answer: Yes – add version metadata to the filename (e.g., `Report_v3_2024-11-02.pdf`)
      or store it in custom PDF properties before invoking the save method.
    question: Can I combine page range saving with java document versioning?
  - answer: PDF retains 100 % of annotation features; DOCX and XPS preserve most,
      but may drop interactive elements like sticky notes.
    question: What formats support full annotation fidelity?
  - answer: Use `Runtime.getRuntime().totalMemory()` and `freeMemory()` before and
      after the operation, or integrate VisualVM/YourKit for real‑time profiling.
    question: How can I monitor memory usage during large saves?
  - answer: Absolutely – iterate over your document collection, set individual `SaveOptions`
      for each, and execute the saves in parallel using `ExecutorService`.
    question: Is batch saving of multiple documents with different page ranges possible?
  type: FAQPage
tags:
- save selected pdf pages
- GroupDocs.Annotation
- Java PDF processing
- spring boot document saving
- pdf compression
title: บันทึกหน้าที่เลือกจาก PDF ด้วย GroupDocs.Annotation สำหรับ Java
type: docs
url: /th/java/document-saving/
weight: 4
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
{{< blocks/products/pf/backtop-button >}}

# บันทึกหน้า PDF ที่เลือกด้วย GroupDocs.Annotation สำหรับ Java

การลดขนาด PDF ในแอปพลิเคชัน Java เป็นความท้าทายที่พบบ่อย โดยเฉพาะเมื่อคุณต้อง **บันทึกหน้า PDF ที่เลือก** พร้อมคง annotation ไว้และรักษาประสิทธิภาพสูง ในคู่มือนี้คุณจะได้เรียนรู้ว่าการบันทึกช่วงหน้าที่เลือกมีความสำคัญอย่างไร GroupDocs.Annotation ทำให้เรื่องนี้ง่ายขึ้นอย่างไร และจะผสานกับ **spring boot document saving** และ **java document versioning** เพื่อสร้างโซลูชันที่พร้อมใช้งานในระดับผลิตจริง ไม่ว่าคุณจะสร้างแพลตฟอร์มตรวจสอบกฎหมาย พอร์ทัลการศึกษา หรือเวิร์กโฟลว์ที่ต้องปฏิบัติตามข้อกำหนด เทคนิคต่อไปนี้จะช่วยให้ไฟล์มีขนาดเบาลงโดยไม่สูญเสียความแม่นยำของ annotation

## คำตอบอย่างรวดเร็ว
- **บันทึกหน้า PDF ที่เลือกคืออะไร?** คือการส่งออกเฉพาะหน้าที่คุณต้องการจาก PDF พร้อมบีบอัดและคง annotation ไว้  
- **ทำไมต้องเลือก GroupDocs.Annotation สำหรับ Java?** ไลบรารีมีฟีเจอร์บันทึกช่วงหน้าในตัว รองรับรูปแบบผลลัพธ์กว่า 30 แบบ และสามารถลดขนาดได้ถึง 70 % สำหรับเอกสารทั่วไป  
- **สามารถใช้ร่วมกับ Spring Boot ได้หรือไม่?** ใช่ – API ทำงานร่วมกับบริการ Spring Boot ได้อย่างราบรื่น รองรับ endpoint การบันทึกเอกสารแบบอะซิงโครนัส  
- **การเวอร์ชันเอกสารใน Java ช่วยอย่างไร?** การฝังเมตาดาต้าเวอร์ชันในชื่อไฟล์หรือคุณสมบัติ PDF ทำให้ทีมติดตามการเปลี่ยนแปลงและหลีกเลี่ยงความขัดแย้งได้  
- **เคล็ดลับประสิทธิภาพที่ทำให้ใช้หน่วยความจำน้อย?** การประมวลผลแบบสตรีม การโหลดแบบเลือกเฉพาะหน้า และการทำลายออบเจกต์เอกสารอย่างชัดเจนช่วยลดภาระบน heap ของ JVM

## บันทึกหน้า PDF ที่เลือกคืออะไร?
**บันทึกหน้า PDF ที่เลือก** หมายถึงการสกัดเฉพาะหน้าที่คุณระบุจาก PDF พร้อมบีบอัดภาพและฟอนต์ตามต้องการ แล้วเขียนผลลัพธ์ไปยังไฟล์ใหม่ วิธีนี้สามารถลดขนาดไฟล์ได้ครึ่งหนึ่งหรือมากกว่านั้น ในขณะที่คง annotation ทั้งหมดไว้ ซึ่งสำคัญต่อการดาวน์โหลดที่เร็วและค่าใช้จ่ายการจัดเก็บที่ต่ำลง

## วิธีบันทึกหน้า PDF ที่เลือกด้วย GroupDocs.Annotation?
โหลดเอกสาร กำหนดหน้าที่ต้องการ ตั้งค่าการบีบอัด แล้วบันทึก ขั้นแรกเปิด PDF ต้นฉบับด้วย `AnnotationApi` จากนั้นระบุหมายเลขหน้า ตั้งค่า `SaveOptions` ให้บีบอัดสูงสุดและอาจทำ flatten แล้วเรียกเมธอด `save` พร้อมส่ง output stream กระบวนการสั้น ๆ ห้าขั้นตอนนี้ทำงานได้ทั้งในแอปพลิเคชัน Java ธรรมดาและ microservice Spring Boot

### ขั้นตอนที่ 1: เริ่มต้น Annotation API
`AnnotationApi` เป็นจุดเข้าหลักสำหรับการทำงาน annotation ทั้งหมดใน GroupDocs.Annotation  
คุณจะได้มาจากการสร้างอินสแตนซ์ `AnnotationApi` พร้อมคีย์ไลเซนส์ของคุณ

### ขั้นตอนที่ 2: กำหนดช่วงหน้า
ระบุหน้าที่คุณต้องการเก็บไว้ ตัวอย่างเช่น หน้า 1‑5 และ 10‑12 ครอบคลุมส่วนที่สำคัญที่สุดในสัญญากฎหมาย

### ขั้นตอนที่ 3: ตั้งค่าตัวเลือกการบันทึก
`SaveOptions` ให้คุณกำหนดระดับการบีบอัด รูปแบบผลลัพธ์ และว่าจะทำ flatten annotation หรือไม่ การตั้งค่า `compressionLevel` เป็น `Maximum` มักให้การลดขนาดสูงสุด

### ขั้นตอนที่ 4: ดำเนินการบันทึก
เรียกเมธอด `save` พร้อมเอกสารต้นฉบับ, `SaveOptions` ที่กำหนด, และ output stream API จะเขียนเฉพาะหน้าที่เลือกและบีบอัดแบบเรียลไทม์

### ขั้นตอนที่ 5: ทำความสะอาดทรัพยากร
หลังบันทึกเรียก `close()` บนออบเจกต์เอกสารเพื่อปล่อยไฟล์แฮนด์เดิลและช่วยให้ garbage collector คืนหน่วยความจำ

## ทำไมต้องใช้ GroupDocs.Annotation สำหรับ Java?
GroupDocs.Annotation รองรับ **รูปแบบเข้าและออกกว่า 30 แบบ** และสามารถ **ลดขนาด PDF ได้สูงสุดถึง 70 %** เมื่อเปิดใช้การบันทึกช่วงหน้าและบีบอัดสูงสุด ไลบรารีจะคงความแม่นยำของ annotation โดยอัตโนมัติ ไม่ต้องเขียนโค้ด post‑processing เอง API ระดับสูงช่วยซ่อนการจัดการ PDF ระดับล่าง แต่ยังให้การควบคุมละเอียดระดับการบีบอัดและการเลือกหน้า

## ข้อกำหนดเบื้องต้น
- Java 17 หรือใหม่กว่า  
- ระบบ build Maven หรือ Gradle  
- GroupDocs.Annotation สำหรับ Java (ดาวน์โหลดจากเว็บไซต์ทางการ)  
- ตัวเลือก: Spring Boot 3.x สำหรับการรวม REST  

## การบันทึกช่วงหน้าที่ฉลาด (page range saving java)

การบันทึกหน้าแบบเลือกเป็นหัวใจของ **บันทึกหน้า PDF ที่เลือก** แทนการส่งออกไฟล์ทั้งหมด—บางครั้งหลายร้อยหน้า—คุณจะมุ่งเน้นเฉพาะหน้าที่มี annotation หรือเนื้อหาที่ผู้ใช้ร้องขอ เทคนิคนี้สามารถลดขนาดไฟล์ได้ **50 %–70 %** โดยเฉพาะ PDF ที่มีกราฟิกหนาแน่น

### ตัวอย่างจากโลกจริง
สัญญาขนาด 300 หน้า ที่มี annotation บนหน้า 12‑15 และ 200‑205 สามารถลดจาก 45 MB เหลือใต้ 12 MB เพียงบันทึกหน้าเหล่านั้นเท่านั้น

## การรวมเข้ากับระบบควบคุมเวอร์ชัน (java document versioning)

**java document versioning** หมายถึงการแนบตัวระบุเวอร์ชัน (เช่น `v1.3`, timestamp, ID ผู้เขียน) ไปกับไฟล์ที่บันทึกแต่ละครั้ง GroupDocs.Annotation ให้คุณฝังคุณสมบัติกำหนดเองลงในเมตาดาต้า PDF ทำให้ทุกผู้มีส่วนได้ส่วนเสียเห็นเวอร์ชันที่ตรงกัน

### วิธีทำงาน
- ใช้ `DocumentProperty` เพื่อเพิ่มฟิลด์ `Version`, `Author`, และ `SavedOn`  
- ใส่สตริงเวอร์ชันในชื่อไฟล์ผลลัพธ์ เช่น `Contract_v2_2024-09-15.pdf`  
- เก็บเมตาดาต้าเดียวกันในฐานข้อมูลเพื่อเป็น audit trail

## spring boot document saving คืออะไร?
**spring boot document saving** หมายถึงการเปิดเผยตรรกะการบันทึกเอกสารเป็น endpoint RESTful ภายใน microservice Spring Boot Endpoint จะรับ PDF, พารามิเตอร์ช่วงหน้า (ถ้ามี) และคืนไฟล์ที่ลดขนาดหรือ URL ดาวน์โหลด โดยใช้การจัดการคำขอแบบอะซิงโครนัสและสตรีมของ Spring คุณสามารถให้บริการ PDF ขนาดใหญ่โดยไม่บล็อกเธรด ส่งมอบประสบการณ์ที่ตอบสนองต่อผู้ใช้ได้ดี

## java document versioning ทำงานอย่างไร?
java document versioning ทำงานโดยอัปเดตเมตาดาต้าเอกสารโปรแกรมก่อนการบันทึกแต่ละครั้ง คุณตั้งค่าคุณสมบัติเช่น `Version` และ `LastModified` แล้วบันทึกไฟล์ วิธีนี้รับประกันว่า PDF ทุกไฟล์ที่บันทึกจะมีประวัติเวอร์ชันของตนเอง ทำให้สามารถ rollback และ audit ได้ง่าย การเพิ่มคุณสมบัติ timestamp เช่น `SavedOn` ช่วยบ่งบอกเวลาที่สร้างเวอร์ชันแต่ละอัน ซึ่งมีคุณค่าสำหรับการรายงานการปฏิบัติตามข้อกำหนด

## เคล็ดลับการเพิ่มประสิทธิภาพ

### การจัดการหน่วยความจำ
- **การประมวลผลแบบสตรีม**: ใช้ `InputStream`/`OutputStream` เพื่อหลีกเลี่ยงการโหลด PDF ทั้งไฟล์เข้าสู่ RAM  
- **การโหลดแบบเลือก**: โหลดเฉพาะหน้าที่คุณจะบันทึก; GroupDocs.Annotation สามารถเปิดเอกสารในโหมด “partial”  
- **การทำลายอย่างชัดเจน**: เรียก `document.close()` หลังแต่ละการดำเนินการเพื่อปล่อยทรัพยากรเนทีฟโดยเร็ว

### การปรับขนาดไฟล์
- **ตั้งค่าการบีบอัด**: ตั้ง `SaveOptions.compressionLevel` เป็น `Maximum` เพื่อให้ไฟล์เล็กที่สุด  
- **การเลือกรูปแบบ**: เมื่อขนาด PDF ยังสูงอยู่ ให้พิจารณาแปลงเป็น **XPS** หรือ **DOCX** ซึ่งอาจเล็กลงได้ถึง 30 % สำหรับเอกสารที่เป็นข้อความเป็นหลัก  
- **การ flatten annotation**: สำหรับการปล่อยเวอร์ชันสุดท้าย ให้ flatten annotation ลงในเนื้อหาหน้าเพื่อขจัดเลเยอร์ annotation เพิ่มและลดขนาด

## สถานการณ์การบันทึกทั่วไปและวิธีแก้

### สถานการณ์ 1: การตรวจสอบเอกสารกฎหมาย
ทนายต้องการเฉพาะข้อที่มี annotation ใช้การบันทึกช่วงหน้าเพื่อสกัดหน้า 30‑45 ฝังเมตาดาต้าเวอร์ชัน และส่งไฟล์ 5 MB แทนไฟล์ต้นฉบับ 25 MB

### สถานการณ์ 2: เอกสารเทคนิค
วิศวกร annotate แผนภาพในสเปค 200 หน้า โดยบันทึกเฉพาะหน้าที่มีแผนภาพและบีบอัดภาพ คุณจะได้ PDF ที่กระจายได้ภายใต้ 10 MB ซึ่งพอเหมาะกับระบบควบคุมเวอร์ชันส่วนใหญ่

### สถานการณ์ 3: เนื้อหาการศึกษา
อาจารย์ annotate สไลด์การบรรยาย ส่งออกสไลด์ที่มี annotation เป็น PDF แยกไฟล์ พร้อมบีบอัดสูงสุดเพื่อให้ดาวน์โหลดเร็วบนอุปกรณ์มือถือ

### สถานการณ์ 4: การตรวจสอบตามข้อกำหนด
ผู้ตรวจสอบต้องการเส้นทางที่สมบูรณ์และไม่เปลี่ยนแปลง บันทึกเอกสารเต็มรูปแบบพร้อม annotation ทั้งหมด ฝังแฮชเชิงคริปโตในเมตาดาต้า และเก็บไฟล์เวอร์ชันในที่เก็บปลอดภัย

## การแก้ไขปัญหาการบันทึกที่พบบ่อย

### ปัญหา: annotation หายหลังบันทึก
**คำตอบโดยตรง:** เกิดจากรูปแบบผลลัพธ์ที่เลือกไม่รองรับประเภท annotation บางประเภท ให้เปลี่ยนเป็น PDF หรือแปลง annotation ที่ไม่รองรับเป็นรูปแบบที่รองรับก่อนบันทึก

### ปัญหา: ประสิทธิภาพการบันทึกช้า
**คำตอบโดยตรง:** PDF ขนาดใหญ่พร้อม annotation จำนวนมากใช้ CPU มาก เปิดการประมวลผลแบบอะซิงโครนัสใน Spring Boot ใช้ thread pool และตรวจสอบ heap ของ JVM ด้วย `Runtime.getRuntime().freeMemory()`

### ปัญหา: การแสดงผลไม่สอดคล้องกันระหว่าง viewer
**คำตอบโดยตรง:** Viewer ต่าง ๆ แสดง annotation แตกต่างกัน ทดสอบกับ Adobe Acrobat, Foxit, และปลั๊กอิน PDF ของเบราว์เซอร์ แล้วปรับ `SaveOptions` (เช่น ตั้ง `renderMode` เป็น `Standard`) เพื่อให้ผลลัพธ์สอดคล้อง

### ปัญหา: ขัดแย้งในการควบคุมเวอร์ชัน
**คำตอบโดยตรง:** ใช้การเขียนไฟล์แบบ atomic – เขียนไปยังไฟล์ชั่วคราว แล้วเปลี่ยนชื่อเป็นชื่อไฟล์เวอร์ชันสุดท้ายเมื่อบันทึกสำเร็จ

## แนวทางปฏิบัติที่ดีที่สุดสำหรับระบบผลิต

- **ต้องมีการจัดการข้อผิดพลาดที่แข็งแรง** – จับ `IOException`, `LicenseException`, และ `AnnotationException` เพื่อให้ผู้ใช้ได้รับข้อความชัดเจน  
- **เปิดเผย callback ความคืบหน้า** – ใน Spring Boot ให้คืนค่า `DeferredResult` ที่สตรีมเปอร์เซ็นต์ความคืบหน้าไปยังคลายเอนต์  
- **ทดสอบกับขนาดเอกสารจริง** – จำลอง PDF 200 หน้า พร้อมภาพความละเอียดสูง เพื่อยืนยันว่าการใช้หน่วยความจำไม่เกิน 500 MB  
- **วางแผนสำรองข้อมูล** – เขียน PDF ที่บีบอัดลงในโฟลเดอร์ staging ก่อน; หากดำเนินการสำเร็จให้ย้ายไปยังโฟลเดอร์ production  
- **บันทึกอัตราการบีบอัด** – เก็บขนาดไฟล์ก่อน/หลังใน log เพื่อเฝ้าติดตามประสิทธิภาพของกลยุทธ์ลดขนาด

## การรวมกับเฟรมเวิร์ก Java สมัยใหม่

GroupDocs.Annotation ทำงานได้ทันทีกับ Spring Boot, Jakarta EE, และ Micronaut เมื่อคุณสร้าง microservice ให้เปิด endpoint `/documents/save` ที่รับ payload JSON มี `pageRanges` และ `versionInfo` ใช้ `CompletableFuture` รันงานบันทึกแบบอะซิงโครนัส แล้วอัปเดตตารางสถานะในฐานข้อมูลเมื่อไฟล์ถูกจัดเก็บ

## คำถามที่พบบ่อย

**ถาม: จะเปิดใช้การบันทึกช่วงหน้าใน Java บริการ Spring Boot อย่างไร?**  
ตอบ: ฉีด `AnnotationApi` bean, ตั้งค่า `SaveOptions` พร้อมช่วงหน้าที่ต้องการ, แล้วเปิด `@PostMapping` ที่เรียกบันทึกแบบอะซิงโครนัส

**ถาม: สามารถผสานการบันทึกช่วงหน้ากับ java document versioning ได้หรือไม่?**  
ตอบ: ทำได้ – เพิ่มเมตาดาต้าเวอร์ชันลงในชื่อไฟล์ (เช่น `Report_v3_2024-11-02.pdf`) หรือเก็บในคุณสมบัติ PDF ก่อนเรียกเมธอดบันทึก

**ถาม: รูปแบบใดสนับสนุนความแม่นยำของ annotation อย่างเต็ม?**  
ตอบ: PDF รักษา 100 % ของฟีเจอร์ annotation; DOCX และ XPS รักษาส่วนใหญ่แต่อาจสูญเสียองค์ประกอบเชิงโต้ตอบเช่น sticky notes

**ถาม: จะตรวจสอบการใช้หน่วยความจำระหว่างการบันทึกขนาดใหญ่ได้อย่างไร?**  
ตอบ: ใช้ `Runtime.getRuntime().totalMemory()` และ `freeMemory()` ก่อนและหลังการดำเนินการ หรือรวม VisualVM/YourKit เพื่อโปรไฟล์แบบเรียลไทม์

**ถาม: สามารถบันทึกหลายเอกสารพร้อมช่วงหน้าต่างๆ ได้หรือไม่?**  
ตอบ: แน่นอน – วนลูปผ่านคอลเลกชันเอกสาร ตั้ง `SaveOptions` แยกสำหรับแต่ละไฟล์ แล้วดำเนินการบันทึกแบบขนานด้วย `ExecutorService`

## แหล่งข้อมูล

- [Save Specific Page Range with GroupDocs.Annotation for Java: A Complete Guide](./groupdocs-annotation-java-save-specific-page-range/)  
- [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- [GroupDocs.Annotation for Java API Reference](https://reference.groupdocs.com/annotation/java/)  
- [Download GroupDocs.Annotation for Java](https://releases.groupdocs.com/annotation/java/)  
- [GroupDocs.Annotation Forum](https://forum.groupdocs.com/c/annotation)  
- [Free Support](https://forum.groupdocs.com/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  

## สรุป

ด้วยการเชี่ยวชาญ **บันทึกหน้า PDF ที่เลือก** ด้วย GroupDocs.Annotation คุณสามารถส่งมอบ PDF ที่เบาและคง annotation อย่างครบถ้วน โหลดเร็ว ใช้พื้นที่จัดเก็บน้อยลง และผสานเข้ากับ **spring boot document saving** และ **java document versioning** ได้อย่างไร้รอยต่อ ใช้เทคนิคการเลือกช่วงหน้า ปรับการบีบอัด และปฏิบัติตามรายการตรวจสอบแนวทางปฏิบัติที่ดีที่สุด เพื่อสร้างเวิร์กโฟลว์เอกสารที่เชื่อถือได้และมีประสิทธิภาพสูง

---

**อัปเดตล่าสุด:** 2026-11-01  
**ทดสอบกับ:** GroupDocs.Annotation for Java 23.12  
**ผู้เขียน:** GroupDocs

## บทเรียนที่เกี่ยวข้อง

- [Page Range Saving Java with GroupDocs.Annotation – Complete Guide](/annotation/java/document-saving/)  
- [Load PDF Annotations Java - Complete GroupDocs Annotation Management Guide](/annotation/java/annotation-management/groupdocs-annotation-java-manage-documents/)  
- [Complete Guide - How to Save Annotated PDF with GroupDocs.Annotation for Java](/annotation/java/annotation-management/annotations-groupdocs-annotation-java-tutorial/)

{{< /blocks/products/pf/backtop-button >}}

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}