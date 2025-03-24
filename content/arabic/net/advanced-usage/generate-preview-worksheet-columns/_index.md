---
title: إنشاء أعمدة ورقة عمل المعاينة
linktitle: إنشاء أعمدة ورقة عمل المعاينة
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. برنامج تعليمي خطوة بخطوة لمطوري .NET. تعزيز التطبيقات الخاصة بك.
weight: 15
url: /ar/net/advanced-usage/generate-preview-worksheet-columns/
---

# إنشاء أعمدة ورقة عمل المعاينة

## مقدمة
مرحبًا بك في برنامجنا التعليمي الشامل حول الاستفادة من إمكانات GroupDocs.Annotation لـ .NET! في هذا الدليل، سنرشدك خلال عملية استخدام هذه الأداة القوية لإضافة تعليقات توضيحية إلى المستندات بشكل فعال. سواء كنت مطورًا متمرسًا أو وافدًا جديدًا إلى عالم تطوير .NET، فإن هذا البرنامج التعليمي سيزودك بالمعرفة والمهارات اللازمة لدمج ميزات التعليقات التوضيحية بسلاسة في تطبيقاتك.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:
### 1. إعداد بيئة تطوير .NET
تأكد من إعداد بيئة تطوير .NET عاملة على جهازك. يمكنك تنزيل أحدث إصدار من .NET SDK من موقع Microsoft على الويب.
### 2. GroupDocs.Annotation لمكتبة .NET
 قم بتنزيل وتثبيت GroupDocs.Annotation لمكتبة .NET من الملف المتوفر[رابط التحميل](https://releases.groupdocs.com/annotation/net/). اتبع تعليمات التثبيت لدمج المكتبة في مشروعك بنجاح.
### 3. مستند الإدخال
قم بإعداد مستند نموذجي (على سبيل المثال، "input.xlsx") الذي تنوي إضافة تعليقات توضيحية إليه باستخدام GroupDocs.Annotation لـ .NET. تأكد من إمكانية الوصول إلى المستند من دليل المشروع الخاص بك.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء الضرورية إلى مشروعك. توفر مساحات الأسماء هذه إمكانية الوصول إلى الفئات والأساليب المطلوبة لأداء مهام التعليقات التوضيحية للمستند بشكل فعال.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

الآن بعد أن قمنا بإعداد بيئة التطوير الخاصة بنا واستوردنا مساحات الأسماء المطلوبة، فلنتعمق في إنشاء أعمدة ورقة عمل المعاينة للمستند الخاص بنا.
## الخطوة 1: تهيئة خيارات المعاينة
```csharp
PreviewOptions previewOptions = new PreviewOptions(
    pageNumber => new FileStream(Path.Combine("Your Document Directory", $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose()
);
```
## الخطوة 2: تحديد أعمدة ورقة العمل
```csharp
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));
```
## الخطوة 3: تهيئة الحواشي مع مستند الإدخال
```csharp
using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
## الخطوة 4: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## خاتمة
تهانينا! لقد تعلمت بنجاح كيفية إنشاء أعمدة ورقة عمل المعاينة باستخدام GroupDocs.Annotation لـ .NET. ومن خلال هذه المعرفة، يمكنك الآن دمج إمكانات التعليقات التوضيحية المتقدمة في تطبيقات .NET الخاصة بك بسهولة.
## الأسئلة الشائعة
### هل يتوافق GroupDocs.Annotation مع أطر عمل .NET الأخرى؟
نعم، يدعم GroupDocs.Annotation أطر عمل .NET المتنوعة، بما في ذلك .NET Core و.NET Framework.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية التي تم إنشاؤها باستخدام GroupDocs.Annotation؟
قطعاً! يوفر GroupDocs.Annotation خيارات تخصيص شاملة لمظهر التعليق التوضيحي، بما في ذلك اللون والعتامة ونوع التعليق التوضيحي.
### هل يدعم GroupDocs.Annotation تنسيقات المستندات بخلاف Excel؟
نعم، يدعم GroupDocs.Annotation نطاقًا واسعًا من تنسيقات المستندات، بما في ذلك PDF وWord وPowerPoint والمزيد.
### هل يتوفر الدعم الفني لمستخدمي GroupDocs.Annotation؟
 نعم، يمكنك الوصول إلى الدعم الفني ومنتديات المجتمع من خلال الخدمة المتوفرة[رابط الدعم](https://forum.groupdocs.com/c/annotation/10).
### هل يمكنني تجربة GroupDocs.Annotation قبل شراء الترخيص؟
 بالطبع! يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Annotation من[موقع إلكتروني](https://releases.groupdocs.com/).