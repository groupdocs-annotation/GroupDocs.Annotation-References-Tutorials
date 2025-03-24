---
title: ลบการตอบกลับคำอธิบายประกอบใน .NET
linktitle: ลบการตอบกลับคำอธิบายประกอบใน .NET
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีลบการตอบกลับคำอธิบายประกอบใน .NET โดยใช้ GroupDocs.Annotation คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
weight: 15
url: /th/net/removing-annotations/remove-replies-to-annotations/
---

# ลบการตอบกลับคำอธิบายประกอบใน .NET

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีลบการตอบกลับคำอธิบายประกอบใน .NET โดยใช้ GroupDocs.Annotation GroupDocs.Annotation เป็นไลบรารี .NET อันทรงพลังที่ช่วยให้นักพัฒนาใส่คำอธิบายประกอบในเอกสารได้อย่างง่ายดาย ไม่ว่าจะเป็นการเพิ่มความคิดเห็น การเน้นข้อความ หรือการเพิ่มตราประทับ GroupDocs.Annotation มีชุดเครื่องมือที่ครอบคลุมสำหรับคำอธิบายประกอบในเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และ .NET
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
-  ติดตั้ง GroupDocs.Annotation สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
- ความเข้าใจเกี่ยวกับวิธีการทำงานของคำอธิบายประกอบใน GroupDocs.Annotation

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการ GroupDocs.Annotation ในโค้ด C# ของคุณ
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
 โหลดเอกสารที่มีคำอธิบายประกอบพร้อมการตอบกลับโดยใช้`Annotator` ระดับ.
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: รับการรวบรวมคำอธิบายประกอบ
ดึงข้อมูลคอลเลกชันคำอธิบายประกอบจากเอกสาร
```csharp
List<AnnotationBase> annotations = annotator.Get();
```
## ขั้นตอนที่ 3: ลบการตอบกลับ
ลบการตอบกลับคำอธิบายประกอบ ตัวอย่างเช่น ลองลบคำตอบแรกตามดัชนี
```csharp
annotations[0].Replies.RemoveAt(0);
```
## ขั้นตอนที่ 4: บันทึกการเปลี่ยนแปลง
บันทึกการเปลี่ยนแปลงที่ทำกับคำอธิบายประกอบ
```csharp
annotator.Update(annotations);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารพร้อมคำอธิบายประกอบที่แก้ไขไปยังตำแหน่งที่ต้องการ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```
## ขั้นตอนที่ 6: แสดงการยืนยัน
แสดงข้อความยืนยันว่าบันทึกเอกสารเรียบร้อยแล้ว
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีลบการตอบกลับคำอธิบายประกอบใน .NET โดยใช้ GroupDocs.Annotation ด้วยขั้นตอนง่ายๆ เพียงไม่กี่ขั้นตอน คุณสามารถจัดการคำอธิบายประกอบในเอกสารของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถลบการตอบกลับหลายรายการพร้อมกันได้หรือไม่
ใช่ คุณสามารถลบการตอบกลับหลายรายการได้โดยการวนซ้ำในคอลเลกชันการตอบกลับและลบออกทีละรายการ
### GroupDocs.Annotation รองรับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### GroupDocs.Annotation มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Annotation ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะขอความช่วยเหลือและสนับสนุน GroupDocs.Annotation ได้ที่ไหน
 คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10) เพื่อขอความช่วยเหลือและสนับสนุน