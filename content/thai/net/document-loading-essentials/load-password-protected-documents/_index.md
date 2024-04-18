---
title: โหลดเอกสารที่ป้องกันด้วยรหัสผ่าน
linktitle: โหลดเอกสารที่ป้องกันด้วยรหัสผ่าน
second_title: GroupDocs.Annotation .NET API
description: ปรับปรุงการทำงานร่วมกันและการตรวจสอบเอกสารด้วย GroupDocs.Annotation สำหรับ .NET ใส่คำอธิบายประกอบ PDF และราบรื่นยิ่งขึ้นในแอป .NET ของคุณ
type: docs
weight: 17
url: /th/net/document-loading-essentials/load-password-protected-documents/
---
## การแนะนำ
ในโลกที่หมุนไปอย่างรวดเร็วในปัจจุบัน การทำงานร่วมกันเป็นกุญแจสู่ความสำเร็จ ไม่ว่าคุณจะทำงานในโครงการร่วมกับเพื่อนร่วมงาน ลูกค้า หรือคู่ค้า ความสามารถในการใส่คำอธิบายประกอบและแบ่งปันเอกสารอย่างมีประสิทธิภาพสามารถปรับปรุงประสิทธิภาพการทำงานและปรับปรุงขั้นตอนการทำงานได้อย่างมาก GroupDocs.Annotation สำหรับ .NET นำเสนอโซลูชันอันทรงพลังสำหรับการใส่คำอธิบายประกอบ PDF และรูปแบบเอกสารอื่นๆ โดยตรงภายในแอปพลิเคชัน .NET ของคุณ ช่วยให้สามารถทำงานร่วมกันและกระบวนการตรวจสอบเอกสารได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำดิ่งสู่โลกแห่งคำอธิบายประกอบเอกสารด้วย GroupDocs.Annotation สำหรับ .NET มีข้อกำหนดเบื้องต้นบางประการที่คุณต้องตรวจสอบให้แน่ใจก่อน:
### 1. ติดตั้ง GroupDocs.Annotation สำหรับ .NET
 ในการเริ่มต้น คุณจะต้องดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Annotation สำหรับ .NET คุณสามารถค้นหาลิงค์ดาวน์โหลด[ที่นี่](https://releases.groupdocs.com/annotation/net/)- ปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้เพื่อตั้งค่าไลบรารีในสภาพแวดล้อม .NET ของคุณ
### 2. รับใบอนุญาตหรือใช้ใบอนุญาตชั่วคราว
 GroupDocs.Annotation สำหรับ .NET จำเป็นต้องมีใบอนุญาตที่ถูกต้องเพื่อปลดล็อกการทำงานเต็มรูปแบบ คุณสามารถซื้อใบอนุญาตได้จากเว็บไซต์ GroupDocs[ที่นี่](https://purchase.groupdocs.com/buy)หรือคุณสามารถขอใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### 3. ความคุ้นเคยกับการพัฒนา C# และ .NET
ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C# และการพัฒนา .NET ถือเป็นสิ่งสำคัญในการใช้ GroupDocs.Annotation สำหรับ .NET ได้อย่างมีประสิทธิภาพ หากคุณยังใหม่กับ C# หรือ .NET ลองพิจารณาทำความคุ้นเคยกับภาษาและกรอบงานผ่านบทช่วยสอนและแหล่งข้อมูลออนไลน์

## นำเข้าเนมสเปซที่จำเป็น
ก่อนที่คุณจะเริ่มใส่คำอธิบายประกอบในเอกสาร ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ ซึ่งช่วยให้คุณเข้าถึงคลาสและวิธีการที่ได้รับจาก GroupDocs.Annotation สำหรับ .NET ได้อย่างราบรื่น
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ตอนนี้คุณมีข้อกำหนดเบื้องต้นและนำเข้าเนมสเปซที่จำเป็นแล้ว เรามาเจาะลึกเรื่องการใส่คำอธิบายประกอบเอกสารที่มีการป้องกันด้วยรหัสผ่านโดยใช้ GroupDocs.Annotation สำหรับ .NET กันดีกว่า ด้านล่างนี้เป็นคำแนะนำทีละขั้นตอนเพื่อช่วยให้คุณทำงานนี้สำเร็จ:
## ขั้นตอนที่ 1: โหลดเอกสาร
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
LoadOptions loadOptions = new LoadOptions() { Password = "1234" };
```
ในขั้นตอนนี้ เราจะกำหนดเส้นทางเอาต์พุตสำหรับเอกสารที่มีคำอธิบายประกอบ และระบุตัวเลือกการโหลด รวมถึงรหัสผ่านที่จำเป็นในการเปิดเอกสารที่มีการป้องกันด้วยรหัสผ่าน
## ขั้นตอนที่ 2: เริ่มต้นคำอธิบายประกอบ
```csharp
using (Annotator annotator = new Annotator("input.pdf"_PROTECTED, loadOptions))
```
 ที่นี่เราสร้างอินสแตนซ์ของ`Annotator` คลาสส่งผ่านเส้นทางไปยังเอกสารอินพุตและตัวเลือกการโหลดเป็นพารามิเตอร์ ที่`using` คำสั่งทำให้มั่นใจได้ว่า`Annotator` วัตถุถูกกำจัดอย่างเหมาะสมหลังการใช้งาน
## ขั้นตอนที่ 3: เพิ่มคำอธิบายประกอบ
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
 ในขั้นตอนนี้ เราจะสร้างใหม่`AreaAnnotation` วัตถุ ระบุตำแหน่งและขนาดของกล่องคำอธิบายประกอบ ตลอดจนสีพื้นหลัง จากนั้นเราจะเพิ่มคำอธิบายประกอบให้กับเอกสารโดยใช้`Add` วิธีการของ`Annotator` วัตถุ.
## ขั้นตอนที่ 4: บันทึกเอกสารคำอธิบายประกอบ
```csharp
annotator.Save(outputPath);
```
 สุดท้าย เราจะบันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุโดยใช้`Save` วิธีการของ`Annotator` วัตถุ.
## ขั้นตอนที่ 5: แสดงข้อความยืนยัน
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
เพื่อให้ข้อเสนอแนะแก่ผู้ใช้ เราจะแสดงข้อความยืนยันที่ระบุว่าเอกสารได้รับการบันทึกเรียบร้อยแล้ว และระบุตำแหน่งของไฟล์เอาต์พุต

## บทสรุป
โดยสรุป GroupDocs.Annotation สำหรับ .NET นำเสนอโซลูชันที่มีประสิทธิภาพและเต็มไปด้วยฟีเจอร์มากมายสำหรับการใส่คำอธิบายประกอบเอกสารภายในแอปพลิเคชัน .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนที่ให้ไว้ในบทความนี้ คุณสามารถรวมความสามารถในการใส่คำอธิบายประกอบเอกสารเข้ากับโปรเจ็กต์ของคุณได้อย่างง่ายดาย เปิดใช้งานกระบวนการทำงานร่วมกันและการตรวจสอบเอกสารที่ได้รับการปรับปรุง
## คำถามที่พบบ่อย
### ถาม: GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับเอกสารทุกรูปแบบหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ
### ถาม: ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่สร้างด้วย GroupDocs.Annotation สำหรับ .NET ได้หรือไม่
อย่างแน่นอน! GroupDocs.Annotation สำหรับ .NET มีตัวเลือกการปรับแต่งคำอธิบายประกอบที่ครอบคลุม ซึ่งช่วยให้คุณควบคุมแง่มุมต่างๆ ได้ เช่น สี ขนาด ความทึบ และอื่นๆ
### ถาม: GroupDocs.Annotation สำหรับ .NET มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถดาวน์โหลด GroupDocs.Annotation สำหรับ .NET เวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/)เวอร์ชันทดลองช่วยให้คุณสามารถประเมินผลิตภัณฑ์ก่อนตัดสินใจซื้อ
### ถาม: ฉันจะรับการสนับสนุน GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
 หากคุณมีคำถามหรือพบปัญหาใดๆ ในขณะที่ใช้ GroupDocs.Annotation สำหรับ .NET คุณสามารถไปที่ฟอรั่มการสนับสนุน[ที่นี่](https://forum.groupdocs.com/c/annotation/10) เพื่อขอความช่วยเหลือจากชุมชนและทีมสนับสนุน GroupDocs
### ถาม: ฉันสามารถรวม GroupDocs.Annotation สำหรับ .NET เข้ากับแอปพลิเคชันบนเว็บและเดสก์ท็อปได้หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET ได้รับการออกแบบมาให้เข้ากันได้กับทั้งแอปพลิเคชันบนเว็บและเดสก์ท็อป โดยให้ความยืดหยุ่นในการรวมฟังก์ชันคำอธิบายประกอบเอกสารเข้ากับโครงการของคุณ