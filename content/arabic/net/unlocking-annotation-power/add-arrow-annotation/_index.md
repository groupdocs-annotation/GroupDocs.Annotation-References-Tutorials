---
title: أضف تعليقًا توضيحيًا على شكل سهم إلى المستند
linktitle: أضف تعليقًا توضيحيًا على شكل سهم إلى المستند
second_title: GroupDocs.Annotation .NET API
description: تعرف على كيفية إضافة تعليقات توضيحية على شكل أسهم إلى مستنداتك باستخدام GroupDocs.Annotation لـ .NET. تعزيز وضوح الوثيقة والتفاعل دون عناء.
weight: 11
url: /ar/net/unlocking-annotation-power/add-arrow-annotation/
---

# أضف تعليقًا توضيحيًا على شكل سهم إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة تعليقات توضيحية على شكل أسهم إلى مستنداتك باستخدام GroupDocs.Annotation لـ .NET. تعتبر التعليقات التوضيحية على شكل أسهم مفيدة للإشارة إلى الاتجاه أو الإشارة إلى عناصر محددة داخل المستند.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Annotation لـ .NET: قم بتثبيت مكتبة GroupDocs.Annotation لـ .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير تم إعدادها لتطوير .NET، بما في ذلك Visual Studio أو أي بيئة تطوير متكاملة مفضلة أخرى.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية للوصول إلى الفئات والأساليب المطلوبة للتعليق التوضيحي.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تهيئة الحواشي
قم بتهيئة الحواشي من خلال توفير مسار ملف مستند الإدخال.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 2: إنشاء تعليق توضيحي للسهم
قم بإنشاء مثيل لفئة ArrowAnnotation وحدد خصائصه مثل الموضع والرسالة والعتامة ولون القلم والنمط والعرض وما إلى ذلك.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
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
## الخطوة 3: إضافة تعليق توضيحي
 قم بإضافة تعليق توضيحي على شكل سهم إلى المستند باستخدام`Add` طريقة الحواشي.
```csharp
	annotator.Add(arrow);
```
## الخطوة 4: حفظ المستند
احفظ المستند المشروح في مسار الإخراج المحدد.
```csharp
	annotator.Save(outputPath);
}
```
## الخطوة 5: عرض التأكيد
عرض رسالة تأكيد تشير إلى نجاح حفظ المستند.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
لقد نجحت الآن في إضافة تعليق توضيحي على شكل سهم إلى مستندك باستخدام GroupDocs.Annotation لـ .NET.

## خاتمة
في هذا البرنامج التعليمي، قمنا بتغطية عملية إضافة تعليقات توضيحية على شكل أسهم إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات، يمكنك تحسين مستنداتك بمؤشرات اتجاه واضحة، مما يجعلها أكثر إفادة وجاذبية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر التعليق التوضيحي للسهم؟
نعم، يمكنك تخصيص خصائص مختلفة مثل اللون والنمط والعرض والتعتيم لتناسب تفضيلاتك ومتطلبات المستند.
### هل GroupDocs.Annotation متوافق مع جميع تنسيقات المستندات؟
يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وDOCX وPPTX وXLSX والمزيد.
### هل يمكنني إضافة تعليقات توضيحية برمجيًا باستخدام GroupDocs.Annotation؟
نعم، يوفر GroupDocs.Annotation واجهات برمجة التطبيقات التي تسمح لك بإضافة التعليقات التوضيحية وتحريرها وإزالتها من المستندات برمجيًا.
### هل يقدم GroupDocs.Annotation نسخة تجريبية مجانية؟
 نعم، يمكنك تجربة GroupDocs.Annotation مجانًا عن طريق تنزيله من[هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم الفني لـ GroupDocs.Annotation؟
للحصول على الدعم الفني والمساعدة، يمكنك زيارة منتدى GroupDocs.Annotation[هنا](https://forum.groupdocs.com/c/annotation/10).