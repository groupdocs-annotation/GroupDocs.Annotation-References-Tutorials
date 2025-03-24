---
title: เพิ่มข้อความคำอธิบายประกอบแบบเขี่ยๆ ลงในเอกสาร
linktitle: เพิ่มข้อความคำอธิบายประกอบแบบเขี่ยๆ ลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบแบบข้อความที่ไม่ซับซ้อนลงในเอกสารโดยใช้ Groupdocs.Annotation สำหรับ .NET ปรับปรุงกระบวนการทำงานร่วมกันและการตรวจสอบเอกสาร
weight: 25
url: /th/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# เพิ่มข้อความคำอธิบายประกอบแบบเขี่ยๆ ลงในเอกสาร

## การแนะนำ

Groupdocs.Annotation สำหรับ .NET เป็นไลบรารีอเนกประสงค์ที่ช่วยให้นักพัฒนาสามารถรวมความสามารถด้านคำอธิบายประกอบที่มีประสิทธิภาพเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างง่ายดาย ไม่ว่าคุณจะทำงานกับ PDF, เอกสาร Word หรือรูปแบบไฟล์ยอดนิยมอื่นๆ Groupdocs.Annotation มอบโซลูชันที่ราบรื่นสำหรับการใส่คำอธิบายประกอบและปรับปรุงการทำงานร่วมกันในเอกสาร

## ข้อกำหนดเบื้องต้น

ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:

## นำเข้าเนมสเปซ

ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานที่ได้รับจาก Groupdocs.Annotation สำหรับ .NET

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้เราได้ครอบคลุมข้อกำหนดเบื้องต้นแล้ว เรามาแจกแจงขั้นตอนการเพิ่มข้อความคำอธิบายประกอบแบบหยักๆ ออกเป็นหลายขั้นตอนกัน

## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต

กำหนดเส้นทางที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ

เตรียมข้อมูลเบื้องต้นให้กับอ็อบเจ็กต์ Annotator โดยจัดเตรียมเส้นทางเอกสารอินพุต

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบอยู่ที่นี่
}
```

## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบแบบเขี้ยวลากดิน

สร้างวัตถุ SquigglyAnnotation และระบุคุณสมบัติ

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

เพิ่มคำอธิบายประกอบแบบหยักที่สร้างขึ้นลงในเอกสาร

```csharp
annotator.Add(squiggly);
```

## ขั้นตอนที่ 5: บันทึกเอกสาร

บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ

```csharp
annotator.Save(outputPath);
```

## ขั้นตอนที่ 6: แสดงการยืนยัน

แสดงข้อความยืนยันการบันทึกเอกสารที่มีคำอธิบายประกอบสำเร็จ

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป

โดยสรุป Groupdocs.Annotation สำหรับ .NET มอบชุดเครื่องมือที่มีประสิทธิภาพสำหรับนักพัฒนาในการรวมฟังก์ชันคำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชัน .NET ได้อย่างราบรื่น ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณสามารถเพิ่มคำอธิบายประกอบข้อความที่ไม่เป็นระเบียบลงในเอกสารของคุณได้อย่างง่ายดาย เพิ่มประสิทธิภาพการทำงานร่วมกันและกระบวนการตรวจสอบเอกสาร

## คำถามที่พบบ่อย

### ถาม: Groupdocs.Annotation สามารถรองรับคำอธิบายประกอบในรูปแบบไฟล์ต่างๆ ได้หรือไม่

ตอบ: ใช่ Groupdocs.Annotation รองรับคำอธิบายประกอบในรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, เอกสาร Word, แผ่นงาน Excel และอื่นๆ

### ถาม: Groupdocs.Annotation เข้ากันได้กับทั้งเดสก์ท็อปและเว็บแอปพลิเคชันหรือไม่

ตอบ: แน่นอน! Groupdocs.Annotation สามารถผสานรวมเข้ากับทั้งแอปพลิเคชันเดสก์ท็อปและเว็บได้อย่างราบรื่น โดยให้ความยืดหยุ่นและความสามารถรอบด้าน

### ถาม: มีตัวเลือกสิทธิ์การใช้งานสำหรับ Groupdocs.Annotation หรือไม่

ตอบ: ใช่ Groupdocs.Annotation นำเสนอตัวเลือกสิทธิ์การใช้งานที่ยืดหยุ่นซึ่งปรับให้เหมาะกับความต้องการของแต่ละบุคคลหรือองค์กร รวมถึงสิทธิ์การใช้งานชั่วคราวสำหรับการทดลองใช้งาน

### ถาม: คำอธิบายประกอบที่สร้างโดยใช้ Groupdocs.Annotation สามารถปรับแต่งได้หรือไม่

ตอบ: แน่นอน! Groupdocs.Annotation มีตัวเลือกการปรับแต่งคำอธิบายประกอบที่ครอบคลุม ช่วยให้นักพัฒนาสามารถปรับแต่งคำอธิบายประกอบให้ตรงกับความต้องการเฉพาะของพวกเขาได้

### ถาม: Groupdocs.Annotation ให้การสนับสนุนและเอกสารสำหรับนักพัฒนาหรือไม่

ตอบ: แน่นอน! Groupdocs.Annotation มอบเอกสารที่ครอบคลุมและฟอรัมการสนับสนุนเฉพาะเพื่อช่วยให้นักพัฒนาใช้คุณสมบัติต่างๆ ได้อย่างมีประสิทธิภาพ