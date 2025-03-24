---
title: إضافة تعليق توضيحي للمسافة إلى المستند
linktitle: إضافة تعليق توضيحي للمسافة إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة التعليقات التوضيحية عن بعد إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. تعزيز التعاون والتواصل دون عناء.
weight: 12
url: /ar/net/unlocking-annotation-power/add-distance-annotation/
---

# إضافة تعليق توضيحي للمسافة إلى المستند

## مقدمة
ستتعلم في هذا البرنامج التعليمي كيفية إضافة تعليق توضيحي عن بعد إلى مستند باستخدام GroupDocs.Annotation لـ .NET. اتبع هذه الخطوات لإنجاز المهمة:
## المتطلبات الأساسية

تأكد من توفر المتطلبات الأساسية التالية قبل المتابعة:

-  GroupDocs.Annotation لمكتبة .NET: قم بتنزيل وتثبيت GroupDocs.Annotation لمكتبة .NET من[هذا الرابط](https://releases.groupdocs.com/annotation/net/).
- مستند للتعليق عليه: قم بإعداد المستند (على سبيل المثال، PDF) الذي تريد إضافة تعليق توضيحي للمسافة إليه.
- بيئة التطوير: قم بإعداد بيئة التطوير الخاصة بك باستخدام Visual Studio أو أي بيئة تطوير متكاملة أخرى من اختيارك.

## استيراد مساحات الأسماء

قبل أن تبدأ، تأكد من تضمين مساحات الأسماء الضرورية في التعليمات البرمجية الخاصة بك. تعد مساحات الأسماء هذه ضرورية للوصول إلى الفئات والأساليب المطلوبة.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## الخطوة 1: تهيئة الحواشي

 ابدأ بتهيئة`Annotator` الكائن الذي يحتوي على المسار إلى المستند الذي تريد إضافة تعليق توضيحي إليه.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```

## الخطوة 2: إنشاء تعليق توضيحي للمسافة

 الآن، قم بإنشاء`DistanceAnnotation` الكائن وتكوين خصائصه مثل أبعاد الصندوق، والرسالة، والعتامة، ولون القلم، وما إلى ذلك.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
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

## الخطوة 3: إضافة تعليق توضيحي

 أضف التعليق التوضيحي للمسافة الذي تم إنشاؤه إلى المستند باستخدام`Add` طريقة كائن الحواشي.

```csharp
annotator.Add(distance);
```

## الخطوة 4: حفظ المستند

احفظ المستند المشروح في الموقع المطلوب على نظامك.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## الخطوة 5: عرض التأكيد

وأخيرًا، قم بعرض رسالة تؤكد نجاح حفظ المستند المشروح.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

تعد إضافة التعليقات التوضيحية عن بعد إلى المستندات باستخدام GroupDocs.Annotation لـ .NET عملية مباشرة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك تحسين مستنداتك بتعليقات توضيحية قيمة، مما يسهل التعاون والتواصل بشكل أفضل.

## الأسئلة الشائعة

### س: هل يمكنني تخصيص مظهر التعليق التوضيحي للمسافة؟

ج: نعم، يمكنك تخصيص خصائص مختلفة مثل اللون، والعتامة، ونمط الخط، وما إلى ذلك، لتناسب متطلباتك.

### س: هل يدعم GroupDocs.Annotation التعليقات التوضيحية على أنواع مختلفة من المستندات؟

ج: نعم، يدعم GroupDocs.Annotation التعليقات التوضيحية على نطاق واسع من تنسيقات المستندات بما في ذلك PDF وWord وExcel وPowerPoint والمزيد.

### س: هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟

 ج: نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من GroupDocs.Annotation من[هذا الرابط](https://releases.groupdocs.com/).

### س: أين يمكنني العثور على وثائق GroupDocs.Annotation لـ .NET؟

 ج: يمكنك الرجوع إلى الوثائق التفصيلية المتاحة[هنا](https://tutorials.groupdocs.com/annotation/net/).

### س: كيف يمكنني الحصول على الدعم أو المساعدة فيما يتعلق بـ GroupDocs.Annotation؟

 ج: يمكنك طلب الدعم والمساعدة من منتدى مجتمع GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).