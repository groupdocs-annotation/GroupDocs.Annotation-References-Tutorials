---
"description": "ปรับปรุงแอปพลิเคชัน .NET ของคุณด้วย GroupDocs.Annotation เพื่อการใส่คำอธิบายประกอบเอกสารอย่างราบรื่น มีบทช่วยสอนแบบทีละขั้นตอนรวมอยู่ด้วย"
"linktitle": "โหลดเอกสารจาก FTP"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "โหลดเอกสารจาก FTP"
"url": "/th/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# โหลดเอกสารจาก FTP

## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นไลบรารีที่มีความยืดหยุ่นซึ่งออกแบบมาเพื่ออำนวยความสะดวกให้กับความสามารถในการใส่คำอธิบายประกอบเอกสารภายในแอปพลิเคชัน .NET ได้อย่างง่ายดาย ไม่ว่าคุณจะจัดการกับ PDF เอกสาร Microsoft Office รูปภาพ หรือรูปแบบอื่น ๆ ไลบรารีนี้มอบโซลูชันแบบครบวงจรสำหรับการเพิ่มคำอธิบายประกอบ เช่น ความคิดเห็น ไฮไลต์ และรูปร่าง เพื่อปรับปรุงการทำงานร่วมกันและการจัดการเอกสาร
## ข้อกำหนดเบื้องต้น
ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. ความรู้เกี่ยวกับ C#: ความเชี่ยวชาญในภาษาการเขียนโปรแกรม C# ถือเป็นสิ่งสำคัญสำหรับการทำความเข้าใจและการนำตัวอย่างโค้ดที่ให้ไว้ในบทช่วยสอนนี้ไปใช้งาน
2. GroupDocs.Annotation สำหรับ .NET: อย่าลืมดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จาก [ลิงค์ดาวน์โหลด](https://releases.groupdocs.com/annotation/net/)ปฏิบัติตามคำแนะนำในการติดตั้งเพื่อรวมไลบรารีเข้ากับโครงการ .NET ของคุณสำเร็จ
## นำเข้าเนมสเปซ
ในการใช้ GroupDocs.Annotation สำหรับฟังก์ชันการทำงานของ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ ทำตามขั้นตอนเหล่านี้:

ภายในโครงการ C# ของคุณ ให้รวมเนมสเปซที่จำเป็นไว้ที่จุดเริ่มต้นของไฟล์โค้ดของคุณ:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

ตอนนี้เรามาดูกระบวนการโหลดเอกสารจาก FTP และเพิ่มคำอธิบายประกอบโดยใช้ GroupDocs.Annotation สำหรับ .NET กัน
## ขั้นตอนที่ 1: กำหนดเส้นทางเอาต์พุต
ระบุเส้นทางเอาต์พุตที่จะบันทึกเอกสารที่มีคำอธิบายประกอบ
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ขั้นตอนที่ 2: โหลดเอกสารจาก FTP
ดึงเอกสารจากเซิร์ฟเวอร์ FTP โดยใช้เส้นทางไฟล์ที่ให้มา
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // จะเพิ่มโค้ดคำอธิบายไว้ที่นี่
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
## ขั้นตอนที่ 4: บันทึกเอกสารที่มีคำอธิบายประกอบ
บันทึกเอกสารที่มีคำอธิบายประกอบไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## ขั้นตอนที่ 5: ดึงไฟล์จาก FTP
นำวิธีการดึงไฟล์จากเซิร์ฟเวอร์ FTP มาใช้
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
## ขั้นตอนที่ 7: รับ File Stream
ดึงข้อมูลสตรีมไฟล์จากการตอบสนองของ FTP
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
โดยสรุป GroupDocs.Annotation สำหรับ .NET ช่วยให้นักพัฒนาสามารถผสานรวมฟังก์ชันการใส่คำอธิบายประกอบเอกสารเข้ากับแอปพลิเคชัน .NET ได้อย่างราบรื่น โดยปฏิบัติตามคำแนะนำทีละขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถโหลดเอกสารจาก FTP และเพิ่มคำอธิบายประกอบได้อย่างง่ายดาย ช่วยเพิ่มประสิทธิภาพการทำงานร่วมกันและการจัดการเอกสารภายในแอปพลิเคชันของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Annotation สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET รองรับรูปแบบเอกสารต่างๆ มากมาย รวมถึง PDF, เอกสาร Microsoft Office, รูปภาพ และอื่นๆ อีกมากมาย
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของคำอธิบายประกอบที่เพิ่มโดยใช้ GroupDocs.Annotation สำหรับ .NET ได้หรือไม่
แน่นอนว่า GroupDocs.Annotation สำหรับ .NET นำเสนอตัวเลือกการปรับแต่งมากมายสำหรับลักษณะที่ปรากฏของคำอธิบายประกอบ รวมถึงสี สไตล์และรูปทรง
### GroupDocs.Annotation สำหรับ .NET รองรับบริการการจัดเก็บข้อมูลบนคลาวด์หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET สามารถรวมเข้ากับบริการจัดเก็บข้อมูลบนคลาวด์ยอดนิยมได้อย่างราบรื่น ช่วยให้คุณโหลดและบันทึกเอกสารจากบริการต่างๆ เช่น Dropbox, Google Drive และ OneDrive ได้
### มีเวอร์ชันทดลองใช้สำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
ใช่ คุณสามารถสำรวจคุณสมบัติของ GroupDocs.Annotation สำหรับ .NET ได้โดยดาวน์โหลดเวอร์ชันทดลองใช้งานฟรีจาก [หน้าวางจำหน่าย](https://releases-groupdocs.com/).
### ฉันจะได้รับความช่วยเหลือด้านเทคนิคหรือการสนับสนุนสำหรับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
สำหรับความช่วยเหลือด้านเทคนิค การแก้ไขปัญหา หรือการสอบถามข้อมูลทั่วไป คุณสามารถไปที่ GroupDocs.Annotation สำหรับ .NET [ฟอรั่มสนับสนุน](https://forum-groupdocs.com/c/annotation/10).