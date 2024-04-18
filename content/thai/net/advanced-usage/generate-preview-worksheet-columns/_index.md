---
title: สร้างคอลัมน์แผ่นงานแสดงตัวอย่าง
linktitle: สร้างคอลัมน์แผ่นงานแสดงตัวอย่าง
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีใส่คำอธิบายประกอบในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET บทช่วยสอนทีละขั้นตอนสำหรับนักพัฒนา .NET ปรับปรุงแอปพลิเคชันของคุณ
type: docs
weight: 15
url: /th/net/advanced-usage/generate-preview-worksheet-columns/
---
## การแนะนำ
ยินดีต้อนรับสู่บทช่วยสอนที่ครอบคลุมของเราเกี่ยวกับการควบคุมความสามารถของ GroupDocs.Annotation สำหรับ .NET! ในคู่มือนี้ เราจะแนะนำคุณตลอดกระบวนการใช้เครื่องมืออันทรงพลังนี้เพื่อใส่คำอธิบายประกอบในเอกสารอย่างมีประสิทธิภาพ ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเป็นมือใหม่ในโลกแห่งการพัฒนา .NET บทช่วยสอนนี้จะช่วยให้คุณมีความรู้และทักษะที่จำเป็นในการรวมคุณสมบัติคำอธิบายประกอบเข้ากับแอปพลิเคชันของคุณได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. การตั้งค่าสภาพแวดล้อมการพัฒนา .NET
ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้บนเครื่องของคุณ คุณสามารถดาวน์โหลด .NET SDK เวอร์ชันล่าสุดได้จากเว็บไซต์ Microsoft
### 2. GroupDocs.Annotation สำหรับ .NET Library
 ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET จากไฟล์ที่ให้มา[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/annotation/net/)- ปฏิบัติตามคำแนะนำในการติดตั้งเพื่อรวมไลบรารีเข้ากับโปรเจ็กต์ของคุณให้สำเร็จ
### 3. ใส่เอกสาร
เตรียมเอกสารตัวอย่าง (เช่น "input.xlsx") ที่คุณต้องการใส่คำอธิบายประกอบโดยใช้ GroupDocs.Annotation สำหรับ .NET ตรวจสอบให้แน่ใจว่าเอกสารสามารถเข้าถึงได้จากไดเรกทอรีโครงการของคุณ

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ เนมสเปซเหล่านี้ให้การเข้าถึงคลาสและวิธีการที่จำเป็นในการดำเนินงานคำอธิบายประกอบเอกสารอย่างมีประสิทธิภาพ

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

ตอนนี้เราได้ตั้งค่าสภาพแวดล้อมการพัฒนาและนำเข้าเนมสเปซที่จำเป็นแล้ว เรามาเริ่มสร้างคอลัมน์เวิร์กชีทแสดงตัวอย่างสำหรับเอกสารของเรากันดีกว่า
## ขั้นตอนที่ 1: เริ่มต้นตัวเลือกการแสดงตัวอย่าง
```csharp
PreviewOptions previewOptions = new PreviewOptions(
    pageNumber => new FileStream(Path.Combine("Your Document Directory", $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose()
);
```
## ขั้นตอนที่ 2: กำหนดคอลัมน์แผ่นงาน
```csharp
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));
```
## ขั้นตอนที่ 3: เริ่มต้นคำอธิบายประกอบด้วยเอกสารอินพุต
```csharp
using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
## ขั้นตอนที่ 4: แสดงข้อความแสดงความสำเร็จ
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## บทสรุป
ยินดีด้วย! คุณได้เรียนรู้วิธีสร้างคอลัมน์แผ่นงานแสดงตัวอย่างโดยใช้ GroupDocs.Annotation สำหรับ .NET เรียบร้อยแล้ว ด้วยความรู้นี้ คุณสามารถรวมความสามารถคำอธิบายประกอบขั้นสูงเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Annotation เข้ากันได้กับเฟรมเวิร์ก .NET อื่นๆ หรือไม่
ใช่ GroupDocs.Annotation รองรับ .NET Framework ต่างๆ รวมถึง .NET Core และ .NET Framework
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่สร้างด้วย GroupDocs.Annotation ได้หรือไม่
อย่างแน่นอน! GroupDocs.Annotation มีตัวเลือกการปรับแต่งมากมายสำหรับลักษณะคำอธิบายประกอบ รวมถึงสี ความทึบ และประเภทคำอธิบายประกอบ
### GroupDocs.Annotation รองรับรูปแบบเอกสารอื่นที่ไม่ใช่ Excel หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, PowerPoint และอื่นๆ
### มีการสนับสนุนด้านเทคนิคสำหรับผู้ใช้ GroupDocs.Annotation หรือไม่
 ใช่ คุณสามารถเข้าถึงการสนับสนุนทางเทคนิคและฟอรั่มชุมชนผ่านทางที่ให้ไว้[ลิงค์สนับสนุน](https://forum.groupdocs.com/c/annotation/10).
### ฉันสามารถลองใช้ GroupDocs.Annotation ก่อนซื้อใบอนุญาตได้หรือไม่
 แน่นอน! คุณสามารถดาวน์โหลด GroupDocs.Annotation เวอร์ชันทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).