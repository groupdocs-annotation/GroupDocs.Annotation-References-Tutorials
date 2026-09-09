---
categories:
- PDF Processing
date: '2026-06-11'
description: เรียนรู้วิธีเพิ่มคอมโพเนนต์ Dropdown ไปยังเอกสาร PDF ด้วย GroupDocs.Annotation
  สำหรับ .NET. คู่มือฉบับสมบูรณ์พร้อม code examples, best practices, และ troubleshooting
  tips.
keywords:
- add dropdown to pdf
- how to add dropdown
- generate pdf dropdown options
- interactive pdf forms .net
- groupdocs annotation tutorial
lastmod: '2026-06-11'
linktitle: เพิ่มคอมโพเนนต์ Dropdown ไปยังเอกสาร PDF
schemas:
- author: GroupDocs
  dateModified: '2026-06-11'
  description: Learn how to add dropdown components to PDF documents using GroupDocs.Annotation
    for .NET. Complete guide with code examples, best practices, and troubleshooting
    tips.
  headline: Add Dropdown to PDF .NET - Interactive PDF Forms Guide
  type: TechArticle
- questions:
  - answer: Yes. You can modify `PenColor`, `PenStyle`, `BorderWidth`, `Placeholder`,
      and even set a custom background color to match your brand guidelines.
    question: Can I customize the appearance of the dropdown component?
  - answer: It supports .NET Framework 4.x, .NET Core 3.1, and .NET 5/6/7, giving
      you full flexibility across legacy and modern applications.
    question: Is GroupDocs.Annotation for .NET compatible with all .NET versions?
  - answer: Absolutely. Just instantiate a separate `DropdownComponent` for each field,
      adjust the `Box` coordinates, and add them sequentially with `annotator.AddComponent`.
    question: Can I add multiple dropdown components to a single PDF document?
  - answer: Yes. In addition to dropdowns, you can add text highlights, sticky notes,
      area annotations, and more, enabling rich, interactive documents.
    question: Does GroupDocs.Annotation for .NET support other annotation types?
  - answer: Use `annotator.GetComponents` to read back the `DropdownComponent` objects;
      each contains the `SelectedOption` value that the end‑user chose.
    question: How do I retrieve user selections after the PDF is filled?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- pdf-forms
- dropdown-components
- interactive-pdf
- net-development
title: เพิ่ม Dropdown ไปยัง PDF .NET - คู่มือฟอร์ม PDF แบบโต้ตอบ
type: docs
url: /th/net/document-components/add-dropdown-component-to-pdf/
weight: 12
---

# เพิ่ม Dropdown ไปยัง PDF .NET - คู่มือฟอร์มเชิงโต้ตอบแบบครบถ้วน

การเพิ่ม dropdown ไปยังเอกสาร PDF ด้วยโปรแกรมเป็นวิธีที่ทรงพลังในการเปลี่ยนไฟล์คงที่ให้เป็นฟอร์มเชิงโต้ตอบ ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีเพิ่ม dropdown ไปยัง PDF** ด้วย GroupDocs.Annotation สำหรับ .NET, ดูกรณีการใช้งานจริง, และรับเคล็ดลับเกี่ยวกับประสิทธิภาพ, การจัดการข้อผิดพลาด, และการทดสอบ ไม่ว่าคุณจะกำลังสร้างเครื่องมือสำรวจ, พอร์ทัลลงทะเบียน, หรือโซลูชันการรายงานที่ซับซ้อน ขั้นตอนต่อไปนี้จะช่วยคุณสร้างคอมโพเนนต์ dropdown ที่แข็งแรงและเป็นมิตรกับผู้ใช้

## คำตอบสั้น
- **“add dropdown to pdf” ทำอะไร?** มันแทรกฟิลด์รายการที่เลือกได้ลงใน PDF ให้ผู้ใช้เลือกค่าหนึ่งจากตัวเลือกที่กำหนดไว้ล่วงหน้า  
- **ไลบรารีใดสนับสนุน?** GroupDocs.Annotation สำหรับ .NET มี API ที่จัดการเต็มรูปแบบสำหรับการสร้าง, สไตล์, และบันทึก dropdown  
- **ต้องมีไลเซนส์หรือไม่?** มีรุ่นทดลองฟรี; ต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานในสภาพแวดล้อมการผลิต  
- **สามารถเติมตัวเลือกแบบไดนามิกได้หรือไม่?** ได้ — ตัวเลือกสามารถสร้างจากฐานข้อมูล, เว็บเซอร์วิส, หรือไฟล์คอนฟิกในเวลารันไทม์  
- **รองรับ .NET 6 หรือไม่?** แน่นอน; ไลบรารีรองรับ .NET Framework 4.x, .NET Core 3.1, และ .NET 5/6/7

