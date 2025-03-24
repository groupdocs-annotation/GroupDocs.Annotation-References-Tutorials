---
title: أضف تعليقًا توضيحيًا للعلامة المائية إلى المستند
linktitle: أضف تعليقًا توضيحيًا للعلامة المائية إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية للعلامة المائية إلى مستنداتك بسهولة باستخدام GroupDocs.Annotation for .NET. تعزيز وضوح الوثيقة والأمن.
weight: 28
url: /ar/net/unlocking-annotation-power/add-watermark-annotation/
---

# أضف تعليقًا توضيحيًا للعلامة المائية إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية إضافة تعليق توضيحي للعلامة المائية إلى مستند باستخدام GroupDocs.Annotation لـ .NET. تعتبر التعليقات التوضيحية للعلامة المائية مفيدة للإشارة إلى حالة المستند، أو وضع علامة عليها على أنها سرية، أو إضافة أي معلومات أخرى ذات صلة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  GroupDocs.Annotation لـ .NET: يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: تأكد من تثبيت Visual Studio على نظامك.
3. المعرفة الأساسية بـ C#: الإلمام بلغة البرمجة C# ضروري لفهم أمثلة التعليمات البرمجية وتنفيذها.

## استيراد مساحات الأسماء

قبل أن نبدأ البرمجة، دعونا نستورد مساحات الأسماء الضرورية:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

الآن، دعنا نقسم عملية إضافة تعليق توضيحي للعلامة المائية إلى خطوات متعددة:

## الخطوة 1: تحديد مسار الإخراج

 أولاً، نحتاج إلى تحديد مسار الإخراج حيث سيتم حفظ المستند المشروح. سوف نستخدم`Path` فئة من`System.IO` مساحة الاسم لدمج مسار دليل الإخراج مع اسم الملف.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 2: تهيئة الحواشي

بعد ذلك، سنقوم بتهيئة الحواشي من خلال توفير مسار مستند الإدخال. سيسمح لنا ذلك بإضافة تعليقات توضيحية إلى المستند.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```

## الخطوة 3: إنشاء تعليق توضيحي للعلامة المائية

الآن، لنقم بإنشاء كائن تعليق توضيحي للعلامة المائية بالخصائص المطلوبة مثل الزاوية والموضع والنص ولون الخط والعتامة وما إلى ذلك.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## الخطوة 4: إضافة تعليق توضيحي للعلامة المائية

 الآن، سنقوم بإضافة تعليق توضيحي للعلامة المائية إلى المستند باستخدام الملف`Add` طريقة كائن الحواشي.

```csharp
annotator.Add(watermark);
```

## الخطوة 5: حفظ المستند

وأخيرًا، سنقوم بحفظ المستند المشروح في مسار الإخراج المحدد.

```csharp
annotator.Save(outputPath);
```

## خاتمة

في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي للعلامة المائية إلى مستند باستخدام GroupDocs.Annotation لـ .NET. تعد التعليقات التوضيحية للعلامة المائية أداة قيمة لوضع علامة على المستندات بالمعلومات ذات الصلة أو الإشارة إلى حالتها.

## الأسئلة الشائعة

### س: هل يمكنني تخصيص مظهر التعليق التوضيحي للعلامة المائية؟

ج: نعم، يمكنك تخصيص خصائص مختلفة مثل النص وحجم الخط واللون والعتامة والموضع وما إلى ذلك، لتخصيص العلامة المائية وفقًا لمتطلباتك.

### س: هل يتوافق GroupDocs.Annotation لـ .NET مع تنسيقات المستندات المختلفة؟

ج: نعم، يدعم GroupDocs.Annotation نطاقًا واسعًا من تنسيقات المستندات بما في ذلك تنسيقات PDF وMicrosoft Word وExcel وPowerPoint وتنسيقات الصور.

### س: هل يمكنني إضافة تعليقات توضيحية متعددة إلى مستند واحد؟

ج: بالتأكيد، يتيح لك GroupDocs.Annotation إضافة تعليقات توضيحية متعددة من أنواع مختلفة إلى مستند واحد، مما يتيح لك وضع علامات شاملة على المستند.

### س: هل يوفر GroupDocs.Annotation الدعم للتعليق التوضيحي التعاوني؟

ج: نعم، يعمل GroupDocs.Annotation على تسهيل التعليقات التوضيحية التعاونية من خلال السماح للمستخدمين بإضافة التعليقات والردود والتعليقات التوضيحية، مما يعزز التعاون الفعال بين أعضاء الفريق.

### س: هل هناك إصدار تجريبي متاح لـ GroupDocs.Annotation لـ .NET؟

 ج: نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).