---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية على الصور إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. حسّن إدارة المستندات بفضل إمكانيات التعليقات التوضيحية الفعّالة."
"linktitle": "إضافة تعليق توضيحي للصورة إلى المستند (المسار البعيد)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي للصورة إلى المستند (المسار البعيد)"
"url": "/ar/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# إضافة تعليق توضيحي للصورة إلى المستند (المسار البعيد)

## مقدمة
في هذا البرنامج التعليمي، سنشرح عملية إضافة تعليقات توضيحية على الصور إلى مستند باستخدام GroupDocs.Annotation لـ .NET. توفر هذه المكتبة أدوات فعّالة لإضافة تعليقات توضيحية على أنواع مختلفة من المستندات برمجيًا.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1. GroupDocs.Annotation لـ .NET: قم بتنزيل المكتبة وتثبيتها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير عمل جاهزة لتطوير .NET.
3. المستند: جهّز المستند الذي تريد إضافة تعليقات توضيحية إليه. في هذا البرنامج التعليمي، سنفترض أن لديك مستند PDF باسم `input.pdf`.
4. صورة للتعليق التوضيحي: اختر الصورة التي تريد استخدامها للتعليق التوضيحي. تأكد من إعداد رابط الصورة أو مسارها المحلي.

## استيراد مساحات الأسماء
قبل أن نبدأ في الترميز، دعنا نستورد مساحات الأسماء الضرورية:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## الخطوة 1: تعيين مسار الإخراج
أولاً، قم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
إنشاء مثيل لـ `Annotator` الفئة وتحديد مستند الإدخال.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```
## الخطوة 3: إضافة تعليق توضيحي للصورة
الآن، لنُضِف شرح الصورة إلى المستند. سنُحدِّد خصائص شرح الصورة، مثل الموضع، والتعتيم، ورقم الصفحة، ومسار الصورة.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // حدد موضع التعليق التوضيحي
    CreatedOn = DateTime.Now, // تعيين تاريخ الإنشاء
    Opacity = 0.7, // ضبط التعتيم (0 إلى 1)
    PageNumber = 0, // حدد رقم الصفحة
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // أدخل عنوان URL للصورة
};
annotator.Add(image); // أضف تعليقًا على الصورة
```
## الخطوة 4: حفظ المستند
احفظ المستند الموضح في مسار الإخراج المحدد.
```csharp
annotator.Save(outputPath);
```
## الخطوة 5: عرض مسار الإخراج
إعلام المستخدم بنجاح عملية حفظ المستند وعرض مسار الإخراج.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليقات توضيحية على الصور إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات، يمكنك تحسين تطبيقات إدارة المستندات لديك بإمكانيات تعليقات توضيحية فعّالة.
## الأسئلة الشائعة
### هل يمكن استخدام GroupDocs.Annotation مع تنسيقات مستندات أخرى بالإضافة إلى PDF؟
نعم، يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل GroupDocs.Annotation متوافق مع .NET Core؟
نعم، GroupDocs.Annotation متوافق مع كل من .NET Framework و.NET Core.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
نعم، يمكنك تخصيص مظهر التعليقات التوضيحية مثل اللون والتعتيم والحجم.
### هل يدعم GroupDocs.Annotation ميزات التعليق التوضيحي التعاوني؟
نعم، يوفر GroupDocs.Annotation ميزات التعليق التوضيحي التعاوني للتعاون في الوقت الفعلي على المستندات.
### هل هناك نسخة تجريبية متاحة للاختبار؟
نعم، يمكنك الحصول على نسخة تجريبية مجانية من GroupDocs.Annotation من [هنا](https://releases.groupdocs.com/).