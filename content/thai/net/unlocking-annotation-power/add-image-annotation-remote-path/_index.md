---
"description": "เรียนรู้วิธีการเพิ่มคำอธิบายประกอบภาพลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ปรับปรุงการจัดการเอกสารด้วยความสามารถในการใส่คำอธิบายประกอบอันทรงพลัง"
"linktitle": "เพิ่มคำอธิบายภาพลงในเอกสาร (เส้นทางระยะไกล)"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "เพิ่มคำอธิบายภาพลงในเอกสาร (เส้นทางระยะไกล)"
"url": "/th/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# เพิ่มคำอธิบายภาพลงในเอกสาร (เส้นทางระยะไกล)

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำขั้นตอนการเพิ่มคำอธิบายประกอบภาพลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ไลบรารีนี้มอบเครื่องมืออันทรงพลังสำหรับการเพิ่มคำอธิบายประกอบเอกสารประเภทต่างๆ ด้วยโปรแกรม
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. GroupDocs.Annotation สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ให้แน่ใจว่าคุณมีการตั้งค่าสภาพแวดล้อมการพัฒนาการทำงานสำหรับการพัฒนา .NET
3. เอกสาร: เตรียมเอกสารที่คุณต้องการใส่คำอธิบายประกอบ สำหรับบทช่วยสอนนี้ เราจะถือว่าคุณมีเอกสาร PDF ชื่อ `input-pdf`.
4. รูปภาพสำหรับคำอธิบายประกอบ: เลือกรูปภาพที่คุณต้องการใช้สำหรับคำอธิบายประกอบ ตรวจสอบว่าคุณมี URL รูปภาพหรือเส้นทางภายในเครื่องพร้อมแล้ว

## นำเข้าเนมสเปซ
ก่อนที่เราจะเริ่มเขียนโค้ด เรามานำเข้าเนมสเปซที่จำเป็นกันก่อน:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอาต์พุต
ขั้นแรก ให้กำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: เริ่มต้น Annotator
สร้างอินสแตนซ์ของ `Annotator` คลาสและระบุเอกสารอินพุต
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // รหัสคำอธิบายจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: เพิ่มคำอธิบายภาพ
ตอนนี้เรามาเพิ่มคำอธิบายภาพลงในเอกสารกัน เราจะระบุคุณสมบัติของคำอธิบายภาพ เช่น ตำแหน่ง ความทึบ หมายเลขหน้า และเส้นทางของภาพ
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // ระบุตำแหน่งของคำอธิบาย
    CreatedOn = DateTime.Now, // กำหนดวันที่สร้าง
    Opacity = 0.7, // ตั้งค่าความทึบ (0 ถึง 1)
    PageNumber = 0, // ระบุหมายเลขหน้า
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // ระบุ URL ของรูปภาพ
};
annotator.Add(image); // เพิ่มคำอธิบายภาพ
```
## ขั้นตอนที่ 4: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Save(outputPath);
```
## ขั้นตอนที่ 5: แสดงเส้นทางเอาท์พุต
แจ้งให้ผู้ใช้ทราบเกี่ยวกับการบันทึกเอกสารที่ประสบความสำเร็จและแสดงเส้นทางเอาต์พุต
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการเพิ่มคำอธิบายประกอบภาพลงในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้แล้ว คุณจะสามารถปรับปรุงแอปพลิเคชันการจัดการเอกสารของคุณด้วยความสามารถในการใส่คำอธิบายประกอบอันทรงพลัง
## คำถามที่พบบ่อย
### สามารถใช้ GroupDocs.Annotation กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF ได้หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารต่างๆ รวมถึง Word, Excel, PowerPoint และอื่นๆ อีกมากมาย
### GroupDocs.Annotation เข้ากันได้กับ .NET Core ได้หรือไม่
ใช่ GroupDocs.Annotation เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบได้หรือไม่
ใช่ คุณสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบ เช่น สี ความทึบ และขนาด
### GroupDocs.Annotation รองรับคุณลักษณะการใส่คำอธิบายประกอบแบบร่วมมือกันหรือไม่
ใช่ GroupDocs.Annotation นำเสนอคุณลักษณะการใส่คำอธิบายประกอบแบบร่วมมือกันสำหรับการทำงานร่วมกันแบบเรียลไทม์บนเอกสาร
### มีเวอร์ชันทดลองใช้สำหรับการทดสอบหรือไม่?
ใช่ คุณสามารถรับรุ่นทดลองใช้งาน GroupDocs.Annotation ได้ฟรีจาก [ที่นี่](https://releases-groupdocs.com/).