---
title: أضف تعليقًا توضيحيًا للقطع الناقص إلى المستند
linktitle: أضف تعليقًا توضيحيًا للقطع الناقص إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية على شكل قطع ناقص إلى المستندات في .NET باستخدام GroupDocs.Annotation. تعزيز التعاون والتواصل دون عناء.
weight: 13
url: /ar/net/unlocking-annotation-power/add-ellipse-annotation/
---

# أضف تعليقًا توضيحيًا للقطع الناقص إلى المستند

## مقدمة
ستتعلم في هذا البرنامج التعليمي كيفية إضافة تعليق توضيحي على شكل قطع ناقص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. سيرشدك هذا الدليل خطوة بخطوة خلال العملية، مما يضمن أنك تفهم كل خطوة بوضوح.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Annotation لـ .NET: تأكد من تنزيل وتثبيت GroupDocs.Annotation لـ .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. IDE (بيئة التطوير المتكاملة): ستحتاج إلى IDE مثبت على نظامك، مثل Visual Studio، لكتابة التعليمات البرمجية وتنفيذها.

## استيراد مساحات الأسماء
أولاً، قم باستيراد مساحات الأسماء الضرورية لمشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تعيين مسار الإخراج
حدد مسار الإخراج حيث سيتم حفظ المستند المشروح:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
قم بتهيئة التعليق التوضيحي من خلال توفير مسار مستند الإدخال:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 3: إنشاء تعليق توضيحي للقطع الناقص
 إنشاء مثيل لـ`EllipseAnnotation` الفئة وتعيين خصائصها:
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
## الخطوة 4: إضافة تعليق توضيحي
أضف تعليقًا توضيحيًا للقطع الناقص إلى المستند:
```csharp
annotator.Add(ellipse);
```
## الخطوة 5: حفظ المستند
احفظ المستند المشروح في مسار الإخراج:
```csharp
annotator.Save(outputPath);
```

## خاتمة
تهانينا! لقد قمت بنجاح بإضافة تعليق توضيحي على شكل قطع ناقص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. يمكنك الآن دمج هذه الوظيفة في تطبيقات .NET الخاصة بك لتحسين التعاون والتواصل في المستندات.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليق التوضيحي للقطع الناقص؟
نعم، يمكنك تخصيص خصائص مختلفة مثل لون الخلفية، ولون الحدود، والعتامة، وما إلى ذلك، وفقًا لمتطلباتك.
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
يدعم GroupDocs.Annotation for .NET نطاقًا واسعًا من تنسيقات المستندات بما في ذلك PDF وDOCX وPPTX وXLSX والمزيد.
### هل يمكنني إضافة تعليقات توضيحية متعددة إلى مستند واحد؟
نعم، يمكنك إضافة تعليقات توضيحية متعددة بما في ذلك علامات الحذف والمستطيلات والنص وما إلى ذلك إلى مستند واحد.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/) لتقييم ميزاته.
### أين يمكنني الحصول على الدعم الفني لـ GroupDocs.Annotation لـ .NET؟
 يمكنك الحصول على الدعم الفني من منتدى مجتمع GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).