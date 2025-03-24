---
title: وضع تعليق توضيحي للصورة فوق النص
linktitle: وضع تعليق توضيحي للصورة فوق النص
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية للصور فوق النص في .NET باستخدام GroupDocs.Annotation لإدارة المستندات والتعاون بكفاءة.
weight: 21
url: /ar/net/advanced-usage/put-image-annotation-over-text/
---

# وضع تعليق توضيحي للصورة فوق النص

## مقدمة
في عالم تطوير .NET، يقدم GroupDocs.Annotation حلاً قويًا لإضافة التعليقات التوضيحية إلى المستندات، مما يجعل التعاون وإدارة المستندات أكثر كفاءة. أحد المتطلبات الشائعة هو وضع التعليقات التوضيحية للصور فوق النص، وهو ما يمكن تحقيقه بسهولة باستخدام GroupDocs.Annotation for .NET.
## المتطلبات الأساسية
قبل الغوص في عملية وضع التعليقات التوضيحية للصور على النص باستخدام GroupDocs.Annotation for .NET، تأكد من أن لديك ما يلي:
1.  GroupDocs.Annotation لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة، مثل Visual Studio أو أي برنامج .NET IDE آخر.
3. ملفات المستندات والصور: قم بإعداد ملف المستند (PDF، DOCX، وما إلى ذلك) وملف الصورة الذي تريد استخدامه للتعليقات التوضيحية.
4. الفهم الأساسي لـ C#: الإلمام بلغة البرمجة C# ضروري لتنفيذ مقتطفات التعليمات البرمجية المتوفرة في هذا البرنامج التعليمي.

## استيراد مساحات الأسماء
قبل متابعة عملية التعليق التوضيحي، تأكد من استيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## الخطوة 1: تحديد مسار الإخراج
أولاً، حدد مسار الإخراج حيث سيتم حفظ المستند المشروح:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## الخطوة 2: تهيئة الحواشي
 تهيئة`Annotator` الكائن عن طريق توفير مسار مستند الإدخال:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز التعليق التوضيحي هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي للصورة
 يخترع`ImageAnnotation` كائن بالخصائص المطلوبة مثل أبعاد الصندوق، والعتامة، ورقم الصفحة، ومسار الصورة، ومؤشر z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## الخطوة 4: إضافة تعليق توضيحي
 أضف التعليق التوضيحي للصورة إلى المستند باستخدام`Add` طريقة`Annotator` هدف:
```csharp
annotator.Add(image);
```
## الخطوة 5: حفظ المستند المشروح
احفظ المستند المشروح في مسار الإخراج المحدد:
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
عرض رسالة نجاح مع المسار إلى المستند المشروح:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، تعد إضافة التعليقات التوضيحية للصور فوق النص في تطبيقات .NET باستخدام GroupDocs.Annotation عملية مباشرة. من خلال اتباع الدليل التفصيلي المقدم في هذا البرنامج التعليمي، يمكنك إضافة تعليقات توضيحية للمستندات بكفاءة وتعزيز إمكانات التعاون وإدارة المستندات في مشاريع .NET الخاصة بك.
## الأسئلة الشائعة
### هل يمكنني إضافة تعليقات توضيحية إلى المستندات بخلاف ملفات PDF؟
نعم، يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة مثل DOCX وXLSX وPPTX والمزيد.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على دعم لـ GroupDocs.Annotation؟
 يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).
### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟
 نعم يمكنك الحصول على ترخيص مؤقت من[هنا](https://purchase.groupdocs.com/temporary-license/) لأغراض تجريبية.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يوفر GroupDocs.Annotation خيارات متنوعة لتخصيص مظهر التعليقات التوضيحية مثل اللون والعتامة وحجم الخط وما إلى ذلك.