---
title: قم بإزالة التعليقات التوضيحية باستخدام خيارات الحفظ في .NET
linktitle: قم بإزالة التعليقات التوضيحية باستخدام خيارات الحفظ في .NET
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إزالة التعليقات التوضيحية من ملف PDF والمستندات الأخرى في .NET باستخدام GroupDocs.Annotation. دليل خطوة بخطوة مع أمثلة التعليمات البرمجية.
weight: 14
url: /ar/net/removing-annotations/remove-annotations-using-save-options/
---

# قم بإزالة التعليقات التوضيحية باستخدام خيارات الحفظ في .NET

## مقدمة

تعد GroupDocs.Annotation for .NET أداة قوية تسمح للمطورين بإضافة وظيفة التعليقات التوضيحية إلى تطبيقات .NET الخاصة بهم بسهولة. سواء كنت تعمل على نظام إدارة المستندات، أو نظام أساسي للتعاون، أو أي تطبيق آخر يتضمن معالجة المستندات، فإن GroupDocs.Annotation يوفر مجموعة شاملة من الميزات لإضافة تعليقات توضيحية إلى PDF وتنسيقات المستندات الأخرى بسلاسة.

## المتطلبات الأساسية

قبل الغوص في عالم التعليقات التوضيحية للمستندات باستخدام GroupDocs.Annotation for .NET، تأكد من توفر المتطلبات الأساسية التالية:

### 1. قم بتثبيت GroupDocs.Annotation لـ .NET

 ابدأ بتنزيل وتثبيت GroupDocs.Annotation لـ .NET. يمكنك تنزيل أحدث إصدار من[download page](https://releases.groupdocs.com/annotation/net/).

## استيراد مساحات الأسماء

لبدء استخدام GroupDocs.Annotation في مشروع .NET الخاص بك، تحتاج إلى استيراد مساحات الأسماء الضرورية. فيما يلي مساحات الأسماء التي ستستخدمها بشكل شائع:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


الآن، دعونا نستعرض عملية إزالة التعليقات التوضيحية من مستند باستخدام ميزة "خيارات الحفظ" في .NET:

## الخطوة 1: تحديد مسار الإخراج

أولاً، حدد مسار الإخراج حيث سيتم حفظ المستند الذي يحتوي على التعليقات التوضيحية التي تمت إزالتها. يمكنك استخدام ال`Path.Combine` طريقة لدمج مسار الدليل مع اسم ملف الإخراج.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## الخطوة 2: تهيئة الحواشي

 بعد ذلك، قم بتهيئة مثيل لـ`Annotator` فئة عن طريق توفير المسار إلى المستند الذي يحتوي على التعليقات التوضيحية.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // سيتم وضع رمز إزالة التعليقات التوضيحية هنا
}
```

## الخطوة 3: حفظ المستند مع إزالة التعليقات التوضيحية

 الآن، استخدم`Save` طريقة`Annotator` الصف جنبا إلى جنب مع`SaveOptions` لحفظ المستند مع التعليقات التوضيحية التي تمت إزالتها. في ال`SaveOptions` ، تعيين`AnnotationTypes` الملكية ل`AnnotationType.None` لإزالة كافة التعليقات التوضيحية.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## الخطوة 4: عرض رسالة النجاح

وأخيرًا، قم بعرض رسالة نجاح تشير إلى أنه تم حفظ المستند بنجاح مع إزالة التعليقات التوضيحية.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة

في الختام، GroupDocs.Annotation for .NET يبسط عملية إزالة التعليقات التوضيحية من المستندات. باتباع الدليل الموضح أعلاه خطوة بخطوة، يمكن للمطورين دمج وظيفة إزالة التعليقات التوضيحية بسلاسة في تطبيقات .NET الخاصة بهم.

## الأسئلة الشائعة

### س: هل يمكن لـ GroupDocs.Annotation إزالة التعليقات التوضيحية من تنسيقات المستندات الأخرى إلى جانب PDF؟

ج: يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة، بما في ذلك PDF وWord وExcel وPowerPoint، مما يسمح لك بإزالة التعليقات التوضيحية من مجموعة واسعة من المستندات.

### س: هل من السهل دمج GroupDocs.Annotation في مشاريع .NET الحالية؟

ج: نعم، يوفر GroupDocs.Annotation واجهة برمجة تطبيقات بسيطة ووثائق شاملة، مما يسهل على المطورين دمج ميزات التعليقات التوضيحية في تطبيقات .NET الخاصة بهم.

### س: هل يدعم GroupDocs.Annotation الإزالة الانتقائية للتعليقات التوضيحية؟

ج: نعم، يسمح GroupDocs.Annotation للمطورين بتحديد أنواع التعليقات التوضيحية المراد إزالتها، مما يمنحهم المرونة في إدارة التعليقات التوضيحية داخل مستنداتهم.

### س: هل يمكنني تجربة GroupDocs.Annotation مجانًا قبل الشراء؟

 ج: نعم، يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Annotation من[صفحة الإصدارات](https://releases.groupdocs.com/) لاستكشاف ميزاته قبل اتخاذ قرار الشراء.

### س: أين يمكنني الحصول على دعم لـ GroupDocs.Annotation؟

 ج: للحصول على المساعدة الفنية والدعم المجتمعي، يمكنك زيارة[GroupDocs. منتدى التعليقات التوضيحية](https://forum.groupdocs.com/c/annotation/10).