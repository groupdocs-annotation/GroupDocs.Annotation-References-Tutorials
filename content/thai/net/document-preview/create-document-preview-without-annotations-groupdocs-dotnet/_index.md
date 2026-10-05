---
categories:
- Document Processing
date: '2026-10-05'
description: เรียนรู้วิธีซ่อน annotations ขณะสร้างตัวอย่างเอกสารที่สะอาดใน C# ด้วย
  GroupDocs.Annotation .NET. คู่มือขั้นตอนโดยละเอียดพร้อมตัวอย่างโค้ด เคล็ดลับประสิทธิภาพ
  และการแก้ไขปัญหา
keywords:
- how to hide annotations
- preview document without annotations
- remove annotations from preview
- clean document preview .NET
- generate document preview without annotations
lastmod: '2026-10-05'
linktitle: ตัวอย่างเอกสารโดยไม่มี Annotations
og_description: เรียนรู้วิธีซ่อน annotations ขณะสร้างตัวอย่างเอกสารที่สะอาดใน C#.
  คู่มือนี้ครอบคลุมการตั้งค่า โค้ด เคล็ดลับประสิทธิภาพ และการแก้ไขปัญหา
og_image_alt: Guide showing how to generate document preview without annotations using
  GroupDocs.Annotation for .NET
og_title: วิธีซ่อน annotations เมื่อสร้างตัวอย่างเอกสารใน C#
schemas:
- author: GroupDocs
  dateModified: '2026-10-05'
  description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  headline: How to hide annotations when generating document preview in C#
  type: TechArticle
