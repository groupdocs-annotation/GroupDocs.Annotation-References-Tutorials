---
"description": "เรียนรู้วิธีการเพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF โดยใช้ Groupdocs.Annotation สำหรับ .NET ปรับปรุง PDF ของคุณด้วยองค์ประกอบแบบโต้ตอบ"
"linktitle": "เพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF"
"url": "/th/net/document-components/add-checkbox-component-to-pdf/"
type: docs
"weight": 11
---

# เพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการเพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF โดยใช้ Groupdocs.Annotation สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. Groupdocs.Annotation สำหรับ .NET SDK: คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ไว้แล้ว

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
ตอนนี้เรามาแบ่งตัวอย่างออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ที่นี่เราจะกำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสาร PDF ที่แก้ไขแล้ว
## ขั้นตอนที่ 2: เริ่มต้น Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
เริ่มต้นการใช้งาน `Annotator` วัตถุโดยส่งผ่านเส้นทางเอกสาร PDF อินพุต
## ขั้นตอนที่ 3: สร้างส่วนประกอบกล่องกาเครื่องหมาย
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
สร้าง `CheckBoxComponent` วัตถุและปรับแต่งคุณสมบัติเช่น `Checked`- `Box` ขนาด- `PenColor`, `Style`, และเพิ่มการตอบกลับบางส่วน
## ขั้นตอนที่ 4: เพิ่มส่วนประกอบกล่องกาเครื่องหมาย
```csharp
annotator.Add(checkBox);
```
เพิ่มส่วนประกอบกล่องกาเครื่องหมายที่สร้างขึ้นลงในเอกสาร PDF
## ขั้นตอนที่ 5: บันทึกเอกสาร
```csharp
annotator.Save("result.pdf");
```
บันทึกเอกสาร PDF ที่แก้ไขแล้วด้วยส่วนประกอบกล่องกาเครื่องหมาย
## ขั้นตอนที่ 6: แสดงเส้นทางเอาท์พุต
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
แสดงเส้นทางที่บันทึกเอกสาร PDF ที่แก้ไข

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการเพิ่มส่วนประกอบกล่องกาเครื่องหมายลงในเอกสาร PDF โดยใช้ Groupdocs.Annotation สำหรับ .NET ด้วยความรู้ดังกล่าว คุณสามารถปรับปรุงเอกสาร PDF ของคุณด้วยองค์ประกอบแบบโต้ตอบได้
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะของช่องกาเครื่องหมายได้ไหม
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ เช่น สี สไตล์ และขนาด ตามความต้องการของคุณได้
### Groupdocs.Annotation สำหรับ .NET เหมาะสำหรับการใช้งานเชิงพาณิชย์หรือไม่
ใช่ Groupdocs.Annotation สำหรับ .NET นำเสนอใบอนุญาตเชิงพาณิชย์สำหรับธุรกิจ
### ฉันสามารถทดลองใช้ Groupdocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่
ใช่ คุณสามารถใช้ประโยชน์จากการทดลองใช้ฟรีได้จาก [ที่นี่](https://releases-groupdocs.com/).
### ฉันสามารถค้นหาการสนับสนุนสำหรับ Groupdocs.Annotation สำหรับ .NET ได้ที่ไหน
คุณสามารถค้นหาการสนับสนุนและทรัพยากรได้ที่ [ฟอรั่ม Groupdocs](https://forum-groupdocs.com/c/annotation/10).
### ฉันต้องมีใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการทดสอบหรือไม่?
คุณสามารถขอใบอนุญาตชั่วคราวเพื่อการทดสอบได้จาก [ที่นี่](https://purchase-groupdocs.com/temporary-license/).