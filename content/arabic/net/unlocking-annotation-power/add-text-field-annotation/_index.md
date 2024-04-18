---
title: إضافة تعليق توضيحي لحقل النص إلى المستند
linktitle: إضافة تعليق توضيحي لحقل النص إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية دمج التعليقات التوضيحية لحقول النص بسلاسة في تطبيقات .NET الخاصة بك باستخدام Groupdocs.Annotation لـ .NET.
type: docs
weight: 21
url: /ar/net/unlocking-annotation-power/add-text-field-annotation/
---
## مقدمة
تعد Groupdocs.Annotation for .NET أداة قوية تسمح للمطورين بإضافة ميزات التعليقات التوضيحية إلى تطبيقات .NET الخاصة بهم دون عناء. سواء كنت تعمل على نظام إدارة المستندات، أو نظام أساسي تعاوني، أو أي تطبيق حيث يكون التعليق التوضيحي للمستند أمرًا ضروريًا، فإن Groupdocs.Annotation يبسط العملية من خلال مجموعة شاملة من الميزات وواجهة برمجة التطبيقات البديهية.
في هذا البرنامج التعليمي، سوف نتعمق في إحدى الوظائف الأساسية لـ Groupdocs.Annotation لـ .NET: إضافة تعليق توضيحي لحقل النص إلى مستند. باتباع هذا الدليل التفصيلي، ستتعلم كيفية دمج التعليقات التوضيحية لحقول النص بسلاسة في تطبيقات .NET الخاصة بك، مما يعزز تجربة المستخدم وإمكانيات التعاون.
## المتطلبات الأساسية
قبل الغوص في التنفيذ، تأكد من توفر المتطلبات الأساسية التالية:
### 1. تثبيت Groupdocs.Annotation لـ .NET
 أولاً وقبل كل شيء، تحتاج إلى تنزيل Groupdocs.Annotation لـ .NET وتثبيته. يمكنك العثور على رابط التحميل[هنا](https://releases.groupdocs.com/annotation/net/) . اتبع تعليمات التثبيت المتوفرة في الوثائق[هنا](https://reference.groupdocs.com/annotation/net/) لإعداد المكتبة بشكل صحيح.
### 2. إعداد بيئة التطوير
تأكد من أن لديك بيئة تطوير تم إعدادها لتطوير .NET. يتضمن ذلك تثبيت IDE متوافق مثل Visual Studio و.NET Framework على نظامك.
### 3. الفهم الأساسي لبرمجة C#
تعرف على أساسيات لغة البرمجة C#، حيث سيتضمن هذا البرنامج التعليمي كتابة كود C# لدمج التعليقات التوضيحية لحقول النص.

## استيراد مساحات الأسماء
في مشروع C# الخاص بك، ابدأ باستيراد مساحات الأسماء الضرورية للاستفادة من وظائف Groupdocs.Annotation.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن، لنتابع إضافة تعليق توضيحي لحقل نصي إلى مستند باستخدام Groupdocs.Annotation لـ .NET.
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 3: إنشاء كائن TextFieldAnnotation
```csharp
TextFieldAnnotation textField = new TextFieldAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Text = "Some text",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is text field annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## الخطوة 4: إضافة تعليق توضيحي إلى المستند
```csharp
annotator.Add(textField);
```
## الخطوة 5: حفظ المستند مع التعليق التوضيحي
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، يعد دمج التعليقات التوضيحية لحقول النص في تطبيقات .NET الخاصة بك باستخدام Groupdocs.Annotation لـ .NET عملية مباشرة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك تحسين التعاون في المستندات وتفاعل المستخدم داخل تطبيقاتك بسلاسة.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليقات التوضيحية لحقل النص؟
نعم، يمكنك تخصيص سمات مختلفة مثل لون الخلفية وحجم الخط والعتامة وما إلى ذلك، وفقًا لمتطلباتك.
### هل Groupdocs.Annotation for .NET متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم Groupdocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وDOCX وPPTX وXLSX والمزيد.
### هل يمكنني إضافة تعليقات توضيحية متعددة لنفس المستند؟
بالتأكيد، يمكنك إضافة تعليقات توضيحية متعددة من أنواع مختلفة إلى نفس المستند، مما يتيح التفاعل الغني للمستند.
### هل هناك إصدار تجريبي متاح لـ Groupdocs.Annotation لـ .NET؟
 نعم، يمكنك استكشاف ميزات Groupdocs.Annotation عن طريق الوصول إلى النسخة التجريبية المجانية[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على دعم لـ Groupdocs.Annotation لـ .NET؟
 يمكنك العثور على المساعدة والتفاعل مع المجتمع في منتدى Groupdocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).