- description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  name: How to hide annotations when generating document preview in C#
  steps:
  - name: initialize your annotator (the foundation)
    text: The `Annotator` class loads a document and provides methods for rendering
      and annotation manipulation. csharp using (Annotator annotator = new Annotator("path/to/your/document"))
      { // All your preview generation happens within this scope }
  - name: configure your preview options (this is where the magic happens)
    text: The `PreviewOptions` class defines rendering parameters such as format,
      resolution, and whether annotations are included. csharp // Define how each
      page should be handled during preview generation PreviewOptions previewOptions
      = new PreviewOptions(pageNumber => { var pagePath = $"output_directory\\r
  - name: generate the preview (the payoff)
    text: The `GeneratePreview` method processes the document according to the supplied
      options and returns file paths for the created images. csharp annotator.Document.GeneratePreview(previewOptions);
  type: HowTo
- questions:
  - answer: Absolutely! GroupDocs.Annotation supports over 50 formats—including PDF,
      PPTX, XLSX, and common image types. See the [documentation](https://docs.groupdocs.com/annotation/net/)
      for the full list.
    question: Can I preview documents other than DOCX files?
  - answer: Initialise the `Annotator` with a `LoadOptions` object that includes the
      password. The `LoadOptions` class lets you specify the document password and
      other loading parameters.
    question: How do I handle password‑protected documents?
  - answer: Yes. The same code works in ASP.NET, but store generated images in a temporary
      folder and clean them up after the response to avoid disk bloat.
    question: Can I generate previews in a web application?
  - answer: PNG offers the highest quality, JPEG loads faster, and WebP provides the
      best compression if your target browsers support it. PNG is the safest default.
    question: What’s the best output format for web display?
  - answer: Process pages in batches of 5‑10, monitor memory usage, and optionally
      show a progress bar to improve the user experience.
    question: How do I handle very large documents efficiently?
  type: FAQPage
tags:
- groupdocs
- document-preview
- annotations
- dotnet
- csharp
title: วิธีซ่อน annotations เมื่อสร้างตัวอย่างเอกสารใน C#
type: docs
url: /th/net/document-preview/create-document-preview-without-annotations-groupdocs-dotnet/
weight: 1
---

# วิธีซ่อนคำอธิบายเมื่อสร้างตัวอย่างเอกสารใน C#

หากคุณต้องการแชร์ตัวอย่างเอกสารแต่ต้องการ **ซ่อนคำอธิบาย** คุณอยู่ในสถานที่ที่ถูกต้อง บทแนะนำนี้จะแสดงวิธีสร้างตัวอย่างที่สะอาด ปราศจากคำอธิบายใน C# ด้วย GroupDocs.Annotation สำหรับ .NET ครอบคลุมทุกอย่างตั้งแต่การติดตั้งจนถึงการปรับประสิทธิภาพ

## คำตอบสั้น
- **คลาสหลักที่สร้างตัวอย่างคืออะไร?** The `Annotator` class.
- **ตัวเลือกใดที่ปิดการทำงานของคำอธิบาย?** Set `RenderAnnotations = false` in `PreviewOptions`.
- **เวอร์ชัน .NET ขั้นต่ำคืออะไร?** .NET 6 is recommended; .NET Core 3.1 also works.
- **ฉันสามารถดูตัวอย่าง PDF และไฟล์ Word ได้หรือไม่?** Yes – over 50 formats are supported.
- **ฉันต้องการใบอนุญาตสำหรับการทดสอบหรือไม่?** A temporary license is available for free trials.

## วิธีซ่อนคำอธิบายคืออะไร?
*วิธีซ่อนคำอธิบาย* คือกระบวนการสร้างภาพตัวอย่างเอกสารโดยการกดทับความคิดเห็น การไฮไลท์ หรือการทำเครื่องหมายใด ๆ ที่มีในไฟล์ต้นฉบับ เทคนิคนี้ทำให้ผลลัพธ์ภาพมีเฉพาะเนื้อหาต้นฉบับเท่านั้น ทำให้เหมาะสำหรับการเผยแพร่สาธารณะ การนำเสนอให้ลูกค้า หรือสถานการณ์ใด ๆ ที่ต้องการซ่อนบันทึกภายใน

## ทำไมคุณต้องการตัวอย่างเอกสารที่สะอาด (และวิธีการได้มา)
เมื่อคุณแชร์ตัวอย่างให้กับลูกค้า พันธมิตร หรือสาธารณะ ความคิดเห็นภายในอาจดูไม่เป็นมืออาชีพหรือแม้กระทั่งเปิดเผยกลยุทธ์ที่เป็นความลับ ตัวอย่างที่สะอาดช่วยให้โฟกัสอยู่ที่เนื้อหาและปกป้องกระบวนการทำงานของคุณ GroupDocs.Annotation ให้คุณสลับการแสดงคำอธิบายได้ จึงสามารถสร้างทั้งเวอร์ชันที่มีคำอธิบายและเวอร์ชันที่สะอาดจากไฟล์ต้นฉบับเดียวกัน

## สิ่งที่คุณต้องเตรียมก่อนเริ่ม

### สิ่งที่ต้องเตรียมล่วงหน้า?
เพื่อเริ่มต้นคุณต้องมีส่วนประกอบต่อไปนี้ติดตั้งบนเครื่องพัฒนา การมีสิ่งเหล่านี้พร้อมจะทำให้โค้ดทำงานโดยไม่มีข้อผิดพลาดระหว่างรันและคุณสามารถทดสอบกระบวนการสร้างตัวอย่างทั้งหมดได้ในเครื่อง

- GroupDocs.Annotation for .NET 25.4.0 หรือใหม่กว่า (รุ่นล่าสุดเพิ่มการสร้างตัวอย่างที่ปรับให้ใช้หน่วยความจำน้อยลง).
- Visual Studio 2022 หรือ IDE ที่รองรับ .NET ใดก็ได้.
- ใบอนุญาต GroupDocs ที่ถูกต้อง (ใบอนุญาตชั่วคราวฟรีสำหรับการประเมิน).

## การตั้งค่าอย่างรวดเร็ว: นำ GroupDocs.Annotation เข้าสู่โครงการของคุณ

### ตัวเลือก 1: คอนโซล NuGet Package Manager
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### ตัวเลือก 2: .NET CLI (ความชอบส่วนตัวของฉัน)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**เคล็ดลับ:** รักษาเวอร์ชันของแพ็กเกจให้สอดคล้องกันในทุกสมาชิกของทีมเพื่อหลีกเลี่ยงความแตกต่างในการแสดงผลที่ละเอียดอ่อน.

ตรวจสอบการติดตั้งด้วยการตรวจสอบความถูกต้องสั้น ๆ:
```csharp
using System.IO;
using GroupDocs.Annotation;

// This should compile without errors
using (Annotator annotator = new Annotator("path/to/document"))
{
    // You're good to go!
}
```

## คุณจะสร้างตัวอย่างโดยไม่มีคำอธิบายได้อย่างไร?
โหลดเอกสารด้วย `Annotator` ตั้งค่า `PreviewOptions` และเรียก `GeneratePreview` การตั้งค่า `RenderAnnotations = false` จะบอกเอนจินให้ละเว้นทุกความคิดเห็น การไฮไลท์ และตราประทับจากภาพผลลัพธ์.

### ขั้นตอนที่ 1: เริ่มต้น annotator ของคุณ (พื้นฐาน)
The `Annotator` class loads a document and provides methods for rendering and annotation manipulation.
```csharp
```csharp
using (Annotator annotator = new Annotator("path/to/your/document"))
{
    // All your preview generation happens within this scope
}
```
```

### ขั้นตอนที่ 2: ตั้งค่า preview options ของคุณ (ที่นี่คือจุดที่เกิดความมหัศจรรย์)
The `PreviewOptions` class defines rendering parameters such as format, resolution, and whether annotations are included.
```csharp
```csharp
// Define how each page should be handled during preview generation
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = $"output_directory\\result{pageNumber}.png";
    return File.Create(pagePath);
});

// Set the output format for the preview as PNG
previewOptions.PreviewFormat = PreviewFormats.PNG;

// Specify which pages to include in the preview generation
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};

// The key setting: disable rendering of annotations
previewOptions.RenderAnnotations = false;
```
```

### ขั้นตอนที่ 3: สร้างตัวอย่าง (ผลลัพธ์ที่ได้)
The `GeneratePreview` method processes the document according to the supplied options and returns file paths for the created images.
```csharp
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
```

## ปัญหาที่พบบ่อย (และวิธีแก้ไข)

### ปัญหา 1: ข้อผิดพลาด “File not found”
**อาการ:** เกิดข้อยกเว้นเมื่อสร้าง `Annotator`.
**วิธีแก้:** ใช้เส้นทางแบบเต็มหรือยืนยันว่าเส้นทางสัมพันธ์ของคุณถูกต้อง การตรวจสอบความถูกต้องอย่างรวดเร็วมีลักษณะดังนี้:
```csharp
string fullPath = Path.GetFullPath("your-document.pdf");
using (Annotator annotator = new Annotator(fullPath))
```

### ปัญหา 2: คุณภาพตัวอย่างแย่
**อาการ:** ภาพผลลัพธ์ดูเบลอหรือเป็นพิกเซล.
**วิธีแก้:** เพิ่มค่าการตั้งค่า DPI ใน `PreviewOptions` เพื่อปรับปรุงความคมชัด:
```csharp
previewOptions.Width = 1920;  // Higher resolution
previewOptions.Height = 1080;
```

### ปัญหา 3: ปัญหาหน่วยความจำกับเอกสารขนาดใหญ่
**อาการ:** `OutOfMemoryException` หรือการประมวลผลที่ช้าอย่างเห็นได้ชัด.
**วิธีแก้:** ประมวลผลหน้าเป็นชุดแทนการโหลดไฟล์ทั้งหมดพร้อมกัน:
```csharp
// Process 5 pages at a time instead of all at once
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5};
```

## กรณีการใช้งานจริง (ที่นี่สำคัญจริง ๆ)

### การแชร์เอกสารทางกฎหมาย
บริษัทกฎหมายสามารถแจกจ่ายตัวอย่างสัญญาที่ซ่อนบันทึกการเจรจาภายใน ทำให้การสื่อสารกับลูกค้าเป็นมืออาชีพ.

### การตีพิมพ์ทางวิชาการ
นักวิจัยสามารถแชร์ร่างต้นฉบับที่สะอาดหลังการตรวจสอบโดยผู้ตรวจสอบ, ลบความคิดเห็นของผู้ตรวจสอบก่อนส่งวารสาร.

### รายงานธุรกิจ
ผู้มีส่วนได้ส่วนเสียจะได้รับรายงานที่เรียบหรูโดยไม่มีโน้ต “ตรวจสอบตัวเลขนี้” หรือ “อัปเดตก่อนการประชุมคณะกรรมการ” ซึ่งอาจทำให้ความเชื่อมั่นลดลง.

### การเก็บเอกสาร
ทีมปฏิบัติตามกฎระเบียบเก็บสำเนาที่ไม่มีคำอธิบายเพื่อให้เป็นไปตามมาตรฐานกฎระเบียบพร้อมกับรักษาเวอร์ชันที่มีคำอธิบายเดิมไว้สำหรับอ้างอิงภายใน.

## แนวทางปฏิบัติที่ดีที่สุดสำหรับประสิทธิภาพ

### คุณควรจัดการหน่วยความจำสำหรับไฟล์ขนาดใหญ่อย่างไร?
ประมวลผลหน้าเป็นชุดเล็ก ๆ และทำลาย `Annotator` อย่างทันท่วงที วิธีนี้ลดการใช้หน่วยความจำสูงสุดได้ถึง 60 % สำหรับเอกสารที่มีมากกว่า 200 หน้า.
```csharp
// Good: Dispose properly
using (Annotator annotator = new Annotator(documentPath))
{
    // Generate preview
} // Automatically disposed here

// Avoid: Manual disposal (easy to forget)
Annotator annotator = new Annotator(documentPath);
// ... use annotator
annotator.Dispose(); // Easy to forget or skip due to exceptions
```

### คุณจะเร่งการประมวลผลเป็นชุดได้อย่างไร?
แบ่งเอกสาร 100 หน้าเป็นกลุ่มละ 10 หน้า สร้างแต่ละกลุ่มต่อเนื่องกัน และเขียนผลลัพธ์ไปยังโฟลเดอร์ชั่วคราว เทคนิคนี้ลดเวลาการประมวลผลทั้งหมดประมาณ 30 % บนฮาร์ดแวร์เซิร์ฟเวอร์ทั่วไป.
```csharp
// Process in batches of 10 pages
for (int startPage = 1; startPage <= totalPages; startPage += 10)
{
    int endPage = Math.Min(startPage + 9, totalPages);
    var pageRange = Enumerable.Range(startPage, endPage - startPage + 1).ToArray();
    
    previewOptions.PageNumbers = pageRange;
    annotator.Document.GeneratePreview(previewOptions);
}
```

### คุณเลือกรูปแบบผลลัพธ์ที่เหมาะสมอย่างไร?
- **PNG:** ความคมชัดภาพที่ดีที่สุด; เหมาะสำหรับแผนผังละเอียด.  
- **JPEG:** ขนาดไฟล์เล็กกว่า; เหมาะสำหรับเอกสารที่มีข้อความมากที่ยอมรับการบีบอัดเล็กน้อย.  
- **WebP:** รูปแบบสมัยใหม่ที่บีบอัดได้ดี; ตรวจสอบการสนับสนุนของเบราว์เซอร์ก่อนนำไปใช้.

## ตัวเลือกการกำหนดค่าขั้นสูง

### คุณสามารถปรับแต่งการตั้งชื่อไฟล์ได้อย่างไร?
Lambda ของ `PreviewOptions` ให้คุณแทรกหมายเลขหน้า, เวลาประทับ, หรือรหัสกำหนดเองลงในชื่อไฟล์แต่ละไฟล์.
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    string timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
    var pagePath = $"previews\\{timestamp}_page_{pageNumber:D3}.png";
    return File.Create(pagePath);
});
```

### คุณควบคุมคุณภาพภาพได้อย่างไร?
ปรับคุณสมบัติ `Width`, `Height`, และ `Resolution` ใน `PreviewOptions`. ขนาดที่ใหญ่ขึ้นให้คุณภาพสูงขึ้นแต่ไฟล์ใหญ่ขึ้น.
```csharp
previewOptions.Width = 2400;   // Higher resolution
previewOptions.Height = 3200;  // Maintains aspect ratio
previewOptions.PreviewFormat = PreviewFormats.PNG; // Best quality
```

### คุณสามารถประมวลผลเฉพาะหน้าที่ต้องการได้อย่างไร?
ตั้งค่าคอลเลกชัน `PageNumbers` ให้เป็นหน้าที่ต้องการอย่างแม่นยำ ซึ่งจะลด I/O และเร่งการสร้างสำหรับเอกสารหลายร้อยหน้า.
```csharp
// Only process odd pages (useful for double-sided documents)
var oddPages = Enumerable.Range(1, totalPages)
                        .Where(p => p % 2 == 1)
                        .ToArray();
