---
title: เพิ่มคำอธิบายประกอบวงรีลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบวงรีลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบวงรีให้กับเอกสารใน .NET โดยใช้ GroupDocs.Annotation ปรับปรุงการทำงานร่วมกันและการสื่อสารได้อย่างง่ายดาย
weight: 13
url: /th/net/unlocking-annotation-power/add-ellipse-annotation/
---
## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีเพิ่มคำอธิบายประกอบวงรีให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET คำแนะนำทีละขั้นตอนนี้จะแนะนำคุณตลอดกระบวนการ เพื่อให้มั่นใจว่าคุณเข้าใจแต่ละขั้นตอนอย่างชัดเจน
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): คุณจะต้องติดตั้ง IDE บนระบบของคุณ เช่น Visual Studio เพื่อเขียนและรันโค้ด

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นไปยังโปรเจ็กต์ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
เริ่มต้นคำอธิบายประกอบโดยระบุเส้นทางเอกสารอินพุต:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบวงรี
 สร้างอินสแตนซ์ของ`EllipseAnnotation` คลาสและตั้งค่าคุณสมบัติ:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
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
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
เพิ่มคำอธิบายประกอบวงรีให้กับเอกสาร:
```csharp
annotator.Add(ellipse);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุต:
```csharp
annotator.Save(outputPath);
```

## บทสรุป
ยินดีด้วย! คุณได้เพิ่มคำอธิบายประกอบวงรีลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET เรียบร้อยแล้ว ตอนนี้คุณสามารถรวมฟังก์ชันการทำงานนี้เข้ากับแอปพลิเคชัน .NET ของคุณเพื่อปรับปรุงการทำงานร่วมกันและการสื่อสารของเอกสาร
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบวงรีได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ได้ เช่น สีพื้นหลัง สีเส้นขอบ ความทึบ ฯลฯ ตามความต้องการของคุณ
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, PPTX, XLSX และอื่นๆ
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวได้หรือไม่
ได้ คุณสามารถเพิ่มคำอธิบายประกอบได้หลายรายการ เช่น วงรี สี่เหลี่ยม ข้อความ ฯลฯ ลงในเอกสารเดียว
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/) เพื่อประเมินคุณสมบัติของมัน
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน
 คุณสามารถรับการสนับสนุนทางเทคนิคได้จากฟอรัมชุมชน GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).