---
title: เพิ่มคำอธิบายประกอบลูกศรลงในเอกสาร
linktitle: เพิ่มคำอธิบายประกอบลูกศรลงในเอกสาร
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีเพิ่มคำอธิบายประกอบแบบลูกศรลงในเอกสารของคุณโดยใช้ GroupDocs.Annotation สำหรับ .NET เพิ่มความชัดเจนของเอกสารและการโต้ตอบได้อย่างง่ายดาย
weight: 11
url: /th/net/unlocking-annotation-power/add-arrow-annotation/
---

# เพิ่มคำอธิบายประกอบลูกศรลงในเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการเพิ่มคำอธิบายประกอบแบบลูกศรให้กับเอกสารของคุณโดยใช้ GroupDocs.Annotation สำหรับ .NET คำอธิบายประกอบแบบลูกศรมีประโยชน์ในการระบุทิศทางหรือชี้องค์ประกอบเฉพาะภายในเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET: ติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/annotation/net/).
2. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนาสำหรับการพัฒนา .NET รวมถึง Visual Studio หรือ IDE ที่ต้องการอื่นๆ

## นำเข้าเนมสเปซ
ประการแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่จำเป็นสำหรับคำอธิบายประกอบ
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ขั้นตอนที่ 1: เริ่มต้นคำอธิบายประกอบ
เตรียมข้อมูลเบื้องต้นให้กับคำอธิบายประกอบโดยระบุเส้นทางไฟล์เอกสารอินพุต
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ขั้นตอนที่ 2: สร้างคำอธิบายประกอบลูกศร
สร้างอินสแตนซ์ของคลาส ArrowAnnotation และกำหนดคุณสมบัติของคลาส เช่น ตำแหน่ง ข้อความ ความทึบ สีปากกา สไตล์ ความกว้าง ฯลฯ
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
		PageNumber = 0,
		PenColor = 65535,
		PenStyle = PenStyle.Dot,
		PenWidth = 3,
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
## ขั้นตอนที่ 3: เพิ่มคำอธิบายประกอบ
 เพิ่มคำอธิบายประกอบลูกศรลงในเอกสารโดยใช้`Add` วิธีการของคำอธิบายประกอบ
```csharp
	annotator.Add(arrow);
```
## ขั้นตอนที่ 4: บันทึกเอกสาร
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
	annotator.Save(outputPath);
}
```
## ขั้นตอนที่ 5: แสดงการยืนยัน
แสดงข้อความยืนยันที่ระบุว่าการบันทึกเอกสารสำเร็จ
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
ตอนนี้ คุณได้เพิ่มคำอธิบายประกอบแบบลูกศรลงในเอกสารของคุณโดยใช้ GroupDocs.Annotation for .NET เรียบร้อยแล้ว

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการเพิ่มคำอธิบายประกอบแบบลูกศรให้กับเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถปรับปรุงเอกสารของคุณด้วยตัวบ่งชี้ทิศทางที่ชัดเจน ทำให้มีข้อมูลและมีส่วนร่วมมากขึ้น
## คำถามที่พบบ่อย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบลูกศรได้หรือไม่
ใช่ คุณสามารถปรับแต่งคุณสมบัติต่างๆ ได้ เช่น สี สไตล์ ความกว้าง และความทึบ เพื่อให้เหมาะกับความต้องการและข้อกำหนดของเอกสาร
### GroupDocs.Annotation เข้ากันได้กับเอกสารทุกรูปแบบหรือไม่
GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, PPTX, XLSX และอื่นๆ
### ฉันสามารถเพิ่มคำอธิบายประกอบโดยทางโปรแกรมโดยใช้ GroupDocs.Annotation ได้หรือไม่
ใช่ GroupDocs.Annotation มี API ที่ช่วยให้คุณสามารถเพิ่ม แก้ไข และลบคำอธิบายประกอบออกจากเอกสารได้โดยทางโปรแกรม
### GroupDocs.Annotation ให้ทดลองใช้ฟรีหรือไม่
 ได้ คุณสามารถลองใช้ GroupDocs.Annotation ได้ฟรีโดยดาวน์โหลดจาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Annotation ได้จากที่ไหน
สำหรับการสนับสนุนทางเทคนิคและความช่วยเหลือ คุณสามารถไปที่ฟอรัม GroupDocs.Annotation[ที่นี่](https://forum.groupdocs.com/c/annotation/10).