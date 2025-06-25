---
"description": "تعرّف على كيفية إضافة تعليقات روابط إلى المستندات باستخدام Groupdocs.Annotation لـ .NET. حسّن التعاون والتفاعل بسهولة."
"linktitle": "إضافة تعليق الرابط إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق الرابط إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-link-annotation/"
"weight": 16
---

# إضافة تعليق الرابط إلى المستند

## مقدمة
Groupdocs.Annotation for .NET مكتبة فعّالة تُمكّن المطورين من دمج وظائف التعليقات التوضيحية الشاملة في تطبيقات .NET الخاصة بهم بسهولة. ومن أهم ميزاتها إمكانية إضافة تعليقات توضيحية للروابط إلى المستندات، مما يُعزز التعاون والتفاعل.
## المتطلبات الأساسية
قبل الخوض في عملية إضافة تعليقات الارتباط، تأكد من أن لديك المتطلبات الأساسية التالية:
- فهم أساسي للغة البرمجة C#.
- تم تثبيت Groupdocs.Annotation لمكتبة .NET.
- الوصول إلى المستند الذي تريد التعليق عليه.

## استيراد مساحات الأسماء
أولاً، عليك استيراد مساحات الأسماء اللازمة لاستخدام Groupdocs.Annotation لوظائف .NET. يتيح هذا لتطبيقك الوصول إلى الفئات والأساليب اللازمة لشرح المستندات.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تعيين مسار الإخراج
قم بتحديد المسار الذي تريد حفظ المستند الموضح فيه.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
إنشاء مثيل لـ `Annotator` الفئة عن طريق توفير مسار المستند الذي تريد التعليق عليه.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```
## الخطوة 3: إنشاء تعليق الرابط
تعريف أ `LinkAnnotation` الكائن وتحديد خصائصه مثل الرسالة، والتعتيم، ورقم الصفحة، ولون الخلفية، والنقاط، والردود، وعنوان URL.
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
## الخطوة 4: إضافة التعليقات التوضيحية
أضف تعليق الرابط الذي تم إنشاؤه إلى المستند باستخدام `Add` طريقة مثيل المشرح.
```csharp
annotator.Add(link);
```
## الخطوة 5: حفظ المستند
احفظ المستند الموضح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
إعلام المستخدم بنجاح حفظ المستند الموضح.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، باتباع الخطوات المذكورة أعلاه، يمكنك بسهولة إضافة تعليقات روابط إلى المستندات باستخدام Groupdocs.Annotation لـ .NET. هذا يُحسّن التعاون في المستندات ويوفر للمستخدمين ميزات تفاعلية.
## الأسئلة الشائعة
### هل Groupdocs.Annotation لـ .NET متوافق مع جميع أنواع المستندات؟
يدعم Groupdocs.Annotation لـ .NET مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وWord وExcel والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يمكنك تخصيص خصائص مختلفة للتعليقات التوضيحية مثل اللون والتعتيم والحجم لتناسب متطلباتك.
### هل يوفر Groupdocs.Annotation لـ .NET ميزات التعاون في الوقت الفعلي؟
نعم، يوفر Groupdocs.Annotation لـ .NET ميزات التعاون في الوقت الفعلي مما يسمح لمستخدمين متعددين بتعليق المستندات في نفس الوقت.
### هل يتوفر الدعم الفني لمنتجات Groupdocs؟
نعم، يتوفر الدعم الفني لمنتجات Groupdocs من خلال المنتدى والدعم [هنا](https://forum.groupdocs.com/c/annotation/10).
### هل يمكنني تجربة Groupdocs.Annotation لـ .NET قبل الشراء؟
نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من Groupdocs.Annotation لـ .NET لاستكشاف ميزاته قبل إجراء عملية شراء[هنا](https://purchase.groupdocs.com/temporary-license/).