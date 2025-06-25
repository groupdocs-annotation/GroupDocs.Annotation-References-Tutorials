---
"description": "استكشف قوة GroupDocs.Annotation لـ .NET وأضف إمكانيات التعليق التوضيحي على المستندات إلى تطبيقاتك بسهولة."
"linktitle": "إضافة تعليق توضيحي لجزء نص البحث إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي لجزء نص البحث إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# إضافة تعليق توضيحي لجزء نص البحث إلى المستند

## مقدمة
في مجال تطوير .NET، تُعد GroupDocs.Annotation أداةً فعّالة لإضافة تعليقات توضيحية إلى المستندات بسلاسة. سواءً كنت مطورًا محترفًا أو مبتدئًا في عالم .NET، سيشرح لك هذا البرنامج التعليمي الشامل أساسيات استخدام GroupDocs.Annotation لـ .NET، بدءًا من استيراد مساحات الأسماء ووصولًا إلى إتقان تعقيدات إضافة تعليقات توضيحية لأجزاء نص البحث إلى مستنداتك.
## مقدمة
يُمكّن GroupDocs.Annotation for .NET المطورين من دمج إمكانيات التعليق التوضيحي على المستندات في تطبيقاتهم بسهولة. بفضل واجهة برمجة التطبيقات سهلة الاستخدام وميزاتها القوية، يُمكن للمطورين التعليق التوضيحي على مختلف تنسيقات المستندات، بما في ذلك ملفات PDF، ومستندات Microsoft Office، والصور، وغيرها.
## المتطلبات الأساسية
قبل الغوص في GroupDocs.Annotation لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:

## استيراد مساحات الأسماء
أولاً، قم باستيراد المساحات الأساسية اللازمة للوصول إلى فئات وطرق GroupDocs.Annotation في مشروع .NET الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحديد مسار الإخراج
ابدأ بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
بعد ذلك، قم بتهيئة مثيل لـ `Annotator` الفئة من خلال توفير المسار إلى المستند الذي تريد التعليق عليه:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 3: إنشاء شرح توضيحي لجزء من نص البحث
إنشاء `SearchTextFragment` كائن بالخصائص المطلوبة، مثل النص الذي تريد البحث عنه، وحجم الخط، وعائلة الخط، ولون الخط، ولون الخلفية:
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
## الخطوة 4: إضافة التعليقات التوضيحية
أضف شرح النص البحثي الذي تم إنشاؤه إلى المستند باستخدام `Add` طريقة المشرح:
```csharp
annotator.Add(searchText);
```
## الخطوة 5: حفظ المستند الموضح
احفظ المستند الموضح في مسار الإخراج المحدد:
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
أبلغ المستخدم بأن المستند تم حفظه بنجاح:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، يُبسّط GroupDocs.Annotation لـ .NET عملية إضافة التعليقات التوضيحية إلى المستندات، مما يُحسّن التعاون وعمليات مراجعة المستندات. باتباع الخطوات الموضحة في هذا الدليل، يمكنك دمج إمكانيات التعليقات التوضيحية للمستندات بسلاسة في تطبيقات .NET الخاصة بك.
## الأسئلة الشائعة
### هل GroupDocs.Annotation متوافق مع كافة تنسيقات المستندات؟
نعم، يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات، بما في ذلك ملفات PDF، ومستندات Microsoft Office، والصور، والمزيد.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
بالتأكيد! يوفر GroupDocs.Annotation خيارات تخصيص شاملة للتعليقات التوضيحية، مما يسمح لك بتعديل خصائص مثل حجم الخط ولونه ونمطه.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟
نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من GroupDocs.Annotation لاستكشاف ميزاته وقدراته قبل إجراء عملية شراء [هنا](https://releases.groupdocs.com/)..
### أين يمكنني العثور على الدعم لـ GroupDocs.Annotation؟
للحصول على الدعم والمساعدة بشأن GroupDocs.Annotation، يمكنك زيارة GroupDocs [المنتدى](https://forum.groupdocs.com/c/annotation/10) مخصص للاستفسارات والمناقشات المتعلقة بالتعليقات التوضيحية.
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Annotation؟
يمكنك الحصول على ترخيص مؤقت لـ GroupDocs.Annotation من خلال GroupDocs [موقع إلكتروني](https://purchase.groupdocs.com/temporary-license/)، مما يتيح لك تقييم المنتج بالكامل.