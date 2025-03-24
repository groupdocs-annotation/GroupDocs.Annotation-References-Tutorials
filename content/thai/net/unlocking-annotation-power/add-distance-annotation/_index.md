---
title: เพิ่มคำอธิบายประกอบระยะทางลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบระยะทางลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบระยะทางให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและการสื่อสารได้อย่างง่ายดาย
weight: 12
url: /th/net/unlocking-annotation-power/add-distance-annotation/
---

# เพิ่มคำอธิบายประกอบระยะทางลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีเพิ่มคำอธิบายประกอบระยะทางให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ทำตามขั้นตอนเหล่านี้เพื่อทำงานให้สำเร็จ:
## ข้อกำหนดเบื้องต้น

ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้ก่อนดำเนินการต่อ:

-  GroupDocs.Annotation สำหรับ .NET Library: ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET Library จาก[ลิงค์นี้](https://releases.groupdocs.com/annotation/net/).
- เอกสารที่จะใส่คำอธิบายประกอบ: เตรียมเอกสาร (เช่น PDF) ที่คุณต้องการเพิ่มคำอธิบายประกอบระยะทาง
- สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วย Visual Studio หรือ IDE อื่น ๆ ที่คุณเลือก

## นำเข้าเนมสเปซ

ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าได้รวมเนมสเปซที่จำเป็นในโค้ดของคุณ เนมสเปซเหล่านี้จำเป็นสำหรับการเข้าถึงคลาสและวิธีการที่จำเป็น

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## ขั้นตอนที่ 1: เริ่มต้นคำอธิบายประกอบ

 เริ่มต้นด้วยการเริ่มต้น`Annotator` วัตถุที่มีเส้นทางไปยังเอกสารที่คุณต้องการใส่คำอธิบายประกอบ

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบจะอยู่ที่นี่
}
```

## ขั้นตอนที่ 2: สร้างคำอธิบายประกอบระยะทาง

 ตอนนี้สร้าง`DistanceAnnotation` object และกำหนดค่าคุณสมบัติของมัน เช่น ขนาดกล่อง ข้อความ ความทึบ สีปากกา ฯลฯ

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## ขั้นตอนที่ 3: เพิ่มคำอธิบายประกอบ

 เพิ่มคำอธิบายประกอบระยะทางที่สร้างขึ้นให้กับเอกสารโดยใช้`Add` วิธีการของวัตถุคำอธิบายประกอบ

```csharp
annotator.Add(distance);
```

## ขั้นตอนที่ 4: บันทึกเอกสาร

บันทึกเอกสารที่มีคำอธิบายประกอบไปยังตำแหน่งที่ต้องการบนระบบของคุณ

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## ขั้นตอนที่ 5: แสดงการยืนยัน

สุดท้าย ให้แสดงข้อความยืนยันการบันทึกเอกสารที่มีคำอธิบายประกอบสำเร็จ

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป

การเพิ่มคำอธิบายประกอบแบบระยะทางให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET เป็นกระบวนการที่ไม่ซับซ้อน ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถปรับปรุงเอกสารของคุณด้วยคำอธิบายประกอบที่มีคุณค่า อำนวยความสะดวกในการทำงานร่วมกันและการสื่อสารที่ดียิ่งขึ้น

## คำถามที่พบบ่อย

### ถาม: ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบระยะทางได้หรือไม่

ตอบ: ได้ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ได้ เช่น สี ความทึบ สไตล์เส้น ฯลฯ เพื่อให้เหมาะกับความต้องการของคุณ

### ถาม: GroupDocs.Annotation รองรับคำอธิบายประกอบในเอกสารประเภทต่างๆ หรือไม่

ตอบ: ได้ GroupDocs.Annotation รองรับคำอธิบายประกอบในรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ

### ถาม: GroupDocs.Annotation มีให้ทดลองใช้ฟรีหรือไม่

 ตอบ: ได้ คุณสามารถเข้าถึง GroupDocs.Annotation รุ่นทดลองใช้ฟรีได้จาก[ลิงค์นี้](https://releases.groupdocs.com/).

### ถาม: ฉันจะหาเอกสารสำหรับ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน

 ตอบ: คุณสามารถดูเอกสารรายละเอียดที่มีอยู่ได้[ที่นี่](https://tutorials.groupdocs.com/annotation/net/).

### ถาม: ฉันจะรับการสนับสนุนหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Annotation ได้อย่างไร

 ตอบ: คุณสามารถขอรับการสนับสนุนและความช่วยเหลือได้จากฟอรัมชุมชน GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).