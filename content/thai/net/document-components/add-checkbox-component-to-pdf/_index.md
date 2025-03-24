---
title: เพิ่มส่วนประกอบช่องทำเครื่องหมายลงในเอกสาร PDF
linktitle: เพิ่มส่วนประกอบช่องทำเครื่องหมายลงในเอกสาร PDF
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มส่วนประกอบช่องทำเครื่องหมายลงในเอกสาร PDF โดยใช้ Groupdocs.Annotation สำหรับ .NET ปรับปรุง PDF ของคุณด้วยองค์ประกอบแบบโต้ตอบ
weight: 11
url: /th/net/document-components/add-checkbox-component-to-pdf/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มส่วนประกอบช่องทำเครื่องหมายลงในเอกสาร PDF โดยใช้ Groupdocs.Annotation สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  Groupdocs.Annotation สำหรับ .NET SDK: คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET แล้ว

## นำเข้าเนมสเปซ
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
ตอนนี้ เรามาแบ่งตัวอย่างออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ที่นี่ เรากำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสาร PDF ที่แก้ไข
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 เริ่มต้น`Annotator` วัตถุโดยผ่านเส้นทางเอกสาร PDF อินพุต
## ขั้นตอนที่ 3: สร้างส่วนประกอบช่องทำเครื่องหมาย
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 สร้างก`CheckBoxComponent` วัตถุและปรับแต่งคุณสมบัติของมันเช่น`Checked`, `Box` ขนาด`PenColor`, `Style`และเพิ่มคำตอบบางส่วน
## ขั้นตอนที่ 4: เพิ่มส่วนประกอบช่องทำเครื่องหมาย
```csharp
annotator.Add(checkBox);
```
เพิ่มส่วนประกอบช่องทำเครื่องหมายที่สร้างขึ้นลงในเอกสาร PDF
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save("result.pdf");
```
บันทึกเอกสาร PDF ที่แก้ไขด้วยส่วนประกอบช่องทำเครื่องหมาย
## ขั้นตอนที่ 6: แสดงเส้นทางเอาต์พุต
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
แสดงเส้นทางที่บันทึกเอกสาร PDF ที่แก้ไข

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มส่วนประกอบช่องทำเครื่องหมายลงในเอกสาร PDF โดยใช้ Groupdocs.Annotation สำหรับ .NET ด้วยความรู้นี้ คุณสามารถปรับปรุงเอกสาร PDF ของคุณด้วยองค์ประกอบแบบโต้ตอบได้
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของช่องทำเครื่องหมายได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ เช่น สี สไตล์ และขนาดได้ตามความต้องการของคุณ
### Groupdocs.Annotation สำหรับ .NET เหมาะสำหรับการใช้งานเชิงพาณิชย์หรือไม่
ใช่ Groupdocs.Annotation สำหรับ .NET เสนอใบอนุญาตเชิงพาณิชย์สำหรับธุรกิจ
### ฉันสามารถลองใช้ Groupdocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ Groupdocs.Annotation สำหรับ .NET ได้ที่ไหน
 คุณสามารถค้นหาการสนับสนุนและแหล่งข้อมูลได้ที่[ฟอรั่ม Groupdocs](https://forum.groupdocs.com/c/annotation/10).
### ฉันจำเป็นต้องมีใบอนุญาตชั่วคราวเพื่อการทดสอบหรือไม่?
 คุณสามารถขอรับใบอนุญาตชั่วคราวสำหรับการทดสอบได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).