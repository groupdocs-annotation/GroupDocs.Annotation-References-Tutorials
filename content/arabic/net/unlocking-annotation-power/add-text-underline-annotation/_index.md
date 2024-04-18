---
title: أضف نصًا تحته تعليق توضيحي إلى المستند
linktitle: أضف نصًا تحته تعليق توضيحي إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية نصية مسطرة إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. تعزيز التعاون والتواصل دون عناء.
type: docs
weight: 27
url: /ar/net/unlocking-annotation-power/add-text-underline-annotation/
---
## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية إضافة تعليق توضيحي تحته خط إلى مستند باستخدام GroupDocs.Annotation لـ .NET. يمكن أن تكون التعليقات التوضيحية التي تحتها خط مفيدة للتأكيد على أجزاء معينة من المستند، مثل المقاطع المهمة أو النقاط الرئيسية.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من تثبيت المتطلبات الأساسية التالية:
1.  GroupDocs.Annotation لـ .NET: قم بتنزيل وتثبيت GroupDocs.Annotation لـ .NET من[هنا](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: تأكد من تثبيت .NET Framework على نظامك.

## استيراد مساحات الأسماء
أولاً، لنستورد مساحات الأسماء الضرورية إلى مشروعنا:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن، دعونا نقسم المثال إلى عدة خطوات:
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
في هذه الخطوة، نحدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
## الخطوة 2: تهيئة الحواشي
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 هنا، نقوم بتهيئة مثيل لـ`Annotator` فئة عن طريق توفير مسار وثيقة الإدخال.
## الخطوة 3: إنشاء تعليق توضيحي تحته خط
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // يدعم العمل مستندات Word وPDF فقط
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
 تتضمن هذه الخطوة إنشاء`UnderlineAnnotation`كائن ذو خصائص متنوعة مثل لون الخط والرسالة والعتامة ورقم الصفحة ولون الخلفية ولون التسطير والنقاط والردود.
## الخطوة 4: إضافة تعليق توضيحي إلى المستند
```csharp
annotator.Add(underline);
```
هنا، نضيف الشرح الذي تحته خط إلى الوثيقة.
## الخطوة 5: حفظ المستند المشروح
```csharp
annotator.Save(outputPath);
```
وأخيرًا، نقوم بحفظ المستند المشروح في مسار الإخراج المحدد.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي تحته خط إلى مستند باستخدام GroupDocs.Annotation لـ .NET. توفر هذه المكتبة القوية خيارات متنوعة للتعليقات التوضيحية لتحسين التعاون والتواصل في المستندات.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليق التوضيحي الذي تحته خط؟
نعم، يمكنك تخصيص خصائص مثل اللون والعتامة والموضع وفقًا لمتطلباتك.
### هل GroupDocs.Annotation متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Annotation نطاقًا واسعًا من تنسيقات المستندات بما في ذلك Word وPDF.
### هل يمكنني إضافة تعليقات توضيحية متعددة إلى مستند واحد؟
بالتأكيد، يتيح لك GroupDocs.Annotation إضافة تعليقات توضيحية متعددة من أنواع مختلفة إلى المستند.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من[هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم بخصوص GroupDocs.Annotation؟
 يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).