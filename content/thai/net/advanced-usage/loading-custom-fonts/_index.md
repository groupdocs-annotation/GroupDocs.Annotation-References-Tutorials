---
title: กำลังโหลดแบบอักษรที่กำหนดเอง
linktitle: กำลังโหลดแบบอักษรที่กำหนดเอง
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีโหลดแบบอักษรที่กำหนดเองใน GroupDocs.Annotation สำหรับ .NET ได้อย่างราบรื่น เพื่อปรับปรุงคำอธิบายประกอบในเอกสาร ปฏิบัติตามทีละขั้นตอนของเราเพื่อการบูรณาการที่ง่ายดาย
type: docs
weight: 20
url: /th/net/advanced-usage/loading-custom-fonts/
---
## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถเพิ่มคุณลักษณะคำอธิบายประกอบให้กับแอปพลิเคชัน .NET ของตนได้อย่างง่ายดาย หนึ่งในฟังก์ชันหลักที่มีให้คือความสามารถในการโหลดแบบอักษรที่กำหนดเอง ช่วยให้ปรับแต่งได้มากขึ้นและมีความยืดหยุ่นในคำอธิบายประกอบในเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนดำเนินการบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา .NET: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการทำงานที่ตั้งค่าไว้สำหรับการพัฒนา .NET
3. การเข้าถึงแบบอักษรที่กำหนดเอง: เตรียมแบบอักษรที่กำหนดเองที่คุณต้องการโหลดลงในแอปพลิเคชันของคุณ

## นำเข้าเนมสเปซ
ในโปรเจ็กต์ .NET ของคุณ ให้นำเข้าเนมสเปซที่จำเป็นสำหรับการใช้ GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของวัตถุคำอธิบายประกอบ
 สร้างอินสแตนซ์ของ`Annotator` คลาสโดยระบุเส้นทางไปยังเอกสาร PDF อินพุตพร้อมกับไดเร็กทอรีแบบอักษรที่กำหนดเอง:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // รหัสของคุณสำหรับการดำเนินการเพิ่มเติมจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการแสดงตัวอย่าง
กำหนดตัวเลือกการแสดงตัวอย่างเพื่อระบุวิธีการสร้างการแสดงตัวอย่างเอกสาร คุณสามารถตั้งค่าตัวเลือกต่างๆ เช่น รูปแบบการแสดงตัวอย่าง หมายเลขหน้า ฯลฯ:
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
 ใช้`GeneratePreview` วิธีการของ`Document` คุณสมบัติในการสร้างตัวอย่างด้วยแบบอักษรที่กำหนดเอง:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## ขั้นตอนที่ 4: แสดงเส้นทางเอาต์พุต
สุดท้ายนี้ ให้แสดงข้อความที่ระบุถึงการสร้างตัวอย่างเอกสารที่ประสบความสำเร็จพร้อมกับเส้นทางไดเร็กทอรีเอาต์พุต:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## บทสรุป
โดยสรุป การโหลดแบบอักษรที่กำหนดเองใน GroupDocs.Annotation สำหรับ .NET ช่วยให้นักพัฒนามีความยืดหยุ่นในการปรับแต่งคำอธิบายประกอบเอกสารตามความต้องการของพวกเขา ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมแบบอักษรที่กำหนดเองเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น และปรับปรุงประสบการณ์คำอธิบายประกอบสำหรับผู้ใช้
## คำถามที่พบบ่อย
### ฉันสามารถโหลดแบบอักษรที่กำหนดเองหลายแบบพร้อมกันได้หรือไม่
 ใช่ คุณสามารถระบุไดเร็กทอรีฟอนต์ได้หลายไดเร็กทอรีเมื่อสร้างอินสแตนซ์`Annotator` วัตถุ.
### มีข้อจำกัดเกี่ยวกับประเภทของแบบอักษรที่รองรับหรือไม่?
GroupDocs.Annotation สำหรับ .NET รองรับแบบอักษรหลากหลายประเภท รวมถึงแบบอักษร TrueType (.ttf) และ OpenType (.otf)
### ฉันสามารถเปลี่ยนแบบอักษรที่โหลดแบบไดนามิกระหว่างรันไทม์ได้หรือไม่
ได้ คุณสามารถแก้ไขไดเร็กทอรีแบบอักษรแบบไดนามิกและโหลดคำอธิบายประกอบเอกสารซ้ำได้ตามต้องการ
### GroupDocs.Annotation รองรับการฝังแบบอักษรในเอกสารเอาท์พุตหรือไม่
ได้ คุณสามารถฝังแบบอักษรที่กำหนดเองในเอกสารเอาท์พุตได้เพื่อให้แน่ใจว่ามีการเรนเดอร์ที่สอดคล้องกันบนแพลตฟอร์มต่างๆ
### มีวิธีจัดการลิขสิทธิ์แบบอักษรภายในแอปพลิเคชันหรือไม่
GroupDocs.Annotation มีตัวเลือกสำหรับจัดการสิทธิ์การใช้งานแบบอักษร รวมถึงสิทธิ์การใช้งานชั่วคราวเพื่อวัตถุประสงค์ในการประเมิน