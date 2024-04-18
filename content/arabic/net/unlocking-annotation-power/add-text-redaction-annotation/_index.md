---
title: أضف تعليقًا توضيحيًا لتنقيح النص إلى المستند
linktitle: أضف تعليقًا توضيحيًا لتنقيح النص إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية لتنقيح النص إلى مستندات PDF باستخدام GroupDocs.Annotation لـ .NET. حماية المعلومات الحساسة دون عناء.
type: docs
weight: 23
url: /ar/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## مقدمة
يمكن أن تكون إضافة تعليق توضيحي لتنقيح النص إلى المستند خطوة حاسمة في إدارة المعلومات الحساسة بشكل آمن. يوفر GroupDocs.Annotation for .NET حلاً قويًا لتحقيق ذلك بسلاسة. في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة تعليق توضيحي لتنقيح النص إلى مستندك خطوة بخطوة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Annotation لـ .NET: تأكد من تثبيت GroupDocs.Annotation لمكتبة .NET. يمكنك تنزيله من[موقع إلكتروني](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير باستخدام IDE متوافق مع .NET مثل Visual Studio.

## استيراد مساحات الأسماء
أولاً، لنستورد مساحات الأسماء الضرورية لمشروعنا:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحديد مسار الإخراج
حدد مسار الإخراج حيث تريد حفظ المستند المشروح. تأكد من أنه يمكن الوصول إليه وقابل للكتابة.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
 قم بتهيئة الحواشي باستخدام مسار مستند الإدخال. يستبدل`"input.pdf"` مع المسار إلى المستند الخاص بك.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي لتنقيح النص
 إنشاء`TextRedactionAnnotation`كائن بالخصائص المطلوبة مثل`PageNumber`, `FontColor` ، و`Points`. تخصيص التعليق التوضيحي وفقًا لمتطلباتك.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## الخطوة 4: إضافة تعليق توضيحي وحفظه
أضف التعليق التوضيحي الذي تم إنشاؤه إلى المستند باستخدام المعلق التوضيحي واحفظ المستند المشروح في مسار الإخراج المحدد.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## الخطوة 5: التحقق من الإخراج
وأخيرًا، تأكد من حفظ المستند بنجاح في مسار الإخراج المحدد.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، تناولنا عملية إضافة تعليق توضيحي لتنقيح النص إلى مستند باستخدام GroupDocs.Annotation لـ .NET. من خلال هذه الخطوات، يمكنك الآن إدارة المعلومات الحساسة بشكل آمن داخل مستنداتك.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليق التوضيحي لتنقيح النص؟
نعم، يمكنك تخصيص خصائص مختلفة مثل لون الخط ولون التعبئة والعتامة لتناسب متطلباتك.
### هل هناك نسخة تجريبية متاحة قبل الشراء؟
 نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من[موقع إلكتروني](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم إذا واجهت أي مشاكل؟
 يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).
### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟
 نعم يمكنك الحصول على ترخيص مؤقت من[صفحة الشراء](https://purchase.groupdocs.com/temporary-license/)للاختبار.
### هل يمكنني إضافة تعليقات توضيحية متعددة إلى مستند واحد؟
بالتأكيد، يتيح لك GroupDocs.Annotation إضافة أنواع مختلفة من التعليقات التوضيحية ومثيلات متعددة إلى مستند واحد.