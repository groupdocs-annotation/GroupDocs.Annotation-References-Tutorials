---
"description": "تعرّف على كيفية إضافة التعليقات التوضيحية النقطية إلى ملفات PDF باستخدام GroupDocs.Annotation لـ .NET. دليل خطوة بخطوة لدمج سلس."
"linktitle": "إضافة تعليق نقطي إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق نقطي إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# إضافة تعليق نقطي إلى المستند

## مقدمة
GroupDocs.Annotation for .NET أداة فعّالة تُمكّن المطورين من إضافة أنواع مُختلفة من التعليقات التوضيحية إلى المستندات برمجيًا. في هذا البرنامج التعليمي، سنُركز على إضافة تعليق توضيحي نقطي إلى مستند باستخدام لغة C#.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1. فهم أساسي للغة البرمجة C#.
2. تم تثبيت Visual Studio على نظامك.
3. تم تثبيت مكتبة GroupDocs.Annotation لـ .NET. يمكنك تنزيلها من [هنا](https://releases.groupdocs.com/annotation/net/).

## استيراد مساحات الأسماء الضرورية
للبدء، تحتاج إلى استيراد المساحات المطلوبة إلى مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
في هذه الخطوة، نقوم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
## الخطوة 2: تهيئة المُعلّق
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
هنا، نقوم بتهيئة `Annotator` الكائن مع مستند الإدخال ("input.pdf").
## الخطوة 3: إنشاء تعليق توضيحي للنقاط
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
في هذه الخطوة، نقوم بإنشاء `PointAnnotation` الكائن وتحديد خصائصه مثل الموضع والرسالة ورقم الصفحة والردود.
## الخطوة 4: إضافة التعليقات التوضيحية
```csharp
annotator.Add(point);
```
هنا، نضيف ملاحظة النقطة التي تم إنشاؤها إلى المستند.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save(outputPath);
```
وأخيرًا، نقوم بحفظ المستند الموضح في مسار الإخراج المحدد.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي نقطي إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باستخدام هذه المكتبة القوية، يمكنك تحسين تطبيقات إدارة المستندات لديك من خلال دمج وظائف التعليق التوضيحي.
## الأسئلة الشائعة
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
نعم، يدعم GroupDocs.Annotation لـ .NET مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF، وMicrosoft Word، وExcel، وPowerPoint، والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
بالتأكيد! يوفر GroupDocs.Annotation لـ .NET خيارات واسعة لتخصيص مظهر التعليقات التوضيحية لتناسب احتياجات تطبيقك.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation لـ .NET؟
نعم، يمكنك الاستفادة من تجربة مجانية من [هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم لأي مشاكل أو استفسارات متعلقة بـ GroupDocs.Annotation لـ .NET؟
يمكنك الحصول على الدعم من منتدى GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).
### هل يمكنني الحصول على ترخيص مؤقت لأغراض الاختبار؟
نعم يمكنك الحصول على ترخيص مؤقت من [هنا](https://purchase.groupdocs.com/temporary-license/).