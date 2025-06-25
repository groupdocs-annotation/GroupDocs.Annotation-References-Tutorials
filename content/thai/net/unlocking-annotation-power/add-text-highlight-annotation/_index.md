---
"description": "เรียนรู้วิธีเพิ่มคำอธิบายเน้นข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและประสิทธิภาพการทำงานด้วยเอกสารที่ครอบคลุมนี้"
"linktitle": "เพิ่มคำอธิบายเน้นข้อความลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายเน้นข้อความลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# เพิ่มคำอธิบายเน้นข้อความลงในเอกสาร

## การแนะนำ
GroupDocs.Annotation สำหรับ .NET ถือเป็นโซลูชันที่มีประสิทธิภาพสำหรับการจัดการเอกสารและการทำงานร่วมกัน ช่วยให้นักพัฒนาสามารถผสานรวมคำอธิบายเน้นข้อความลงในแอปพลิเคชันได้อย่างราบรื่น บทช่วยสอนนี้ทำหน้าที่เป็นแนวทางที่ครอบคลุมในการเพิ่มคำอธิบายเน้นข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยคำแนะนำทีละขั้นตอนและคำอธิบายโดยละเอียด คุณจะได้รับความชำนาญในการใช้ความสามารถของไลบรารีอันทรงพลังนี้
## ข้อกำหนดเบื้องต้น
ก่อนจะลงลึกถึงการใช้งานคำอธิบายเน้นข้อความ โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. การตั้งค่าสภาพแวดล้อม: มีการกำหนดค่าสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการพัฒนา .NET
2. การติดตั้ง GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จากที่ให้มา [ลิงค์ดาวน์โหลด](https://releases-groupdocs.com/annotation/net/).
3. ความคุ้นเคยกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
4. เอกสารที่จะใส่คำอธิบายประกอบ: เตรียมเอกสาร (เช่น PDF) ที่คุณต้องการใส่คำอธิบายประกอบ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโค้ด C# ของคุณ เพื่อใช้ฟังก์ชันการทำงานของ GroupDocs.Annotation สำหรับ .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#ตอนนี้ เรามาแบ่งกระบวนการเพิ่มข้อความไฮไลต์เป็นขั้นตอนต่างๆ กัน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
ระบุเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบาย:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้น Annotator
สร้างอินสแตนซ์ของ `Annotator` คลาส ส่งผ่านชื่อไฟล์เอกสารเป็นพารามิเตอร์:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## ขั้นตอนที่ 3: สร้างคำอธิบายเน้นข้อความ
สร้างตัวอย่าง `HighlightAnnotation` วัตถุและกำหนดค่าคุณสมบัติของมัน:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
เพิ่มคำอธิบายเน้นข้อความที่สร้างขึ้นลงในเอกสาร:
```csharp
annotator.Add(highlight);
```
## ขั้นตอนที่ 5: บันทึกเอกสารที่มีคำอธิบายประกอบ
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ:
```csharp
annotator.Save(outputPath);
```

## บทสรุป
โดยสรุป GroupDocs.Annotation สำหรับ .NET นำเสนอแนวทางที่คล่องตัวในการรวมคำอธิบายเน้นข้อความลงในเอกสาร ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ นักพัฒนาสามารถปรับปรุงการทำงานร่วมกันในเอกสารและประสิทธิภาพการทำงานภายในแอปพลิเคชันของตนได้อย่างราบรื่น
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารต่างๆ รวมถึง PDF, Word, Excel และอื่นๆ อีกมากมาย โปรดดูเอกสารประกอบเพื่อดูรายการทั้งหมด
### คำอธิบายสามารถปรับแต่งตามความต้องการเฉพาะได้หรือไม่
ใช่ นักพัฒนาสามารถควบคุมคุณสมบัติและลักษณะของคำอธิบายประกอบได้อย่างเต็มที่ ช่วยให้ปรับแต่งเพื่อตอบสนองความต้องการที่หลากหลายได้
### มีรุ่นทดลองใช้งานฟรีสำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Annotation สำหรับ .NET ได้โดยเข้าถึงรุ่นทดลองใช้งานฟรีจากที่ให้มา [ลิงค์](https://releases-groupdocs.com/).
### ฉันจะได้รับการสนับสนุนสำหรับปัญหาหรือคำถามต่างๆ ที่เกี่ยวข้องกับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
หากต้องการการสนับสนุนและความช่วยเหลือ คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Annotation [ที่นี่](https://forum-groupdocs.com/c/annotation/10).
### ตัวเลือกการออกใบอนุญาตใดบ้างที่มีให้เลือกใช้สำหรับ GroupDocs.Annotation สำหรับ .NET?
GroupDocs.Annotation สำหรับ .NET นำเสนอตัวเลือกการออกใบอนุญาตต่างๆ รวมถึงใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการทดสอบและใบอนุญาตเชิงพาณิชย์สำหรับสภาพแวดล้อมการผลิต เยี่ยมชมหน้าการซื้อ [ที่นี่](https://purchase.groupdocs.com/buy) สำหรับรายละเอียดเพิ่มเติม