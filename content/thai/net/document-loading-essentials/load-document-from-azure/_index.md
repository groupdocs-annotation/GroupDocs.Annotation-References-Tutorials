---
title: โหลดเอกสารจาก Azure
linktitle: โหลดเอกสารจาก Azure
second_title: GroupDocs.Annotation .NET API
description: เรียนรู้วิธีใส่คำอธิบายประกอบเอกสารใน .NET โดยใช้ GroupDocs.Annotation บทช่วยสอนทีละขั้นตอนสำหรับการผสานรวมกับ Azure Blob Storage อย่างราบรื่น
weight: 11
url: /th/net/document-loading-essentials/load-document-from-azure/
---

# โหลดเอกสารจาก Azure

## การแนะนำ
ในขอบเขตของการจัดการเอกสารและการทำงานร่วมกัน GroupDocs.Annotation สำหรับ .NET กลายเป็นโซลูชันที่มีประสิทธิภาพ ซึ่งอำนวยความสะดวกให้กับฟังก์ชันคำอธิบายประกอบและมาร์กอัปที่ราบรื่นภายในแอปพลิเคชัน .NET บทช่วยสอนนี้จะเจาะลึกความซับซ้อนของการใช้ประโยชน์จาก GroupDocs.Annotation สำหรับ .NET เพื่อใส่คำอธิบายประกอบในเอกสาร โดยให้คำแนะนำทีละขั้นตอนตั้งแต่ข้อกำหนดเบื้องต้นไปจนถึงการใช้งานขั้นสูง
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึก GroupDocs.Annotation สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. การติดตั้ง .NET Framework: GroupDocs.Annotation สำหรับ .NET จำเป็นต้องมีสภาพแวดล้อมรันไทม์ .NET ที่เข้ากันได้ ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework บนระบบของคุณ
2. การเข้าถึงไลบรารี GroupDocs.Annotation: เข้าถึงไลบรารี GroupDocs.Annotation สำหรับ .NET โดยการดาวน์โหลดจากเว็บไซต์หรือผ่านตัวจัดการแพ็คเกจเช่น NuGet
3. เอกสารที่จะใส่คำอธิบายประกอบ: เตรียมเอกสาร (เช่น PDF) ที่คุณต้องการใส่คำอธิบายประกอบ ตรวจสอบให้แน่ใจว่าเอกสารสามารถเข้าถึงได้ทั้งภายในเครื่องหรือผ่านบริการจัดเก็บข้อมูลบนคลาวด์ เช่น Azure Blob Storage

## นำเข้าเนมสเปซ
หากต้องการเริ่มใส่คำอธิบายประกอบในเอกสารโดยใช้ GroupDocs.Annotation สำหรับ .NET ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ ขั้นตอนนี้ช่วยให้แน่ใจว่าคุณสามารถเข้าถึงคลาสและฟังก์ชันที่จำเป็นได้
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## โหลดเอกสารจาก Azure
หากต้องการใส่คำอธิบายประกอบเอกสารที่เก็บไว้ใน Azure Blob Storage ให้ทำตามขั้นตอนเหล่านี้:
### ขั้นตอนที่ 1: ตั้งค่าเส้นทางเอาต์พุต
กำหนดเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### ขั้นตอนที่ 2: ดาวน์โหลดเอกสาร
 ดึงเอกสารจาก Azure Blob Storage โดยเรียกใช้ไฟล์`DownloadFile` วิธี.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // ลอจิกคำอธิบายประกอบ
    annotator.Save(outputPath);
}
```
## ดาวน์โหลดไฟล์จาก Azure Blob Storage
 หากต้องการดาวน์โหลดเอกสารจาก Azure Blob Storage ให้ใช้งาน`DownloadFile` วิธี.
### ขั้นตอนที่ 1: ดึง Blob
เข้าถึงคอนเทนเนอร์ Azure Blob Storage และดึงข้อมูล Blob ที่ต้องการ
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### ขั้นตอนที่ 2: ดาวน์โหลดเนื้อหา Blob
ดาวน์โหลดเนื้อหา Blob ลงในสตรีมหน่วยความจำ
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## รับคอนเทนเนอร์เก็บข้อมูล Azure Blob
 หากต้องการโต้ตอบกับ Azure Blob Storage ให้ใช้งาน`GetContainer` วิธี.
### ขั้นตอนที่ 1: เริ่มต้นข้อมูลรับรองการจัดเก็บข้อมูล
ระบุข้อมูลรับรองบัญชีและข้อมูลปลายทางที่จำเป็น
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### ขั้นตอนที่ 2: สร้างไคลเอนต์ Blob
สร้างไคลเอ็นต์เพื่อโต้ตอบกับ Azure Blob Storage
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### ขั้นตอนที่ 3: ดึงข้อมูลอ้างอิงคอนเทนเนอร์
รับการอ้างอิงถึงคอนเทนเนอร์ที่ระบุ
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### ขั้นตอนที่ 4: สร้างคอนเทนเนอร์หากไม่มีอยู่
ตรวจสอบให้แน่ใจว่ามีคอนเทนเนอร์อยู่ และสร้างมันขึ้นมาหากไม่มี
```csharp
container.CreateIfNotExists();
```

## บทสรุป
GroupDocs.Annotation สำหรับ .NET ช่วยให้นักพัฒนามีความสามารถในการใส่คำอธิบายประกอบเอกสารที่มีประสิทธิภาพ ซึ่งผสานรวมเข้ากับแอปพลิเคชัน .NET ได้อย่างราบรื่น ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถใช้ประโยชน์จากฟังก์ชันของ GroupDocs.Annotation ได้อย่างมีประสิทธิภาพเพื่อใส่คำอธิบายประกอบเอกสารที่จัดเก็บไว้ใน Azure Blob Storage
#### คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Annotation รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, PPTX และอื่นๆ
### คำอธิบายประกอบสามารถปรับแต่งตามความต้องการเฉพาะได้หรือไม่
ใช่ GroupDocs.Annotation นำเสนอตัวเลือกการปรับแต่งที่ครอบคลุมสำหรับคำอธิบายประกอบ ช่วยให้ผู้ใช้สามารถปรับเปลี่ยนรูปลักษณ์ พฤติกรรม และข้อมูลเมตาได้
### GroupDocs.Annotation เหมาะสำหรับการใส่คำอธิบายประกอบเอกสารร่วมกันหรือไม่
อย่างแน่นอน! GroupDocs.Annotation อำนวยความสะดวกในการใส่คำอธิบายประกอบเอกสารร่วมกันโดยทำให้ผู้ใช้หลายคนสามารถเพิ่ม แก้ไข และตรวจทานคำอธิบายประกอบได้พร้อมๆ กัน
### GroupDocs.Annotation มีความเข้ากันได้ข้ามแพลตฟอร์มหรือไม่
ใช่ GroupDocs.Annotation ได้รับการออกแบบมาให้ทำงานได้อย่างราบรื่นบนแพลตฟอร์มต่างๆ รวมถึง Windows, Linux และ macOS
### มีการสนับสนุนด้านเทคนิคสำหรับผู้ใช้ GroupDocs.Annotation หรือไม่
ใช่ GroupDocs ให้การสนับสนุนด้านเทคนิคอย่างครอบคลุมผ่านทางฟอรัมและช่องทางการสนับสนุนเฉพาะ