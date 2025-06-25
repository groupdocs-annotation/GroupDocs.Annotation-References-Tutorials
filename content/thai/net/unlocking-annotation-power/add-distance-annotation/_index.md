---
"description": "เรียนรู้วิธีเพิ่มคำอธิบายระยะทางลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการทำงานร่วมกันและการสื่อสารได้อย่างง่ายดาย"
"linktitle": "เพิ่มคำอธิบายระยะทางลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายระยะทางลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# เพิ่มคำอธิบายระยะทางลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีเพิ่มคำอธิบายระยะทางลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปฏิบัติตามขั้นตอนเหล่านี้เพื่อทำงานให้สำเร็จ:
## ข้อกำหนดเบื้องต้น

ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้ก่อนดำเนินการต่อ:

- GroupDocs.Annotation สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET จาก [ลิงค์นี้](https://releases-groupdocs.com/annotation/net/).
- เอกสารที่จะใส่คำอธิบายประกอบ: เตรียมเอกสาร (เช่น PDF) ที่คุณต้องการเพิ่มคำอธิบายประกอบระยะทาง
- สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วย Visual Studio หรือ IDE อื่น ๆ ตามที่คุณต้องการ

## นำเข้าเนมสเปซ

ก่อนเริ่มต้น โปรดแน่ใจว่าได้ใส่เนมสเปซที่จำเป็นในโค้ดของคุณแล้ว เนมสเปซเหล่านี้มีความจำเป็นสำหรับการเข้าถึงคลาสและเมธอดที่จำเป็น

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## ขั้นตอนที่ 1: เริ่มต้น Annotator

เริ่มต้นด้วยการเริ่มต้น `Annotator` วัตถุที่มีเส้นทางไปยังเอกสารที่คุณต้องการใส่คำอธิบายประกอบ

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายจะอยู่ที่นี่
}
```

## ขั้นตอนที่ 2: สร้างคำอธิบายระยะทาง

ตอนนี้สร้าง `DistanceAnnotation` วัตถุและกำหนดค่าคุณสมบัติเช่น ขนาดกล่อง ข้อความ ความทึบ สีปากกา ฯลฯ

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

เพิ่มคำอธิบายระยะทางที่สร้างขึ้นลงในเอกสารโดยใช้ `Add` วิธีการของวัตถุคำอธิบายประกอบ

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

การเพิ่มคำอธิบายระยะทางลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET เป็นกระบวนการที่ตรงไปตรงมา เพียงทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณก็สามารถเพิ่มคุณค่าให้กับเอกสารของคุณด้วยคำอธิบายที่มีประโยชน์ ซึ่งช่วยให้ทำงานร่วมกันและสื่อสารกันได้ดีขึ้น

## คำถามที่พบบ่อย

### ถาม: ฉันสามารถปรับแต่งลักษณะของคำอธิบายระยะทางได้หรือไม่

A: ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ เช่น สี ความทึบ สไตล์เส้น ฯลฯ ให้เหมาะกับความต้องการของคุณได้

### ถาม: GroupDocs.Annotation รองรับคำอธิบายประกอบในเอกสารประเภทต่างๆ หรือไม่

ตอบ: ใช่ GroupDocs.Annotation รองรับคำอธิบายประกอบบนเอกสารหลากหลายรูปแบบ รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ อีกมากมาย

### ถาม: มีรุ่นทดลองใช้งานฟรีสำหรับ GroupDocs.Annotation หรือไม่

A: ใช่ คุณสามารถเข้าถึงรุ่นทดลองใช้งานฟรีของ GroupDocs.Annotation ได้จาก [ลิงค์นี้](https://releases-groupdocs.com/).

### ถาม: ฉันสามารถค้นหาเอกสารสำหรับ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน

A: คุณสามารถดูเอกสารรายละเอียดที่มีอยู่ได้ [ที่นี่](https://tutorials-groupdocs.com/annotation/net/).

### ถาม: ฉันจะได้รับการสนับสนุนหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Annotation ได้อย่างไร

A: คุณสามารถขอรับการสนับสนุนและความช่วยเหลือจากฟอรัมชุมชน GroupDocs.Annotation ได้ [ที่นี่](https://forum-groupdocs.com/c/annotation/10).