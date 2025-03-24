---
title: เพิ่มคำอธิบายประกอบการแทนที่ข้อความลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบการแทนที่ข้อความลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบการแทนที่ข้อความลงในเอกสาร .NET ของคุณได้อย่างง่ายดายโดยใช้ GroupDocs.Annotation สำหรับ .NET เพิ่มความสามารถในการจัดการเอกสารของคุณ
weight: 24
url: /th/net/unlocking-annotation-power/add-text-replacement-annotation/
---

# เพิ่มคำอธิบายประกอบการแทนที่ข้อความลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มคำอธิบายประกอบการแทนที่ข้อความลงในเอกสารของคุณโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีอันทรงพลังนี้ช่วยให้นักพัฒนาจัดการและใส่คำอธิบายประกอบเอกสารประเภทต่าง ๆ โดยทางโปรแกรม เมื่อสิ้นสุดบทช่วยสอนนี้ คุณจะได้รับความรู้ในการผสานรวมคำอธิบายประกอบการแทนที่ข้อความเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง .NET Framework แล้ว
ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนเครื่องพัฒนาของคุณแล้ว คุณสามารถดาวน์โหลดได้จากเว็บไซต์ Microsoft
### 2. GroupDocs.Annotation สำหรับ .NET Library
 ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET จาก[เว็บไซต์](https://releases.groupdocs.com/annotation/net/)- ไลบรารีนี้มีเครื่องมือและฟังก์ชันที่จำเป็นในการทำงานกับคำอธิบายประกอบในรูปแบบเอกสารต่างๆ
### 3. การตั้งค่าสภาพแวดล้อมการพัฒนา
ตั้งค่าสภาพแวดล้อมการพัฒนาที่คุณต้องการ เช่น Visual Studio เพื่อสร้างและเรียกใช้แอปพลิเคชัน .NET

## นำเข้าเนมสเปซ
ก่อนที่จะเจาะลึกในส่วนของการเขียนโค้ด เรามานำเข้าเนมสเปซที่จำเป็นสำหรับการทำงานกับ GroupDocs.Annotation สำหรับ .NET กันดีกว่า:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ที่นี่ เรากำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบจะถูกวางไว้ที่นี่
}
```
เราเริ่มต้นออบเจ็กต์ Annotator โดยการระบุเอกสารอินพุต ("input.pdf") ภายในบล็อกการใช้งานเพื่อให้แน่ใจว่ามีการกำจัดทรัพยากรอย่างเหมาะสม
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบทดแทน
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    TextToReplace = "replaced text"
};
```
ที่นี่ เราสร้างออบเจ็กต์ ReplacementAnnotation ที่มีคุณสมบัติต่างๆ เช่น วันที่สร้าง สีแบบอักษร ข้อความ ความทึบ หมายเลขหน้า สีพื้นหลัง จุด (พิกัด) การตอบกลับ (ความคิดเห็น) และข้อความที่จะแทนที่
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
```csharp
annotator.Add(replacement);
```
เราเพิ่มคำอธิบายประกอบการแทนที่ที่สร้างขึ้นให้กับคำอธิบายประกอบ
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save(outputPath);
```
สุดท้าย เราจะบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
## ขั้นตอนที่ 6: แสดงข้อความแสดงความสำเร็จ
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
ข้อความแสดงความสำเร็จจะปรากฏขึ้นเพื่อระบุว่าเอกสารได้รับการบันทึกเรียบร้อยแล้ว

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการเพิ่มคำอธิบายประกอบการแทนที่ข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและทำความเข้าใจข้อกำหนดเบื้องต้น คุณสามารถรวมฟังก์ชันการทำงานนี้เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### ฉันสามารถใส่คำอธิบายประกอบเอกสารในรูปแบบต่างๆ โดยใช้ GroupDocs.Annotation สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET รองรับการใส่คำอธิบายประกอบในเอกสารหลากหลายรูปแบบ เช่น PDF, DOCX, PPTX, XLSX และอื่นๆ
### GroupDocs.Annotation สำหรับ .NET เหมาะสำหรับทั้งเดสก์ท็อปและเว็บแอปพลิเคชันหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET สามารถใช้ได้ทั้งบนเดสก์ท็อปและเว็บแอปพลิเคชัน ทำให้นักพัฒนามีความยืดหยุ่น
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่เพิ่มโดยใช้ GroupDocs.Annotation สำหรับ .NET ได้หรือไม่
แน่นอน คุณสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้โดยการแก้ไขคุณสมบัติ เช่น สี ความทึบ แบบอักษร ฯลฯ
### GroupDocs.Annotation สำหรับ .NET ให้การสนับสนุนฟีเจอร์คำอธิบายประกอบการทำงานร่วมกันหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET มีคุณสมบัติสำหรับคำอธิบายประกอบแบบทำงานร่วมกัน ช่วยให้ผู้ใช้หลายคนสามารถใส่คำอธิบายประกอบในเอกสารได้พร้อมกัน
### GroupDocs.Annotation สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
ใช่ คุณสามารถทดลองใช้ GroupDocs.Annotation สำหรับ .NET ได้ฟรีจาก[เว็บไซต์](https://releases.groupdocs.com/).