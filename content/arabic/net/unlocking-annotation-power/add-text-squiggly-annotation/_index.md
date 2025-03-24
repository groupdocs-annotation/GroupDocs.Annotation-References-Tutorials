---
title: أضف تعليقًا توضيحيًا نصيًا متعرجًا إلى المستند
linktitle: أضف تعليقًا توضيحيًا نصيًا متعرجًا إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة التعليقات التوضيحية النصية المتعرجة إلى المستندات بسهولة باستخدام Groupdocs.Annotation for .NET. تعزيز عمليات التعاون ومراجعة المستندات.
weight: 25
url: /ar/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## مقدمة

تعد Groupdocs.Annotation for .NET مكتبة متعددة الاستخدامات تمكن المطورين من دمج إمكانات التعليقات التوضيحية القوية في تطبيقات .NET الخاصة بهم دون عناء. سواء كنت تعمل مع ملفات PDF أو مستندات Word أو تنسيقات الملفات الشائعة الأخرى، يوفر Groupdocs.Annotation حلاً سلسًا للتعليق على المستندات وتحسين التعاون فيها.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:

## استيراد مساحات الأسماء

تأكد من استيراد مساحات الأسماء الضرورية للوصول إلى الوظائف التي يوفرها Groupdocs.Annotation لـ .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن بعد أن قمنا بتغطية المتطلبات الأساسية، دعنا نقسم عملية إضافة التعليقات التوضيحية النصية المتعرجة إلى خطوات متعددة.

## الخطوة 1: تحديد مسار الإخراج

حدد المسار الذي سيتم حفظ المستند المشروح فيه.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 2: تهيئة الحواشي

قم بتهيئة كائن Annotator من خلال توفير مسار مستند الإدخال.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // رمز التعليق التوضيحي يذهب هنا
}
```

## الخطوة 3: إنشاء تعليق توضيحي متعرج

قم بإنشاء كائن SquigglyAnnotation وحدد خصائصه.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

أضف التعليق التوضيحي المتعرج الذي تم إنشاؤه إلى المستند.

```csharp
annotator.Add(squiggly);
```

## الخطوة 5: حفظ المستند

احفظ المستند المشروح في مسار الإخراج المحدد.

```csharp
annotator.Save(outputPath);
```

## الخطوة 6: عرض التأكيد

عرض رسالة تؤكد نجاح حفظ المستند المشروح.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

في الختام، يوفر Groupdocs.Annotation for .NET للمطورين مجموعة قوية من الأدوات لدمج وظائف التعليقات التوضيحية للمستندات في تطبيقات .NET الخاصة بهم بسلاسة. باتباع هذا الدليل المفصّل خطوة بخطوة، يمكنك بسهولة إضافة تعليقات نصية متعرجة إلى مستنداتك، مما يعزز التعاون وعمليات مراجعة المستندات.

## الأسئلة الشائعة

### س: هل يمكن لـ Groupdocs.Annotation دعم التعليقات التوضيحية على تنسيقات الملفات المختلفة؟

ج: نعم، يدعم Groupdocs.Annotation التعليقات التوضيحية على نطاق واسع من تنسيقات الملفات، بما في ذلك ملفات PDF ومستندات Word وأوراق Excel والمزيد.

### س: هل Groupdocs.Annotation متوافق مع كل من تطبيقات سطح المكتب والويب؟

ج: بالتأكيد! يمكن دمج Groupdocs.Annotation بسلاسة في كل من تطبيقات سطح المكتب والويب، مما يوفر المرونة والتنوع.

### س: هل هناك أي خيارات ترخيص متاحة لـ Groupdocs.Annotation؟

ج: نعم، يوفر Groupdocs.Annotation خيارات ترخيص مرنة مصممة لتناسب احتياجات الأفراد أو المؤسسات، بما في ذلك التراخيص المؤقتة للأغراض التجريبية.

### س: هل يمكن تخصيص التعليقات التوضيحية التي تم إنشاؤها باستخدام Groupdocs.Annotation؟

ج: بالتأكيد! يوفر Groupdocs.Annotation خيارات تخصيص واسعة النطاق للتعليقات التوضيحية، مما يسمح للمطورين بتخصيص التعليقات التوضيحية وفقًا لمتطلباتهم المحددة.

### س: هل يقدم Groupdocs.Annotation الدعم والوثائق للمطورين؟

ج: بالفعل! يوفر Groupdocs.Annotation وثائق شاملة ومنتديات دعم مخصصة لمساعدة المطورين في استخدام ميزاته بفعالية.