---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية لنصوص مشطوبة إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. حسّن التعاون وعمليات مراجعة المستندات بكفاءة."
"linktitle": "إضافة تعليق توضيحي لشطب النص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي لشطب النص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# إضافة تعليق توضيحي لشطب النص إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية إضافة تعليق توضيحي لشطب النص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. توفر هذه المكتبة أدوات فعّالة لإضافة تعليقات توضيحية على أنواع مختلفة من المستندات، مما يُحسّن التعاون وعمليات مراجعة المستندات.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:
1. GroupDocs.Annotation لـ .NET: ثبّت المكتبة. يمكنك تنزيلها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة لتطوير .NET.
3. المستند: قم بإعداد مستند جاهز للتعليق عليه، مثل ملف PDF.

## استيراد مساحات الأسماء
أولاً، قم باستيراد مساحات الأسماء اللازمة للوصول إلى وظائف GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن، دعنا نقسم عملية إضافة تعليق شطب النص إلى خطوات متعددة:
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
هنا، نقوم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
## الخطوة 2: تهيئة المُعلّق
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
قم بتهيئة كائن المعلق من خلال توفير المسار إلى مستند الإدخال (ملف PDF في هذه الحالة).
## الخطوة 3: إنشاء تعليق توضيحي للشطب
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
قم بإنشاء كائن StrikeoutAnnotation بالخصائص المطلوبة مثل الرسالة، والتعتيم، ورقم الصفحة، ولون الخلفية، والنقط (الإحداثيات)، والردود.
## الخطوة 4: إضافة التعليقات التوضيحية
```csharp
annotator.Add(strikeout);
```
أضف تعليق الشطب الذي تم إنشاؤه إلى المستند.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save(outputPath);
```
احفظ المستند الموضح في مسار الإخراج المحدد.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي لشطب النص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. تتيح هذه المكتبة القوية إضافة تعليقات توضيحية فعّالة للمستندات، مما يُحسّن التعاون وعمليات مراجعة المستندات.
## الأسئلة الشائعة
### هل GroupDocs.Annotation متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وWord وExcel وPowerPoint والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
بالتأكيد، يمكنك تخصيص خصائص التعليقات التوضيحية مثل اللون والتعتيم وحجم الخط والمزيد وفقًا لمتطلباتك.
### هل يوفر GroupDocs.Annotation ميزات التعاون؟
نعم، يسهل GroupDocs.Annotation التعاون من خلال السماح للمستخدمين بإضافة التعليقات والردود والتوضيحات إلى المستندات.
### هل هناك نسخة تجريبية مجانية متاحة؟
نعم، يمكنك الاستفادة من تجربة مجانية من [هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم لـ GroupDocs.Annotation؟
يمكنك الحصول على الدعم من [منتدى GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).