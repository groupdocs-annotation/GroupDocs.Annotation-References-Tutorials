---
"description": "เรียนรู้วิธีการเพิ่มคำอธิบายประกอบข้อความลงในเอกสาร PDF โดยใช้ GroupDocs.Annotation สำหรับ .NET ปกป้องข้อมูลที่ละเอียดอ่อนได้อย่างง่ายดาย"
"linktitle": "เพิ่มคำอธิบายการแก้ไขข้อความลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายการแก้ไขข้อความลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# เพิ่มคำอธิบายการแก้ไขข้อความลงในเอกสาร

## การแนะนำ
การเพิ่มคำอธิบายประกอบการแก้ไขข้อความลงในเอกสารถือเป็นขั้นตอนสำคัญในการจัดการข้อมูลสำคัญอย่างปลอดภัย GroupDocs.Annotation สำหรับ .NET นำเสนอโซลูชันที่มีประสิทธิภาพเพื่อให้บรรลุเป้าหมายนี้ได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มคำอธิบายประกอบการแก้ไขข้อความลงในเอกสารของคุณทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก [เว็บไซต์](https://releases-groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาด้วย IDE ที่เข้ากันได้กับ .NET เช่น Visual Studio

## การนำเข้าเนมสเปซ
ก่อนอื่นให้เรานำเข้าเนมสเปซที่จำเป็นเข้าสู่โปรเจ็กต์ของเรา:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่คุณต้องการบันทึกเอกสารที่มีคำอธิบายประกอบ ตรวจสอบให้แน่ใจว่าสามารถเข้าถึงและเขียนได้
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้น Annotator
เริ่มต้นตัวอธิบายด้วยเส้นทางเอกสารอินพุต แทนที่ `"input.pdf"` พร้อมเส้นทางไปยังเอกสารของคุณ
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างคำอธิบายการแก้ไขข้อความ
สร้าง `TextRedactionAnnotation` วัตถุที่มีคุณสมบัติตามต้องการ เช่น `PageNumber`- `FontColor`, และ `Points`. ปรับแต่งคำอธิบายตามความต้องการของคุณ
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## ขั้นตอนที่ 4: เพิ่มคำอธิบายและบันทึก
เพิ่มคำอธิบายประกอบที่สร้างลงในเอกสารโดยใช้เครื่องมือคำอธิบายประกอบ และบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## ขั้นตอนที่ 5: ตรวจสอบผลลัพธ์
สุดท้ายนี้ ให้ยืนยันว่าเอกสารได้รับการบันทึกไปยังเส้นทางเอาต์พุตที่ระบุเรียบร้อยแล้ว
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้แนะนำขั้นตอนการเพิ่มคำอธิบายประกอบข้อความลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยขั้นตอนเหล่านี้ คุณสามารถจัดการข้อมูลสำคัญภายในเอกสารของคุณได้อย่างปลอดภัยแล้ว
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายข้อความได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ เช่น สีแบบอักษร สีเติม และความทึบ เพื่อให้เหมาะกับความต้องการของคุณได้
### มีเวอร์ชันทดลองใช้งานก่อนการซื้อหรือไม่?
ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้งานฟรีได้จาก [เว็บไซต์](https://releases-groupdocs.com/).
### ฉันจะได้รับการสนับสนุนได้อย่างไรหากพบปัญหาใดๆ?
คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน GroupDocs.Annotation [ที่นี่](https://forum-groupdocs.com/c/annotation/10).
### ฉันต้องมีใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการทดสอบหรือไม่?
ใช่ คุณสามารถขอใบอนุญาตชั่วคราวได้จาก [หน้าการซื้อ](https://purchase.groupdocs.com/temporary-license/) เพื่อการทดสอบ
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวได้หรือไม่
แน่นอน GroupDocs.Annotation ช่วยให้คุณสามารถเพิ่มคำอธิบายประกอบประเภทต่างๆ และอินสแตนซ์ต่างๆ มากมายลงในเอกสารเดียวได้