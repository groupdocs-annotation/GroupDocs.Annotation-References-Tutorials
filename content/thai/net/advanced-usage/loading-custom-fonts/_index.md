---
"description": "เรียนรู้วิธีการโหลดแบบอักษรที่กำหนดเองใน GroupDocs.Annotation สำหรับ .NET ได้อย่างราบรื่นเพื่อปรับปรุงคำอธิบายประกอบเอกสาร ปฏิบัติตามขั้นตอนทีละขั้นตอนของเราเพื่อการผสานรวมที่ง่ายดาย"
"linktitle": "กำลังโหลดแบบอักษรที่กำหนดเอง"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "กำลังโหลดแบบอักษรที่กำหนดเอง"
"url": "/th/net/advanced-usage/loading-custom-fonts/"
"weight": 20
---

# กำลังโหลดแบบอักษรที่กำหนดเอง

## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถเพิ่มฟีเจอร์คำอธิบายประกอบให้กับแอปพลิเคชัน .NET ได้อย่างง่ายดาย หนึ่งในฟังก์ชันหลักที่ไลบรารีนี้มีให้คือความสามารถในการโหลดแบบอักษรที่กำหนดเอง ซึ่งช่วยให้ปรับแต่งและมีความยืดหยุ่นมากขึ้นในการใส่คำอธิบายประกอบในเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำเนินการกับบทช่วยสอน โปรดแน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Annotation สำหรับไลบรารี .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก [ที่นี่](https://releases-groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา .NET: ตรวจสอบให้แน่ใจว่าคุณมีการตั้งค่าสภาพแวดล้อมการทำงานสำหรับการพัฒนา .NET
3. การเข้าถึงแบบอักษรที่กำหนดเอง: เตรียมแบบอักษรที่กำหนดเองที่คุณต้องการโหลดลงในแอปพลิเคชันของคุณ

## นำเข้าเนมสเปซ
ในโครงการ .NET ของคุณ นำเข้าเนมสเปซที่จำเป็นสำหรับการใช้ GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของวัตถุ Annotator
สร้างอินสแตนซ์ของ `Annotator` คลาสโดยให้เส้นทางไปยังเอกสาร PDF อินพุตพร้อมกับไดเร็กทอรีแบบอักษรที่กำหนดเอง:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // รหัสของคุณสำหรับการดำเนินการต่อไปจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการแสดงตัวอย่าง
กำหนดตัวเลือกการแสดงตัวอย่างเพื่อระบุว่าจะสร้างตัวอย่างเอกสารอย่างไร คุณสามารถตั้งค่าตัวเลือกต่างๆ เช่น รูปแบบการแสดงตัวอย่าง หมายเลขหน้า เป็นต้น:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## ขั้นตอนที่ 3: สร้างตัวอย่างเอกสาร
การใช้ประโยชน์จาก `GeneratePreview` วิธีการของ `Document` คุณสมบัติในการสร้างตัวอย่างด้วยแบบอักษรที่กำหนดเอง:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## ขั้นตอนที่ 4: แสดงเส้นทางผลลัพธ์
ในที่สุด ให้แสดงข้อความแจ้งว่าการสร้างตัวอย่างเอกสารสำเร็จแล้ว พร้อมทั้งระบุเส้นทางไดเร็กทอรีเอาท์พุต:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## บทสรุป
โดยสรุป การโหลดแบบอักษรที่กำหนดเองใน GroupDocs.Annotation สำหรับ .NET ช่วยให้นักพัฒนาสามารถปรับแต่งคำอธิบายประกอบเอกสารตามความต้องการของตนเองได้อย่างยืดหยุ่น เมื่อทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้แล้ว คุณสามารถผสานแบบอักษรที่กำหนดเองเข้ากับแอปพลิเคชัน .NET ได้อย่างราบรื่น และปรับปรุงประสบการณ์ในการเขียนคำอธิบายประกอบให้กับผู้ใช้
## คำถามที่พบบ่อย
### ฉันสามารถโหลดแบบอักษรที่กำหนดเองหลายตัวพร้อมกันได้ไหม
ใช่ คุณสามารถระบุไดเรกทอรีแบบอักษรหลายตัวเมื่อสร้างอินสแตนซ์ `Annotator` วัตถุ.
### มีข้อจำกัดใด ๆ เกี่ยวกับประเภทของแบบอักษรที่รองรับหรือไม่
GroupDocs.Annotation สำหรับ .NET รองรับฟอนต์หลายประเภท รวมถึงฟอนต์ TrueType (.ttf) และ OpenType (.otf)
### ฉันสามารถเปลี่ยนฟอนต์ที่โหลดแบบไดนามิกระหว่างการรันไทม์ได้หรือไม่
ใช่ คุณสามารถปรับเปลี่ยนไดเร็กทอรีแบบอักษรแบบไดนามิกและโหลดคำอธิบายเอกสารใหม่ตามต้องการได้
### GroupDocs.Annotation รองรับการฝังแบบอักษรในเอกสารผลลัพธ์หรือไม่
ใช่ คุณสามารถฝังแบบอักษรที่กำหนดเองในเอกสารผลลัพธ์เพื่อให้แน่ใจว่าการแสดงผลมีความสอดคล้องกันบนแพลตฟอร์มต่างๆ
### มีวิธีจัดการการอนุญาตสิทธิ์แบบอักษรภายในแอปพลิเคชันหรือไม่
GroupDocs.Annotation มีตัวเลือกสำหรับการจัดการใบอนุญาตแบบอักษร รวมถึงใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินผล