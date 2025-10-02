---
"description": "เรียนรู้วิธีการเพิ่มคำอธิบายประกอบรูปวงรีในเอกสารใน .NET โดยใช้ GroupDocs.Annotation ปรับปรุงการทำงานร่วมกันและการสื่อสารได้อย่างง่ายดาย"
"linktitle": "เพิ่มคำอธิบายวงรีลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายวงรีลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# เพิ่มคำอธิบายวงรีลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีเพิ่มคำอธิบายวงรีลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET คำแนะนำทีละขั้นตอนนี้จะแนะนำคุณตลอดกระบวนการเพื่อให้แน่ใจว่าคุณเข้าใจแต่ละขั้นตอนอย่างชัดเจน
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. GroupDocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): คุณจะต้องติดตั้ง IDE ในระบบของคุณ เช่น Visual Studio เพื่อเขียนและดำเนินการโค้ด

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นลงในโครงการของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบาย:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้น Annotator
เริ่มต้นตัวอธิบายโดยระบุเส้นทางเอกสารอินพุต:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ขั้นตอนที่ 3: สร้างคำอธิบายวงรี
สร้างอินสแตนซ์ของ `EllipseAnnotation` คลาสและกำหนดคุณสมบัติของมัน:
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
เพิ่มคำอธิบายวงรีลงในเอกสาร:
```csharp
annotator.Add(ellipse);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายลงในเส้นทางเอาต์พุต:
```csharp
annotator.Save(outputPath);
```

## บทสรุป
ขอแสดงความยินดี! คุณได้เพิ่มคำอธิบายวงรีลงในเอกสารสำเร็จแล้วโดยใช้ GroupDocs.Annotation สำหรับ .NET ขณะนี้คุณสามารถรวมฟังก์ชันนี้เข้ากับแอปพลิเคชัน .NET เพื่อปรับปรุงการทำงานร่วมกันและการสื่อสารในเอกสาร
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะของคำอธิบายวงรีได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ เช่น สีพื้นหลัง สีเส้นขอบ ความทึบ ฯลฯ ตามความต้องการของคุณได้
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารหลากหลาย เช่น PDF, DOCX, PPTX, XLSX และอื่นๆ อีกมากมาย
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวได้หรือไม่
ใช่ คุณสามารถเพิ่มคำอธิบายประกอบต่างๆ ได้หลายรายการ เช่น วงรี สี่เหลี่ยมผืนผ้า ข้อความ ฯลฯ ลงในเอกสารเดียวได้
### มีเวอร์ชันทดลองใช้สำหรับการทดสอบหรือไม่
ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีได้จาก [ที่นี่](https://releases.groupdocs.com/) เพื่อประเมินคุณสมบัติของมัน
### ฉันสามารถรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Annotation สำหรับ .NET ได้จากที่ไหน
คุณสามารถรับการสนับสนุนด้านเทคนิคได้จากฟอรัมชุมชน GroupDocs.Annotation [ที่นี่](https://forum-groupdocs.com/c/annotation/10).