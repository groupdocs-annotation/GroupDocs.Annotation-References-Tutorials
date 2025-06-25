---
"description": "تعلّم كيفية إضافة تعليقات نصية متعرجة إلى المستندات بسهولة باستخدام Groupdocs.Annotation لـ .NET. حسّن التعاون وعمليات مراجعة المستندات."
"linktitle": "إضافة تعليق نصي متعرج إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق نصي متعرج إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# إضافة تعليق نصي متعرج إلى المستند

## مقدمة

Groupdocs.Annotation لـ .NET هي مكتبة متعددة الاستخدامات تُمكّن المطورين من دمج إمكانيات التعليق التوضيحي الفعّالة في تطبيقات .NET الخاصة بهم بسهولة. سواء كنت تعمل على ملفات PDF أو مستندات Word أو غيرها من تنسيقات الملفات الشائعة، تُوفر Groupdocs.Annotation حلاً سلسًا للتعليق التوضيحي وتعزيز التعاون في المستندات.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:

## استيراد مساحات الأسماء

تأكد من استيراد المساحات الأساسية اللازمة للوصول إلى الوظائف التي توفرها Groupdocs.Annotation لـ .NET.

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

قم بتحديد المسار الذي سيتم حفظ المستند الموضح فيه.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 2: تهيئة المُعلّق

قم بتهيئة كائن المعلق من خلال توفير مسار المستند الإدخالي.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // رمز التعليق يذهب هنا
}
```

## الخطوة 3: إنشاء تعليق متعرج

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

## الخطوة 4: إضافة التعليقات التوضيحية

أضف التعليقات التوضيحية المتعرجة التي تم إنشاؤها إلى المستند.

```csharp
annotator.Add(squiggly);
```

## الخطوة 5: حفظ المستند

احفظ المستند الموضح في مسار الإخراج المحدد.

```csharp
annotator.Save(outputPath);
```

## الخطوة 6: عرض التأكيد

عرض رسالة تؤكد نجاح حفظ المستند الموضح.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

في الختام، يوفر Groupdocs.Annotation for .NET للمطورين مجموعة أدوات فعّالة لدمج وظائف التعليقات التوضيحية للمستندات بسلاسة في تطبيقات .NET الخاصة بهم. باتباع هذا الدليل المفصل، يمكنك بسهولة إضافة تعليقات توضيحية نصية متعرجة إلى مستنداتك، مما يُحسّن التعاون وعمليات مراجعة المستندات.

## الأسئلة الشائعة

### س: هل يمكن لـ Groupdocs.Annotation دعم التعليقات التوضيحية على تنسيقات الملفات المختلفة؟

ج: نعم، يدعم Groupdocs.Annotation التعليق التوضيحي على مجموعة واسعة من تنسيقات الملفات، بما في ذلك ملفات PDF، ومستندات Word، وجداول بيانات Excel، والمزيد.

### س: هل Groupdocs.Annotation متوافق مع كل من تطبيقات سطح المكتب والويب؟

ج: بالتأكيد! يُمكن دمج Groupdocs.Annotation بسلاسة في تطبيقات سطح المكتب والويب، مما يوفر مرونةً وتنوعًا.

### س: هل هناك أي خيارات ترخيص متاحة لـ Groupdocs.Annotation؟

ج: نعم، يوفر Groupdocs.Annotation خيارات ترخيص مرنة مصممة لتناسب احتياجات الأفراد أو المؤسسات، بما في ذلك التراخيص المؤقتة لأغراض التجربة.

### س: هل يمكن تخصيص التعليقات التوضيحية التي تم إنشاؤها باستخدام Groupdocs.Annotation؟

ج: بالتأكيد! يوفر Groupdocs.Annotation خيارات تخصيص شاملة للشروح، مما يسمح للمطورين بتخصيص الشروح وفقًا لاحتياجاتهم الخاصة.

### س: هل يوفر Groupdocs.Annotation الدعم والتوثيق للمطورين؟

ج: بالتأكيد! يوفر Groupdocs.Annotation توثيقًا شاملًا ومنتديات دعم مخصصة لمساعدة المطورين على استخدام ميزاته بفعالية.