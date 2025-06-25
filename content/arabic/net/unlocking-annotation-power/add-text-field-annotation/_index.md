---
"description": "تعرف على كيفية دمج تعليقات حقول النص بسلاسة في تطبيقات .NET الخاصة بك باستخدام Groupdocs.Annotation لـ .NET."
"linktitle": "إضافة تعليق حقل النص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق حقل النص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-field-annotation/"
"weight": 21
---

# إضافة تعليق حقل النص إلى المستند

## مقدمة
Groupdocs.Annotation لـ .NET أداة فعّالة تُمكّن المطورين من إضافة ميزات التعليقات التوضيحية إلى تطبيقات .NET بسهولة. سواء كنت تعمل على نظام إدارة مستندات، أو منصة تعاونية، أو أي تطبيق يتطلب إضافة تعليقات توضيحية، فإن Groupdocs.Annotation يُبسّط العملية بفضل مجموعة ميزاته الشاملة وواجهة برمجة التطبيقات سهلة الاستخدام.
في هذا البرنامج التعليمي، سنتعمق في إحدى الوظائف الأساسية لأداة Groupdocs.Annotation لـ .NET: إضافة تعليق توضيحي لحقل نصي إلى مستند. باتباع هذا الدليل التفصيلي، ستتعلم كيفية دمج تعليقات الحقول النصية بسلاسة في تطبيقات .NET، مما يُحسّن تجربة المستخدم وقدرات التعاون.
## المتطلبات الأساسية
قبل البدء في التنفيذ، تأكد من توفر المتطلبات الأساسية التالية:
### 1. تثبيت Groupdocs.Annotation لـ .NET
أولاً وقبل كل شيء، عليك تنزيل وتثبيت Groupdocs.Annotation لـ .NET. يمكنك العثور على رابط التنزيل. [هنا](https://releases.groupdocs.com/annotation/net/). اتبع تعليمات التثبيت الواردة في الوثائق [هنا](https://tutorials.groupdocs.com/annotation/net/) لإعداد المكتبة بشكل صحيح.
### 2. إعداد بيئة التطوير
تأكد من إعداد بيئة تطوير متوافقة مع .NET. يتضمن ذلك تثبيت بيئة تطوير متكاملة متوافقة، مثل Visual Studio و.NET Framework، على نظامك.
### 3. فهم أساسيات برمجة C#
تعرف على أساسيات لغة البرمجة C#، حيث سيتضمن هذا البرنامج التعليمي كتابة كود C# لدمج تعليقات حقول النص.

## استيراد مساحات الأسماء
في مشروع C# الخاص بك، ابدأ باستيراد المساحات الأساسية اللازمة لاستخدام وظائف Groupdocs.Annotation.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

الآن، دعنا ننتقل إلى إضافة تعليق حقل نص إلى مستند باستخدام Groupdocs.Annotation لـ .NET.
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 3: إنشاء كائن TextFieldAnnotation
```csharp
TextFieldAnnotation textField = new TextFieldAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Text = "Some text",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is text field annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## الخطوة 4: إضافة تعليق توضيحي إلى المستند
```csharp
annotator.Add(textField);
```
## الخطوة 5: حفظ المستند مع التعليقات التوضيحية
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، يُعد دمج تعليقات حقول النص في تطبيقات .NET باستخدام Groupdocs.Annotation for .NET عملية سهلة وبسيطة. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك تحسين التعاون بين المستندات وتفاعل المستخدمين داخل تطبيقاتك بسلاسة.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر تعليقات حقل النص؟
نعم، يمكنك تخصيص سمات مختلفة مثل لون الخلفية وحجم الخط والتعتيم وما إلى ذلك، وفقًا لمتطلباتك.
### هل Groupdocs.Annotation لـ .NET متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم Groupdocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وDOCX وPPTX وXLSX والمزيد.
### هل يمكنني إضافة تعليقات متعددة إلى نفس المستند؟
بالتأكيد، يمكنك إضافة تعليقات متعددة من أنواع مختلفة إلى نفس المستند، مما يتيح تفاعلًا غنيًا بين المستندات.
### هل هناك نسخة تجريبية متاحة لـ Groupdocs.Annotation لـ .NET؟
نعم، يمكنك استكشاف ميزات Groupdocs.Annotation من خلال الوصول إلى النسخة التجريبية المجانية [هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على الدعم لـ Groupdocs.Annotation لـ .NET؟
يمكنك العثور على المساعدة والتفاعل مع المجتمع على منتدى Groupdocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).