## “add dropdown to pdf” คืออะไร?
**“Add dropdown to pdf”** หมายถึงการแทรกฟิลด์ฟอร์ม dropdown ลงในเอกสาร PDF ด้วยโปรแกรม ฟิลด์นี้จะแสดงรายการค่าที่เลือกได้แบบกะทัดรัด ช่วยให้การเก็บข้อมูลมีประสิทธิภาพโดยไม่ทำให้หน้าเอกสารรก และสามารถสไตล์ให้ตรงกับเนื้อหารอบข้างเพื่อประสบการณ์ผู้ใช้ที่ราบรื่น

## ทำไมต้องใช้ GroupDocs.Annotation สำหรับ .NET เพื่อเพิ่มคอมโพเนนต์ dropdown?
GroupDocs.Annotation รองรับ **รูปแบบเข้า‑ออกกว่า 30 แบบ** และสามารถประมวลผล PDF ที่มี **สูงสุด 500 หน้า** พร้อมใช้หน่วยความจำไม่เกิน 100 MB ไลบรารีแทรก annotation โดยไม่เปลี่ยนแปลงสตรีมเนื้อหาเดิม ทำให้ข้อความ, รูปภาพ, และเวกเตอร์เดิมคงอยู่ไม่ถูกแก้ไข API ของมันเป็น thread‑safe สามารถประมวลผลหลายเอกสารพร้อมกันในสภาพแวดล้อมที่ต้องการ throughput สูง

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Annotation สำหรับ .NET** – ดาวน์โหลดไลบรารีจาก [here](https://releases.groupdocs.com/annotation/net/)  
- **สภาพแวดล้อมการพัฒนา .NET** – แนะนำให้ใช้ Visual Studio 2022 หรือใหม่กว่า  
- **PDF ต้นฉบับ** – PDF ใดก็ได้ที่คุณต้องการเพิ่ม dropdown เข้าไป  
- **ความรู้พื้นฐาน C#** – คุ้นเคยกับคลาส, อ็อบเจ็กต์, และคอลเลกชัน

**Pro Tip:** เมื่อจัดการกับ PDF ขนาดใหญ่หรืองานแบบแบตช์ ให้ห่อโลจิกการ annotation ไว้ในเมธอดแบบ asynchronous และใช้ `ConfigureAwait(false)` เพื่อให้ UI คงตอบสนองได้

## การนำเข้า Namespaces
ขั้นตอนแรกคือการนำชนิดที่ต้องการเข้าไปในสโคป Namespaces เหล่านี้เปิดเผยคลาส annotation หลัก, ตัวช่วยด้านเรขาคณิต, และยูทิลิตี้สีที่คุณต้องใช้

Namespace `GroupDocs.Annotation` มีคลาส `Annotator` ส่วน `GroupDocs.Annotation.Models` มีการกำหนด `DropdownComponent`

**Definition Anchor:** `Annotator` คือจุดเข้าหลักสำหรับการอ่าน, แก้ไข, และบันทึก annotation ของ PDF ใน GroupDocs.Annotation

## คู่มือการทำงานแบบขั้นตอน‑โดย‑ขั้นตอน

ต่อไปนี้เป็นการเดินผ่านแบบสั้นและตอบคำถามแต่ละหัวข้อโดยตรง (40‑70 คำ) เพื่อให้สอดคล้องกับข้อกำหนดการสกัดคำตอบของ AI

### ฉันจะตั้งค่าเส้นทางเอาต์พุตสำหรับ PDF ที่แก้ไขแล้วอย่างไร?
กำหนดเส้นทางระบบไฟล์ที่ PDF ที่มี annotation จะถูกบันทึกโดยใช้ `Path.Combine` เพื่อให้แน่ใจว่าตัวคั่นถูกต้องบน Windows, Linux, และ macOS ป้องกันการเขียนทับไฟล์ต้นฉบับ เลือกโฟลเดอร์แยกสำหรับเอาต์พุต ตรวจสอบสิทธิ์การเขียน และอาจเพิ่ม timestamp ไปที่ชื่อไฟล์เพื่อหลีกเลี่ยงการชนกันของชื่อเมื่อรันหลายครั้ง

### ฉันจะเริ่มต้นอินสแตนซ์ Annotator อย่างไร?
`Annotator` เป็นคลาสหลักที่อ่านและเขียน annotation ของ PDF สร้างอ็อบเจ็กต์ `Annotator` โดยส่งพาธของ PDF ต้นฉบับเข้าไปในคอนสตรัคเตอร์ภายในบล็อก `using` คำสั่ง `using` รับประกันว่าทรัพยากรที่ไม่จัดการจะถูกปล่อยทันทีเมื่อบล็อกสิ้นสุด ลดการรั่วของหน่วยความจำในบริการที่ทำงานต่อเนื่องและทำให้ thread‑safe

### ฉันจะสร้างคอมโพเนนต์ dropdown พร้อมตัวเลือกที่กำหนดเองอย่างไร?
`DropdownComponent` แทนฟิลด์ฟอร์ม PDF ที่แสดงเป็นรายการคลิกได้ สร้างอินสแตนซ์ `DropdownComponent`, ตั้งค่าคอลเลกชัน `Options`, และกำหนดคุณสมบัติสไตล์เช่น `Box`, `PenColor`, และ `Placeholder` คุณสมบัติ `SelectedOption` สามารถกำหนดค่าที่เลือกล่วงหน้าได้ ส่วน `PageNumber` (เริ่มจากศูนย์) กำหนดหน้าที่ dropdown ปรากฏ ให้คุณควบคุมตำแหน่งและลักษณะได้เต็มที่

### ฉันจะเพิ่มคอมโพเนนต์ dropdown ที่กำหนดค่าแล้วลงใน PDF อย่างไร?
`AddComponent` เพิ่มคอมโพเนนต์ annotation ใหม่ลงในเอกสาร PDF เรียก `annotator.AddComponent(dropdown)` เพื่อฝังคอมโพเนนต์ลงในเลเยอร์ annotation ของ PDF การทำงานนี้เป็น atomic; คอมโพเนนต์จะเป็นส่วนหนึ่งของเอกสารทันทีและจะมองเห็นได้ในโปรแกรมอ่าน PDF ที่รองรับฟิลด์ฟอร์ม ทำให้พฤติกรรมสอดคล้องกันบนทุกแพลตฟอร์ม

### ฉันจะบันทึก PDF พร้อม dropdown ใหม่อย่างไร?
`Save` เขียน PDF ที่แก้ไขแล้วพร้อม annotation ทั้งหมดลงไฟล์ เรียก `annotator.Save(outputPath)` เพื่อบันทึก PDF ที่มี annotation ไปยังดิสก์ เมธอดจะสร้างไฟล์ใหม่โดยคงต้นฉบับไว้ไม่เปลี่ยนแปลง ซึ่งสำคัญสำหรับการตรวจสอบ, ควบคุมเวอร์ชัน, และกลยุทธ์การย้อนกลับในสภาพแวดล้อมการผลิต

### ฉันจะแสดงเส้นทางเอาต์พุตเพื่อยืนยันผลอย่างไร?
ใช้ `Console.WriteLine` หรือ logger โครงสร้างเพื่อเขียนค่า `outputPath` ไปยังคอนโซลหรือไฟล์บันทึก การวนลูปข้อมูลนี้ช่วยให้นักพัฒนายืนยันการทำงานสำเร็จ, หาไฟล์ที่สร้างได้ง่ายขึ้น, และให้บันทึกการตรวจสอบที่สามารถเชื่อมโยงกับขั้นตอนการประมวลผลอื่น ๆ ใน pipeline อัตโนมัติ

## สถานการณ์การใช้งานทั่วไป

### ฉันจะเติมตัวเลือก dropdown แบบไดนามิกจากฐานข้อมูลอย่างไร?
ดึงแถวจากแหล่งข้อมูลของคุณ, แปลงเป็น `List<string>` แล้วกำหนดให้กับคุณสมบัติ `Options` วิธีนี้ทำให้ฟอร์มปรับตัวตามกฎธุรกิจที่เปลี่ยนแปลงโดยไม่ต้องคอมไพล์ใหม่ และคุณสามารถแคชรายการเพื่อประสิทธิภาพหรือรีเฟรชทุกคำขอเพื่อสะท้อนข้อมูลล่าสุด

### ฉันจะเพิ่มหลาย dropdown บนหน้าเดียวโดยไม่ทับกันอย่างไร?
คำนวณพิกัด `Box` ของแต่ละคอมโพเนนต์ตามการจัดวางแบบกริดหรือระยะขอบ ตรวจสอบให้ค่า `Y` ลดลง (หรือเพิ่มขึ้น ขึ้นอยู่กับระบบพิกัดของ PDF) ระหว่างคอมโพเนนต์ และตรวจสอบให้ความสูงรวมไม่เกินพื้นที่พิมพ์ของหน้า การเพิ่มช่องว่างแนวตั้งเล็กน้อย (เช่น 5 pt) ระหว่างกล่องช่วยรักษาความชัดเจนของภาพ

## เคล็ดลับด้านประสิทธิภาพและแนวปฏิบัติที่ดีที่สุด

### ฉันควรจัดการหน่วยความจำอย่างไรเมื่อประมวลผล PDF ขนาดใหญ่?
ประมวลผลทีละหน้าและใช้อินสแตนซ์ `Annotator` เพียงตัวเดียวเมื่อเป็นไปได้ ปล่อยคอลเลกชันขนาดใหญ่เช่นรายการตัวเลือกหลังจากเพิ่มคอมโพเนนต์แล้ว และหลีกเลี่ยงการโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำหากต้องการแก้ไขเพียงไม่กี่หน้า การสตรีม PDF ผ่าน API ลดการใช้หน่วยความจำสูงสุดและเพิ่ม throughput

### กลยุทธ์การจัดการข้อผิดพลาดที่แนะนำสำหรับการทำ annotation คืออะไร?
ห่อเวิร์กโฟลว์ annotation ทั้งหมดในบล็อก `try‑catch` ที่จับ `AnnotationException` และ `Exception` ทั่วไป บันทึกรายละเอียดข้อยกเว้นรวมถึง stack trace, ชื่อไฟล์, และตัวระบุ PDF แล้วหรือจะ rethrow เพื่อให้ชั้นบนจัดการต่อหรือคืนค่าโค้ดข้อผิดพลาดที่เป็นมิตรกับผู้ใช้ วิธีการระบบนี้ทำให้การล้มเหลวถูกบันทึกและวินิจฉัยได้โดยไม่สูญเสียเอกสารที่ประมวลผลแล้ว

### ฉันจะทำให้ตำแหน่งคอมโพเนนต์คงที่บน PDF viewer ต่าง ๆ อย่างไร?
ใช้แอตทริบิวต์ annotation มาตรฐานของ PDF เช่นเส้นขอบแบบ solid และสี RGB, และให้ความสูงของ `Box` อย่างน้อย **15 pt** เพื่อให้ Adobe Reader แสดงได้อย่างเต็มที่ ทดสอบผลลัพธ์บนอย่างน้อยสาม viewer (Adobe Acrobat Reader, ตัวอ่าน PDF ใน Chrome, และตัวอ่าน PDF บนมือถือ) เพื่อจับจุดบกพร่องการเรนเดอร์ตั้งแต่แรกและปรับสไตล์ตามต้องการ

## การแก้ไขปัญหาปัญหาทั่วไป

### ทำไม dropdown ไม่ปรากฏใน PDF?
ตรวจสอบให้พิกัด `Box` อยู่ภายในขนาดหน้ากระดาษ; คุณสามารถดึงขนาดหน้าด้วย `annotator.GetPageSize(pageNumber)` เพื่อตรวจสอบความกว้างและความสูง นอกจากนี้ตรวจสอบว่า `PageNumber` เริ่มจากศูนย์; ค่า `1` จะชี้ไปที่หน้าที่สอง ดังนั้นข้อผิดพลาด off‑by‑one อาจทำให้คอมโพเนนต์ซ่อนอยู่บนหน้าที่ไม่คาดคิด

### ทำไมบางตัวเลือกถึงถูกตัดหรือซ่อน?
เพิ่มความสูงของ `Box` หรือ ลดขนาดฟอนต์ผ่านการตั้งค่าสไตล์ของคอมโพเนนต์ บาง viewer ต้องการความสูงขั้นต่ำ **20 pt** เพื่อให้รายการ dropdown ขยายเต็ม ดังนั้นการปรับความสูงจะทำให้ตัวเลือกทั้งหมดมองเห็นได้เมื่อผู้ใช้คลิกฟิลด์

### ทำไมการประมวลผลจึงช้าลงเมื่อ PDF มีขนาดใหญ่มาก?
ไฟล์ขนาดใหญ่เพิ่มความกดดันของหน่วยความจำและการใช้ CPU แบ่งเอกสารเป็นชิ้นย่อยด้วย `annotator.ExtractPages`, ทำ annotation แต่ละชิ้นแยกกัน, แล้วรวมผลด้วย `annotator.Combine` วิธีแบ่งชิ้นนี้ลดการใช้หน่วยความจำสูงสุดและอนุญาตให้ประมวลผลแบบขนานของส่วนที่แยกจากกัน ทำให้ throughput โดยรวมดีขึ้นอย่างมาก

### ทำไม dropdown ถึงดูแตกต่างใน PDF reader ต่าง ๆ?
Viewer แต่ละตัวตีความ flag ของ annotation แตกต่างกัน ใช้เฉพาะคุณสมบัติหลัก (`PenColor`, `PenStyle`, `BorderWidth`) และหลีกเลี่ยงส่วนขยายเฉพาะผู้ผลิต การทดสอบอย่างสม่ำเสมอบน Adobe Acrobat, Chrome, และ viewer บนมือถือจะกำจัดความแตกต่างส่วนใหญ่และทำให้ประสบการณ์ผู้ใช้เป็นเอกภาพ

## สรุป
โดยทำตามคู่มือนี้คุณจะรู้ **วิธีเพิ่ม dropdown ไปยัง pdf** ด้วย GroupDocs.Annotation สำหรับ .NET ตั้งแต่การตั้งค่าสภาพแวดล้อม, การจัดการแหล่งข้อมูลแบบไดนามิก, จนถึงการเพิ่มประสิทธิภาพ ประเด็นสำคัญคือ:

- ใช้ `Annotator` และ `DropdownComponent` เพื่อสร้างฟิลด์ฟอร์มที่สอดคล้องมาตรฐานและมั่นคง  
- ปฏิบัติตามรูปแบบที่ดีที่สุดสำหรับเส้นทางไฟล์, การปล่อยทรัพยากร, และการจัดการข้อผิดพลาด  
- ทดสอบบน viewer หลายตัวและคำนึงถึงข้อจำกัดของขนาดหน้าเพื่อรับประกันประสบการณ์ผู้ใช้ที่ไร้ที่ติ

เริ่มจาก dropdown เดียว, ตรวจสอบผลลัพธ์, แล้วค่อยขยายเป็นฟอร์มที่ซับซ้อนพร้อมองค์ประกอบเชิงโต้ตอบหลายตัว ความยืดหยุ่นของ GroupDocs.Annotation ทำให้คุณสามารถพัฒนา PDF ตามความต้องการทางธุรกิจที่เปลี่ยนแปลงได้

## คำถามที่พบบ่อย

**Q: ฉันสามารถปรับแต่งลักษณะของคอมโพเนนต์ dropdown ได้หรือไม่?**  
A: ได้ คุณสามารถแก้ไข `PenColor`, `PenStyle`, `BorderWidth`, `Placeholder` และแม้กระทั่งตั้งค่าสีพื้นหลังแบบกำหนดเองให้สอดคล้องกับแนวทางแบรนด์ของคุณ

**Q: GroupDocs.Annotation สำหรับ .NET รองรับเวอร์ชัน .NET ทั้งหมดหรือไม่?**  
A: รองรับ .NET Framework 4.x, .NET Core 3.1, และ .NET 5/6/7 ให้ความยืดหยุ่นเต็มที่ทั้งในแอปพลิเคชันเก่าและใหม่

**Q: ฉันสามารถเพิ่มหลายคอมโพเนนต์ dropdown ลงใน PDF เอกสารเดียวได้หรือไม่?**  
A: แน่นอน เพียงสร้าง `DropdownComponent` แยกสำหรับแต่ละฟิลด์ ปรับพิกัด `Box` แล้วเพิ่มลงไปตามลำดับด้วย `annotator.AddComponent`

**Q: GroupDocs.Annotation สำหรับ .NET รองรับประเภท annotation อื่น ๆ หรือไม่?**  
A: ใช่ นอกจาก dropdown คุณยังสามารถเพิ่มการไฮไลท์ข้อความ, sticky notes, area annotations, และอื่น ๆ เพื่อสร้างเอกสารเชิงโต้ตอบที่หลากหลาย

**Q: ฉันจะดึงค่าที่ผู้ใช้เลือกหลังจาก PDF ถูกกรอกแล้วอย่างไร?**  
A: ใช้ `annotator.GetComponents` เพื่ออ่านอ็อบเจ็กต์ `DropdownComponent` แต่ละตัว; แต่ละอ็อบเจ็กต์จะมีค่า `SelectedOption` ที่ผู้ใช้เลือกไว้

**Q: มีเวอร์ชันทดลองที่สามารถทดสอบก่อนซื้อหรือไม่?**  
A: มี คุณสามารถดาวน์โหลดเวอร์ชันทดลองฟรีได้ [here](https://releases.groupdocs.com/). เวอร์ชันทดลองให้ฟังก์ชันเต็มพร้อมข้อจำกัดจำนวนหน้าที่ประมวลผล

**Q: ตัวเลือก dropdown สามารถโหลดจากแหล่งข้อมูลภายนอกได้หรือไม่?**  
A: แน่นอน ดึงข้อมูลจากฐานข้อมูล SQL, REST API, หรือไฟล์คอนฟิก, แปลงคอลเลกชันเป็น `List<string>` แล้วกำหนดให้กับ `Options` ของคอมโพเนนต์

**Q: จะเกิดอะไรขึ้นหากฉันตั้งค่าพิกัด Box ที่ไม่ถูกต้อง?**  
A: คอมโพเนนต์อาจถูกตัดหรือมองไม่เห็น ควรตรวจสอบให้ค่า X, Y, Width, และ Height อยู่ภายในขอบเขตของหน้า; ใช้ `annotator.GetPageSize` เป็นข้อมูลอ้างอิง

---

**Last Updated:** 2026-06-11  
**Tested With:** GroupDocs.Annotation 23.12 for .NET  
**Author:** GroupDocs

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

```csharp
DropdownComponent dropdown = new DropdownComponent
{
    Options = new List<string> { "Item1", "Item2", "Item3" },
    SelectedOption = null,
    Placeholder = "Choose option",
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is dropdown component",
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```

```csharp
annotator.Add(dropdown);
```

```csharp
annotator.Save("result.pdf");
```

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

```csharp
// Example: Populating from a data source
var countryOptions = GetCountriesFromDatabase(); // Your data retrieval method
dropdown.Options = countryOptions.Select(c => c.Name).ToList();
```

```csharp
// First dropdown
var dropdown1 = new DropdownComponent
{
    Options = new List<string> { "Option A", "Option B", "Option C" },
    Box = new Rectangle(100, 100, 150, 30), // X: 100, Y: 100
    // ... other properties
};

// Second dropdown (positioned below the first)
var dropdown2 = new DropdownComponent
{
    Options = new List<string> { "Choice 1", "Choice 2", "Choice 3" },
    Box = new Rectangle(100, 150, 150, 30), // X: 100, Y: 150
    // ... other properties
};
```

```csharp
try
{
    using (Annotator annotator = new Annotator("input.pdf"))
    {
        // Your dropdown creation code here
        annotator.Add(dropdown);
        annotator.Save("result.pdf");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error adding dropdown component: {ex.Message}");
    // Log the error or handle it according to your application's needs
}
```

## บทแนะนำที่เกี่ยวข้อง

- [PDF Interactive Components .NET - Complete Implementation Guide](/annotation/net/document-components/)
- [Add Checkbox to PDF .NET - Interactive PDF Components Guide](/annotation/net/document-components/add-checkbox-component-to-pdf/)
- [Add Form Fields to PDF .NET - Complete GroupDocs.Annotation Tutorial](/annotation/net/form-field-annotations/)