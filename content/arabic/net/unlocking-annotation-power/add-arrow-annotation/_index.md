---
"description": "تعرّف على كيفية إضافة تعليقات الأسهم إلى مستنداتك باستخدام GroupDocs.Annotation لـ .NET. حسّن وضوح مستنداتك وتفاعليتها بسهولة."
"linktitle": "إضافة تعليق السهم إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق السهم إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-arrow-annotation/"
"weight": 11
---

# إضافة تعليق السهم إلى المستند

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية إضافة تعليقات الأسهم إلى مستنداتك باستخدام GroupDocs.Annotation لـ .NET. تُعد تعليقات الأسهم مفيدة للإشارة إلى الاتجاهات أو عناصر محددة داخل المستند.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
1. GroupDocs.Annotation لـ .NET: ثبّت مكتبة GroupDocs.Annotation لـ .NET. يمكنك تنزيلها من [هنا](https://releases.groupdocs.com/annotation/net/).
2. بيئة التطوير: تأكد من إعداد بيئة تطوير لتطوير .NET، بما في ذلك Visual Studio أو أي بيئة تطوير متكاملة أخرى مفضلة.

## استيراد مساحات الأسماء
أولاً، يتعين عليك استيراد مساحات الأسماء الضرورية للوصول إلى الفئات والطرق المطلوبة للتعليق التوضيحي.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## الخطوة 1: تهيئة المُعلّق
قم بتهيئة المشرح من خلال توفير مسار ملف المستند الإدخالي.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## الخطوة 2: إنشاء تعليق السهم
قم بإنشاء مثيل لفئة ArrowAnnotation وقم بتعريف خصائصها مثل الموضع والرسالة والتعتيم ولون القلم والأسلوب والعرض وما إلى ذلك.
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
## الخطوة 3: إضافة التعليقات التوضيحية
أضف تعليق السهم إلى المستند باستخدام `Add` طريقة المشرح.
```csharp
	annotator.Add(arrow);
```
## الخطوة 4: حفظ المستند
احفظ المستند الموضح في مسار الإخراج المحدد.
```csharp
	annotator.Save(outputPath);
}
```
## الخطوة 5: عرض التأكيد
عرض رسالة تأكيد تشير إلى نجاح حفظ المستند.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
لقد قمت الآن بإضافة تعليق سهمي إلى مستندك بنجاح باستخدام GroupDocs.Annotation لـ .NET.

## خاتمة
في هذا البرنامج التعليمي، تناولنا عملية إضافة تعليقات الأسهم إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. باتباع هذه الخطوات، يمكنك تحسين مستنداتك بمؤشرات اتجاهية واضحة، مما يجعلها أكثر إفادة وتفاعلية.
## الأسئلة الشائعة
### هل يمكنني تخصيص مظهر تعليق السهم؟
نعم، يمكنك تخصيص خصائص مختلفة مثل اللون والأسلوب والعرض والتعتيم لتناسب متطلبات الدروس والمستندات الخاصة بك.
### هل GroupDocs.Annotation متوافق مع كافة تنسيقات المستندات؟
يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وDOCX وPPTX وXLSX والمزيد.
### هل يمكنني إضافة التعليقات التوضيحية برمجيًا باستخدام GroupDocs.Annotation؟
نعم، يوفر GroupDocs.Annotation واجهات برمجة التطبيقات التي تسمح لك بإضافة التعليقات التوضيحية وتحريرها وإزالتها من المستندات بطريقة برمجية.
### هل يقدم GroupDocs.Annotation نسخة تجريبية مجانية؟
نعم، يمكنك تجربة GroupDocs.Annotation مجانًا عن طريق تنزيله من [هنا](https://releases.groupdocs.com/).
### أين يمكنني الحصول على الدعم الفني لـ GroupDocs.Annotation؟
للحصول على الدعم الفني والمساعدة، يمكنك زيارة منتدى GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).