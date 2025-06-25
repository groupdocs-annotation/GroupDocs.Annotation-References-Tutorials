---
"description": "เรียนรู้วิธีการเพิ่มคำอธิบายจุดใน PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET คำแนะนำทีละขั้นตอนสำหรับการผสานรวมที่ราบรื่น"
"linktitle": "เพิ่มคำอธิบายจุดลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายจุดลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# เพิ่มคำอธิบายจุดลงในเอกสาร

## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นเครื่องมืออันทรงพลังที่ช่วยให้นักพัฒนาสามารถเพิ่มคำอธิบายประกอบประเภทต่างๆ ลงในเอกสารด้วยโปรแกรม ในบทช่วยสอนนี้ เราจะเน้นที่การเพิ่มคำอธิบายประกอบแบบจุดลงในเอกสารโดยใช้ C#
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
2. Visual Studio ติดตั้งอยู่บนระบบของคุณแล้ว
3. ติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).

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
## ขั้นตอนที่ 2: เริ่มต้น Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
ที่นี่เราจะเริ่มต้น `Annotator` วัตถุที่มีเอกสารอินพุต ("input.pdf")
## ขั้นตอนที่ 3: สร้างคำอธิบายจุด
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
ในขั้นตอนนี้เราจะสร้าง `PointAnnotation` วัตถุและระบุคุณสมบัติเช่น ตำแหน่ง ข้อความ หมายเลขหน้า และการตอบกลับ
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
```csharp
annotator.Add(point);
```
ที่นี่เราจะเพิ่มคำอธิบายจุดที่สร้างขึ้นลงในเอกสาร
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save(outputPath);
```
ในที่สุด เราบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการเพิ่มคำอธิบายประกอบแบบจุดลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยไลบรารีอันทรงพลังนี้ คุณสามารถปรับปรุงแอปพลิเคชันการจัดการเอกสารของคุณได้ด้วยการรวมฟังก์ชันคำอธิบายประกอบ
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารต่างๆ มากมาย เช่น PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
แน่นอน! GroupDocs.Annotation สำหรับ .NET มีตัวเลือกมากมายในการปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบเพื่อให้เหมาะกับความต้องการของแอปพลิเคชันของคุณ
### มีรุ่นทดลองใช้งานฟรีสำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
ใช่ คุณสามารถใช้ประโยชน์จากการทดลองใช้ฟรีได้จาก [ที่นี่](https://releases-groupdocs.com/).
### ฉันจะได้รับการสนับสนุนสำหรับปัญหาหรือคำถามต่างๆ ที่เกี่ยวข้องกับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
คุณสามารถรับการสนับสนุนจากฟอรัม GroupDocs.Annotation [ที่นี่](https://forum-groupdocs.com/c/annotation/10).
### ฉันสามารถขอใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์การทดสอบได้หรือไม่
ใช่ คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [ที่นี่](https://purchase-groupdocs.com/temporary-license/).