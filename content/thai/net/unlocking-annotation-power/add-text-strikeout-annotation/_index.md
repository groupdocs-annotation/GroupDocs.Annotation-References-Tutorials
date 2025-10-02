---
"description": "เรียนรู้วิธีเพิ่มคำอธิบายข้อความขีดฆ่าลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงกระบวนการทำงานร่วมกันและการตรวจสอบเอกสารอย่างมีประสิทธิภาพ"
"linktitle": "เพิ่มคำอธิบายการขีดฆ่าข้อความลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายการขีดฆ่าข้อความลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# เพิ่มคำอธิบายการขีดฆ่าข้อความลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะมาเรียนรู้วิธีการเพิ่มคำอธิบายข้อความขีดฆ่าลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีนี้มอบเครื่องมืออันทรงพลังสำหรับใส่คำอธิบายประเภทเอกสารต่างๆ เพื่อปรับปรุงการทำงานร่วมกันและกระบวนการตรวจสอบเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Annotation สำหรับ .NET: ติดตั้งไลบรารี คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการพัฒนา .NET
3. เอกสาร: เตรียมเอกสารเพื่อใส่คำอธิบายประกอบ เช่น ไฟล์ PDF

## การนำเข้าเนมสเปซ
ก่อนอื่น นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs หมายเหตุ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้ มาแบ่งกระบวนการเพิ่มคำอธิบายการขีดฆ่าข้อความออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ที่นี่เราจะกำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
## ขั้นตอนที่ 2: เริ่มต้น Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
เริ่มต้นวัตถุ Annotator โดยระบุเส้นทางไปยังเอกสารอินพุต (ไฟล์ PDF ในกรณีนี้)
## ขั้นตอนที่ 3: สร้างคำอธิบายการขีดฆ่า
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
สร้างอ็อบเจ็กต์ StrikeoutAnnotation ที่มีคุณสมบัติตามต้องการ เช่น ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง จุด (พิกัด) และการตอบกลับ
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
```csharp
annotator.Add(strikeout);
```
เพิ่มคำอธิบายการขีดฆ่าที่สร้างขึ้นลงในเอกสาร
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save(outputPath);
```
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการเพิ่มคำอธิบายข้อความขีดฆ่าลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีอันทรงพลังนี้ช่วยให้สามารถใส่คำอธิบายประกอบเอกสารได้อย่างมีประสิทธิภาพ ช่วยเพิ่มประสิทธิภาพในการทำงานร่วมกันและกระบวนการตรวจสอบเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Annotation เข้ากันได้กับรูปแบบเอกสารต่างๆ หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารต่างๆ มากมาย เช่น PDF, Word, Excel, PowerPoint และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
แน่นอน คุณสามารถปรับแต่งคุณสมบัติของคำอธิบายประกอบ เช่น สี ความทึบ ขนาดตัวอักษร และอื่นๆ ตามความต้องการของคุณได้
### GroupDocs.Annotation มีคุณลักษณะการทำงานร่วมกันหรือไม่
ใช่ GroupDocs.Annotation ช่วยอำนวยความสะดวกในการทำงานร่วมกันโดยอนุญาตให้ผู้ใช้เพิ่มความคิดเห็น คำตอบ และคำอธิบายประกอบลงในเอกสารได้
### มีการทดลองใช้ฟรีหรือไม่?
ใช่ คุณสามารถใช้ประโยชน์จากการทดลองใช้ฟรีได้จาก [ที่นี่](https://releases-groupdocs.com/).
### ฉันจะได้รับการสนับสนุนสำหรับ GroupDocs.Annotation ได้จากที่ไหน
คุณสามารถรับการสนับสนุนได้จาก [ฟอรั่ม GroupDocs.Annotation](https://forum-groupdocs.com/c/annotation/10).