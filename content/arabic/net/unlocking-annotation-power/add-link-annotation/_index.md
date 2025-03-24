---
title: إضافة تعليق توضيحي للارتباط إلى المستند
linktitle: إضافة تعليق توضيحي للارتباط إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية للارتباط إلى المستندات باستخدام Groupdocs.Annotation لـ .NET. تعزيز التعاون والتفاعل دون عناء.
weight: 16
url: /ar/net/unlocking-annotation-power/add-link-annotation/
---

# إضافة تعليق توضيحي للارتباط إلى المستند

## مقدمة
تعد Groupdocs.Annotation for .NET مكتبة قوية تمكن المطورين من دمج وظائف التعليقات التوضيحية الشاملة في تطبيقات .NET الخاصة بهم دون عناء. إحدى الميزات الرئيسية التي يقدمها هي القدرة على إضافة تعليقات توضيحية للارتباط إلى المستندات، وتعزيز التعاون والتفاعل.
## المتطلبات الأساسية
قبل الغوص في عملية إضافة التعليقات التوضيحية للرابط، تأكد من توفر المتطلبات الأساسية التالية:
- الفهم الأساسي للغة البرمجة C#.
- تم تثبيت Groupdocs.Annotation لمكتبة .NET.
- الوصول إلى المستند الذي تريد التعليق عليه.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء اللازمة لاستخدام Groupdocs.Annotation لوظائف .NET. يتيح ذلك لتطبيقك الوصول إلى الفئات والأساليب المطلوبة لإضافة تعليقات توضيحية إلى المستندات.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تعيين مسار الإخراج
حدد المسار الذي تريد حفظ المستند المشروح فيه.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
 إنشاء مثيل لـ`Annotator` class عن طريق توفير مسار المستند الذي تريد التعليق عليه.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي للارتباط
 تعريف أ`LinkAnnotation` الكائن وتحديد خصائصه مثل الرسالة، والعتامة، ورقم الصفحة، ولون الخلفية، والنقاط، والردود، وعنوان URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## الخطوة 4: إضافة تعليق توضيحي
 أضف تعليقًا توضيحيًا للارتباط الذي تم إنشاؤه إلى المستند باستخدام ملف`Add` طريقة مثيل الحواشي.
```csharp
annotator.Add(link);
```
## الخطوة 5: حفظ المستند
احفظ المستند المشروح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
أبلغ المستخدم بنجاح حفظ المستند المشروح.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، باتباع الخطوات المذكورة أعلاه، يمكنك إضافة تعليقات توضيحية للارتباط بسهولة إلى المستندات باستخدام Groupdocs.Annotation for .NET. يؤدي هذا إلى تحسين التعاون في المستندات ويوفر للمستخدمين ميزات تفاعلية.
## الأسئلة الشائعة
### هل Groupdocs.Annotation for .NET متوافق مع كافة أنواع المستندات؟
يدعم Groupdocs.Annotation for .NET نطاقًا واسعًا من تنسيقات المستندات بما في ذلك PDF وWord وExcel والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يمكنك تخصيص خصائص مختلفة للتعليقات التوضيحية مثل اللون والعتامة والحجم لتناسب متطلباتك.
### هل يوفر Groupdocs.Annotation for .NET ميزات التعاون في الوقت الفعلي؟
نعم، يوفر Groupdocs.Annotation for .NET ميزات التعاون في الوقت الفعلي مما يسمح لعدة مستخدمين بالتعليق على المستندات في وقت واحد.
### هل يتوفر الدعم الفني لمنتجات Groupdocs؟
 نعم، يتوفر الدعم الفني لمنتجات Groupdocs من خلال المنتدى والدعم[هنا](https://forum.groupdocs.com/c/annotation/10).
### هل يمكنني تجربة Groupdocs.Annotation لـ .NET قبل الشراء؟
نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من Groupdocs.Annotation لـ .NET لاستكشاف ميزاته قبل إجراء عملية شراء[هنا](https://purchase.groupdocs.com/temporary-license/).