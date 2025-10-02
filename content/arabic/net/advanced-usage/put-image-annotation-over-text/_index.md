---
"description": "تعرف على كيفية إضافة تعليقات الصور فوق النص في .NET باستخدام GroupDocs.Annotation لإدارة المستندات والتعاون بكفاءة."
"linktitle": "وضع تعليق توضيحي للصورة فوق النص"
"second_title": "GroupDocs.Annotation .NET API"
"title": "وضع تعليق توضيحي للصورة فوق النص"
"url": "/ar/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# وضع تعليق توضيحي للصورة فوق النص

## مقدمة
في عالم تطوير .NET، تُقدم GroupDocs.Annotation حلاً فعّالاً لإضافة التعليقات التوضيحية إلى المستندات، مما يزيد من كفاءة التعاون وإدارة المستندات. من المتطلبات الشائعة إضافة تعليقات توضيحية على الصور فوق النصوص، وهو أمر يُمكن إنجازه بسلاسة باستخدام GroupDocs.Annotation لـ .NET.
## المتطلبات الأساسية
قبل الخوض في عملية إضافة تعليقات الصور فوق النص باستخدام GroupDocs.Annotation لـ .NET، تأكد من توفر ما يلي:
1. GroupDocs.Annotation لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير مناسبة، مثل Visual Studio أو أي .NET IDE أخرى.
3. ملفات المستندات والصور: قم بإعداد ملف المستند (PDF، DOCX، وما إلى ذلك) وملف الصورة الذي تريد استخدامه للتعليقات التوضيحية.
4. الفهم الأساسي للغة البرمجة C#: من الضروري أن تكون على دراية بلغة البرمجة C# لتنفيذ مقتطفات التعليمات البرمجية المقدمة في هذا البرنامج التعليمي.

## استيراد مساحات الأسماء
قبل المتابعة بعملية التعليق التوضيحي، تأكد من استيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## الخطوة 1: تحديد مسار الإخراج
أولاً، قم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## الخطوة 2: تهيئة المُعلّق
تهيئة `Annotator` الكائن عن طريق توفير مسار المستند الإدخالي:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي للصورة
إنشاء `ImageAnnotation` كائن بالخصائص المطلوبة مثل أبعاد المربع، والتعتيم، ورقم الصفحة، ومسار الصورة، ومؤشر Z:
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
## الخطوة 4: إضافة التعليقات التوضيحية
أضف تعليق الصورة إلى المستند باستخدام `Add` طريقة `Annotator` هدف:
```csharp
annotator.Add(image);
```
## الخطوة 5: حفظ المستند الموضح
احفظ المستند الموضح في مسار الإخراج المحدد:
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض رسالة النجاح
عرض رسالة نجاح مع المسار إلى المستند الموضح:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، إضافة تعليقات توضيحية على الصور فوق النصوص في تطبيقات .NET باستخدام GroupDocs.Annotation عملية سهلة وبسيطة. باتباع الدليل المفصل في هذا البرنامج التعليمي، يمكنك إضافة تعليقات توضيحية على المستندات بكفاءة، وتعزيز قدرات التعاون وإدارة المستندات في مشاريع .NET الخاصة بك.
## الأسئلة الشائعة
### هل يمكنني التعليق على مستندات أخرى غير ملفات PDF؟
نعم، يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة مثل DOCX وXLSX وPPTX والمزيد.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية من [هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم لـ GroupDocs.Annotation؟
يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).
### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟
نعم يمكنك الحصول على ترخيص مؤقت من [هنا](https://purchase.groupdocs.com/temporary-license/) لأغراض الاختبار.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يوفر GroupDocs.Annotation خيارات مختلفة لتخصيص مظهر التعليقات التوضيحية مثل اللون والتعتيم وحجم الخط وما إلى ذلك.