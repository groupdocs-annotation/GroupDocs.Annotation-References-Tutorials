---
title: เพิ่มคำอธิบายประกอบการเรียบเรียงข้อความลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบการเรียบเรียงข้อความลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบการแก้ไขข้อความลงในเอกสาร PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET ปกป้องข้อมูลที่ละเอียดอ่อนได้อย่างง่ายดาย
weight: 23
url: /th/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# เพิ่มคำอธิบายประกอบการเรียบเรียงข้อความลงในเอกสาร

## การแนะนำ
การเพิ่มคำอธิบายประกอบการแก้ไขข้อความลงในเอกสารอาจเป็นขั้นตอนสำคัญในการจัดการข้อมูลที่ละเอียดอ่อนอย่างปลอดภัย GroupDocs.Annotation สำหรับ .NET มอบโซลูชันที่มีประสิทธิภาพเพื่อให้บรรลุเป้าหมายนี้ได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มคำอธิบายประกอบการแก้ไขข้อความลงในเอกสารของคุณทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาด้วย IDE ที่เข้ากันได้กับ .NET เช่น Visual Studio

## การนำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นให้กับโปรเจ็กต์ของเรา:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่คุณต้องการบันทึกเอกสารที่มีคำอธิบายประกอบ ตรวจสอบให้แน่ใจว่าสามารถเข้าถึงได้และเขียนได้
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
 เริ่มต้นคำอธิบายประกอบด้วยเส้นทางเอกสารอินพุต แทนที่`"input.pdf"` พร้อมเส้นทางไปยังเอกสารของคุณ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบการโต้ตอบข้อความ
 สร้างก`TextRedactionAnnotation`วัตถุที่มีคุณสมบัติที่ต้องการเช่น`PageNumber`, `FontColor` , และ`Points`- ปรับแต่งคำอธิบายประกอบตามความต้องการของคุณ
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบและบันทึก
เพิ่มคำอธิบายประกอบที่สร้างขึ้นให้กับเอกสารโดยใช้คำอธิบายประกอบและบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## ขั้นตอนที่ 5: ตรวจสอบผลลัพธ์
สุดท้าย ยืนยันว่าเอกสารได้รับการบันทึกไปยังเส้นทางเอาต์พุตที่ระบุเรียบร้อยแล้ว
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้อธิบายขั้นตอนการเพิ่มคำอธิบายประกอบการแก้ไขข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยขั้นตอนเหล่านี้ คุณสามารถจัดการข้อมูลที่ละเอียดอ่อนภายในเอกสารของคุณได้อย่างปลอดภัย
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบการปกปิดข้อความได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ได้ เช่น สีแบบอักษร สีเติม และความทึบเพื่อให้เหมาะกับความต้องการของคุณ
### มีรุ่นทดลองใช้ก่อนซื้อหรือไม่?
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนได้อย่างไรหากฉันประสบปัญหาใดๆ
 คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).
### ฉันจำเป็นต้องมีใบอนุญาตชั่วคราวเพื่อการทดสอบหรือไม่?
 ใช่ คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[หน้าซื้อ](https://purchase.groupdocs.com/temporary-license/)สำหรับการทดสอบ
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวได้หรือไม่
แน่นอนว่า GroupDocs.Annotation ช่วยให้คุณสามารถเพิ่มคำอธิบายประกอบประเภทต่างๆ และหลายอินสแตนซ์ลงในเอกสารเดียวได้