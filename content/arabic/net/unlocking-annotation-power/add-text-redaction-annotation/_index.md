---
"description": "تعرّف على كيفية إضافة تعليقات تحرير النصوص إلى مستندات PDF باستخدام GroupDocs.Annotation لـ .NET. احمِ معلوماتك الحساسة بسهولة."
"linktitle": "إضافة تعليق تحرير النص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق تحرير النص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# إضافة تعليق تحرير النص إلى المستند

## مقدمة
إضافة تعليق تحرير نصي إلى مستند خطوة أساسية في إدارة المعلومات الحساسة بأمان. يوفر GroupDocs.Annotation for .NET حلاً فعالاً لتحقيق ذلك بسلاسة. في هذا البرنامج التعليمي، سنرشدك خطوة بخطوة خلال عملية إضافة تعليق تحرير نصي إلى مستندك.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1. GroupDocs.Annotation لـ .NET: تأكد من تثبيت مكتبة GroupDocs.Annotation لـ .NET. يمكنك تنزيلها من [موقع إلكتروني](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير باستخدام IDE متوافق مع .NET مثل Visual Studio.

## استيراد مساحات الأسماء
أولاً، دعنا نستورد مساحات الأسماء الضرورية لمشروعنا:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تحديد مسار الإخراج
حدّد مسار الإخراج الذي تريد حفظ المستند المُعلّق عليه فيه. تأكّد من إمكانية الوصول إليه وإمكانية الكتابة فيه.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
قم بتهيئة المُعلِّق باستخدام مسار مستند الإدخال. استبدل `"input.pdf"` مع المسار إلى مستندك.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // سيتم وضع رمز الشرح هنا
}
```
## الخطوة 3: إنشاء تعليق تحريري للنص
إنشاء `TextRedactionAnnotation` كائن بالخصائص المطلوبة مثل `PageNumber`، `FontColor`، و `Points`. قم بتخصيص التعليق التوضيحي وفقًا لمتطلباتك.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
    }
};
```
## الخطوة 4: إضافة التعليقات التوضيحية وحفظها
قم بإضافة التعليق التوضيحي الذي تم إنشاؤه إلى المستند باستخدام المشرح ثم احفظ المستند المشرح في مسار الإخراج المحدد.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## الخطوة 5: التحقق من الناتج
أخيرًا، تأكد من حفظ المستند بنجاح في مسار الإخراج المحدد.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، شرحنا عملية إضافة تعليق تحريري نصي إلى مستند باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات، يمكنك الآن إدارة المعلومات الحساسة داخل مستنداتك بأمان.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر تعليق تحرير النص؟
نعم، يمكنك تخصيص خصائص مختلفة مثل لون الخط ولون التعبئة والتعتيم لتناسب متطلباتك.
### هل هناك نسخة تجريبية متاحة قبل الشراء؟
نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من [موقع إلكتروني](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم إذا واجهت أي مشاكل؟
يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).
### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟
نعم يمكنك الحصول على ترخيص مؤقت من [صفحة الشراء](https://purchase.groupdocs.com/temporary-license/) للاختبار.
### هل يمكنني إضافة تعليقات متعددة إلى مستند واحد؟
بالتأكيد، يسمح لك GroupDocs.Annotation بإضافة أنواع مختلفة من التعليقات التوضيحية ومثيلات متعددة إلى مستند واحد.