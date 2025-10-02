---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية مسطرة للنصوص إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. حسّن التعاون والتواصل بسهولة."
"linktitle": "إضافة تعليق توضيحي لتسطير النص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي لتسطير النص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# إضافة تعليق توضيحي لتسطير النص إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنشرح عملية إضافة تعليق توضيحي لتسطير النص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. يمكن أن يكون تعليق التوضيح التوضيحي لتسطير النص مفيدًا لإبراز أجزاء معينة من المستند، مثل الفقرات المهمة أو النقاط الرئيسية.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من تثبيت المتطلبات الأساسية التالية:
1. GroupDocs.Annotation لـ .NET: قم بتنزيل GroupDocs.Annotation لـ .NET وتثبيته من [هنا](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: تأكد من تثبيت .NET Framework على نظامك.

## استيراد مساحات الأسماء
أولاً، دعنا نستورد مساحات الأسماء الضرورية إلى مشروعنا:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن، دعونا نقسم المثال إلى خطوات متعددة:
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
في هذه الخطوة، نقوم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
## الخطوة 2: تهيئة المُعلّق
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
هنا، نقوم بتهيئة مثيل لـ `Annotator` الفئة عن طريق توفير مسار مستند الإدخال.
## الخطوة 3: إنشاء تعليق توضيحي مسطر
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // الأعمال المدعومة فقط هي مستندات Word وPDF
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
تتضمن هذه الخطوة إنشاء `UnderlineAnnotation` كائن يحتوي على خصائص مختلفة مثل لون الخط والرسالة والتعتيم ورقم الصفحة ولون الخلفية ولون التسطير والنقاط والردود.
## الخطوة 4: إضافة تعليق توضيحي إلى المستند
```csharp
annotator.Add(underline);
```
هنا نضيف تعليق التسطير إلى المستند.
## الخطوة 5: حفظ المستند الموضح
```csharp
annotator.Save(outputPath);
```
وأخيرًا، نقوم بحفظ المستند الموضح في مسار الإخراج المحدد.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي لتسطير النص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. توفر هذه المكتبة القوية خيارات تعليق توضيحية متنوعة لتعزيز التعاون والتواصل في المستندات.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليق التوضيحي؟
نعم، يمكنك تخصيص خصائص مثل اللون والتعتيم والموضع وفقًا لمتطلباتك.
### هل GroupDocs.Annotation متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك Word وPDF.
### هل يمكنني إضافة تعليقات متعددة إلى مستند واحد؟
بالتأكيد، يسمح لك GroupDocs.Annotation بإضافة تعليقات متعددة من أنواع مختلفة إلى مستند.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟
نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من [هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم لـ GroupDocs.Annotation؟
يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).