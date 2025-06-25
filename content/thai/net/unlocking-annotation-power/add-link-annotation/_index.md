---
"description": "เรียนรู้วิธีเพิ่มคำอธิบายลิงก์ลงในเอกสารโดยใช้ Groupdocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและการโต้ตอบได้อย่างง่ายดาย"
"linktitle": "เพิ่มคำอธิบายลิงก์ลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายลิงก์ลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-link-annotation/"
"weight": 16
---

# เพิ่มคำอธิบายลิงก์ลงในเอกสาร

## การแนะนำ
Groupdocs.Annotation สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถผสานรวมฟังก์ชันคำอธิบายประกอบที่ครอบคลุมเข้ากับแอปพลิเคชัน .NET ได้อย่างง่ายดาย หนึ่งในฟีเจอร์หลักที่ไลบรารีนี้มีให้คือความสามารถในการเพิ่มคำอธิบายประกอบลิงก์ลงในเอกสาร ซึ่งช่วยเพิ่มประสิทธิภาพการทำงานร่วมกันและการโต้ตอบ
## ข้อกำหนดเบื้องต้น
ก่อนจะเริ่มกระบวนการเพิ่มคำอธิบายลิงก์ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
- ติดตั้ง Groupdocs.Annotation สำหรับไลบรารี .NET
- การเข้าถึงเอกสารที่คุณต้องการใส่คำอธิบายประกอบ

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อใช้ Groupdocs.Annotation สำหรับฟังก์ชันการทำงานของ .NET วิธีนี้จะช่วยให้แอปพลิเคชันของคุณสามารถเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการใส่คำอธิบายประกอบเอกสารได้
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
## ขั้นตอนที่ 2: เริ่มต้น Annotator
สร้างอินสแตนซ์ของ `Annotator` คลาสโดยระบุเส้นทางของเอกสารที่คุณต้องการใส่คำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างคำอธิบายลิงก์
กำหนดนิยาม `LinkAnnotation` วัตถุและระบุคุณสมบัติเช่น ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง จุด การตอบกลับ และ URL
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
เพิ่มคำอธิบายลิงก์ที่สร้างขึ้นลงในเอกสารโดยใช้ `Add` วิธีการของอินสแตนซ์คำอธิบายประกอบ
```csharp
annotator.Add(link);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Save(outputPath);
```
## ขั้นตอนที่ 6: แสดงข้อความแสดงว่าสำเร็จ
แจ้งให้ผู้ใช้ทราบถึงการบันทึกเอกสารที่มีคำอธิบายประกอบสำเร็จ
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
โดยสรุป หากทำตามขั้นตอนข้างต้น คุณสามารถเพิ่มคำอธิบายประกอบลิงก์ลงในเอกสารได้อย่างราบรื่นโดยใช้ Groupdocs.Annotation สำหรับ .NET ซึ่งจะช่วยเพิ่มประสิทธิภาพการทำงานร่วมกันในเอกสารและมอบคุณลักษณะแบบโต้ตอบให้กับผู้ใช้
## คำถามที่พบบ่อย
### Groupdocs.Annotation สำหรับ .NET เข้ากันได้กับเอกสารทุกประเภทหรือไม่
Groupdocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารหลากหลาย เช่น PDF, Word, Excel และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ของคำอธิบายประกอบ เช่น สี ความทึบ และขนาด เพื่อให้เหมาะกับความต้องการของคุณได้
### Groupdocs.Annotation สำหรับ .NET มีคุณลักษณะการทำงานร่วมกันแบบเรียลไทม์หรือไม่
ใช่ Groupdocs.Annotation สำหรับ .NET ให้คุณลักษณะการทำงานร่วมกันแบบเรียลไทม์ซึ่งอนุญาตให้ผู้ใช้หลายรายสามารถใส่คำอธิบายประกอบในเอกสารพร้อมกันได้
### มีการสนับสนุนด้านเทคนิคสำหรับผลิตภัณฑ์ Groupdocs หรือไม่
ใช่ การสนับสนุนด้านเทคนิคสำหรับผลิตภัณฑ์ Groupdocs พร้อมให้บริการผ่านฟอรัมและการสนับสนุน [ที่นี่](https://forum-groupdocs.com/c/annotation/10).
### ฉันสามารถทดลองใช้ Groupdocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่
ใช่ คุณสามารถใช้ประโยชน์จากการทดลองใช้ Groupdocs.Annotation สำหรับ .NET ฟรีเพื่อสำรวจคุณลักษณะต่าง ๆ ก่อนตัดสินใจซื้อ[ที่นี่](https://purchase-groupdocs.com/temporary-license/).