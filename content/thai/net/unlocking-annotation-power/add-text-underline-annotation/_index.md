---
title: เพิ่มข้อความที่ขีดเส้นใต้คำอธิบายประกอบลงในเอกสาร
linktitle: เพิ่มข้อความที่ขีดเส้นใต้คำอธิบายประกอบลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มข้อความที่ขีดเส้นใต้คำอธิบายประกอบลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและการสื่อสารได้อย่างง่ายดาย
type: docs
weight: 27
url: /th/net/unlocking-annotation-power/add-text-underline-annotation/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการเพิ่มข้อความที่ขีดเส้นใต้คำอธิบายประกอบให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET คำอธิบายประกอบที่ขีดเส้นใต้อาจเป็นประโยชน์ในการเน้นส่วนเฉพาะของเอกสาร เช่น ข้อความสำคัญหรือประเด็นสำคัญ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนระบบของคุณ

## การนำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นเข้าสู่โปรเจ็กต์ของเรา:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้ เรามาแบ่งตัวอย่างออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ในขั้นตอนนี้ เราจะกำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 ที่นี่เราเริ่มต้นอินสแตนซ์ของ`Annotator` คลาสโดยการจัดเตรียมเส้นทางของเอกสารอินพุต
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบแบบขีดเส้นใต้
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // รองรับการทำงานเฉพาะเอกสาร Word และ PDF เท่านั้น
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
 ขั้นตอนนี้เกี่ยวข้องกับการสร้าง`UnderlineAnnotation`วัตถุที่มีคุณสมบัติหลากหลาย เช่น สีแบบอักษร ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง สีขีดเส้นใต้ จุด และการตอบกลับ
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบลงในเอกสาร
```csharp
annotator.Add(underline);
```
ที่นี่ เราเพิ่มคำอธิบายประกอบที่ขีดเส้นใต้ลงในเอกสาร
## ขั้นตอนที่ 5: บันทึกเอกสารคำอธิบายประกอบ
```csharp
annotator.Save(outputPath);
```
สุดท้าย เราจะบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มข้อความที่ขีดเส้นใต้คำอธิบายประกอบให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีอันทรงพลังนี้มีตัวเลือกคำอธิบายประกอบที่หลากหลายเพื่อปรับปรุงการทำงานร่วมกันและการสื่อสารในเอกสาร
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่ขีดเส้นใต้ได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติ เช่น สี ความทึบ และตำแหน่งได้ตามความต้องการของคุณ
### GroupDocs.Annotation เข้ากันได้กับรูปแบบเอกสารที่แตกต่างกันหรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word และ PDF
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวได้หรือไม่
GroupDocs.Annotation ช่วยให้คุณสามารถเพิ่มคำอธิบายประกอบหลายประเภทลงในเอกสารได้
### GroupDocs.Annotation มีให้ทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Annotation ได้ที่ไหน
 คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).