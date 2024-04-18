---
title: โหลดเอกสารจาก FTP
linktitle: โหลดเอกสารจาก FTP
second_title: GroupDocs.Annotation .NET API
description: ปรับปรุงแอปพลิเคชัน .NET ของคุณด้วย GroupDocs.Annotation เพื่อคำอธิบายประกอบเอกสารที่ราบรื่น รวมการสอนทีละขั้นตอน
type: docs
weight: 12
url: /th/net/document-loading-essentials/load-document-from-ftp/
---
## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นไลบรารีอเนกประสงค์ที่ออกแบบมาเพื่ออำนวยความสะดวกในความสามารถในการใส่คำอธิบายประกอบเอกสารภายในแอปพลิเคชัน .NET ได้อย่างง่ายดาย ไม่ว่าคุณจะจัดการกับ PDF, เอกสาร Microsoft Office, รูปภาพ หรือรูปแบบอื่นๆ ไลบรารีนี้มอบโซลูชันแบบครบวงจรสำหรับการเพิ่มคำอธิบายประกอบ เช่น ความคิดเห็น ไฮไลต์ และรูปร่าง เพื่อปรับปรุงการทำงานร่วมกันและการจัดการเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. ความรู้เกี่ยวกับ C#: ความเชี่ยวชาญในภาษาการเขียนโปรแกรม C# เป็นสิ่งสำคัญในการทำความเข้าใจและนำตัวอย่างโค้ดที่ให้ไว้ในบทช่วยสอนนี้ไปใช้
2.  GroupDocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าได้ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/annotation/net/)- ทำตามคำแนะนำในการติดตั้งเพื่อรวมไลบรารีเข้ากับโครงการ .NET ของคุณให้สำเร็จ
## นำเข้าเนมสเปซ
ในการใช้ GroupDocs.Annotation สำหรับฟังก์ชัน .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ ทำตามขั้นตอนเหล่านี้:

ภายในโปรเจ็กต์ C# ของคุณ ให้รวมเนมสเปซที่จำเป็นไว้ที่จุดเริ่มต้นของไฟล์โค้ดของคุณ:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

ตอนนี้ เรามาเจาะลึกกระบวนการโหลดเอกสารจาก FTP และเพิ่มคำอธิบายประกอบโดยใช้ GroupDocs.Annotation สำหรับ .NET กัน
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
ระบุเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: โหลดเอกสารจาก FTP
ดึงเอกสารจากเซิร์ฟเวอร์ FTP โดยใช้เส้นทางไฟล์ที่ให้ไว้
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // รหัสคำอธิบายประกอบจะถูกเพิ่มที่นี่
}
```
## ขั้นตอนที่ 3: เพิ่มคำอธิบายประกอบ
กำหนดและเพิ่มคำอธิบายประกอบที่ต้องการ เช่น คำอธิบายประกอบพื้นที่ ลงในเอกสาร
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## ขั้นตอนที่ 4: บันทึกเอกสารคำอธิบายประกอบ
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## ขั้นตอนที่ 5: ดึงไฟล์จาก FTP
ใช้วิธีการดึงไฟล์จากเซิร์ฟเวอร์ FTP
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## ขั้นตอนที่ 6: สร้างคำขอ FTP
สร้างคำขอ FTP เพื่อดาวน์โหลดไฟล์
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## ขั้นตอนที่ 7: รับสตรีมไฟล์
ดึงสตรีมไฟล์จากการตอบกลับ FTP
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## บทสรุป
โดยสรุป GroupDocs.Annotation สำหรับ .NET ช่วยให้นักพัฒนาสามารถรวมฟังก์ชันคำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น ด้วยการทำตามคำแนะนำทีละขั้นตอนที่สรุปไว้ในบทช่วยสอนนี้ คุณจะสามารถโหลดเอกสารจาก FTP และเพิ่มคำอธิบายประกอบได้อย่างง่ายดาย เพิ่มประสิทธิภาพการทำงานร่วมกันและการจัดการเอกสารภายในแอปพลิเคชันของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, เอกสาร Microsoft Office, รูปภาพ และอื่นๆ
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่เพิ่มโดยใช้ GroupDocs.Annotation สำหรับ .NET ได้หรือไม่
แน่นอนว่า GroupDocs.Annotation สำหรับ .NET มีตัวเลือกการปรับแต่งมากมายสำหรับลักษณะคำอธิบายประกอบ รวมถึงสี สไตล์ และรูปร่าง
### GroupDocs.Annotation สำหรับ .NET ให้การสนับสนุนบริการจัดเก็บข้อมูลบนคลาวด์หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET ทำงานร่วมกับบริการจัดเก็บข้อมูลบนคลาวด์ยอดนิยมได้อย่างราบรื่น ช่วยให้คุณสามารถโหลดและบันทึกเอกสารจากบริการต่างๆ เช่น Dropbox, Google Drive และ OneDrive
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
 ใช่ คุณสามารถสำรวจคุณลักษณะต่างๆ ของ GroupDocs.Annotation สำหรับ .NET ได้ด้วยการดาวน์โหลดเวอร์ชันทดลองใช้ฟรีจาก[หน้าปล่อย](https://releases.groupdocs.com/).
### ฉันจะรับความช่วยเหลือด้านเทคนิคหรือการสนับสนุนสำหรับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
 สำหรับความช่วยเหลือทางเทคนิค การแก้ไขปัญหา หรือการสอบถามข้อมูลทั่วไป คุณสามารถไปที่ GroupDocs.Annotation สำหรับ .NET[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/annotation/10).