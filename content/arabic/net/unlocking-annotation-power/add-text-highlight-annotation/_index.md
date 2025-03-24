---
title: إضافة تعليق توضيحي لتمييز النص إلى المستند
linktitle: إضافة تعليق توضيحي لتمييز النص إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة التعليقات التوضيحية المميزة للنص إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. تعزيز التعاون والإنتاجية مع هذا الشامل.
weight: 22
url: /ar/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# إضافة تعليق توضيحي لتمييز النص إلى المستند

## مقدمة
في مجال إدارة المستندات والتعاون، يظهر GroupDocs.Annotation for .NET كحل قوي، يمكّن المطورين من دمج التعليقات التوضيحية المميزة للنص بسلاسة في تطبيقاتهم. يعد هذا البرنامج التعليمي بمثابة دليل شامل لإضافة تعليقات توضيحية لتمييز النص إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. من خلال التعليمات خطوة بخطوة والشروحات التفصيلية، سوف تكتسب الكفاءة في تسخير قدرات هذه المكتبة القوية.
## المتطلبات الأساسية
قبل الخوض في تنفيذ التعليقات التوضيحية المميزة للنص، تأكد من توفر المتطلبات الأساسية التالية:
1. إعداد البيئة: تمتع ببيئة تطوير مناسبة تم تكوينها لتطوير .NET.
2.  تثبيت GroupDocs.Annotation لـ .NET: قم بتنزيل وتثبيت GroupDocs.Annotation لـ .NET من الملفات المتوفرة[رابط التحميل](https://releases.groupdocs.com/annotation/net/).
3. الإلمام بـ C#: الفهم الأساسي للغة البرمجة C#.
4. مستند للتعليق عليه: قم بإعداد مستند (على سبيل المثال، PDF) الذي تنوي إضافة تعليق توضيحي إليه.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء الضرورية في كود C# الخاص بك للاستفادة من وظائف GroupDocs.Annotation لـ .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#الآن، دعنا نقسم عملية إضافة التعليقات التوضيحية المميزة إلى خطوات متعددة:
## الخطوة 1: تحديد مسار الإخراج
حدد مسار الإخراج حيث سيتم حفظ المستند المشروح:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
 إنشاء مثيل لـ`Annotator` فئة، بتمرير اسم ملف المستند كمعلمة:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## الخطوة 3: إنشاء تعليق توضيحي مميز
 إنشاء مثيل أ`HighlightAnnotation` الكائن وتكوين خصائصه:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## الخطوة 4: إضافة تعليق توضيحي
أضف التعليق التوضيحي المميز الذي تم إنشاؤه إلى المستند:
```csharp
annotator.Add(highlight);
```
## الخطوة 5: حفظ المستند المشروح
احفظ المستند المشروح في مسار الإخراج المحدد:
```csharp
annotator.Save(outputPath);
```

## خاتمة
في الختام، يقدم GroupDocs.Annotation for .NET أسلوبًا مبسطًا لدمج التعليقات التوضيحية المميزة للنص في المستندات. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكن للمطورين تحسين التعاون في المستندات والإنتاجية داخل تطبيقاتهم بسلاسة.
## الأسئلة الشائعة
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
يدعم GroupDocs.Annotation for .NET تنسيقات المستندات المختلفة، بما في ذلك PDF وWord وExcel والمزيد. راجع الوثائق للحصول على القائمة الكاملة.
### هل يمكن تخصيص التعليقات التوضيحية وفقًا لمتطلبات محددة؟
نعم، يتمتع المطورون بالتحكم الكامل في خصائص التعليقات التوضيحية ومظهرها، مما يسمح بالتخصيص لتلبية الاحتياجات المتنوعة.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation لـ .NET؟
 نعم، يمكنك استكشاف ميزات GroupDocs.Annotation for .NET عن طريق الوصول إلى النسخة التجريبية المجانية من[وصلة](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم لأية مشكلات أو استفسارات تتعلق بـ GroupDocs.Annotation لـ .NET؟
 للحصول على الدعم والمساعدة، يمكنك زيارة منتدى GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).
### ما هي خيارات الترخيص المتوفرة لـ GroupDocs.Annotation لـ .NET؟
 يقدم GroupDocs.Annotation for .NET خيارات ترخيص متنوعة، بما في ذلك التراخيص المؤقتة لأغراض الاختبار والتراخيص التجارية لبيئات الإنتاج. قم بزيارة صفحة الشراء[هنا](https://purchase.groupdocs.com/buy) لمزيد من التفاصيل.