---
"description": "تعلّم كيفية تدوير مستندات PDF بسهولة باستخدام Groupdocs.Annotation لـ .NET. حسّن كفاءة إدارة المستندات."
"linktitle": "تدوير مستندات PDF"
"second_title": "GroupDocs.Annotation .NET API"
"title": "تدوير مستندات PDF"
"url": "/ar/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# تدوير مستندات PDF

## مقدمة
يُعد تدوير مستندات PDF أمرًا بالغ الأهمية عند التعامل مع ملفات تتطلب عرضًا أو معالجة مختلفة. في هذا البرنامج التعليمي، سنستكشف كيفية تدوير مستندات PDF خطوة بخطوة باستخدام Groupdocs.Annotation لـ .NET.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1. مكتبة Groupdocs.Annotation لـ .NET: تأكد من تنزيل مكتبة Groupdocs.Annotation لـ .NET وتثبيتها. يمكنك تنزيلها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. المعرفة الأساسية لبرمجة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا للغة البرمجة C# وكيفية العمل مع مكتبات .NET.

## استيراد مساحات الأسماء
أولاً، يتعين عليك استيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك للوصول إلى الوظائف التي توفرها مكتبة Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحميل مستند PDF
ابدأ بتحميل مستند PDF الذي تريد تدويره باستخدام `Annotator` فصل.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## الخطوة 2: تعيين صفحات التدوير والمعالجة
حدد زاوية الدوران والصفحات التي تريد تدويرها. في هذا المثال، سندوّر الصفحة الأولى 90 درجة باتجاه عقارب الساعة.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## الخطوة 3: حفظ المستند المُدار
احفظ مستند PDF المُدار بالتغييرات المحددة.
```csharp
annotator.Save("result.pdf");
```
## الخطوة 4: عرض التأكيد
أبلغ المستخدم بأن المستند تم تدويره بنجاح.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## خاتمة
تدوير مستندات PDF عملية أساسية، ومع Groupdocs.Annotation لـ .NET، يصبح الأمر بسيطًا وفعالًا. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك تدوير ملفات PDF بسهولة وفقًا لاحتياجاتك.
## الأسئلة الشائعة
### هل يمكنني تدوير صفحات متعددة في مستند PDF باستخدام Groupdocs.Annotation لـ .NET؟
نعم، يمكنك تحديد صفحات متعددة لتدويرها عن طريق ضبط `ProcessPages` الممتلكات وفقا لذلك.
### هل Groupdocs.Annotation لـ .NET متوافق مع كافة إصدارات إطار عمل .NET؟
يدعم Groupdocs.Annotation لـ .NET مجموعة واسعة من إصدارات إطار عمل .NET، مما يضمن التوافق مع معظم بيئات التطوير.
### هل يوفر Groupdocs.Annotation لـ .NET خيارات لتدوير مستندات PDF في اتجاهات مختلفة؟
نعم، يمكنك تدوير مستندات PDF في اتجاه عقارب الساعة، أو عكس اتجاه عقارب الساعة، أو بزوايا مخصصة بناءً على متطلباتك.
### هل يمكنني دمج Groupdocs.Annotation لـ .NET في نظام إدارة المستندات الحالي الخاص بي؟
بالتأكيد، يوفر Groupdocs.Annotation لـ .NET خيارات تكامل سلسة، مما يسمح لك بتعزيز قدرات إدارة المستندات بسهولة.
### هل هناك نسخة تجريبية متاحة لـ Groupdocs.Annotation لـ .NET؟
نعم، يمكنك الحصول على نسخة تجريبية مجانية من [هنا](https://releases.groupdocs.com/).