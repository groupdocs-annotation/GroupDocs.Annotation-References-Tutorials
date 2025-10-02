---
"description": "تعرّف على كيفية إضافة عناصر القائمة المنسدلة إلى ملفات PDF باستخدام GroupDocs.Annotation لـ .NET. اتبع دليلنا خطوة بخطوة للتكامل السلس."
"linktitle": "إضافة مكون القائمة المنسدلة إلى مستند PDF"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة مكون القائمة المنسدلة إلى مستند PDF"
"url": "/ar/net/document-components/add-dropdown-component-to-pdf/"
type: docs
"weight": 12
---

# إضافة مكون القائمة المنسدلة إلى مستند PDF

## مقدمة
يوفر GroupDocs.Annotation for .NET مجموعة أدوات فعّالة لإضافة تعليقات توضيحية برمجية على مستندات PDF. ومن الميزات المفيدة إمكانية إضافة عناصر منسدلة إلى مستندات PDF، مما يُحسّن تفاعليتها وسهولة استخدامها.
## المتطلبات الأساسية
قبل البدء، تأكد من أن لديك ما يلي:
1. GroupDocs.Annotation لـ .NET: قم بتنزيل المكتبة وتثبيتها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير .NET.
3. مستند PDF: قم بإعداد مستند PDF الذي تريد إضافة مكون القائمة المنسدلة إليه.

## استيراد مساحات الأسماء
تأكد من استيراد المساحات الأساسية اللازمة إلى مشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تعيين مسار الإخراج
قم بتحديد مسار الإخراج حيث سيتم حفظ المستند المعدل:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
إنشاء مثيل لـ `Annotator` الفئة عن طريق تمرير مسار مستند PDF المدخل:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## الخطوة 3: إنشاء مكون القائمة المنسدلة
قم بتحديد خصائص مكون القائمة المنسدلة:
```csharp
DropdownComponent dropdown = new DropdownComponent
{
    Options = new List<string> { "Item1", "Item2", "Item3" },
    SelectedOption = null,
    Placeholder = "Choose option",
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is dropdown component",
    PageNumber = 0,
    PenColor = 65535,
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
## الخطوة 4: إضافة مكون القائمة المنسدلة
أضف مكون القائمة المنسدلة إلى مستند PDF:
```csharp
annotator.Add(dropdown);
```
## الخطوة 5: حفظ المستند
حفظ المستند المعدل:
```csharp
annotator.Save("result.pdf");
```
## الخطوة 6: عرض مسار الإخراج
عرض رسالة تشير إلى نجاح حفظ المستند مع مسار الإخراج:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في هذا البرنامج التعليمي، استكشفنا كيفية تحسين مستندات PDF بإضافة عناصر قائمة منسدلة باستخدام GroupDocs.Annotation لـ .NET. باتباع هذا الدليل المفصل، يمكنك بسهولة دمج هذه الوظيفة في تطبيقات .NET، مما يوفر للمستخدمين تجربة عرض مستندات تفاعلية وديناميكية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر مكون القائمة المنسدلة؟
نعم، يمكنك تخصيص خصائص مختلفة مثل الخيارات، ونص العنصر النائب، وأبعاد المربع، ولون القلم، والأسلوب وفقًا لمتطلباتك.
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة إصدارات .NET؟
نعم، GroupDocs.Annotation لـ .NET متوافق مع كافة الإصدارات الرئيسية لإطار عمل .NET.
### هل يمكنني إضافة مكونات منسدلة متعددة إلى مستند PDF واحد؟
بالتأكيد، يمكنك إضافة عدد لا حصر له من مكونات القائمة المنسدلة إلى مستند PDF.
### هل يدعم GroupDocs.Annotation لـ .NET أنواع التعليقات التوضيحية الأخرى؟
نعم، يدعم GroupDocs.Annotation لـ .NET أنواعًا مختلفة من التعليقات التوضيحية بما في ذلك التعليقات النصية، والتعليقات التوضيحية للمنطق، والتعليقات التوضيحية للنقط، والتعليقات التوضيحية المشطوبة.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
نعم يمكنك الوصول إلى النسخة التجريبية [هنا](https://releases.groupdocs.com/).