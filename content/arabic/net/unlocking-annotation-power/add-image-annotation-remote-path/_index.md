---
title: إضافة تعليق توضيحي للصورة إلى المستند (المسار البعيد)
linktitle: إضافة تعليق توضيحي للصورة إلى المستند (المسار البعيد)
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية للصور إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. تعزيز إدارة المستندات من خلال إمكانات التعليقات التوضيحية القوية.
type: docs
weight: 15
url: /ar/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية إضافة التعليقات التوضيحية للصور إلى مستند باستخدام GroupDocs.Annotation لـ .NET. توفر هذه المكتبة أدوات قوية لإضافة تعليقات توضيحية لأنواع مختلفة من المستندات برمجيًا.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Annotation لـ .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير عمل معدة لتطوير .NET.
3.  المستند: قم بإعداد المستند الذي تريد إضافة تعليقات توضيحية إليه. في هذا البرنامج التعليمي، سنفترض أن لديك مستند PDF اسمه`input.pdf`.
4. صورة للتعليق التوضيحي: اختر الصورة التي تريد استخدامها للتعليق التوضيحي. تأكد من أن عنوان URL للصورة أو المسار المحلي جاهز.

## استيراد مساحات الأسماء
قبل أن نبدأ البرمجة، دعونا نستورد مساحات الأسماء الضرورية:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## الخطوة 1: تعيين مسار الإخراج
أولاً، حدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
 إنشاء مثيل لـ`Annotator` فئة وحدد مستند الإدخال.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```
## الخطوة 3: إضافة تعليق توضيحي للصورة
الآن، دعونا نضيف التعليق التوضيحي للصورة إلى المستند. سنقوم بتحديد خصائص التعليق التوضيحي للصورة مثل الموضع، والتعتيم، ورقم الصفحة، ومسار الصورة.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // حدد موضع التعليق التوضيحي
    CreatedOn = DateTime.Now, // ضبط تاريخ الإنشاء
    Opacity = 0.7, // ضبط العتامة (0 إلى 1)
    PageNumber = 0, // حدد رقم الصفحة
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // توفير عنوان URL للصورة
};
annotator.Add(image); // أضف التعليق التوضيحي للصورة
```
## الخطوة 4: حفظ المستند
احفظ المستند المشروح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
```
## الخطوة 5: عرض مسار الإخراج
أبلغ المستخدم بعملية حفظ المستند الناجحة واعرض مسار الإخراج.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليقات توضيحية للصور إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات، يمكنك تحسين تطبيقات إدارة المستندات لديك من خلال إمكانات التعليقات التوضيحية القوية.
## الأسئلة الشائعة
### هل يمكن استخدام GroupDocs.Annotation مع تنسيقات المستندات الأخرى إلى جانب PDF؟
نعم، يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل GroupDocs.Annotation متوافق مع .NET Core؟
نعم، GroupDocs.Annotation متوافق مع كل من .NET Framework و.NET Core.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يمكنك تخصيص مظهر التعليقات التوضيحية مثل اللون والعتامة والحجم.
### هل يدعم GroupDocs.Annotation ميزات التعليقات التوضيحية التعاونية؟
نعم، يوفر GroupDocs.Annotation ميزات التعليقات التوضيحية التعاونية للتعاون في الوقت الفعلي على المستندات.
### هل هناك نسخة تجريبية متاحة للاختبار؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من GroupDocs.Annotation من[هنا](https://releases.groupdocs.com/).