---
title: إضافة مكون الزر إلى وثيقة PDF
linktitle: إضافة مكون الزر إلى وثيقة PDF
second_title: GroupDocs.Annotation .NET API
description: قم بتحسين مستندات PDF الخاصة بك باستخدام مكونات الأزرار التفاعلية باستخدام Groupdocs.Annotation for .NET. اتبع البرنامج التعليمي خطوة بخطوة لتحقيق التكامل السلس.
weight: 10
url: /ar/net/document-components/add-button-component-to-pdf/
---

# إضافة مكون الزر إلى وثيقة PDF

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة مكون الزر إلى مستند PDF باستخدام Groupdocs.Annotation for .NET. سيضمن هذا الدليل التفصيلي أنه يمكنك بسهولة دمج هذه الميزة في مشروعك.
## المتطلبات الأساسية
قبل البدء، تأكد من توفر المتطلبات الأساسية التالية:
1.  Groupdocs.Annotation لـ .NET: تأكد من تثبيت Groupdocs.Annotation لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تمتع ببيئة تطوير مناسبة تم إعدادها مع تثبيت .NET Framework.

## استيراد مساحات الأسماء
قبل المتابعة، قم باستيراد مساحات الأسماء الضرورية إلى مشروعك:
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
تهانينا! لقد نجحت في إضافة مكون الزر إلى مستند PDF باستخدام Groupdocs.Annotation لـ .NET.

## خاتمة
في هذا البرنامج التعليمي، أوضحنا كيفية دمج Button Components في مستندات PDF باستخدام Groupdocs.Annotation for .NET. باتباع هذه الخطوات، يمكنك تحسين مستندات PDF الخاصة بك بميزات تفاعلية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر الزر؟
نعم، يمكنك تخصيص خصائص مختلفة مثل الحجم واللون ونمط مكون الزر وفقًا لمتطلباتك.
### هل Groupdocs.Annotation for .NET متوافق مع كافة إصدارات PDF؟
يدعم Groupdocs.Annotation for .NET نطاقًا واسعًا من إصدارات PDF، مما يضمن التوافق مع معظم المستندات.
### هل يمكنني إضافة مكونات أزرار متعددة إلى مستند PDF واحد؟
بالتأكيد، يمكنك إضافة أي عدد تريده من مكونات الأزرار إلى مستند PDF باستخدام Groupdocs.Annotation for .NET.
### هل يقدم Groupdocs.Annotation for .NET الدعم لتنسيقات الملفات الأخرى؟
نعم، بالإضافة إلى PDF، يدعم Groupdocs.Annotation for .NET العديد من تنسيقات المستندات الأخرى بما في ذلك DOCX وPPTX وXLSX.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من Groupdocs.Annotation لـ .NET من[هنا](https://releases.groupdocs.com/).