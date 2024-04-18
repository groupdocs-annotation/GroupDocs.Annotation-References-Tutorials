---
title: เพิ่มคำอธิบายประกอบรูปภาพลงในเอกสาร (เส้นทางในเครื่อง)
linktitle: เพิ่มคำอธิบายประกอบรูปภาพลงในเอกสาร (เส้นทางในเครื่อง)
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบรูปภาพลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET เพิ่มความสามารถในการประมวลผลเอกสารได้อย่างง่ายดาย
type: docs
weight: 14
url: /th/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถเพิ่มคำอธิบายประกอบประเภทต่างๆ ลงในเอกสารโดยทางโปรแกรม ในบทช่วยสอนนี้ เราจะได้เรียนรู้วิธีเพิ่มคำอธิบายประกอบรูปภาพลงในเอกสารโดยใช้เส้นทางในเครื่อง
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. ความรู้พื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
2. ติดตั้ง Visual Studio บนระบบของคุณแล้ว
3. GroupDocs.Annotation สำหรับไลบรารี .NET ที่ติดตั้งหรืออ้างอิงในโครงการของคุณ
4. เอกสารอินพุต (เช่น PDF) และไฟล์รูปภาพสำหรับใส่คำอธิบายประกอบ
## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นไปยังไฟล์ C# ของคุณ เนมสเปซเหล่านี้ให้สิทธิ์เข้าถึงคลาสและวิธีการที่จำเป็นสำหรับการทำงานกับ GroupDocs.Annotation
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
เริ่มต้นคำอธิบายประกอบโดยระบุเส้นทางไปยังเอกสารอินพุต
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายประกอบอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: สร้างคำอธิบายประกอบรูปภาพ
 สร้างอินสแตนซ์ของ`ImageAnnotation`และระบุคุณสมบัติ เช่น ตำแหน่ง ความทึบ หมายเลขหน้า และเส้นทางรูปภาพ
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## ขั้นตอนที่ 4: เพิ่มคำอธิบายประกอบ
 เพิ่มคำอธิบายประกอบรูปภาพที่สร้างขึ้นลงในเอกสารโดยใช้`Add` วิธีการของคำอธิบายประกอบ
```csharp
annotator.Add(image);
```
## ขั้นตอนที่ 5: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุต
```csharp
annotator.Save(outputPath);
```
## ขั้นตอนที่ 6: แสดงเส้นทางเอาต์พุต
แสดงข้อความที่ระบุการบันทึกเอกสารสำเร็จและตำแหน่งของไฟล์เอาต์พุต
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีเพิ่มคำอธิบายประกอบรูปภาพลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยการทำตามขั้นตอนง่ายๆ เหล่านี้ คุณจะสามารถเพิ่มความสามารถในการประมวลผลเอกสารของคุณด้วยคุณลักษณะคำอธิบายประกอบที่มีประสิทธิภาพ
## คำถามที่พบบ่อย
### ฉันสามารถใส่คำอธิบายประกอบในเอกสารอื่นที่ไม่ใช่ PDF ได้หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### GroupDocs.Annotation เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Annotation เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
แน่นอน คุณสามารถปรับแต่งลักษณะ ขนาด สี และคุณสมบัติอื่นๆ ของคำอธิบายประกอบได้ตามความต้องการของคุณ
### GroupDocs.Annotation ให้การสนับสนุนคำอธิบายประกอบการทำงานร่วมกันหรือไม่
ใช่ GroupDocs.Annotation นำเสนอคุณลักษณะคำอธิบายประกอบที่ทำงานร่วมกัน ซึ่งช่วยให้ผู้ใช้หลายคนสามารถใส่คำอธิบายประกอบในเอกสารได้พร้อมกัน
### ฉันจะขอความช่วยเหลือหรือสนับสนุนเพิ่มเติมได้จากที่ไหน?
คุณสามารถไปที่ฟอรัม GroupDocs.Annotation เพื่อขอความช่วยเหลือและการสนับสนุนจากชุมชน