---
title: เพิ่มคำอธิบายประกอบลิงก์ลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบลิงก์ลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบลิงก์ลงในเอกสารโดยใช้ Groupdocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและการโต้ตอบได้อย่างง่ายดาย
weight: 16
url: /th/net/unlocking-annotation-power/add-link-annotation/
---

# เพิ่มคำอธิบายประกอบลิงก์ลงในเอกสาร

## การแนะนำ
Groupdocs.Annotation สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถรวมฟังก์ชันคำอธิบายประกอบที่ครอบคลุมเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างง่ายดาย หนึ่งในคุณสมบัติหลักที่มีให้คือความสามารถในการเพิ่มคำอธิบายประกอบลิงก์ลงในเอกสาร ปรับปรุงการทำงานร่วมกันและการโต้ตอบ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกกระบวนการเพิ่มคำอธิบายประกอบลิงก์ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- ติดตั้ง Groupdocs.Annotation สำหรับไลบรารี .NET แล้ว
- เข้าถึงเอกสารที่คุณต้องการใส่คำอธิบายประกอบ

## นำเข้าเนมสเปซ
ประการแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อใช้ Groupdocs.Annotation สำหรับฟังก์ชัน .NET ซึ่งช่วยให้แอปพลิเคชันของคุณสามารถเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการใส่คำอธิบายประกอบเอกสาร
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอาต์พุต
กำหนดเส้นทางที่คุณต้องการบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
 สร้างอินสแตนซ์ของ`Annotator` คลาสโดยระบุเส้นทางของเอกสารที่คุณต้องการใส่คำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบลิงก์
 กำหนด`LinkAnnotation` object และระบุคุณสมบัติของมัน เช่น ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง จุด การตอบกลับ และ URL
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
 เพิ่มคำอธิบายประกอบลิงก์ที่สร้างขึ้นลงในเอกสารโดยใช้`Add` วิธีการของอินสแตนซ์คำอธิบายประกอบ
```csharp
annotator.Add(link);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Save(outputPath);
```
## ขั้นตอนที่ 6: แสดงข้อความแสดงความสำเร็จ
แจ้งให้ผู้ใช้ทราบเกี่ยวกับการบันทึกเอกสารที่มีคำอธิบายประกอบได้สำเร็จ
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
โดยสรุป เมื่อทำตามขั้นตอนข้างต้น คุณจะสามารถเพิ่มคำอธิบายประกอบลิงก์ลงในเอกสารได้อย่างราบรื่นโดยใช้ Groupdocs.Annotation สำหรับ .NET สิ่งนี้ช่วยปรับปรุงการทำงานร่วมกันในเอกสารและมอบคุณสมบัติแบบโต้ตอบให้กับผู้ใช้
## คำถามที่พบบ่อย
### Groupdocs.Annotation สำหรับ .NET เข้ากันได้กับเอกสารทุกประเภทหรือไม่
Groupdocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ของคำอธิบายประกอบได้ เช่น สี ความทึบ และขนาด เพื่อให้เหมาะกับความต้องการของคุณ
### Groupdocs.Annotation สำหรับ .NET นำเสนอคุณสมบัติการทำงานร่วมกันแบบเรียลไทม์หรือไม่
ใช่ Groupdocs.Annotation สำหรับ .NET มีคุณสมบัติการทำงานร่วมกันแบบเรียลไทม์ ทำให้ผู้ใช้หลายคนสามารถใส่คำอธิบายประกอบในเอกสารได้พร้อมกัน
### มีการสนับสนุนทางเทคนิคสำหรับผลิตภัณฑ์ Groupdocs หรือไม่
 ใช่ การสนับสนุนด้านเทคนิคสำหรับผลิตภัณฑ์ Groupdocs มีให้ผ่านฟอรัมและการสนับสนุน[ที่นี่](https://forum.groupdocs.com/c/annotation/10).
### ฉันสามารถลองใช้ Groupdocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่
ใช่ คุณสามารถทดลองใช้ Groupdocs.Annotation สำหรับ .NET ได้ฟรี เพื่อสำรวจคุณลักษณะต่างๆ ก่อนตัดสินใจซื้อ[ที่นี่](https://purchase.groupdocs.com/temporary-license/).