---
title: تدوير وثائق PDF
linktitle: تدوير وثائق PDF
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية تدوير مستندات PDF بسهولة باستخدام Groupdocs.Annotation لـ .NET. تحسين كفاءة إدارة الوثائق.
weight: 22
url: /ar/net/advanced-usage/rotating-pdf-documents/
---
## مقدمة
يمكن أن يكون تدوير مستندات PDF مهمة حاسمة عند التعامل مع الملفات التي تحتاج إلى عرضها أو معالجتها بشكل مختلف. في هذا البرنامج التعليمي، سوف نستكشف كيفية تدوير مستندات PDF خطوة بخطوة باستخدام Groupdocs.Annotation for .NET.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1.  Groupdocs.Annotation لمكتبة .NET: تأكد من أنك قمت بتنزيل وتثبيت Groupdocs.Annotation لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. المعرفة الأساسية ببرمجة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا للغة البرمجة C# وكيفية العمل مع مكتبات .NET.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك للوصول إلى الوظائف التي توفرها مكتبة Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: قم بتحميل مستند PDF
 ابدأ بتحميل مستند PDF الذي تريد تدويره باستخدام ملف`Annotator` فصل.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## الخطوة 2: ضبط صفحات التدوير والمعالجة
حدد زاوية التدوير والصفحات التي تريد تدويرها. في هذا المثال، سنقوم بتدوير الصفحة الأولى بمقدار 90 درجة في اتجاه عقارب الساعة.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## الخطوة 3: احفظ المستند الذي تم تدويره
احفظ مستند PDF الذي تم تدويره بالتغييرات المحددة.
```csharp
annotator.Save("result.pdf");
```
## الخطوة 4: عرض التأكيد
أبلغ المستخدم أنه تم تدوير المستند بنجاح.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## خاتمة
يعد تدوير مستندات PDF عملية أساسية، ومع Groupdocs.Annotation لـ .NET، تصبح عملية بسيطة وفعالة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك بسهولة تدوير ملفات PDF وفقًا لمتطلباتك.
## الأسئلة الشائعة
### هل يمكنني تدوير صفحات متعددة في مستند PDF باستخدام Groupdocs.Annotation لـ .NET؟
 نعم، يمكنك تحديد صفحات متعددة لتدويرها عن طريق ضبط`ProcessPages` الممتلكات وفقا لذلك.
### هل Groupdocs.Annotation لـ .NET متوافق مع كافة إصدارات .NET Framework؟
يدعم Groupdocs.Annotation for .NET نطاقًا واسعًا من إصدارات .NET Framework، مما يضمن التوافق مع معظم بيئات التطوير.
### هل يوفر Groupdocs.Annotation for .NET خيارات لتدوير مستندات PDF في اتجاهات مختلفة؟
نعم، يمكنك تدوير مستندات PDF في اتجاه عقارب الساعة، أو عكس اتجاه عقارب الساعة، أو بزوايا مخصصة بناءً على متطلباتك.
### هل يمكنني دمج Groupdocs.Annotation لـ .NET في نظام إدارة المستندات الموجود لدي؟
بالتأكيد، يوفر Groupdocs.Annotation for .NET خيارات تكامل سلسة، مما يسمح لك بتحسين قدرات إدارة المستندات دون عناء.
### هل هناك إصدار تجريبي متاح لـ Groupdocs.Annotation لـ .NET؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).