---
"description": "حسّن مستندات PDF لديك باستخدام أزرار تفاعلية باستخدام Groupdocs.Annotation لـ .NET. اتبع دليلنا خطوة بخطوة لدمج سلس."
"linktitle": "إضافة مكون الزر إلى مستند PDF"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة مكون الزر إلى مستند PDF"
"url": "/ar/net/document-components/add-button-component-to-pdf/"
"weight": 10
---

# إضافة مكون الزر إلى مستند PDF

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة مكون زر إلى مستند PDF باستخدام Groupdocs.Annotation لـ .NET. سيضمن لك هذا الدليل التفصيلي سهولة دمج هذه الميزة في مشروعك.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1. Groupdocs.Annotation لـ .NET: تأكد من تثبيت مكتبة Groupdocs.Annotation لـ .NET. يمكنك تنزيلها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة مع تثبيت إطار عمل .NET.

## استيراد مساحات الأسماء
قبل المتابعة، قم باستيراد المساحات الأساسية اللازمة إلى مشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تهيئة مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: إضافة مكون الزر
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BorderStyle.Dashed,
        BorderWidth = 0,
        BorderColor = 0,
        AlternateName = "Name",
        PartialName = "Patial Name",
        NormalCaption = "Caption",
        ButtonColor = 16761035,
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
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
## الخطوة 3: عرض مسار الإخراج
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
تهانينا! لقد نجحت في إضافة مكون زر إلى مستند PDF باستخدام Groupdocs.Annotation لـ .NET.

## خاتمة
في هذا البرنامج التعليمي، شرحنا كيفية دمج مكونات الأزرار في مستندات PDF باستخدام Groupdocs.Annotation لـ .NET. باتباع هذه الخطوات، يمكنك تحسين مستندات PDF الخاصة بك بميزات تفاعلية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر الزر؟
نعم، يمكنك تخصيص خصائص مختلفة مثل الحجم واللون ونمط مكون الزر وفقًا لمتطلباتك.
### هل Groupdocs.Annotation لـ .NET متوافق مع كافة إصدارات PDF؟
يدعم Groupdocs.Annotation لـ .NET مجموعة واسعة من إصدارات PDF، مما يضمن التوافق مع معظم المستندات.
### هل يمكنني إضافة مكونات أزرار متعددة إلى مستند PDF واحد؟
بالتأكيد، يمكنك إضافة عدد غير محدود من مكونات الأزرار إلى مستند PDF باستخدام Groupdocs.Annotation لـ .NET.
### هل يوفر Groupdocs.Annotation لـ .NET الدعم لتنسيقات الملفات الأخرى؟
نعم، بالإضافة إلى PDF، يدعم Groupdocs.Annotation for .NET تنسيقات المستندات الأخرى المتنوعة بما في ذلك DOCX وPPTX وXLSX.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من Groupdocs.Annotation لـ .NET من [هنا](https://releases.groupdocs.com/).