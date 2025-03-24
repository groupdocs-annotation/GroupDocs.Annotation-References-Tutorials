---
title: เพิ่มคำอธิบายประกอบเน้นข้อความลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบเน้นข้อความลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบแบบเน้นข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและประสิทธิภาพการทำงานด้วยความครอบคลุมนี้
weight: 22
url: /th/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## การแนะนำ
ในด้านการจัดการเอกสารและการทำงานร่วมกัน GroupDocs.Annotation สำหรับ .NET ถือเป็นโซลูชันที่มีประสิทธิภาพ ช่วยให้นักพัฒนาสามารถรวมคำอธิบายประกอบแบบเน้นข้อความเข้ากับแอปพลิเคชันของตนได้อย่างราบรื่น บทช่วยสอนนี้ทำหน้าที่เป็นแนวทางที่ครอบคลุมในการเพิ่มคำอธิบายประกอบแบบเน้นข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยคำแนะนำทีละขั้นตอนและคำอธิบายโดยละเอียด คุณจะได้รับความเชี่ยวชาญในการควบคุมความสามารถของไลบรารีอันทรงพลังนี้
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกการใช้งานคำอธิบายประกอบแบบเน้นข้อความ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. การตั้งค่าสภาพแวดล้อม: มีสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการกำหนดค่าสำหรับการพัฒนา .NET
2.  การติดตั้ง GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จากไฟล์ที่ให้มา[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/annotation/net/).
3. ความคุ้นเคยกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
4. เอกสารที่จะใส่คำอธิบายประกอบ: เตรียมเอกสาร (เช่น PDF) ที่คุณตั้งใจจะใส่คำอธิบายประกอบ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโค้ด C# ของคุณเพื่อใช้ฟังก์ชันการทำงานของ GroupDocs.Annotation สำหรับ .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#ตอนนี้ เราจะแจกแจงขั้นตอนการเพิ่มคำอธิบายประกอบแบบเน้นข้อความออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
ระบุเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
 สร้างอินสแตนซ์ของ`Annotator` คลาสส่งชื่อไฟล์เอกสารเป็นพารามิเตอร์:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบไฮไลต์
 ยกตัวอย่าง`HighlightAnnotation` วัตถุและกำหนดค่าคุณสมบัติ:
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
เพิ่มคำอธิบายประกอบไฮไลต์ที่สร้างขึ้นลงในเอกสาร:
```csharp
annotator.Add(highlight);
```
## ขั้นตอนที่ 5: บันทึกเอกสารคำอธิบายประกอบ
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ:
```csharp
annotator.Save(outputPath);
```

## บทสรุป
โดยสรุป GroupDocs.Annotation สำหรับ .NET นำเสนอแนวทางที่มีประสิทธิภาพในการรวมคำอธิบายประกอบแบบเน้นข้อความลงในเอกสาร ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ นักพัฒนาสามารถปรับปรุงการทำงานร่วมกันและประสิทธิภาพการทำงานของเอกสารภายในแอปพลิเคชันของตนได้อย่างราบรื่น
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel และอื่นๆ โปรดดูเอกสารประกอบสำหรับรายการทั้งหมด
### คำอธิบายประกอบสามารถปรับแต่งตามความต้องการเฉพาะได้หรือไม่
ใช่ นักพัฒนาสามารถควบคุมคุณสมบัติและรูปลักษณ์ของคำอธิบายประกอบได้อย่างเต็มที่ ทำให้สามารถปรับแต่งให้ตรงตามความต้องการที่หลากหลายได้
### GroupDocs.Annotation สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ได้ คุณสามารถสำรวจคุณลักษณะต่างๆ ของ GroupDocs.Annotation สำหรับ .NET ได้โดยการเข้าถึงรุ่นทดลองใช้ฟรีจากโปรแกรมที่ให้มา[ลิงค์](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับปัญหาหรือข้อสงสัยที่เกี่ยวข้องกับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
 สำหรับการสนับสนุนและความช่วยเหลือ คุณสามารถไปที่ฟอรัม GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation สำหรับ .NET มีตัวเลือกสิทธิ์การใช้งานใดบ้าง
 GroupDocs.Annotation สำหรับ .NET มีตัวเลือกการอนุญาตให้ใช้สิทธิที่หลากหลาย รวมถึงใบอนุญาตชั่วคราวสำหรับวัตถุประสงค์ในการทดสอบ และใบอนุญาตเชิงพาณิชย์สำหรับสภาพแวดล้อมการใช้งานจริง เยี่ยมชมหน้าการซื้อ[ที่นี่](https://purchase.groupdocs.com/buy) สำหรับรายละเอียดเพิ่มเติม