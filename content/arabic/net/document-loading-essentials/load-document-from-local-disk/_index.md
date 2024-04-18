---
title: تحميل المستند من القرص المحلي
linktitle: تحميل المستند من القرص المحلي
second_title: GroupDocs.Annotation .NET API
description: أطلق العنان لقوة التعليقات التوضيحية للمستند باستخدام GroupDocs.Annotation لـ .NET. قم بدمج ميزات التعليقات التوضيحية بسلاسة في تطبيقات .NET الخاصة بك.
type: docs
weight: 13
url: /ar/net/document-loading-essentials/load-document-from-local-disk/
---
## مقدمة
لم يكن إطلاق إمكانات التعليقات التوضيحية للمستند أسهل من أي وقت مضى مع GroupDocs.Annotation for .NET. تعمل هذه الأداة القوية على تمكين المطورين من دمج ميزات التعليقات التوضيحية القوية بسلاسة في تطبيقات .NET الخاصة بهم. في هذا الدليل الشامل، سنرشدك خلال عملية الاستفادة من GroupDocs.Annotation لـ .NET لإضافة تعليقات توضيحية إلى المستندات خطوة بخطوة. سواء كنت مطورًا متمرسًا أو بدأت للتو، سيزودك هذا البرنامج التعليمي بالمعرفة اللازمة لتعزيز التعاون في المستندات وتبسيط سير عملك.
## المتطلبات الأساسية
قبل الغوص في التعليقات التوضيحية للمستند باستخدام GroupDocs.Annotation for .NET، تأكد من توفر المتطلبات الأساسية التالية:
1. المعرفة الأساسية بـ C#: الإلمام بأساسيات لغة البرمجة C# أمر ضروري.
2. تثبيت GroupDocs.Annotation لـ .NET: قم بتنزيل وتثبيت GroupDocs.Annotation لـ .NET من[هنا](https://releases.groupdocs.com/annotation/net/).
3. بيئة التطوير: قم بإعداد بيئة تطوير باستخدام Visual Studio أو أي بيئة تطوير متكاملة (IDE) متوافقة.

## استيراد مساحات الأسماء
لبدء إضافة تعليقات توضيحية إلى المستندات باستخدام GroupDocs.Annotation لـ .NET، قم باستيراد مساحات الأسماء الضرورية إلى مشروعك:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## الخطوة 1: تحميل المستند من القرص المحلي
أولاً، تحتاج إلى تحميل المستند من القرص المحلي لديك. استخدم مقتطف الكود التالي:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 2: تحديد منطقة التعليقات التوضيحية
بعد ذلك، حدد منطقة التعليق التوضيحي. في هذا المثال، سنقوم بإنشاء AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## الخطوة 3: حفظ المستند مع التعليقات التوضيحية
بعد إضافة تعليقات توضيحية للمستند، احفظه مع التعليقات التوضيحية:
```csharp
    annotator.Save(outputPath);
}
```
## الخطوة 4: عرض رسالة النجاح
وأخيرًا، قم بعرض رسالة نجاح مع مسار الإخراج:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## خاتمة
في الختام، يوفر GroupDocs.Annotation for .NET حلاً قويًا لدمج إمكانات التعليقات التوضيحية للمستند في تطبيقات .NET الخاصة بك. باتباع هذا الدليل المفصّل خطوة بخطوة، يمكنك إضافة تعليقات توضيحية إلى المستندات بسهولة وتعزيز التعاون في مشاريعك.
## الأسئلة الشائعة
### هل يمكنني تجربة GroupDocs.Annotation لـ .NET قبل الشراء؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على وثائق GroupDocs.Annotation لـ .NET؟
 يمكنك الوصول إلى الوثائق[هنا](https://reference.groupdocs.com/annotation/net/).
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Annotation لـ .NET؟
 يمكنك الحصول على ترخيص مؤقت من[هنا](https://purchase.groupdocs.com/temporary-license/).
### هل يتوفر الدعم لـ GroupDocs.Annotation لـ .NET؟
 نعم، يمكنك العثور على الدعم في منتدى GroupDocs[هنا](https://forum.groupdocs.com/c/annotation/10).
### أين يمكنني شراء GroupDocs.Annotation لـ .NET؟
 يمكنك شراء GroupDocs.Annotation لـ .NET[هنا](https://purchase.groupdocs.com/buy).