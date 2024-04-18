---
title: إضافة تعليق توضيحي للمنطقة إلى المستند
linktitle: إضافة تعليق توضيحي للمنطقة إلى المستند
second_title: GroupDocs.Annotation .NET API
description: قم بتحسين التعاون في المستندات باستخدام Groupdocs.Annotation لـ .NET. تعرف على كيفية إضافة التعليقات التوضيحية للمنطقة خطوة بخطوة.
type: docs
weight: 10
url: /ar/net/unlocking-annotation-power/add-area-annotation/
---
## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة التعليقات التوضيحية للمنطقة إلى المستندات باستخدام Groupdocs.Annotation for .NET. تعد التعليقات التوضيحية للمنطقة ميزة قيمة تسمح للمستخدمين بتسليط الضوء على مناطق معينة من المستند، مما يوفر الوضوح والسياق للمحتوى.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  Groupdocs.Annotation for .NET: تأكد من تثبيت المكتبات والتبعيات الضرورية. يمكنك تنزيلها من[موقع إلكتروني](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تمتع ببيئة تطوير مناسبة تم إعدادها لتطوير .NET.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء المطلوبة إلى مشروعك. تحتوي مساحات الأسماء هذه على الفئات والأساليب اللازمة للعمل مع التعليقات التوضيحية.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## الخطوة 1: تهيئة مسار الإخراج
حدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
 إنشاء مثيل لـ`Annotator` class عن طريق تمرير مسار المستند كمعلمة.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي للمنطقة
حدد خصائص التعليق التوضيحي للمنطقة، مثل لون الخلفية، والموضع، والرسالة، والعتامة، وما إلى ذلك.
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
 أضف التعليق التوضيحي للمنطقة إلى المستند باستخدام`Add` طريقة`Annotator` مثال.
```csharp
annotator.Add(area);
```
## الخطوة 5: حفظ المستند
احفظ المستند المشروح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
أبلغ المستخدم أنه تم وضع تعليقات توضيحية على المستند وحفظه بنجاح.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة التعليقات التوضيحية للمنطقة إلى المستندات باستخدام Groupdocs.Annotation لـ .NET. باتباع الدليل المفصّل خطوة بخطوة، يمكنك بسهولة تحسين مستنداتك من خلال التعليقات التوضيحية القيمة، مما يؤدي إلى تحسين التعاون والفهم.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليق التوضيحي للمنطقة؟
نعم، يمكنك تخصيص جوانب مختلفة مثل لون الخلفية، والتعتيم، ونمط القلم، وما إلى ذلك، لتناسب تفضيلاتك.
### هل Groupdocs.Annotation متوافق مع تنسيقات المستندات الأخرى؟
نعم، يدعم Groupdocs.Annotation تنسيقات المستندات المختلفة بما في ذلك PDF وDOCX وPPTX والمزيد.
### هل يمكنني إضافة تعليقات توضيحية متعددة لنفس المستند؟
بالتأكيد، يمكنك إضافة تعليقات توضيحية متعددة من أنواع مختلفة إلى نفس المستند حسب الحاجة.
### هل يوفر Groupdocs.Annotation التوافق بين الأنظمة الأساسية؟
نعم، Groupdocs.Annotation متوافق مع .NET Framework، مما يجعله مناسبًا لبيئات تطوير Windows وLinux وmacOS.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
 نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من[موقع إلكتروني](https://releases.groupdocs.com/).