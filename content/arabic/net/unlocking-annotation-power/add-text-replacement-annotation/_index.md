---
"description": "تعلّم كيفية إضافة تعليقات توضيحية بديلة للنصوص إلى مستندات .NET بسهولة باستخدام GroupDocs.Annotation for .NET. حسّن قدراتك على معالجة المستندات."
"linktitle": "إضافة تعليق استبدال النص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق استبدال النص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# إضافة تعليق استبدال النص إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة تعليق توضيحي لاستبدال النص إلى مستنداتك باستخدام GroupDocs.Annotation لـ .NET. تتيح هذه المكتبة القوية للمطورين التعامل مع أنواع مختلفة من المستندات وإضافة تعليقات توضيحية إليها برمجيًا. بنهاية هذا البرنامج التعليمي، ستكون قد اكتسبت المعرفة اللازمة لدمج تعليقات استبدال النص بسلاسة في تطبيقات .NET.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من تثبيت المتطلبات الأساسية التالية:
### 1. تم تثبيت .NET Framework
تأكد من تثبيت .NET Framework على جهاز التطوير لديك. يمكنك تنزيله من موقع مايكروسوفت.
### 2. GroupDocs.Annotation لمكتبة .NET
قم بتنزيل وتثبيت مكتبة GroupDocs.Annotation لـ .NET من [موقع إلكتروني](https://releases.groupdocs.com/annotation/net/)توفر هذه المكتبة الأدوات والوظائف اللازمة للعمل مع التعليقات التوضيحية في تنسيقات المستندات المختلفة.
### 3. إعداد بيئة التطوير
قم بإعداد بيئة التطوير المفضلة لديك، مثل Visual Studio، لإنشاء تطبيقات .NET وتشغيلها.

## استيراد مساحات الأسماء
قبل الخوض في جزء الترميز، دعنا نستورد مساحات الأسماء الضرورية المطلوبة للعمل مع GroupDocs.Annotation لـ .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
هنا، نقوم بتحديد مسار الإخراج الذي سيتم حفظ المستند الموضح فيه.
## الخطوة 2: تهيئة المُعلّق
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```
نقوم بتهيئة كائن Annotator من خلال تحديد مستند الإدخال ("input.pdf") داخل كتلة الاستخدام لضمان التخلص السليم من الموارد.
## الخطوة 3: إنشاء تعليق بديل
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
    },
    TextToReplace = "replaced text"
};
```
هنا، نقوم بإنشاء كائن ReplacementAnnotation مع خصائص مختلفة مثل تاريخ الإنشاء، ولون الخط، والرسالة، والتعتيم، ورقم الصفحة، ولون الخلفية، والنقاط (الإحداثيات)، والردود (التعليقات)، والنص الذي سيتم استبداله.
## الخطوة 4: إضافة التعليقات التوضيحية
```csharp
annotator.Add(replacement);
```
نضيف التعليق البديل الذي تم إنشاؤه إلى المشرح.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save(outputPath);
```
وأخيرًا، نقوم بحفظ المستند الموضح في مسار الإخراج المحدد.
## الخطوة 6: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
يتم عرض رسالة نجاح تشير إلى أنه تم حفظ المستند بنجاح.

## خاتمة
في هذا البرنامج التعليمي، تناولنا عملية إضافة تعليقات توضيحية لاستبدال النصوص إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. باتباع هذا الدليل خطوة بخطوة وفهم المتطلبات الأساسية، يمكنك دمج هذه الوظيفة بسهولة في تطبيقات .NET.
## الأسئلة الشائعة
### هل يمكنني التعليق على مستندات بتنسيقات مختلفة باستخدام GroupDocs.Annotation لـ .NET؟
نعم، يدعم GroupDocs.Annotation لـ .NET التعليق على تنسيقات المستندات المختلفة مثل PDF، وDOCX، وPPTX، وXLSX، والمزيد.
### هل GroupDocs.Annotation لـ .NET مناسب لكل من تطبيقات سطح المكتب والويب؟
نعم، يمكن استخدام GroupDocs.Annotation لـ .NET في كل من تطبيقات سطح المكتب والويب، مما يوفر المرونة للمطورين.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية المضافة باستخدام GroupDocs.Annotation لـ .NET؟
بالتأكيد، يمكنك تخصيص مظهر التعليقات التوضيحية عن طريق تعديل خصائص مثل اللون والتعتيم والخط وما إلى ذلك.
### هل يوفر GroupDocs.Annotation لـ .NET الدعم لميزات التعليق التوضيحي التعاوني؟
نعم، يوفر GroupDocs.Annotation لـ .NET ميزات للتعليق التوضيحي التعاوني، مما يسمح لمستخدمين متعددين بالتعليق التوضيحي على المستندات في نفس الوقت.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation لـ .NET؟
نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من GroupDocs.Annotation لـ .NET من [موقع إلكتروني](https://releases.groupdocs.com/).