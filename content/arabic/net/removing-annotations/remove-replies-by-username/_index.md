---
title: إزالة الردود حسب اسم المستخدم في .NET
linktitle: إزالة الردود حسب اسم المستخدم في .NET
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية للمستندات بسلاسة باستخدام Groupdocs.Annotation لـ .NET. عزز التعاون وإدارة المستندات باستخدام هذه الأداة القوية.
weight: 17
url: /ar/net/removing-annotations/remove-replies-by-username/
---
## مقدمة
تعد Groupdocs.Annotation for .NET أداة قوية لإضافة تعليقات توضيحية للمستندات بسلاسة داخل تطبيقات .NET الخاصة بك. سواء كنت تعمل مع ملفات PDF أو مستندات Word أو أي تنسيق ملف آخر مدعوم، تعمل هذه المكتبة على تبسيط عملية إضافة التعليقات التوضيحية والإبرازات والتعليقات، مما يعزز إمكانات التعاون وإدارة المستندات.
## المتطلبات الأساسية
قبل الغوص في عالم التعليقات التوضيحية للمستندات باستخدام Groupdocs.Annotation for .NET، تأكد من توفر المتطلبات الأساسية التالية:
1.  تثبيت Groupdocs.Annotation لـ .NET: ابدأ بتنزيل وتثبيت مكتبة Groupdocs.Annotation لـ .NET. يمكنك الحصول على المكتبة من[رابط التحميل](https://releases.groupdocs.com/annotation/net/).
2. فهم .NET Framework: تعد الكفاءة في برمجة .NET أمرًا ضروريًا للاستفادة من إمكانات Groupdocs.Annotation بشكل فعال.
3. مستند للتعليق عليه: قم بإعداد المستند الذي تنوي التعليق عليه. يمكن أن يكون هذا مستند PDF أو Word أو أي تنسيق ملف آخر مدعوم.
4. المعرفة الأساسية بـ C#: تعرف على لغة البرمجة C#، حيث يتم استخدام Groupdocs.Annotation for .NET بشكل أساسي ضمن تطبيقات C#.

## استيراد مساحات الأسماء
للبدء في إضافة تعليقات توضيحية إلى المستندات باستخدام Groupdocs.Annotation لـ .NET، قم باستيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;
```
## الخطوة 1: تحديد مسار الإخراج
 ابدأ بتحديد مسار الإخراج حيث سيتم حفظ المستند المشروح. يمكنك استخدام ال`Path.Combine` طريقة الجمع بين مسارات الدليل:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تحميل المستند المشروح
 قم بتحميل المستند الذي يحتوي على التعليقات التوضيحية مع الردود باستخدام الملف`Annotator` فصل:
```csharp
using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
```
## الخطوة 3: الحصول على التعليقات التوضيحية
استرداد مجموعة التعليقات التوضيحية من المستند الذي تم تحميله:
```csharp
List<AnnotationBase> annotations = annotator.Get();
```
## الخطوة 4: إزالة الردود
قم بإزالة كافة الردود التي يتطابق فيها اسم المؤلف مع اسم المستخدم المحدد. في هذا المثال، ستتم إزالة الردود التي كتبها "توم":
```csharp
annotations[0].Replies.RemoveAll(x => x.User.Name == "Tom");
```
## الخطوة 5: حفظ التغييرات
احفظ التعليقات التوضيحية المحدثة مرة أخرى في المستند وحدد مسار الإخراج:
```csharp
annotator.Update(annotations);
annotator.Save(outputPath);
```
## الخطوة 6: عرض التأكيد
أخيرًا، أبلغ المستخدم بأن المستند قد تم حفظه بنجاح وقم بتوفير المسار إلى ملف الإخراج:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## خاتمة
يقدم Groupdocs.Annotation for .NET حلاً مباشرًا وفعالاً لإضافة تعليقات توضيحية إلى المستندات داخل تطبيقات .NET الخاصة بك. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك دمج إمكانيات التعليقات التوضيحية للمستندات في مشاريعك بسلاسة، مما يعزز التعاون وإدارة المستندات.
## الأسئلة الشائعة
### هل Groupdocs.Annotation متوافق مع جميع تنسيقات المستندات؟
يدعم Groupdocs.Annotation مجموعة واسعة من تنسيقات المستندات، بما في ذلك PDF وWord وExcel وPowerPoint والمزيد. راجع الوثائق للحصول على قائمة كاملة بالتنسيقات المدعومة.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يوفر Groupdocs.Annotation خيارات شاملة لتخصيص مظهر التعليقات التوضيحية، بما في ذلك اللون والحجم والخط والنمط.
### هل Groupdocs.Annotation مناسب لتطبيقات الويب؟
قطعاً! يمكن دمج Groupdocs.Annotation بسلاسة في تطبيقات الويب التي تم تطويرها باستخدام ASP.NET أو ASP.NET Core.
### هل يدعم Groupdocs.Annotation التعليقات التوضيحية التعاونية؟
نعم، يعمل Groupdocs.Annotation على تسهيل التعليقات التوضيحية التعاونية، مما يسمح لعدة مستخدمين بإضافة التعليقات والإبرازات والتعليقات التوضيحية إلى نفس المستند بشكل متزامن.
### هل هناك نسخة تجريبية متاحة للاختبار؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية من Groupdocs.Annotation من موقع الويب لاستكشاف ميزاته وإمكانياته.