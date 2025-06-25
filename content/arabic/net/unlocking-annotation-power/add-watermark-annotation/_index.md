---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية للعلامات المائية إلى مستنداتك بسهولة باستخدام GroupDocs.Annotation لـ .NET. حسّن وضوح مستنداتك وأمانها."
"linktitle": "إضافة تعليق العلامة المائية إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق العلامة المائية إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# إضافة تعليق العلامة المائية إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنشرح عملية إضافة تعليق علامة مائية إلى مستند باستخدام GroupDocs.Annotation لـ .NET. تُفيد تعليقات العلامة المائية في تحديد حالة المستند، أو تصنيفه على أنه سري، أو إضافة أي معلومات أخرى ذات صلة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. GroupDocs.Annotation لـ .NET: يمكنك تنزيله من [هنا](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: تأكد من تثبيت Visual Studio على نظامك.
3. المعرفة الأساسية بلغة البرمجة C#: المعرفة بلغة البرمجة C# ضرورية لفهم أمثلة التعليمات البرمجية وتنفيذها.

## استيراد مساحات الأسماء

قبل أن نبدأ في الترميز، دعنا نستورد مساحات الأسماء الضرورية:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

الآن، دعونا نقسم عملية إضافة تعليق العلامة المائية إلى عدة خطوات:

## الخطوة 1: تحديد مسار الإخراج

أولاً، علينا تحديد مسار الإخراج الذي سيتم حفظ المستند المُعلّق عليه. سنستخدم `Path` الصف من `System.IO` مساحة اسم لدمج مسار دليل الإخراج مع اسم الملف.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 2: تهيئة المُعلّق

بعد ذلك، سنُهيئ المُعلّق بتوفير مسار مستند الإدخال. سيُتيح لنا هذا إضافة تعليقات توضيحية إلى المستند.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```

## الخطوة 3: إنشاء تعليق العلامة المائية

الآن، دعنا نقوم بإنشاء كائن تعليق العلامة المائية بالخصائص المطلوبة مثل الزاوية والموضع والنص ولون الخط والتعتيم وما إلى ذلك.

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

## الخطوة 4: إضافة تعليق العلامة المائية

الآن، سنضيف تعليق العلامة المائية إلى المستند باستخدام `Add` طريقة كائن المشرح.

```csharp
annotator.Add(watermark);
```

## الخطوة 5: حفظ المستند

وأخيرًا، سنقوم بحفظ المستند الموضح في مسار الإخراج المحدد.

```csharp
annotator.Save(outputPath);
```

## خاتمة

في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليق توضيحي للعلامة المائية إلى مستند باستخدام GroupDocs.Annotation لـ .NET. تُعد تعليقات العلامة المائية أداة قيّمة لتمييز المستندات بالمعلومات ذات الصلة أو للإشارة إلى حالتها.

## الأسئلة الشائعة

### س: هل يمكنني تخصيص مظهر تعليق العلامة المائية؟

ج: نعم، يمكنك تخصيص خصائص مختلفة مثل النص وحجم الخط واللون والتعتيم والموضع وما إلى ذلك، لتخصيص العلامة المائية وفقًا لمتطلباتك.

### س: هل GroupDocs.Annotation لـ .NET متوافق مع تنسيقات المستندات المختلفة؟

ج: نعم، يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك تنسيقات PDF وMicrosoft Word وExcel وPowerPoint والصور.

### س: هل يمكنني إضافة تعليقات متعددة إلى مستند واحد؟

ج: بالتأكيد، يتيح لك GroupDocs.Annotation إضافة تعليقات توضيحية متعددة من أنواع مختلفة إلى مستند واحد، مما يتيح وضع علامات شاملة على المستند.

### س: هل يوفر GroupDocs.Annotation الدعم للتعليق التوضيحي التعاوني؟

ج: نعم، يسهل GroupDocs.Annotation عملية التعليق التوضيحي التعاوني من خلال السماح للمستخدمين بإضافة التعليقات والردود والتعليقات التوضيحية، مما يعزز التعاون الفعال بين أعضاء الفريق.

### س: هل هناك نسخة تجريبية متاحة لـ GroupDocs.Annotation لـ .NET؟

ج: نعم، يمكنك تنزيل نسخة تجريبية مجانية من [هنا](https://releases.groupdocs.com/).