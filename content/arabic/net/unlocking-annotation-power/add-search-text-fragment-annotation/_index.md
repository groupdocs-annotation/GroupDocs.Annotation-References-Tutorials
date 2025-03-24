---
title: إضافة تعليق توضيحي لجزء نص البحث إلى المستند
linktitle: إضافة تعليق توضيحي لجزء نص البحث إلى المستند
second_title: GroupDocs.Annotation .NET API
description: اكتشف قوة GroupDocs.Annotation لـ .NET وأضف إمكانات التعليقات التوضيحية للمستندات بسهولة إلى تطبيقاتك.
weight: 20
url: /ar/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# إضافة تعليق توضيحي لجزء نص البحث إلى المستند

## مقدمة
في مجال تطوير .NET، تبرز GroupDocs.Annotation كأداة قوية لإضافة تعليقات توضيحية إلى المستندات بسلاسة. سواء كنت مطورًا متمرسًا أو مجرد دخول إلى عالم .NET، فإن هذا البرنامج التعليمي الشامل سيرشدك عبر أساسيات استخدام GroupDocs.Annotation لـ .NET، بدءًا من استيراد مساحات الأسماء وحتى إتقان تعقيدات إضافة التعليقات التوضيحية لأجزاء نص البحث إلى موقعك. وثائق.
## مقدمة
يعمل GroupDocs.Annotation for .NET على تمكين المطورين من دمج إمكانات التعليقات التوضيحية للمستندات في تطبيقاتهم دون عناء. بفضل واجهة برمجة التطبيقات البديهية والميزات القوية، يمكن للمطورين إضافة تعليقات توضيحية إلى تنسيقات المستندات المختلفة، بما في ذلك ملفات PDF ومستندات Microsoft Office والصور والمزيد.
## المتطلبات الأساسية
قبل الغوص في GroupDocs.Annotation لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:

## استيراد مساحات الأسماء
أولاً، قم باستيراد مساحات الأسماء الضرورية للوصول إلى فئات GroupDocs.Annotation وأساليبه في مشروع .NET الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحديد مسار الإخراج
ابدأ بتحديد مسار الإخراج حيث سيتم حفظ المستند المشروح:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
 بعد ذلك، قم بتهيئة مثيل لـ`Annotator` فئة عن طريق توفير المسار إلى المستند الذي تريد التعليق عليه:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 3: إنشاء تعليق توضيحي لجزء نص البحث
 إنشاء`SearchTextFragment` كائن بالخصائص المطلوبة، مثل النص المطلوب البحث عنه وحجم الخط وعائلة الخط ولون الخط ولون الخلفية:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## الخطوة 4: إضافة تعليق توضيحي
 أضف التعليق التوضيحي لجزء نص البحث الذي تم إنشاؤه إلى المستند باستخدام الملف`Add` طريقة الحواشي :
```csharp
annotator.Add(searchText);
```
## الخطوة 5: حفظ المستند المشروح
احفظ المستند المشروح في مسار الإخراج المحدد:
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
أبلغ المستخدم بأنه تم حفظ المستند بنجاح:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، يعمل GroupDocs.Annotation for .NET على تبسيط عملية إضافة التعليقات التوضيحية إلى المستندات، وتعزيز عمليات التعاون ومراجعة المستندات. باتباع الخطوات الموضحة في هذا الدليل، يمكنك دمج إمكانيات التعليقات التوضيحية للمستند بسلاسة في تطبيقات .NET الخاصة بك.
## الأسئلة الشائعة
### هل GroupDocs.Annotation متوافق مع جميع تنسيقات المستندات؟
نعم، يدعم GroupDocs.Annotation نطاقًا واسعًا من تنسيقات المستندات، بما في ذلك ملفات PDF ومستندات Microsoft Office والصور والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
قطعاً! يوفر GroupDocs.Annotation خيارات تخصيص واسعة النطاق للتعليقات التوضيحية، مما يسمح لك بضبط الخصائص مثل حجم الخط واللون والنمط.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟
 نعم، يمكنك الوصول إلى الإصدار التجريبي المجاني من GroupDocs.Annotation لاستكشاف ميزاته وإمكانياته قبل إجراء عملية شراء[هنا](https://releases.groupdocs.com/)..
### أين يمكنني العثور على دعم لـ GroupDocs.Annotation؟
 للحصول على الدعم والمساعدة فيما يتعلق بـ GroupDocs.Annotation، يمكنك زيارة GroupDocs[المنتدى](https://forum.groupdocs.com/c/annotation/10) مخصص للاستفسارات والمناقشات المتعلقة بالتعليقات التوضيحية.
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Annotation؟
 يمكنك الحصول على ترخيص مؤقت لـ GroupDocs.Annotation من خلال GroupDocs[موقع إلكتروني](https://purchase.groupdocs.com/temporary-license/)مما يتيح لك تقييم المنتج بشكل كامل.