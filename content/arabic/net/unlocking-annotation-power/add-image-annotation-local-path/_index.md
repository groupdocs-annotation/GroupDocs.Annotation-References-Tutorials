---
title: إضافة تعليق توضيحي للصورة إلى المستند (المسار المحلي)
linktitle: إضافة تعليق توضيحي للصورة إلى المستند (المسار المحلي)
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية للصور إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. تعزيز قدرات معالجة المستندات بسهولة.
weight: 14
url: /ar/net/unlocking-annotation-power/add-image-annotation-local-path/
---

# إضافة تعليق توضيحي للصورة إلى المستند (المسار المحلي)

## مقدمة
تعد GroupDocs.Annotation for .NET مكتبة قوية تسمح للمطورين بإضافة أنواع مختلفة من التعليقات التوضيحية إلى المستندات برمجيًا. في هذا البرنامج التعليمي، سوف نتعلم كيفية إضافة تعليقات توضيحية للصور إلى مستند باستخدام مسار محلي.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1. المعرفة الأساسية بلغة البرمجة C#.
2. تم تثبيت Visual Studio على نظامك.
3. GroupDocs.Annotation لمكتبة .NET المثبتة أو المشار إليها في مشروعك.
4. مستند إدخال (على سبيل المثال، PDF) وملف صورة للتعليق التوضيحي.
## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى ملف C# الخاص بك. توفر مساحات الأسماء هذه إمكانية الوصول إلى الفئات والأساليب المطلوبة للعمل مع GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## الخطوة 1: تحديد مسار الإخراج
حدد مسار الإخراج حيث سيتم حفظ المستند المشروح.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة الحواشي
قم بتهيئة التعليق التوضيحي من خلال توفير المسار إلى مستند الإدخال.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // رمز التعليق التوضيحي يذهب هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي للصورة
 إنشاء مثيل لـ`ImageAnnotation`فئة وتحديد خصائصها مثل الموضع، والتعتيم، ورقم الصفحة، ومسار الصورة.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## الخطوة 4: إضافة تعليق توضيحي
 أضف التعليق التوضيحي للصورة التي تم إنشاؤها إلى المستند باستخدام الملف`Add` طريقة الحواشي.
```csharp
annotator.Add(image);
```
## الخطوة 5: حفظ المستند
احفظ المستند المشروح في مسار الإخراج.
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض مسار الإخراج
عرض رسالة تشير إلى نجاح حفظ المستند وموقع ملف الإخراج.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليقات توضيحية للصور إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات البسيطة، يمكنك تحسين قدرات معالجة المستندات الخاصة بك من خلال ميزات التعليقات التوضيحية القوية.
## الأسئلة الشائعة
### هل يمكنني إضافة تعليقات توضيحية إلى مستندات أخرى غير PDF؟
نعم، يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل GroupDocs.Annotation متوافق مع .NET Core؟
نعم، GroupDocs.Annotation متوافق مع كل من .NET Framework و.NET Core.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
بالتأكيد، يمكنك تخصيص المظهر والحجم واللون والخصائص الأخرى للتعليقات التوضيحية وفقًا لمتطلباتك.
### هل يوفر GroupDocs.Annotation الدعم للتعليق التوضيحي التعاوني؟
نعم، يوفر GroupDocs.Annotation ميزات التعليقات التوضيحية التعاونية التي تمكن عدة مستخدمين من إضافة تعليقات توضيحية إلى المستندات في وقت واحد.
### أين يمكنني العثور على مساعدة أو دعم إضافي؟
يمكنك زيارة منتدى GroupDocs.Annotation للحصول على المساعدة والدعم من المجتمع.