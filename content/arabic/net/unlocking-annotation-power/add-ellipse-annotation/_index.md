---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية على شكل نقاط إلى مستندات .NET باستخدام GroupDocs.Annotation. حسّن التعاون والتواصل بسهولة."
"linktitle": "إضافة تعليق توضيحي على شكل قطع ناقص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي على شكل قطع ناقص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# إضافة تعليق توضيحي على شكل قطع ناقص إلى المستند

## مقدمة
في هذا البرنامج التعليمي، ستتعلم كيفية إضافة تعليق توضيحي على شكل نقاط بيضاوية إلى مستند باستخدام GroupDocs.Annotation لـ .NET. سيشرح لك هذا الدليل خطوة بخطوة العملية، ويضمن فهمك لكل خطوة بوضوح.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
1. GroupDocs.Annotation لـ .NET: تأكد من تنزيل GroupDocs.Annotation لـ .NET وتثبيته. يمكنك تنزيله من [هنا](https://releases.groupdocs.com/annotation/net/).
2. IDE (بيئة التطوير المتكاملة): ستحتاج إلى تثبيت IDE على نظامك، مثل Visual Studio، لكتابة التعليمات البرمجية وتنفيذها.

## استيراد مساحات الأسماء
أولاً، قم باستيراد المساحات الأسماء الضرورية لمشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تعيين مسار الإخراج
قم بتحديد مسار الإخراج حيث سيتم حفظ المستند الموضح:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
قم بتهيئة المشرح من خلال توفير مسار مستند الإدخال:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 3: إنشاء شرح القطع الناقص
إنشاء مثيل لـ `EllipseAnnotation` الفئة وتعيين خصائصها:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
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
## الخطوة 4: إضافة التعليقات التوضيحية
أضف تعليق القطع الناقص إلى المستند:
```csharp
annotator.Add(ellipse);
```
## الخطوة 5: حفظ المستند
احفظ المستند الموضح في مسار الإخراج:
```csharp
annotator.Save(outputPath);
```

## خاتمة
تهانينا! لقد نجحت في إضافة شرح بيضاوي إلى مستند باستخدام GroupDocs.Annotation لـ .NET. يمكنك الآن دمج هذه الوظيفة في تطبيقات .NET لديك لتحسين التعاون والتواصل في المستندات.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر شرح القطع الناقص؟
نعم، يمكنك تخصيص خصائص مختلفة مثل لون الخلفية، ولون الحدود، والتعتيم، وما إلى ذلك، وفقًا لمتطلباتك.
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
يدعم GroupDocs.Annotation لـ .NET مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وDOCX وPPTX وXLSX والمزيد.
### هل يمكنني إضافة تعليقات متعددة إلى مستند واحد؟
نعم، يمكنك إضافة تعليقات توضيحية متعددة بما في ذلك النقاط الثلاث، والمستطيلات، والنص، وما إلى ذلك، إلى مستند واحد.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية من [هنا](https://releases.groupdocs.com/) لتقييم ميزاته.
### أين يمكنني الحصول على الدعم الفني لـ GroupDocs.Annotation لـ .NET؟
يمكنك الحصول على الدعم الفني من منتدى مجتمع GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).