previewOptions.PageNumbers = oddPages;
```

## คู่มือการแก้ไขปัญหา

### ทำไมการสร้างตัวอย่างจึงล้มเหลวโดยไม่มีข้อความแจ้ง?
สาเหตุทั่วไปรวมถึง:
1. ไดเรกทอรีผลลัพธ์หายไปหรือไม่มีสิทธิ์เขียน.
2. เอกสารต้นฉบับที่มีการป้องกันด้วยรหัสผ่าน.
3. รูปแบบไฟล์ที่ไม่รองรับ.
4. หน่วยความจำของระบบไม่เพียงพอ.

### ทำไมคำอธิบายยังคงแสดงอยู่?
ตรวจสอบให้แน่ใจว่าได้ตั้งค่า `RenderAnnotations = false` บนอินสแตนซ์ `PreviewOptions` ก่อนเรียก `GeneratePreview`. คุณสมบัติ `RenderAnnotations` ควบคุมว่าชั้นคำอธิบายจะถูกวาดหรือไม่ระหว่างการเรนเดอร์ตัวอย่าง.
```csharp
previewOptions.RenderAnnotations = false;  // Must be explicitly false
previewOptions.RenderComments = false;     // Also disable comments if needed
```

### ทำไมประสิทธิภาพจึงช้า?
- ลดความละเอียดในระหว่างการทดสอบ.
- ประมวลผลน้อยหน้าต่อชุด.
- ตรวจสอบว่าคุณใช้เวอร์ชันล่าสุดของ GroupDocs.Annotation (25.4.0 หรือใหม่กว่า) ซึ่งมีการปรับปรุงประสิทธิภาพ.

## เมื่อไม่ควรใช้วิธีนี้

- **การพรีวิวแบบเรียลไทม์:** สำหรับพรีวิวทันทีบน‑เดี่ยว การเรนเดอร์ฝั่งไคลเอนท์อาจเร็วกว่า.
- **เอกสารเชิงโต้ตอบ:** ฟอร์มหรือสคริปต์ฝังอาจสูญเสียการทำงานเมื่อเรนเดอร์เป็นภาพคงที่.
- **กราฟิกขยายได้:** หากต้องการผลลัพธ์แบบเวกเตอร์ (เช่น SVG) ให้พิจารณาสร้างหน้ PDF แทนภาพแรสเตอร์.

## สรุป

การสร้างตัวอย่างเอกสารที่สะอาดโดยไม่มีคำอธิบายทำได้ง่ายด้วย GroupDocs.Annotation สำหรับ .NET จำไว้ว่า:
1. ทำลาย `Annotator` อย่างเหมาะสม.
2. ตั้งค่า `RenderAnnotations = false` ใน `PreviewOptions`.
3. ประมวลผลเป็นชุดไฟล์ขนาดใหญ่เพื่อรักษาการใช้หน่วยความจำให้ต่ำ.
4. ทดสอบด้วยเอกสารจริงเพื่อปรับ DPI และการเลือกรูปแบบให้เหมาะ.

เริ่มต้นด้วยไฟล์ทดสอบง่าย ๆ ทดลองกับตัวเลือกข้างต้น และคุณจะมีตัวอย่างระดับมืออาชีพ ปราศจากคำอธิบาย พร้อมใช้งานสำหรับผู้ชมทุกประเภท.

## คำถามที่พบบ่อย

**Q: ฉันสามารถพรีวิวเอกสารที่ไม่ใช่ไฟล์ DOCX ได้หรือไม่?**  
A: แน่นอน! GroupDocs.Annotation รองรับกว่า 50 รูปแบบรวมถึง PDF, PPTX, XLSX และประเภทภาพทั่วไป ดูที่ [documentation](https://docs.groupdocs.com/annotation/net/) สำหรับรายการทั้งหมด.

**Q: ฉันจัดการกับเอกสารที่ป้องกันด้วยรหัสผ่านอย่างไร?**  
A: เริ่มต้น `Annotator` ด้วยอ็อบเจ็กต์ `LoadOptions` ที่รวมรหัสผ่าน `LoadOptions` ให้คุณระบุรหัสผ่านของเอกสารและพารามิเตอร์การโหลดอื่น ๆ.
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-doc.pdf", loadOptions))
```

