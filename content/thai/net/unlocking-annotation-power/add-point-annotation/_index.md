---
title: เพิ่มคำอธิบายประกอบจุดลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบจุดลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่ม Point Annotation ลงใน PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET คำแนะนำทีละขั้นตอนเพื่อการผสานรวมที่ราบรื่น
weight: 17
url: /th/net/unlocking-annotation-power/add-point-annotation/
---
## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นเครื่องมืออันทรงประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถเพิ่มคำอธิบายประกอบประเภทต่างๆ ลงในเอกสารโดยทางโปรแกรม ในบทช่วยสอนนี้ เราจะเน้นไปที่การเพิ่ม Point Annotation ให้กับเอกสารโดยใช้ C#
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
2. ติดตั้ง Visual Studio บนระบบของคุณแล้ว
3.  ติดตั้ง GroupDocs.Annotation สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).

## การนำเข้าเนมสเปซที่จำเป็น
ในการเริ่มต้น คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ในขั้นตอนนี้ เราจะกำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 ที่นี่เราเริ่มต้น`Annotator` วัตถุที่มีเอกสารอินพุต ("input.pdf")
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบจุด
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 ในขั้นตอนนี้ เราจะสร้าง a`PointAnnotation` object และระบุคุณสมบัติ เช่น ตำแหน่ง ข้อความ เลขหน้า และการตอบกลับ
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
```csharp
annotator.Add(point);
```
ที่นี่ เราเพิ่มคำอธิบายประกอบแบบจุดที่สร้างขึ้นให้กับเอกสาร
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save(outputPath);
```
สุดท้าย เราจะบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่ม Point Annotation ให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยไลบรารีอันทรงพลังนี้ คุณสามารถเพิ่มประสิทธิภาพแอปพลิเคชันการจัดการเอกสารของคุณได้โดยการรวมฟังก์ชันคำอธิบายประกอบเข้าไว้ด้วยกัน
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
อย่างแน่นอน! GroupDocs.Annotation สำหรับ .NET มีตัวเลือกมากมายในการปรับแต่งรูปลักษณ์ของคำอธิบายประกอบให้เหมาะกับความต้องการของแอปพลิเคชันของคุณ
### GroupDocs.Annotation สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับปัญหาหรือข้อสงสัยที่เกี่ยวข้องกับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
 คุณสามารถรับการสนับสนุนจากฟอรัม GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).
### ฉันสามารถขอรับใบอนุญาตชั่วคราวเพื่อการทดสอบได้หรือไม่
 ใช่ คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).