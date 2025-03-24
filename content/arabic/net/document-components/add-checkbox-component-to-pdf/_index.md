---
title: إضافة مكون خانة الاختيار إلى وثيقة PDF
linktitle: إضافة مكون خانة الاختيار إلى وثيقة PDF
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة مكون Checkbox إلى مستندات PDF باستخدام Groupdocs.Annotation لـ .NET. قم بتحسين ملفات PDF الخاصة بك باستخدام العناصر التفاعلية.
weight: 11
url: /ar/net/document-components/add-checkbox-component-to-pdf/
---

# إضافة مكون خانة الاختيار إلى وثيقة PDF

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة مكون Checkbox إلى مستند PDF باستخدام Groupdocs.Annotation for .NET.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  Groupdocs.Annotation لـ .NET SDK: يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تأكد من إعداد بيئة تطوير .NET.

## استيراد مساحات الأسماء
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
الآن، دعونا نقسم المثال إلى عدة خطوات:
## الخطوة 1: تحديد مسار الإخراج
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
هنا، نحدد مسار الإخراج حيث سيتم حفظ مستند PDF المعدل.
## الخطوة 2: تهيئة الحواشي
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 تهيئة`Annotator` كائن عن طريق تمرير مسار وثيقة PDF الإدخال.
## الخطوة 3: إنشاء مكون خانة الاختيار
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 إنشاء`CheckBoxComponent` الكائن وتخصيص خصائصه مثل`Checked`, `Box` أبعاد،`PenColor`, `Style`، وإضافة بعض الردود.
## الخطوة 4: إضافة مكون خانة الاختيار
```csharp
annotator.Add(checkBox);
```
أضف مكون مربع الاختيار الذي تم إنشاؤه إلى مستند PDF.
## الخطوة 5: حفظ المستند
```csharp
annotator.Save("result.pdf");
```
احفظ مستند PDF المعدل بمكون مربع الاختيار.
## الخطوة 6: عرض مسار الإخراج
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
اعرض المسار الذي تم حفظ مستند PDF المعدل فيه.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية إضافة مكون Checkbox إلى مستند PDF باستخدام Groupdocs.Annotation لـ .NET. باستخدام هذه المعرفة، يمكنك تحسين مستندات PDF الخاصة بك بعناصر تفاعلية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر مربع الاختيار؟
نعم، يمكنك تخصيص خصائص مختلفة مثل اللون والنمط والحجم وفقًا لمتطلباتك.
### هل Groupdocs.Annotation for .NET مناسب للاستخدام التجاري؟
نعم، يقدم Groupdocs.Annotation for .NET تراخيص تجارية للشركات.
### هل يمكنني تجربة Groupdocs.Annotation لـ .NET قبل الشراء؟
 نعم، يمكنك الاستفادة من النسخة التجريبية المجانية من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على دعم لـ Groupdocs.Annotation لـ .NET؟
 يمكنك العثور على الدعم والموارد على[منتدى المستندات الجماعية](https://forum.groupdocs.com/c/annotation/10).
### هل أحتاج إلى ترخيص مؤقت لأغراض الاختبار؟
 يمكنك الحصول على ترخيص مؤقت للاختبار من[هنا](https://purchase.groupdocs.com/temporary-license/).