**Q: ฉันสามารถสร้างพรีวิวในเว็บแอปพลิเคชันได้หรือไม่?**  
A: ได้. โค้ดเดียวกันทำงานใน ASP.NET แต่ให้เก็บภาพที่สร้างไว้ในโฟลเดอร์ชั่วคราวและทำความสะอาดหลังการตอบสนองเพื่อหลีกเลี่ยงการใช้ดิสก์มากเกินไป.

**Q: รูปแบบผลลัพธ์ที่ดีที่สุดสำหรับการแสดงบนเว็บคืออะไร?**  
A: PNG ให้คุณภาพสูงสุด, JPEG โหลดเร็วกว่า, และ WebP มีการบีบอัดที่ดีที่สุดหากเบราว์เซอร์เป้าหมายของคุณรองรับ PNG เป็นค่าเริ่มต้นที่ปลอดภัยที่สุด.

**Q: ฉันจัดการกับเอกสารขนาดใหญ่อย่างมีประสิทธิภาพอย่างไร?**  
A: ประมวลผลหน้าเป็นชุด 5‑10 หน้า, ตรวจสอบการใช้หน่วยความจำ, และอาจแสดงแถบความคืบหน้าเพื่อปรับปรุงประสบการณ์ผู้ใช้.

**Q: ฉันสามารถปรับแต่งคุณภาพภาพผลลัพธ์ได้หรือไม่?**  
A: ได้—ปรับ `Width`, `Height`, และ `Resolution` ใน `PreviewOptions`. ค่าที่ใหญ่ขึ้นเพิ่มคุณภาพแต่ไฟล์ก็ใหญ่ขึ้น.

