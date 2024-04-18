---
title: เพิ่มคำอธิบายประกอบพื้นที่ให้กับเอกสาร
linktitle: เพิ่มคำอธิบายประกอบพื้นที่ให้กับเอกสาร
second_title: GroupDocs.Annotation .NET API
description: ปรับปรุงการทำงานร่วมกันในเอกสารของคุณด้วย Groupdocs.Annotation สำหรับ .NET เรียนรู้วิธีเพิ่มคำอธิบายประกอบพื้นที่ทีละขั้นตอน
type: docs
weight: 10
url: /th/net/unlocking-annotation-power/add-area-annotation/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มคำอธิบายประกอบในพื้นที่ให้กับเอกสารโดยใช้ Groupdocs.Annotation สำหรับ .NET คำอธิบายประกอบในพื้นที่เป็นคุณลักษณะอันทรงคุณค่าที่ช่วยให้ผู้ใช้สามารถเน้นพื้นที่เฉพาะของเอกสาร โดยให้ความชัดเจนและบริบทของเนื้อหา
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  Groupdocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารีและการอ้างอิงที่จำเป็นแล้ว คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: มีสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการพัฒนา .NET

## นำเข้าเนมสเปซ
ขั้นแรก ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ เนมสเปซเหล่านี้มีคลาสและวิธีการที่จำเป็นสำหรับการทำงานกับคำอธิบายประกอบ
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## ขั้นตอนที่ 1: เริ่มต้นเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
 สร้างอินสแตนซ์ของ`Annotator` คลาสโดยส่งเส้นทางของเอกสารเป็นพารามิเตอร์
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบพื้นที่
กำหนดคุณสมบัติของคำอธิบายประกอบในพื้นที่ เช่น สีพื้นหลัง ตำแหน่ง ข้อความ ความทึบ ฯลฯ
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
 เพิ่มคำอธิบายประกอบพื้นที่ให้กับเอกสารโดยใช้`Add` วิธีการของ`Annotator` ตัวอย่าง.
```csharp
annotator.Add(area);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Save(outputPath);
```
## ขั้นตอนที่ 6: แสดงข้อความแสดงความสำเร็จ
แจ้งให้ผู้ใช้ทราบว่าเอกสารได้รับการใส่คำอธิบายประกอบและบันทึกเรียบร้อยแล้ว
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มคำอธิบายประกอบในพื้นที่ให้กับเอกสารโดยใช้ Groupdocs.Annotation สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอน คุณสามารถปรับปรุงเอกสารของคุณได้อย่างง่ายดายด้วยคำอธิบายประกอบที่มีคุณค่า ปรับปรุงการทำงานร่วมกันและความเข้าใจ
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบพื้นที่ได้หรือไม่
ใช่ คุณสามารถปรับแต่งแง่มุมต่างๆ ได้ เช่น สีพื้นหลัง ความทึบ สไตล์ปากกา ฯลฯ เพื่อให้เหมาะกับความต้องการของคุณ
### Groupdocs.Annotation เข้ากันได้กับรูปแบบเอกสารอื่นหรือไม่
ใช่ Groupdocs.Annotation รองรับรูปแบบเอกสารหลากหลาย รวมถึง PDF, DOCX, PPTX และอื่นๆ
### ฉันสามารถเพิ่มคำอธิบายประกอบหลายรายการลงในเอกสารเดียวกันได้หรือไม่
แน่นอน คุณสามารถเพิ่มคำอธิบายประกอบหลายประเภทลงในเอกสารเดียวกันได้ตามต้องการ
### Groupdocs.Annotation มีความเข้ากันได้ข้ามแพลตฟอร์มหรือไม่
ใช่ Groupdocs.Annotation เข้ากันได้กับเฟรมเวิร์ก .NET ทำให้เหมาะสำหรับสภาพแวดล้อมการพัฒนา Windows, Linux และ macOS
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).