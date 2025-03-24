---
title: เพิ่มคำอธิบายประกอบการขีดทับข้อความลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบการขีดทับข้อความลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบแบบขีดทับข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงกระบวนการทำงานร่วมกันและการตรวจสอบเอกสารอย่างมีประสิทธิภาพ
weight: 26
url: /th/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# เพิ่มคำอธิบายประกอบการขีดทับข้อความลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีเพิ่มคำอธิบายประกอบแบบขีดฆ่าลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีนี้มีเครื่องมือที่มีประสิทธิภาพสำหรับใส่คำอธิบายประกอบเอกสารประเภทต่างๆ เพิ่มประสิทธิภาพการทำงานร่วมกันและกระบวนการตรวจสอบเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET: ติดตั้งไลบรารี คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการพัฒนา .NET
3. เอกสาร: เตรียมเอกสารที่พร้อมสำหรับใส่คำอธิบายประกอบ เช่น ไฟล์ PDF

## การนำเข้าเนมสเปซ
ขั้นแรก ให้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs คำอธิบายประกอบ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้ เราจะแจกแจงขั้นตอนการเพิ่มคำอธิบายประกอบที่มีการขีดทับข้อความออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ที่นี่ เรากำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
เริ่มต้นวัตถุ Annotator โดยระบุเส้นทางไปยังเอกสารอินพุต (ไฟล์ PDF ในกรณีนี้)
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบขีดฆ่า
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
สร้างวัตถุ StrikeoutAnnotation ที่มีคุณสมบัติที่ต้องการ เช่น ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง จุด (พิกัด) และการตอบกลับ
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
```csharp
annotator.Add(strikeout);
```
เพิ่มคำอธิบายประกอบขีดฆ่าที่สร้างขึ้นให้กับเอกสาร
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save(outputPath);
```
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มคำอธิบายประกอบแบบขีดฆ่าลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีอันทรงพลังนี้ช่วยให้สามารถใส่คำอธิบายประกอบเอกสารได้อย่างมีประสิทธิภาพ เพิ่มประสิทธิภาพการทำงานร่วมกันและกระบวนการตรวจสอบเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Annotation เข้ากันได้กับรูปแบบเอกสารต่างๆ หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
แน่นอน คุณสามารถปรับแต่งคุณสมบัติคำอธิบายประกอบ เช่น สี ความทึบ ขนาดตัวอักษร และอื่นๆ ตามความต้องการของคุณ
### GroupDocs.Annotation มีฟีเจอร์การทำงานร่วมกันหรือไม่
ใช่ GroupDocs.Annotation อำนวยความสะดวกในการทำงานร่วมกันโดยอนุญาตให้ผู้ใช้เพิ่มความคิดเห็น การตอบกลับ และคำอธิบายประกอบลงในเอกสาร
### มีการทดลองใช้ฟรีหรือไม่?
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Annotation ได้ที่ไหน
 คุณสามารถรับการสนับสนุนจาก[GroupDocs.ฟอรัมคำอธิบายประกอบ](https://forum.groupdocs.com/c/annotation/10).