**Q: ถ้าฉันต้องการทั้งเวอร์ชันที่มีคำอธิบายและเวอร์ชันที่สะอาดควรทำอย่างไร?**  
A: รันพรีวิวสองครั้ง—ครั้งหนึ่งกับ `RenderAnnotations = true` และอีกครั้งกับ `false`. เก็บแต่ละชุดในไดเรกทอรีแยกเพื่อการดึงข้อมูลที่ง่าย.

## แหล่งข้อมูล

- [เอกสาร GroupDocs.Annotation .NET](https://docs.groupdocs.com/annotation/net/)  
- [อ้างอิง API GroupDocs Annotation](https://reference.groupdocs.com/annotation/net/)  
- [การปล่อย GroupDocs สำหรับ .NET](https://releases.groupdocs.com/annotation/net/)  
- [ซื้อใบอนุญาต GroupDocs](https://purchase.groupdocs.com/buy)  
- [การทดลองใช้ GroupDocs ฟรี](https://releases.groupdocs.com/annotation/net/)  
- [ขอใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)  
- [ฟอรั่ม GroupDocs](https://forum.groupdocs.com/c/annotation/)  

**อัปเดตล่าสุด:** 2026-10-05  
**ทดสอบด้วย:** GroupDocs.Annotation 25.4.0 for .NET  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [วิธีลบคำอธิบาย PDF C# – คู่มือ GroupDocs.Annotation](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)
- [สร้างตัวอย่างเอกสารโดยไม่มีคอมเมนต์ใน .NET](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [โหลดฟอนต์แบบกำหนดเอง .NET - คู่มือการบูรณาการ GroupDocs.Annotation](/annotation/net/advanced-usage/loading-custom-fonts/)