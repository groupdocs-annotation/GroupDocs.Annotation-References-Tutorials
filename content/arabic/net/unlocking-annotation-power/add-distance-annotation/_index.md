---
"description": "تعرّف على كيفية إضافة تعليقات المسافة إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. حسّن التعاون والتواصل بسهولة."
"linktitle": "إضافة تعليق المسافة إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق المسافة إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# إضافة تعليق المسافة إلى المستند

## مقدمة
في هذا البرنامج التعليمي، ستتعلم كيفية إضافة تعليق مسافة إلى مستند باستخدام GroupDocs.Annotation لـ .NET. اتبع الخطوات التالية لإتمام المهمة:
## المتطلبات الأساسية

تأكد من توفر المتطلبات الأساسية التالية قبل المتابعة:

- GroupDocs.Annotation لمكتبة .NET: قم بتنزيل وتثبيت مكتبة GroupDocs.Annotation لمكتبة .NET من [هذا الرابط](https://releases.groupdocs.com/annotation/net/).
- المستند الذي تريد إضافة تعليق عليه: قم بإعداد المستند (على سبيل المثال، PDF) الذي تريد إضافة تعليق المسافة إليه.
- بيئة التطوير: قم بإعداد بيئة التطوير الخاصة بك باستخدام Visual Studio أو أي بيئة تطوير متكاملة أخرى من اختيارك.

## استيراد مساحات الأسماء

قبل البدء، تأكد من تضمين مساحات الأسماء اللازمة في الكود. هذه المساحات ضرورية للوصول إلى الفئات والأساليب المطلوبة.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## الخطوة 1: تهيئة المُعلّق

ابدأ بالتهيئة `Annotator` الكائن الذي يحتوي على المسار إلى المستند الذي تريد التعليق عليه.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```

## الخطوة 2: إنشاء تعليق المسافة

الآن قم بإنشاء `DistanceAnnotation` الكائن وتكوين خصائصه مثل أبعاد المربع والرسالة والتعتيم ولون القلم وما إلى ذلك.

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

## الخطوة 3: إضافة التعليقات التوضيحية

أضف تعليق المسافة الذي تم إنشاؤه إلى المستند باستخدام `Add` طريقة كائن المشرح.

```csharp
annotator.Add(distance);
```

## الخطوة 4: حفظ المستند

احفظ المستند الموضح في الموقع المطلوب على نظامك.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## الخطوة 5: عرض التأكيد

وأخيرًا، قم بعرض رسالة تؤكد نجاح حفظ المستند الموضح.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

إضافة تعليقات المسافة إلى المستندات باستخدام GroupDocs.Annotation لـ .NET عملية سهلة وبسيطة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك تحسين مستنداتك بإضافة تعليقات قيّمة، مما يُسهّل التعاون والتواصل بشكل أفضل.

## الأسئلة الشائعة

### س: هل يمكنني تخصيص مظهر شرح المسافة؟

ج: نعم، يمكنك تخصيص خصائص مختلفة مثل اللون، والتعتيم، ونمط الخط، وما إلى ذلك، لتناسب متطلباتك.

### س: هل يدعم GroupDocs.Annotation التعليقات التوضيحية على أنواع مختلفة من المستندات؟

ج: نعم، يدعم GroupDocs.Annotation التعليقات التوضيحية على مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وWord وExcel وPowerPoint والمزيد.

### س: هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟

ج: نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من GroupDocs.Annotation من [هذا الرابط](https://releases.groupdocs.com/).

### س: أين يمكنني العثور على الوثائق الخاصة بـ GroupDocs.Annotation لـ .NET؟

ج: يمكنك الرجوع إلى الوثائق التفصيلية المتوفرة [هنا](https://tutorials.groupdocs.com/annotation/net/).

### س: كيف يمكنني الحصول على الدعم أو المساعدة فيما يتعلق بـ GroupDocs.Annotation؟

ج: يمكنك طلب الدعم والمساعدة من منتدى مجتمع GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).