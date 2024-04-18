---
title: تحميل الخطوط المخصصة
linktitle: تحميل الخطوط المخصصة
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية تحميل الخطوط المخصصة بسلاسة في GroupDocs.Annotation لـ .NET لتحسين التعليقات التوضيحية للمستند. اتبع خطوة بخطوة لسهولة التكامل.
type: docs
weight: 20
url: /ar/net/advanced-usage/loading-custom-fonts/
---
## مقدمة
تعد GroupDocs.Annotation for .NET مكتبة قوية تمكن المطورين من إضافة ميزات التعليقات التوضيحية إلى تطبيقات .NET الخاصة بهم دون عناء. إحدى الوظائف الرئيسية التي تقدمها هي القدرة على تحميل الخطوط المخصصة، مما يسمح بتخصيص محسن ومرونة في التعليقات التوضيحية للمستند.
## المتطلبات الأساسية
قبل متابعة البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1.  GroupDocs.Annotation لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة تطوير .NET: تأكد من أن لديك بيئة عمل معدة لتطوير .NET.
3. الوصول إلى الخطوط المخصصة: قم بإعداد الخطوط المخصصة التي تريد تحميلها في التطبيق الخاص بك.

## استيراد مساحات الأسماء
في مشروع .NET الخاص بك، قم باستيراد مساحات الأسماء اللازمة لاستخدام GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: إنشاء كائن الحواشي
 إنشاء مثيل لـ`Annotator` فئة من خلال توفير المسار إلى مستند PDF المدخل مع أدلة الخطوط المخصصة:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // سيتم وضع الرمز الخاص بك لمزيد من العمليات هنا
}
```
## الخطوة 2: تكوين خيارات المعاينة
حدد خيارات المعاينة لتحديد كيفية إنشاء معاينات المستند. يمكنك ضبط خيارات مثل تنسيق المعاينة، وأرقام الصفحات، وما إلى ذلك:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## الخطوة 3: إنشاء معاينات المستندات
 الاستفادة من`GeneratePreview` طريقة`Document` خاصية إنشاء معاينات بخطوط مخصصة:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## الخطوة 4: عرض مسار الإخراج
أخيرًا، قم بعرض رسالة تشير إلى نجاح إنشاء معاينات المستند مع مسار دليل الإخراج:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## خاتمة
في الختام، فإن تحميل الخطوط المخصصة في GroupDocs.Annotation لـ .NET يوفر للمطورين المرونة اللازمة لتخصيص التعليقات التوضيحية للمستندات وفقًا لمتطلباتهم. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك دمج الخطوط المخصصة بسلاسة في تطبيقات .NET الخاصة بك وتحسين تجربة التعليقات التوضيحية للمستخدمين.
## الأسئلة الشائعة
### هل يمكنني تحميل خطوط مخصصة متعددة في وقت واحد؟
 نعم، يمكنك تحديد أدلة خطوط متعددة عند إنشاء مثيل لـ`Annotator` هدف.
### هل هناك أي قيود على أنواع الخطوط المدعومة؟
يدعم GroupDocs.Annotation for .NET نطاقًا واسعًا من أنواع الخطوط، بما في ذلك خطوط TrueType (.ttf) وOpenType (.otf).
### هل يمكنني تغيير الخطوط المحملة ديناميكيًا أثناء وقت التشغيل؟
نعم، يمكنك تعديل أدلة الخطوط ديناميكيًا وإعادة تحميل التعليقات التوضيحية للمستند حسب الحاجة.
### هل يدعم GroupDocs.Annotation تضمين الخط في مستندات الإخراج؟
نعم، يمكنك تضمين خطوط مخصصة في المستندات الناتجة لضمان العرض المتسق عبر الأنظمة الأساسية المختلفة.
### هل هناك طريقة للتعامل مع ترخيص الخطوط داخل التطبيق؟
يوفر GroupDocs.Annotation خيارات لإدارة ترخيص الخطوط، بما في ذلك التراخيص المؤقتة لأغراض التقييم.