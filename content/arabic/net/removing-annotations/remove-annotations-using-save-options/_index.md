---
"description": "تعرّف على كيفية إزالة التعليقات التوضيحية من ملفات PDF وغيرها من المستندات في .NET باستخدام GroupDocs.Annotation. دليل خطوة بخطوة مع أمثلة برمجية."
"linktitle": "إزالة التعليقات التوضيحية باستخدام خيارات الحفظ في .NET"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إزالة التعليقات التوضيحية باستخدام خيارات الحفظ في .NET"
"url": "/ar/net/removing-annotations/remove-annotations-using-save-options/"
"weight": 14
---

# إزالة التعليقات التوضيحية باستخدام خيارات الحفظ في .NET

## مقدمة

GroupDocs.Annotation لـ .NET أداة فعّالة تُمكّن المطورين من إضافة خاصية التعليقات التوضيحية إلى تطبيقات .NET بسهولة. سواء كنت تعمل على نظام إدارة مستندات، أو منصة تعاون، أو أي تطبيق آخر يتضمن معالجة المستندات، فإن GroupDocs.Annotation يُوفر مجموعة شاملة من الميزات لإضافة التعليقات التوضيحية إلى ملفات PDF وتنسيقات المستندات الأخرى بسلاسة.

## المتطلبات الأساسية

قبل الغوص في عالم التعليق التوضيحي على المستندات باستخدام GroupDocs.Annotation لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:

### 1. تثبيت GroupDocs.Annotation لـ .NET

ابدأ بتنزيل وتثبيت GroupDocs.Annotation لـ .NET. يمكنك تنزيل أحدث إصدار من [صفحة التحميل](https://releases.groupdocs.com/annotation/net/).

## استيراد مساحات الأسماء

لبدء استخدام GroupDocs.Annotation في مشروع .NET الخاص بك، عليك استيراد مساحات الأسماء اللازمة. إليك مساحات الأسماء التي ستستخدمها عادةً:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


الآن، دعنا نستعرض عملية إزالة التعليقات التوضيحية من مستند باستخدام ميزة "خيارات الحفظ" في .NET:

## الخطوة 1: تحديد مسار الإخراج

أولاً، حدد مسار الإخراج الذي سيتم حفظ المستند بعد إزالة التعليقات التوضيحية منه. يمكنك استخدام `Path.Combine` طريقة لدمج مسار الدليل مع اسم ملف الإخراج.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 2: تهيئة المُعلّق

بعد ذلك، قم بتهيئة مثيل لـ `Annotator` الفئة من خلال توفير المسار إلى المستند الذي يحتوي على التعليقات التوضيحية.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // سيتم وضع كود إزالة التعليقات التوضيحية هنا
}
```

## الخطوة 3: حفظ المستند مع إزالة التعليقات التوضيحية

الآن، استخدم `Save` طريقة `Annotator` الصف جنبا إلى جنب مع `SaveOptions` لحفظ المستند مع إزالة التعليقات التوضيحية. في `SaveOptions`، اضبط `AnnotationTypes` الممتلكات إلى `AnnotationType.None` لإزالة كافة التعليقات التوضيحية.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## الخطوة 4: عرض رسالة النجاح

وأخيرًا، اعرض رسالة نجاح تشير إلى أن عملية حفظ المستند قد تم بنجاح مع إزالة التعليقات التوضيحية.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

في الختام، يُبسّط GroupDocs.Annotation لـ .NET عملية إزالة التعليقات التوضيحية من المستندات. باتباع الدليل التفصيلي الموضح أعلاه، يمكن للمطورين دمج وظيفة إزالة التعليقات التوضيحية بسلاسة في تطبيقات .NET الخاصة بهم.

## الأسئلة الشائعة

### س: هل يمكن لـ GroupDocs.Annotation إزالة التعليقات التوضيحية من تنسيقات المستندات الأخرى بالإضافة إلى PDF؟

ج: يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة، بما في ذلك PDF وWord وExcel وPowerPoint، مما يسمح لك بإزالة التعليقات التوضيحية من مجموعة كبيرة من المستندات.

### س: هل من السهل دمج GroupDocs.Annotation في مشاريع .NET الموجودة؟

ج: نعم، يوفر GroupDocs.Annotation واجهة برمجة تطبيقات بسيطة ووثائق شاملة، مما يجعل من السهل على المطورين دمج ميزات التعليقات التوضيحية في تطبيقات .NET الخاصة بهم.

### س: هل يدعم GroupDocs.Annotation الإزالة الانتقائية للتعليقات التوضيحية؟

ج: نعم، يسمح GroupDocs.Annotation للمطورين بتحديد أنواع التعليقات التوضيحية التي يريدون إزالتها، مما يمنحهم المرونة في إدارة التعليقات التوضيحية داخل مستنداتهم.

### س: هل يمكنني تجربة GroupDocs.Annotation مجانًا قبل الشراء؟

ج: نعم، يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Annotation من [صفحة الإصدارات](https://releases.groupdocs.com/) لاستكشاف ميزاته قبل اتخاذ قرار الشراء.

### س: أين يمكنني الحصول على الدعم لـ GroupDocs.Annotation؟

ج: للحصول على المساعدة الفنية ودعم المجتمع، يمكنك زيارة [منتدى GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).