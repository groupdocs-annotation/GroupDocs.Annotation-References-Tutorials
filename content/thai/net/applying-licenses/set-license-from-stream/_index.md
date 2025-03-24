---
title: ตั้งค่าใบอนุญาตจากสตรีม
linktitle: ตั้งค่าใบอนุญาตจากสตรีม
second_title: GroupDocs.Annotation .NET API
description: ปลดล็อกศักยภาพสูงสุดของคำอธิบายประกอบเอกสารใน .NET ด้วย GroupDocs.Annotation ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการบูรณาการที่ราบรื่น
weight: 11
url: /th/net/applying-licenses/set-license-from-stream/
---
## การแนะนำ
ยินดีต้อนรับสู่คำแนะนำที่ครอบคลุมเกี่ยวกับการใช้ GroupDocs.Annotation สำหรับ .NET เพื่อเพิ่มขีดความสามารถในการใส่คำอธิบายประกอบเอกสารของคุณ ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น บทช่วยสอนนี้จะแนะนำคุณในแต่ละขั้นตอน เพื่อให้มั่นใจว่าคุณจะได้ใช้ประโยชน์จากศักยภาพสูงสุดของเครื่องมืออันทรงพลังนี้
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Annotation สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้ง GroupDocs.Annotation สำหรับ .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/annotation/net/).
2.  ใบอนุญาต: รับใบอนุญาตที่ถูกต้องสำหรับ GroupDocs.Annotation คุณสามารถซื้อได้จาก[ที่นี่](https://purchase.groupdocs.com/buy) หรือขอใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
3.  เอกสารประกอบ: ทำความคุ้นเคยกับ[เอกสารประกอบ](https://tutorials.groupdocs.com/annotation/net/) สำหรับ GroupDocs คำอธิบายประกอบ โดยให้ข้อมูลเชิงลึกโดยละเอียดเกี่ยวกับฟังก์ชันการทำงานของ API

## นำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นเพื่อเริ่มใช้ GroupDocs.Annotation ในโปรเจ็กต์ .NET ของคุณ:
```csharp
using System;
using System.IO;
```

## ขั้นตอนที่ 1: ตรวจสอบเส้นทางใบอนุญาต
ตรวจสอบให้แน่ใจว่าได้ตั้งค่าเส้นทางไฟล์ลิขสิทธิ์อย่างถูกต้องในโครงการของคุณ ควรชี้ไปยังตำแหน่งที่เก็บไฟล์ใบอนุญาตของคุณ
## ขั้นตอนที่ 2: ตั้งค่าใบอนุญาต
```csharp
if (File.Exists(Constants.LicensePath))
{
```
ในขั้นตอนนี้ รหัสจะตรวจสอบว่าไฟล์ลิขสิทธิ์อยู่ในเส้นทางที่ระบุหรือไม่
```csharp
    using (FileStream stream = File.OpenRead(Constants.LicensePath))
    {
        License license = new License();
        license.SetLicense(stream);
    }
```
 หากมีไฟล์ลิขสิทธิ์อยู่ ไฟล์นั้นจะอ่านสตรีมไฟล์และตั้งค่าใบอนุญาตโดยใช้`SetLicense` วิธี.
```csharp
    Console.WriteLine("License set successfully.");
}
else
{
```
หากไม่มีไฟล์ใบอนุญาต ระบบจะแจ้งให้ผู้ใช้ขอรับใบอนุญาตจากไซต์ GroupDocs
```csharp
    Console.WriteLine("\nWe do not ship any license with this example. " +
                      "\nVisit the GroupDocs site to obtain either a temporary or permanent license. " +
                      "\nLearn more about licensing at https://buy.groupdocs.com/faqs/licensing -
                      "\nLear how to request temporary license at https://buy.groupdocs.com/temporary-license");
}
```

## บทสรุป
โดยสรุป การเรียนรู้ GroupDocs.Annotation สำหรับ .NET อย่างเชี่ยวชาญจะช่วยเพิ่มขีดความสามารถด้านคำอธิบายประกอบเอกสารของคุณได้อย่างมาก ด้วยการทำตามคำแนะนำทีละขั้นตอนนี้ คุณจะมีความพร้อมที่จะรวมคุณลักษณะคำอธิบายประกอบที่มีประสิทธิภาพเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## คำถามที่พบบ่อย
### ฉันจำเป็นต้องซื้อใบอนุญาตเพื่อใช้ GroupDocs.Annotation สำหรับ .NET หรือไม่
ใช่ คุณต้องมีใบอนุญาตที่ถูกต้องเพื่อปลดล็อกการทำงานเต็มรูปแบบของ GroupDocs.Annotation คุณสามารถซื้อใบอนุญาตถาวรหรือขอใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมิน
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Annotation สำหรับ .NET ได้ที่ไหน
 คุณสามารถค้นหาการสนับสนุนที่ครอบคลุมและมีส่วนร่วมกับชุมชนได้ที่[GroupDocs.ฟอรัมคำอธิบายประกอบ](https://forum.groupdocs.com/c/annotation/10).
### ฉันสามารถลองใช้ GroupDocs.Annotation สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถขอใบอนุญาตทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/) เพื่อสำรวจความสามารถของ GroupDocs.Annotation สำหรับ .NET
### ฉันจะรับเอกสารล่าสุดสำหรับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
 คุณสามารถอ้างถึง[เอกสารประกอบ](https://tutorials.groupdocs.com/annotation/net/) สำหรับ GroupDocs.Annotation สำหรับ .NET เพื่อเข้าถึงการอ้างอิง API และบทช่วยสอนโดยละเอียด
### จะเกิดอะไรขึ้นหากฉันประสบปัญหาเกี่ยวกับใบอนุญาตของฉัน
หากคุณพบปัญหาใดๆ เกี่ยวกับใบอนุญาตของคุณ โปรดติดต่อทีมสนับสนุน GroupDocs เพื่อขอความช่วยเหลือ