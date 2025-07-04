---
"description": "เรียนรู้วิธีการตั้งค่าใบอนุญาตแบบจำกัดปริมาณสำหรับ GroupDocs.Annotation .NET เพื่อใช้ทรัพยากรและความสามารถในการบันทึกคำอธิบายประกอบเอกสารในแอปพลิเคชัน .NET ของคุณ"
"linktitle": "ตั้งค่าใบอนุญาตแบบมิเตอร์"
"second_title": "API ของ GroupDocs.Annotation .NET"
"title": "ตั้งค่าใบอนุญาตแบบมิเตอร์"
"url": "/th/net/applying-licenses/set-metered-license/"
"weight": 12
---

# ตั้งค่าใบอนุญาตแบบมิเตอร์

## การแนะนำ
GroupDocs.Annotation สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถเพิ่มความสามารถในการใส่คำอธิบายประกอบเอกสารลงในแอปพลิเคชัน .NET ได้อย่างง่ายดาย ไม่ว่าคุณจะกำลังสร้างระบบจัดการเอกสาร แพลตฟอร์มการทำงานร่วมกัน หรือแอปพลิเคชันใดๆ ที่เกี่ยวข้องกับการตรวจทานและทำเครื่องหมายเอกสาร GroupDocs.Annotation สำหรับ .NET ก็มีชุดเครื่องมือที่ครอบคลุมเพื่อปรับกระบวนการให้มีประสิทธิภาพ
ในบทช่วยสอนนี้ เราจะเจาะลึกถึงกระบวนการตั้งค่าใบอนุญาตแบบคิดค่าบริการสำหรับ GroupDocs.Annotation .NET ใบอนุญาตแบบคิดค่าบริการช่วยให้คุณจ่ายเฉพาะทรัพยากรที่คุณใช้เท่านั้น ทำให้เป็นโซลูชันที่คุ้มต้นทุนสำหรับโครงการทุกขนาด เมื่อทำตามขั้นตอนที่ระบุไว้ด้านล่าง คุณจะสามารถผสานรวม GroupDocs.Annotation เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น พร้อมทั้งเพิ่มประสิทธิภาพการใช้ทรัพยากรและควบคุมงบประมาณได้
## ข้อกำหนดเบื้องต้น
ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Annotation สำหรับไลบรารี .NET: ดาวน์โหลดไลบรารีจาก [เว็บไซต์](https://releases-groupdocs.com/annotation/net/).
2. การเข้าถึงบัญชี GroupDocs: คุณจะต้องมีบัญชี GroupDocs เพื่อรับคีย์สาธารณะและคีย์ส่วนตัวที่จำเป็นสำหรับการตั้งค่าใบอนุญาตแบบมิเตอร์ หากคุณยังไม่มีบัญชี คุณสามารถสมัครทดลองใช้งานฟรีได้ [ที่นี่](https://releases-groupdocs.com/).
3. ความเข้าใจพื้นฐานเกี่ยวกับ C# และ .NET Framework: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และ .NET framework จะเป็นประโยชน์สำหรับการนำขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ไปปฏิบัติ

## นำเข้าเนมสเปซ
ในการเริ่มต้น โปรดแน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณแล้ว เนมสเปซเหล่านี้มีความจำเป็นสำหรับการโต้ตอบกับฟังก์ชัน GroupDocs.Annotation
```csharp
using System;
```
## ขั้นตอนที่ 1: รับคีย์สาธารณะและส่วนตัว
ก่อนที่จะตั้งค่าใบอนุญาตแบบคิดค่าบริการตามปริมาณการใช้งาน คุณต้องได้รับคีย์สาธารณะและคีย์ส่วนตัวจากแดชบอร์ดบัญชี GroupDocs ของคุณ
1. เข้าสู่ระบบบัญชี GroupDocs ของคุณ
2. ไปที่ส่วนการจัดการใบอนุญาต
3. คัดลอกคีย์สาธารณะและส่วนตัวของคุณที่ได้รับจาก GroupDocs
## ขั้นตอนที่ 2: ตั้งค่าใบอนุญาตแบบมิเตอร์
เมื่อคุณได้รับคีย์สาธารณะและคีย์ส่วนตัวแล้ว คุณสามารถตั้งค่าใบอนุญาตแบบมิเตอร์ในแอปพลิเคชัน .NET ของคุณได้
```csharp
string publicKey = "*****"; // แทนที่ ***** ด้วยคีย์สาธารณะของคุณ
string privateKey = "*****"; // แทนที่ ***** ด้วยคีย์ส่วนตัวของคุณ
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## บทสรุป
โดยสรุป การตั้งค่าใบอนุญาตแบบคิดค่าบริการสำหรับ GroupDocs.Annotation .NET เป็นกระบวนการตรงไปตรงมาที่ช่วยให้มั่นใจได้ว่าโครงการคำอธิบายประกอบเอกสารของคุณจะใช้ทรัพยากรได้อย่างมีประสิทธิภาพและคุ้มต้นทุน เมื่อทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้แล้ว คุณสามารถผสานรวม GroupDocs.Annotation เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น และปรับปรุงความสามารถในการทำงานร่วมกันและตรวจสอบเอกสาร
## คำถามที่พบบ่อย
### ฉันสามารถใช้ GroupDocs.Annotation สำหรับ .NET ในโครงการเชิงพาณิชย์ได้หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET สามารถใช้ได้ทั้งในโครงการเชิงพาณิชย์และไม่ใช่เชิงพาณิชย์ อย่างไรก็ตาม คุณจะต้องได้รับใบอนุญาตที่เหมาะสมตามความต้องการของโครงการของคุณ
### มีเวอร์ชันทดลองใช้สำหรับ GroupDocs.Annotation สำหรับ .NET หรือไม่
ใช่ คุณสามารถใช้ประโยชน์จากการทดลองใช้ GroupDocs.Annotation สำหรับ .NET ได้ฟรีโดยเข้าไปที่ [ลิงค์นี้](https://releases-groupdocs.com/).
### ฉันสามารถรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Annotation สำหรับ .NET ได้อย่างไร
คุณสามารถขอรับการสนับสนุนด้านเทคนิคได้โดยไปที่ฟอรัม GroupDocs [ที่นี่](https://forum-groupdocs.com/c/annotation/10).
### มีตัวเลือกใบอนุญาตชั่วคราวให้เลือกหรือไม่?
ใช่ คุณสามารถขอใบอนุญาตชั่วคราวจาก GroupDocs สำหรับการใช้งานระยะสั้นหรือเพื่อการประเมินผล เยี่ยมชม [ลิงค์นี้](https://purchase.groupdocs.com/temporary-license/) สำหรับข้อมูลเพิ่มเติม
### ฉันสามารถปรับแต่งคุณลักษณะคำอธิบายประกอบตามความต้องการของโครงการของฉันได้หรือไม่
ใช่ GroupDocs.Annotation สำหรับ .NET นำเสนอตัวเลือกการปรับแต่งมากมาย ช่วยให้คุณปรับแต่งคุณลักษณะคำอธิบายประกอบให้เหมาะกับความต้องการเฉพาะของโครงการของคุณได้