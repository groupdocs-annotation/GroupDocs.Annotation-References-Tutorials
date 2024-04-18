---
title: إزالة التعليقات التوضيحية المتعددة بواسطة المعرفات
linktitle: إزالة التعليقات التوضيحية المتعددة بواسطة المعرفات
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إزالة التعليقات التوضيحية المتعددة بواسطة المعرفات في .NET باستخدام GroupDocs.Annotation، مما يعزز قدرات إدارة المستندات الخاصة بك دون عناء.
type: docs
weight: 13
url: /ar/net/removing-annotations/remove-multiple-annotations-by-ids/
---
## مقدمة
في عالم إدارة المستندات والتعاون، تظهر GroupDocs.Annotation for .NET كأداة قوية، تمكن المطورين من إضافة تعليقات توضيحية إلى المستندات ومعالجتها بسلاسة داخل تطبيقات .NET الخاصة بهم. سوف يتعمق هذا البرنامج التعليمي في إحدى الوظائف الأساسية التي تقدمها GroupDocs.Annotation لـ .NET: إزالة التعليقات التوضيحية المتعددة بواسطة المعرفات. باتباع هذا الدليل المفصّل خطوة بخطوة، ستكتسب فهمًا شاملاً لكيفية إزالة التعليقات التوضيحية بكفاءة، مما يمكّنك من تحسين قدرات إدارة المستندات لديك.
## المتطلبات الأساسية
قبل الغوص في هذا البرنامج التعليمي، تأكد من توفر المتطلبات الأساسية التالية:
### 1. تثبيت GroupDocs.Annotation لـ .NET
 أولاً، يجب أن يكون لديك GroupDocs.Annotation for .NET مثبتًا في بيئة التطوير لديك. يمكنك تنزيل الحزمة المطلوبة من[رابط التحميل](https://releases.groupdocs.com/annotation/net/) المقدمة من مستندات المجموعة.
### 2. الفهم الأساسي لبرنامج .NET Framework
يعد الفهم الأساسي لـ .NET Framework ضروريًا لفهم أمثلة التعليمات البرمجية وتنفيذ الحل المقدم بشكل فعال.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء الضرورية إلى تطبيق .NET الخاص بك. توفر مساحات الأسماء هذه إمكانية الوصول إلى الوظائف المطلوبة لمعالجة التعليقات التوضيحية.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
في هذه الخطوة، نحدد المسار الذي سيتم فيه حفظ المستند المعدل مع التعليقات التوضيحية المحذوفة.
## الخطوة 2: إنشاء كائن الحواشي
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
 هنا، نقوم بإنشاء مثيل لـ`Annotator` فئة، وتمرير مسار وثيقة PDF المشروحة كمعلمة.
## الخطوة 3: إزالة التعليقات التوضيحية حسب المعرفات
```csharp
annotator.Remove(new List<int>{0,1});
```
في هذه الخطوة الحاسمة، نحدد معرفات التعليقات التوضيحية المراد إزالتها. يمكن تمرير معرفات متعددة ضمن قائمة للإزالة المتزامنة.
## الخطوة 4: احفظ المستند المعدل
```csharp
annotator.Save(outputPath);
```
بعد إزالة التعليقات التوضيحية المحددة، نقوم بحفظ المستند المعدل في مسار الإخراج المحدد مسبقًا.
## الخطوة 5: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
وأخيرًا، نقوم بإعلام المستخدم بإتمام العملية بنجاح ونوفر المسار الذي يتم فيه حفظ المستند المعدل.

## خاتمة
في الختام، يوضح هذا البرنامج التعليمي عملية إزالة التعليقات التوضيحية المتعددة بواسطة المعرفات باستخدام GroupDocs.Annotation لـ .NET. ومن خلال اتباع الخطوات الموضحة، يمكن للمطورين دمج هذه الوظيفة بسلاسة في تطبيقات .NET الخاصة بهم، وبالتالي تعزيز كفاءة إدارة المستندات والتعاون.
## الأسئلة الشائعة
### هل يمكن إزالة التعليقات التوضيحية من أنواع مختلفة في وقت واحد؟
نعم، يمكن إزالة التعليقات التوضيحية من أنواع مختلفة في وقت واحد عن طريق تحديد المعرفات الخاصة بها في قائمة الإزالة.
### هل يتوافق GroupDocs.Annotation لـ .NET مع كافة إصدارات .NET Framework؟
نعم، GroupDocs.Annotation for .NET متوافق مع إصدارات مختلفة من .NET Framework، مما يضمن تعدد الاستخدامات وسهولة التكامل.
### هل يمكنني تجربة GroupDocs.Annotation لـ .NET قبل الشراء؟
 قطعاً! يمكنك الاستفادة من النسخة التجريبية المجانية من GroupDocs.Annotation لـ .NET من[صفحة الإصدار](https://releases.groupdocs.com/)لاستكشاف ميزاته ووظائفه.
### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟
على الرغم من أن الترخيص المؤقت يمكن أن يعزز تجربة الاختبار الخاصة بك، إلا أنه ليس إلزاميًا لأغراض التجربة. ومع ذلك، لاستخدام الإنتاج، مطلوب ترخيص صالح.
### أين يمكنني طلب المساعدة إذا واجهت أي مشاكل أثناء التنفيذ؟
 يمكنك طلب المساعدة والتفاعل مع مجتمع GroupDocs النابض بالحياة من خلال[منتدى الدعم](https://forum.groupdocs.com/c/annotation/10)، حيث يتوفر الخبراء والمتحمسون بسهولة للإجابة على استفساراتك ومخاوفك.