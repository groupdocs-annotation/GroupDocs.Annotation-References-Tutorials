---
"description": "เรียนรู้วิธีการเพิ่มคำอธิบายประกอบข้อความแบบหยัก ๆ ลงในเอกสารได้อย่างง่ายดายโดยใช้ Groupdocs.Annotation สำหรับ .NET ปรับปรุงกระบวนการทำงานร่วมกันและการตรวจสอบเอกสาร"
"linktitle": "เพิ่มคำอธิบายข้อความหยัก ๆ ลงในเอกสาร"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายข้อความหยัก ๆ ลงในเอกสาร"
"url": "/th/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# เพิ่มคำอธิบายข้อความหยัก ๆ ลงในเอกสาร

## การแนะนำ

Groupdocs.Annotation สำหรับ .NET เป็นไลบรารีที่มีความยืดหยุ่นซึ่งช่วยให้นักพัฒนาสามารถผสานรวมความสามารถในการใส่คำอธิบายประกอบที่มีประสิทธิภาพเข้ากับแอปพลิเคชัน .NET ได้อย่างง่ายดาย ไม่ว่าคุณจะทำงานกับ PDF เอกสาร Word หรือรูปแบบไฟล์ยอดนิยมอื่นๆ Groupdocs.Annotation ก็เป็นโซลูชันที่ราบรื่นสำหรับการใส่คำอธิบายประกอบและปรับปรุงการทำงานร่วมกันในเอกสาร

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

## นำเข้าเนมสเปซ

ตรวจสอบให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานที่ Groupdocs.Annotation จัดทำไว้สำหรับ .NET

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้เราได้ครอบคลุมข้อกำหนดเบื้องต้นแล้ว มาแบ่งกระบวนการในการเพิ่มคำอธิบายแบบข้อความหยักๆ ออกเป็นหลายขั้นตอนกัน

## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต

กำหนดเส้นทางที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ขั้นตอนที่ 2: เริ่มต้น Annotator

เริ่มต้นวัตถุ Annotator โดยระบุเส้นทางเอกสารอินพุต

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายอยู่ที่นี่
}
```

## ขั้นตอนที่ 3: สร้างคำอธิบายแบบหยัก ๆ

สร้างวัตถุ SquigglyAnnotation และระบุคุณสมบัติของมัน

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ

เพิ่มคำอธิบายแบบหยัก ๆ ที่สร้างขึ้นลงในเอกสาร

```csharp
annotator.Add(squiggly);
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

```csharp
annotator.Save(outputPath);
```

## ขั้นตอนที่ 6: แสดงการยืนยัน

แสดงข้อความยืนยันการบันทึกเอกสารที่มีคำอธิบายสำเร็จ

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป

โดยสรุป Groupdocs.Annotation สำหรับ .NET มอบชุดเครื่องมืออันแข็งแกร่งสำหรับนักพัฒนาในการผสานรวมฟังก์ชันการใส่คำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชัน .NET ของพวกเขาอย่างราบรื่น ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณสามารถเพิ่มคำอธิบายประกอบแบบข้อความหยัก ๆ ลงในเอกสารของคุณได้อย่างง่ายดาย ซึ่งช่วยปรับปรุงกระบวนการทำงานร่วมกันและการตรวจสอบเอกสาร

## คำถามที่พบบ่อย

### ถาม: Groupdocs.Annotation รองรับคำอธิบายประกอบในรูปแบบไฟล์ต่างๆ ได้หรือไม่

ตอบ: ใช่ Groupdocs.Annotation รองรับคำอธิบายประกอบบนไฟล์หลากหลายรูปแบบ รวมถึง PDF เอกสาร Word แผ่นงาน Excel และอื่นๆ อีกมากมาย

### ถาม: Groupdocs.Annotation เข้ากันได้กับแอพพลิเคชันเดสก์ท็อปและเว็บหรือไม่

A: แน่นอน! Groupdocs.Annotation สามารถผสานรวมเข้ากับแอพพลิเคชันเดสก์ท็อปและเว็บได้อย่างราบรื่น ช่วยให้มีความยืดหยุ่นและหลากหลาย

### ถาม: มีตัวเลือกใบอนุญาตใดๆ สำหรับ Groupdocs.Annotation หรือไม่

ตอบ: ใช่ Groupdocs.Annotation นำเสนอตัวเลือกการออกใบอนุญาตแบบยืดหยุ่นที่ออกแบบมาเพื่อให้เหมาะกับความต้องการของแต่ละบุคคลหรือองค์กร รวมถึงใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการทดลองใช้

### ถาม: คำอธิบายประกอบที่สร้างโดยใช้ Groupdocs.Annotation สามารถกำหนดเองได้หรือไม่

A: แน่นอน! Groupdocs.Annotation มีตัวเลือกการปรับแต่งคำอธิบายประกอบมากมาย ช่วยให้ผู้พัฒนาสามารถปรับแต่งคำอธิบายประกอบให้เหมาะกับความต้องการเฉพาะของตนเองได้

### ถาม: Groupdocs.Annotation ให้การสนับสนุนและเอกสารประกอบสำหรับนักพัฒนาหรือไม่

A: ถูกต้อง! Groupdocs.Annotation มีเอกสารประกอบที่ครอบคลุมและฟอรัมสนับสนุนเฉพาะเพื่อช่วยให้นักพัฒนาใช้คุณลักษณะต่างๆ ได้อย่างมีประสิทธิภาพ