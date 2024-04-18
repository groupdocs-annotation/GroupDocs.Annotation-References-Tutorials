---
title: โหลดเอกสารจากดิสก์ภายในเครื่อง
linktitle: โหลดเอกสารจากดิสก์ภายในเครื่อง
second_title: GroupDocs.Annotation .NET API
description: ปลดล็อกพลังของคำอธิบายประกอบเอกสารด้วย GroupDocs.Annotation สำหรับ .NET ผสานรวมคุณลักษณะคำอธิบายประกอบเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
type: docs
weight: 13
url: /th/net/document-loading-essentials/load-document-from-local-disk/
---
## การแนะนำ
การปลดล็อกศักยภาพของคำอธิบายประกอบเอกสารง่ายกว่าที่เคยด้วย GroupDocs.Annotation สำหรับ .NET เครื่องมืออันทรงพลังนี้ช่วยให้นักพัฒนาสามารถรวมคุณสมบัติคำอธิบายประกอบที่มีประสิทธิภาพเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น ในคู่มือที่ครอบคลุมนี้ เราจะแนะนำคุณตลอดกระบวนการใช้ประโยชน์จาก GroupDocs.Annotation สำหรับ .NET เพื่อใส่คำอธิบายประกอบในเอกสารทีละขั้นตอน ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น บทช่วยสอนนี้จะช่วยให้คุณมีความรู้ในการปรับปรุงการทำงานร่วมกันในเอกสารและปรับปรุงขั้นตอนการทำงานของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกคำอธิบายประกอบเอกสารด้วย GroupDocs.Annotation สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. ความรู้พื้นฐานของ C#: ความคุ้นเคยกับพื้นฐานภาษาการเขียนโปรแกรม C# เป็นสิ่งสำคัญ
2. การติดตั้ง GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
3. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาด้วย Visual Studio หรือ IDE ที่เข้ากันได้

## นำเข้าเนมสเปซ
หากต้องการเริ่มใส่คำอธิบายประกอบเอกสารด้วย GroupDocs.Annotation สำหรับ .NET ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## ขั้นตอนที่ 1: โหลดเอกสารจากดิสก์ในเครื่อง
ขั้นแรก คุณต้องโหลดเอกสารจากดิสก์ภายในเครื่องของคุณ ใช้ข้อมูลโค้ดต่อไปนี้:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ขั้นตอนที่ 2: กำหนดพื้นที่คำอธิบายประกอบ
ถัดไป กำหนดพื้นที่คำอธิบายประกอบ ในตัวอย่างนี้ เราจะสร้าง AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## ขั้นตอนที่ 3: บันทึกเอกสารพร้อมคำอธิบายประกอบ
หลังจากใส่คำอธิบายประกอบเอกสารแล้ว ให้บันทึกพร้อมกับคำอธิบายประกอบ:
```csharp
    annotator.Save(outputPath);
}
```
## ขั้นตอนที่ 4: แสดงข้อความแสดงความสำเร็จ
สุดท้าย แสดงข้อความแสดงความสำเร็จพร้อมกับเส้นทางเอาต์พุต:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
โดยสรุป GroupDocs.Annotation สำหรับ .NET มอบโซลูชันที่มีประสิทธิภาพสำหรับการรวมความสามารถในการใส่คำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณ ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณสามารถใส่คำอธิบายประกอบในเอกสารและปรับปรุงการทำงานร่วมกันในโครงการของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### ฉันสามารถลองใช้ GroupDocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน
 คุณสามารถเข้าถึงเอกสารประกอบ[ที่นี่](https://reference.groupdocs.com/annotation/net/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### มีการสนับสนุนสำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
 ใช่ คุณสามารถค้นหาการสนับสนุนได้ในฟอรัม GroupDocs[ที่นี่](https://forum.groupdocs.com/c/annotation/10).
### ฉันจะซื้อ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อ GroupDocs.Annotation สำหรับ .NET ได้[ที่นี่](https://purchase.groupdocs.com/buy).