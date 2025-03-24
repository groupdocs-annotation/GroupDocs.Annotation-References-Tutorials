---
title: ลบการตอบกลับด้วย ID ใน .NET
linktitle: ลบการตอบกลับด้วย ID ใน .NET
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีลบการตอบกลับด้วย ID ใน .NET โดยใช้ GroupDocs.Annotation ปฏิบัติตามบทช่วยสอนทีละขั้นตอนของเราเพื่อการจัดการคำอธิบายประกอบเอกสารที่มีประสิทธิภาพ
weight: 16
url: /th/net/removing-annotations/remove-replies-by-id/
---
## การแนะนำ
ในขอบเขตของการพัฒนา .NET ความสามารถในการจัดการคำอธิบายประกอบภายในเอกสารถือเป็นสิ่งสำคัญสำหรับแอปพลิเคชันที่หลากหลาย ไม่ว่าคุณจะทำงานกับ PDF, เอกสาร Word หรือรูปแบบอื่นๆ การมีความสามารถในการจัดการคำอธิบายประกอบโดยทางโปรแกรมจะเปิดโลกแห่งความเป็นไปได้ เครื่องมืออันทรงพลังอย่างหนึ่งสำหรับการจัดการคำอธิบายประกอบใน .NET คือ GroupDocs.Annotation
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกบทช่วยสอนเกี่ยวกับการลบการตอบกลับด้วย ID ใน .NET โดยใช้ GroupDocs.Annotation ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. การติดตั้ง GroupDocs.Annotation
 ขั้นแรก คุณต้องติดตั้ง GroupDocs.Annotation สำหรับ .NET คุณสามารถดาวน์โหลดห้องสมุดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/) และปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้ในเอกสารประกอบ[ที่นี่](https://tutorials.groupdocs.com/annotation/net/).
### 2. ความเข้าใจพื้นฐานเกี่ยวกับ C# และ .NET
จำเป็นต้องมีความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และเฟรมเวิร์ก .NET พร้อมด้วยตัวอย่างในบทช่วยสอนนี้
### 3. เอกสารคำอธิบายประกอบพร้อมคำตอบ
เตรียมเอกสารที่มีคำอธิบายประกอบพร้อมการตอบกลับ เอกสารนี้จะทำหน้าที่เป็นข้อมูลเข้าสำหรับกระบวนการลบ

## นำเข้าเนมสเปซ
ในโปรเจ็กต์ .NET ของคุณ ให้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชัน GroupDocs.Annotation
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ระบุเส้นทางที่คุณต้องการบันทึกเอกสารที่แก้ไขหลังจากลบการตอบกลับ
## ขั้นตอนที่ 2: โหลดเอกสารและคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
{
    List<AnnotationBase> annotations = annotator.Get();
```
 โหลดเอกสารที่มีคำอธิบายประกอบพร้อมการตอบกลับโดยใช้`Annotator` คลาสและดึงข้อมูลคอลเล็กชันคำอธิบายประกอบ
## ขั้นตอนที่ 3: ลบการตอบกลับด้วย ID
```csharp
annotations[0].Replies.RemoveAll(x => x.Id == 4);
```
ระบุการตอบกลับที่คุณต้องการลบออกตาม ID และลบออกจากคอลเลกชันการตอบกลับของคำอธิบายประกอบที่เกี่ยวข้อง
## ขั้นตอนที่ 4: บันทึกการเปลี่ยนแปลง
```csharp
annotator.Update(annotations);
annotator.Save(outputPath);
```
อัปเดตคำอธิบายประกอบด้วยการตอบกลับที่ถูกลบออก และบันทึกเอกสารที่แก้ไขไปยังเส้นทางเอาต์พุตที่ระบุ
## ขั้นตอนที่ 5: ยืนยันความสำเร็จ
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
แสดงข้อความยืนยันที่ระบุว่าบันทึกเอกสารเรียบร้อยแล้วโดยลบการตอบกลับออก

## บทสรุป
โดยสรุป GroupDocs.Annotation สำหรับ .NET มอบโซลูชันที่ตรงไปตรงมาสำหรับการจัดการคำอธิบายประกอบภายในเอกสาร ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถลบการตอบกลับด้วย ID ได้อย่างง่ายดาย ช่วยให้คุณปรับแต่งคำอธิบายประกอบในเอกสารให้ตรงกับความต้องการเฉพาะของคุณได้อย่างง่ายดายและมีประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Annotation สามารถใช้กับเอกสารรูปแบบอื่นนอกเหนือจาก PDF ได้หรือไม่
ใช่ GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint และอื่นๆ
### GroupDocs.Annotation มีให้ทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Annotation ได้ที่ไหน
 คุณสามารถหาการสนับสนุนและมีส่วนร่วมกับชุมชนได้[ที่นี่](https://forum.groupdocs.com/c/annotation/10).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Annotation ได้อย่างไร
 คุณสามารถรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะซื้อ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อ GroupDocs.Annotation ได้[ที่นี่](https://purchase.groupdocs.com/buy).