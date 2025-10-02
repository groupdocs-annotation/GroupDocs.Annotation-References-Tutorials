---
"description": "เรียนรู้วิธีการเพิ่มข้อความขีดเส้นใต้คำอธิบายประกอบลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและการสื่อสารได้อย่างง่ายดาย"
"linktitle": "เพิ่มคำอธิบายขีดเส้นใต้ข้อความลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายขีดเส้นใต้ข้อความลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# เพิ่มคำอธิบายขีดเส้นใต้ข้อความลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำขั้นตอนการเพิ่มคำอธิบายแบบขีดเส้นใต้ข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET คำอธิบายแบบขีดเส้นใต้ข้อความสามารถเป็นประโยชน์ในการเน้นย้ำส่วนต่างๆ ของเอกสาร เช่น ข้อความสำคัญหรือประเด็นสำคัญ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งข้อกำหนดเบื้องต้นต่อไปนี้:
1. GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework ไว้ในระบบของคุณแล้ว

## การนำเข้าเนมสเปซ
ก่อนอื่นให้เรานำเข้าเนมสเปซที่จำเป็นเข้าสู่โปรเจ็กต์ของเรา:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้เรามาแบ่งตัวอย่างออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ในขั้นตอนนี้ เราจะกำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
## ขั้นตอนที่ 2: เริ่มต้น Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
ที่นี่เราจะเริ่มต้นอินสแตนซ์ของ `Annotator` คลาสโดยระบุเส้นทางของเอกสารอินพุต
## ขั้นตอนที่ 3: สร้างคำอธิบายขีดเส้นใต้
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // งานที่ได้รับการสนับสนุนเฉพาะเอกสาร Word และ PDF เท่านั้น
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
ขั้นตอนนี้เกี่ยวข้องกับการสร้าง `UnderlineAnnotation` วัตถุที่มีคุณสมบัติต่างๆ เช่น สีแบบอักษร ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง สีขีดเส้นใต้ จุด และการตอบกลับ
## ขั้นตอนที่ 4: เพิ่มคำอธิบายลงในเอกสาร
```csharp
annotator.Add(underline);
```
ที่นี่เราจะเพิ่มคำอธิบายขีดเส้นใต้ให้กับเอกสาร
## ขั้นตอนที่ 5: บันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
annotator.Save(outputPath);
```
ในที่สุด เราบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการเพิ่มคำอธิบายแบบขีดเส้นใต้ข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีอันทรงพลังนี้มีตัวเลือกคำอธิบายต่างๆ เพื่อเพิ่มประสิทธิภาพการทำงานร่วมกันและการสื่อสารในเอกสาร
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายขีดเส้นใต้ได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติเช่น สี ความทึบ และตำแหน่งตามความต้องการของคุณได้
### GroupDocs.Annotation เข้ากันได้กับรูปแบบเอกสารอื่น ๆ หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารหลากหลาย รวมถึง Word และ PDF
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวได้หรือไม่
แน่นอน GroupDocs.Annotation ช่วยให้คุณสามารถเพิ่มคำอธิบายประกอบหลายประเภทลงในเอกสารได้
### มีรุ่นทดลองใช้งานฟรีสำหรับ GroupDocs.Annotation หรือไม่
ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้งานฟรีได้จาก [ที่นี่](https://releases-groupdocs.com/).
### ฉันจะได้รับการสนับสนุนสำหรับ GroupDocs.Annotation ได้จากที่ไหน
คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน GroupDocs.Annotation [ที่นี่](https://forum-groupdocs.com/c/annotation/10).