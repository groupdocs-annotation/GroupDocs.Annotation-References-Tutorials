---
title: إضافة تعليق توضيحي لخط النص إلى المستند
linktitle: إضافة تعليق توضيحي لخط النص إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية نصية إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. تعزيز عمليات التعاون ومراجعة المستندات بكفاءة.
weight: 26
url: /ar/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# إضافة تعليق توضيحي لخط النص إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية إضافة تعليق توضيحي يتوسطه نص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. توفر هذه المكتبة أدوات قوية لإضافة تعليقات توضيحية إلى أنواع مختلفة من المستندات، وتعزيز عمليات التعاون ومراجعة المستندات.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Annotation لـ .NET: قم بتثبيت المكتبة. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة لتطوير .NET.
3. المستند: احصل على مستند جاهز للتعليق، مثل ملف PDF.

## استيراد مساحات الأسماء
أولاً، قم باستيراد مساحات الأسماء الضرورية للوصول إلى وظائف GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن، دعنا نقسم عملية إضافة تعليق توضيحي لخط النص إلى خطوات متعددة:
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
هنا، نحدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
## الخطوة 2: تهيئة الحواشي
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
قم بتهيئة كائن Annotator من خلال توفير المسار إلى مستند الإدخال (ملف PDF في هذه الحالة).
## الخطوة 3: إنشاء تعليق توضيحي
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
قم بإنشاء كائن StrikeoutAnnotation بالخصائص المطلوبة مثل الرسالة، والعتامة، ورقم الصفحة، ولون الخلفية، والنقاط (الإحداثيات)، والردود.
## الخطوة 4: إضافة تعليق توضيحي
```csharp
annotator.Add(strikeout);
```
قم بإضافة التعليق التوضيحي الذي تم إنشاؤه إلى المستند.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save(outputPath);
```
احفظ المستند المشروح في مسار الإخراج المحدد.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي يتوسطه نص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. تتيح هذه المكتبة القوية إمكانية إضافة تعليقات توضيحية فعالة للمستندات، مما يعزز عمليات التعاون ومراجعة المستندات.
## الأسئلة الشائعة
### هل GroupDocs.Annotation متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وWord وExcel وPowerPoint والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
بالتأكيد، يمكنك تخصيص خصائص التعليقات التوضيحية مثل اللون والعتامة وحجم الخط والمزيد وفقًا لمتطلباتك.
### هل يوفر GroupDocs.Annotation ميزات التعاون؟
نعم، يعمل GroupDocs.Annotation على تسهيل التعاون من خلال السماح للمستخدمين بإضافة التعليقات والردود والتعليقات التوضيحية إلى المستندات.
### هل هناك نسخة تجريبية مجانية متاحة؟
 نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من[هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم بخصوص GroupDocs.Annotation؟
 يمكنك الحصول على الدعم من[GroupDocs. منتدى التعليقات التوضيحية](https://forum.groupdocs.com/c/annotation/10).