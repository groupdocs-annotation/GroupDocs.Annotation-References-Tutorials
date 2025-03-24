---
title: إضافة تعليق توضيحي إلى المستند
linktitle: إضافة تعليق توضيحي إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة التعليقات التوضيحية النقطية إلى ملفات PDF باستخدام GroupDocs.Annotation لـ .NET. دليل خطوة بخطوة للتكامل السلس.
weight: 17
url: /ar/net/unlocking-annotation-power/add-point-annotation/
---
## مقدمة
تعد GroupDocs.Annotation for .NET أداة قوية تسمح للمطورين بإضافة أنواع مختلفة من التعليقات التوضيحية إلى المستندات برمجيًا. في هذا البرنامج التعليمي، سوف نركز على إضافة تعليق توضيحي إلى مستند باستخدام C#.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1. الفهم الأساسي للغة البرمجة C#.
2. تم تثبيت Visual Studio على نظامك.
3.  تم تثبيت GroupDocs.Annotation لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).

## استيراد مساحات الأسماء الضرورية
للبدء، تحتاج إلى استيراد مساحات الأسماء المطلوبة إلى مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
في هذه الخطوة، نحدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
## الخطوة 2: تهيئة الحواشي
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 هنا، نقوم بتهيئة`Annotator` كائن مع مستند الإدخال ("input.pdf").
## الخطوة 3: إنشاء تعليق توضيحي للنقطة
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 في هذه الخطوة نقوم بإنشاء`PointAnnotation` الكائن وتحديد خصائصه مثل الموضع والرسالة ورقم الصفحة والردود.
## الخطوة 4: إضافة تعليق توضيحي
```csharp
annotator.Add(point);
```
هنا، نضيف التعليق التوضيحي النقطي الذي تم إنشاؤه إلى المستند.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save(outputPath);
```
وأخيرًا، نقوم بحفظ المستند المشروح في مسار الإخراج المحدد.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي نقطي إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باستخدام هذه المكتبة القوية، يمكنك تحسين تطبيقات إدارة المستندات الخاصة بك من خلال دمج وظائف التعليقات التوضيحية.
## الأسئلة الشائعة
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
نعم، يدعم GroupDocs.Annotation for .NET نطاقًا واسعًا من تنسيقات المستندات بما في ذلك PDF وMicrosoft Word وExcel وPowerPoint والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
قطعاً! يوفر GroupDocs.Annotation for .NET خيارات شاملة لتخصيص مظهر التعليقات التوضيحية بما يتناسب مع احتياجات التطبيق الخاص بك.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation لـ .NET؟
 نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم لأية مشكلات أو استفسارات تتعلق بـ GroupDocs.Annotation لـ .NET؟
 يمكنك الحصول على الدعم من منتدى GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).
### هل يمكنني الحصول على ترخيص مؤقت لأغراض الاختبار؟
 نعم يمكنك الحصول على ترخيص مؤقت من[هنا](https://purchase.groupdocs.com/temporary-license/).