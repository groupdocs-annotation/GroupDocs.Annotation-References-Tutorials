---
title: إضافة تعليق توضيحي لاستبدال النص إلى المستند
linktitle: إضافة تعليق توضيحي لاستبدال النص إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة التعليقات التوضيحية لاستبدال النص إلى مستندات .NET الخاصة بك بسهولة باستخدام GroupDocs.Annotation لـ .NET. تعزيز قدرات معالجة المستندات الخاصة بك.
weight: 24
url: /ar/net/unlocking-annotation-power/add-text-replacement-annotation/
---

# إضافة تعليق توضيحي لاستبدال النص إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة تعليق توضيحي لاستبدال النص إلى مستنداتك باستخدام GroupDocs.Annotation لـ .NET. تسمح هذه المكتبة القوية للمطورين بمعالجة أنواع مختلفة من المستندات والتعليق عليها برمجيًا. بحلول نهاية هذا البرنامج التعليمي، ستكون مجهزًا بالمعرفة اللازمة لدمج التعليقات التوضيحية لاستبدال النص بسلاسة في تطبيقات .NET الخاصة بك.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من تثبيت المتطلبات الأساسية التالية:
### 1. تم تثبيت .NET Framework
تأكد من تثبيت .NET Framework على جهاز التطوير الخاص بك. يمكنك تنزيله من موقع مايكروسوفت.
### 2. GroupDocs.Annotation لمكتبة .NET
 قم بتنزيل وتثبيت GroupDocs.Annotation لمكتبة .NET من[موقع إلكتروني](https://releases.groupdocs.com/annotation/net/). توفر هذه المكتبة الأدوات والوظائف اللازمة للعمل مع التعليقات التوضيحية بتنسيقات المستندات المختلفة.
### 3. إعداد بيئة التطوير
قم بإعداد بيئة التطوير المفضلة لديك، مثل Visual Studio، لإنشاء تطبيقات .NET وتشغيلها.

## استيراد مساحات الأسماء
قبل الغوص في جزء الترميز، فلنستورد مساحات الأسماء الضرورية المطلوبة للعمل مع GroupDocs.Annotation لـ .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
هنا، نحدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
## الخطوة 2: تهيئة الحواشي
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```
نقوم بتهيئة كائن Annotator عن طريق تحديد مستند الإدخال ("input.pdf") داخل كتلة الاستخدام لضمان التخلص السليم من الموارد.
## الخطوة 3: إنشاء تعليق توضيحي بديل
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    },
    TextToReplace = "replaced text"
};
```
هنا، نقوم بإنشاء كائن استبدال التعليق التوضيحي بخصائص مختلفة مثل تاريخ الإنشاء، ولون الخط، والرسالة، والعتامة، ورقم الصفحة، ولون الخلفية، والنقاط (الإحداثيات)، والردود (التعليقات)، والنص المراد استبداله.
## الخطوة 4: إضافة تعليق توضيحي
```csharp
annotator.Add(replacement);
```
نضيف التعليق التوضيحي البديل الذي تم إنشاؤه إلى المذيع.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save(outputPath);
```
وأخيرًا، نقوم بحفظ المستند المشروح في مسار الإخراج المحدد.
## الخطوة 6: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
يتم عرض رسالة نجاح تشير إلى أنه تم حفظ المستند بنجاح.

## خاتمة
في هذا البرنامج التعليمي، قمنا بتغطية عملية إضافة التعليقات التوضيحية لاستبدال النص إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. باتباع الدليل خطوة بخطوة وفهم المتطلبات الأساسية، يمكنك بسهولة دمج هذه الوظيفة في تطبيقات .NET الخاصة بك.
## الأسئلة الشائعة
### هل يمكنني إضافة تعليقات توضيحية إلى المستندات ذات التنسيقات المختلفة باستخدام GroupDocs.Annotation لـ .NET؟
نعم، يدعم GroupDocs.Annotation for .NET إضافة تعليقات توضيحية إلى تنسيقات المستندات المختلفة مثل PDF وDOCX وPPTX وXLSX والمزيد.
### هل GroupDocs.Annotation for .NET مناسب لكل من تطبيقات سطح المكتب والويب؟
نعم، يمكن استخدام GroupDocs.Annotation for .NET في كل من تطبيقات سطح المكتب والويب، مما يوفر المرونة للمطورين.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية المضافة باستخدام GroupDocs.Annotation لـ .NET؟
بالتأكيد، يمكنك تخصيص مظهر التعليقات التوضيحية عن طريق تعديل الخصائص مثل اللون، والعتامة، والخط، وما إلى ذلك.
### هل يقدم GroupDocs.Annotation for .NET دعمًا لميزات التعليقات التوضيحية التعاونية؟
نعم، يوفر GroupDocs.Annotation for .NET ميزات للتعليق التوضيحي التعاوني، مما يسمح لعدة مستخدمين بالتعليق التوضيحي على المستندات في وقت واحد.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation لـ .NET؟
نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من GroupDocs.Annotation لـ .NET من[موقع إلكتروني](https://releases.groupdocs.com/).