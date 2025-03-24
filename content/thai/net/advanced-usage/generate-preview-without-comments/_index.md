---
title: สร้างการแสดงตัวอย่างโดยไม่มีความคิดเห็น
linktitle: สร้างการแสดงตัวอย่างโดยไม่มีความคิดเห็น
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีผสานรวมความสามารถในการใส่คำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่นโดยใช้ GroupDocs.Annotation สำหรับ .NET
weight: 14
url: /th/net/advanced-usage/generate-preview-without-comments/
---
## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นเครื่องมืออันทรงพลังที่ช่วยให้นักพัฒนาสามารถรวมคุณสมบัติคำอธิบายประกอบเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น ไม่ว่าคุณจะทำงานบนระบบการจัดการเอกสาร แพลตฟอร์มการทำงานร่วมกัน หรือแอปพลิเคชันอื่นๆ ที่ต้องการความสามารถในการใส่คำอธิบายประกอบเอกสาร GroupDocs.Annotation มีชุดเครื่องมือที่ครอบคลุมเพื่อปรับปรุงฟังก์ชันการทำงานของแอปพลิเคชันของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มใช้ GroupDocs.Annotation สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง GroupDocs.Annotation สำหรับ .NET
 ในการเริ่มต้น คุณต้องดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET คุณสามารถค้นหาลิงค์ดาวน์โหลด[ที่นี่](https://releases.groupdocs.com/annotation/net/)- ปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้ในเอกสารประกอบเพื่อให้กระบวนการติดตั้งราบรื่น
### 2. รับใบอนุญาต
 GroupDocs.Annotation สำหรับ .NET ต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์ คุณสามารถขอรับใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy) หรือเลือกใช้ใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/) เพื่อวัตถุประสงค์ในการทดสอบ
### 3. ความคุ้นเคยกับ .NET Framework
ความรู้พื้นฐานเกี่ยวกับ .NET Framework และภาษาการเขียนโปรแกรม C# เป็นสิ่งจำเป็นต่อการใช้งาน GroupDocs.Annotation สำหรับ .NET ได้อย่างมีประสิทธิภาพ

## นำเข้าเนมสเปซ
ตอนนี้คุณได้ตั้งค่าข้อกำหนดเบื้องต้นแล้ว มานำเข้าเนมสเปซที่จำเป็นลงในแอปพลิเคชัน .NET ของคุณกันดีกว่า

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

ทำตามคำแนะนำทีละขั้นตอนเหล่านี้เพื่อสร้างการแสดงตัวอย่างโดยไม่มีความคิดเห็นโดยใช้ GroupDocs.Annotation สำหรับ .NET:
## ขั้นตอนที่ 1: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## ขั้นตอนที่ 2: กำหนดค่าตัวเลือกการแสดงตัวอย่าง
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## ขั้นตอนที่ 3: ระบุรูปแบบการแสดงตัวอย่างและหมายเลขหน้า
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## ขั้นตอนที่ 4: ปิดการใช้งานการแสดงความคิดเห็น
```csharp
    previewOptions.RenderComments = false;
```
## ขั้นตอนที่ 5: สร้างการแสดงตัวอย่าง
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
เมื่อคุณทำตามขั้นตอนเหล่านี้แล้ว แอปพลิเคชัน .NET ของคุณจะสามารถสร้างการแสดงตัวอย่างหน้าที่ระบุจากเอกสารโดยไม่ต้องแสดงความคิดเห็น

## บทสรุป
การรวมคุณสมบัติคำอธิบายประกอบเข้ากับแอปพลิเคชัน .NET ของคุณง่ายกว่าที่เคยด้วย GroupDocs.Annotation สำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมความสามารถในการใส่คำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชันของคุณได้อย่างราบรื่น เพิ่มประสิทธิภาพการทำงานร่วมกันและการจัดการเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, PPTX, XLSX และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่สร้างโดยใช้ GroupDocs.Annotation สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET มีตัวเลือกการปรับแต่งที่ครอบคลุม ซึ่งช่วยให้คุณสามารถปรับแต่งรูปลักษณ์ของคำอธิบายประกอบให้เหมาะกับความต้องการของแอปพลิเคชันของคุณได้
### GroupDocs.Annotation สำหรับ .NET รองรับการทำงานร่วมกันแบบหลายผู้ใช้หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET นำเสนอคุณลักษณะคำอธิบายประกอบที่ทำงานร่วมกัน ช่วยให้ผู้ใช้หลายคนสามารถใส่คำอธิบายประกอบในเอกสารได้พร้อมกัน
### มีการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
 ใช่ การสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Annotation สำหรับ .NET มีให้ผ่านทาง[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/annotation/10).
### ฉันสามารถลองใช้ GroupDocs.Annotation สำหรับ .NET ฟรีก่อนซื้อได้หรือไม่
 ได้ คุณสามารถสำรวจคุณลักษณะต่างๆ ของ GroupDocs.Annotation สำหรับ .NET ได้ด้วยการดาวน์โหลดรุ่นทดลองใช้ฟรี[ที่นี่](https://releases.groupdocs.com/).