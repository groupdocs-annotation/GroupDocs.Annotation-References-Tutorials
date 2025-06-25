---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية على الصور إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. حسّن قدرات معالجة المستندات بسهولة."
"linktitle": "إضافة تعليق توضيحي للصورة إلى المستند (المسار المحلي)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي للصورة إلى المستند (المسار المحلي)"
"url": "/ar/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# إضافة تعليق توضيحي للصورة إلى المستند (المسار المحلي)

## مقدمة
GroupDocs.Annotation for .NET هي مكتبة فعّالة تُمكّن المطورين من إضافة أنواع مُختلفة من التعليقات التوضيحية إلى المستندات برمجيًا. في هذا البرنامج التعليمي، سنتعلم كيفية إضافة تعليقات توضيحية على الصور إلى مستند باستخدام مسار محلي.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:
1. المعرفة الأساسية بلغة البرمجة C#.
2. تم تثبيت Visual Studio على نظامك.
3. تم تثبيت GroupDocs.Annotation لمكتبة .NET أو تم تثبيت البرامج التعليمية عليها في مشروعك.
4. مستند إدخال (على سبيل المثال، PDF) وملف صورة للتعليق.
## استيراد مساحات الأسماء
أولاً، عليك استيراد مساحات الأسماء اللازمة إلى ملف C#. تتيح لك هذه المساحات الوصول إلى الفئات والأساليب اللازمة للعمل مع GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## الخطوة 1: تحديد مسار الإخراج
قم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
قم بتهيئة المشرح من خلال توفير المسار إلى مستند الإدخال.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // رمز التعليق يذهب هنا
}
```
## الخطوة 3: إنشاء تعليق توضيحي للصورة
إنشاء مثيل لـ `ImageAnnotation` الفئة وتحديد خصائصها مثل الموضع والتعتيم ورقم الصفحة ومسار الصورة.
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
## الخطوة 4: إضافة التعليقات التوضيحية
أضف تعليق الصورة الذي تم إنشاؤه إلى المستند باستخدام `Add` طريقة المشرح.
```csharp
annotator.Add(image);
```
## الخطوة 5: حفظ المستند
احفظ المستند الموضح في مسار الإخراج.
```csharp
annotator.Save(outputPath);
```
## الخطوة 6: عرض مسار الإخراج
عرض رسالة تشير إلى نجاح حفظ المستند وموقع ملف الإخراج.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة تعليقات توضيحية على الصور إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات البسيطة، يمكنك تحسين قدرات معالجة المستندات لديك باستخدام ميزات تعليقات توضيحية فعّالة.
## الأسئلة الشائعة
### هل يمكنني التعليق على مستندات أخرى غير PDF؟
نعم، يدعم GroupDocs.Annotation تنسيقات المستندات المختلفة بما في ذلك Word وExcel وPowerPoint والمزيد.
### هل GroupDocs.Annotation متوافق مع .NET Core؟
نعم، GroupDocs.Annotation متوافق مع كل من .NET Framework و.NET Core.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية؟
بالتأكيد، يمكنك تخصيص المظهر والحجم واللون والخصائص الأخرى للتعليقات التوضيحية وفقًا لمتطلباتك.
### هل يوفر GroupDocs.Annotation الدعم للتعليق التوضيحي التعاوني؟
نعم، يوفر GroupDocs.Annotation ميزات التعليق التوضيحي التعاونية التي تمكن مستخدمين متعددين من التعليق التوضيحي على المستندات في نفس الوقت.
### أين يمكنني العثور على مساعدة أو دعم إضافي؟
يمكنك زيارة منتدى GroupDocs.Annotation للحصول على المساعدة والدعم من المجتمع.