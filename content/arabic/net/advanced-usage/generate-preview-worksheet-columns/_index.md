---
"description": "تعلّم كيفية إضافة تعليقات توضيحية إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. دليل إرشادي خطوة بخطوة لمطوري .NET. حسّن تطبيقاتك."
"linktitle": "إنشاء أعمدة ورقة عمل المعاينة"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إنشاء أعمدة ورقة عمل المعاينة"
"url": "/ar/net/advanced-usage/generate-preview-worksheet-columns/"
"weight": 15
---

# إنشاء أعمدة ورقة عمل المعاينة

## مقدمة
مرحبًا بكم في برنامجنا التعليمي الشامل حول كيفية الاستفادة من إمكانيات GroupDocs.Annotation لـ .NET! في هذا الدليل، سنشرح لك كيفية استخدام هذه الأداة الفعّالة لإضافة تعليقات توضيحية إلى المستندات بفعالية. سواء كنت مطورًا محترفًا أو جديدًا في عالم تطوير .NET، سيزودك هذا البرنامج التعليمي بالمعرفة والمهارات اللازمة لدمج ميزات التعليقات التوضيحية بسلاسة في تطبيقاتك.
## المتطلبات الأساسية
قبل الغوص في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
### 1. إعداد بيئة تطوير .NET
تأكد من تثبيت بيئة تطوير .NET فعّالة على جهازك. يمكنك تنزيل أحدث إصدار من حزمة تطوير برامج .NET من موقع مايكروسوفت الإلكتروني.
### 2. GroupDocs.Annotation لمكتبة .NET
قم بتنزيل وتثبيت مكتبة GroupDocs.Annotation لـ .NET من المجلد المقدم [رابط التحميل](https://releases.groupdocs.com/annotation/net/)اتبع تعليمات التثبيت لدمج المكتبة في مشروعك بنجاح.
### 3. مستند الإدخال
حضّر مستندًا نموذجيًا (مثل "input.xlsx") الذي تنوي إضافة تعليقات توضيحية إليه باستخدام GroupDocs.Annotation لـ .NET. تأكد من إمكانية الوصول إلى المستند من دليل مشروعك.

## استيراد مساحات الأسماء
للبدء، استورد مساحات الأسماء اللازمة إلى مشروعك. تتيح هذه المساحات الوصول إلى الفئات والأساليب اللازمة لأداء مهام شرح المستندات بفعالية.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```

الآن بعد أن قمنا بإعداد بيئة التطوير الخاصة بنا واستيراد المساحات المطلوبة، فلننتقل إلى إنشاء أعمدة ورقة عمل المعاينة لمستندنا.
## الخطوة 1: تهيئة خيارات المعاينة
```csharp
PreviewOptions previewOptions = new PreviewOptions(
    pageNumber => new FileStream(Path.Combine("Your Document Directory", $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose()
);
```
## الخطوة 2: تحديد أعمدة ورقة العمل
```csharp
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));
```
## الخطوة 3: تهيئة المُعلق باستخدام مستند الإدخال
```csharp
using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
## الخطوة 4: عرض رسالة النجاح
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## خاتمة
تهانينا! لقد تعلمت بنجاح كيفية إنشاء أعمدة ورقة عمل معاينة باستخدام GroupDocs.Annotation لـ .NET. بفضل هذه المعرفة، يمكنك الآن دمج إمكانيات التعليقات التوضيحية المتقدمة في تطبيقات .NET بسهولة.
## الأسئلة الشائعة
### هل GroupDocs.Annotation متوافق مع أطر عمل .NET الأخرى؟
نعم، يدعم GroupDocs.Annotation العديد من أطر عمل .NET، بما في ذلك .NET Core و.NET Framework.
### هل يمكنني تخصيص مظهر التعليقات التوضيحية التي تم إنشاؤها باستخدام GroupDocs.Annotation؟
بالتأكيد! يوفر GroupDocs.Annotation خيارات تخصيص شاملة لمظهر التعليقات التوضيحية، بما في ذلك اللون، والتعتيم، ونوع التعليقات التوضيحية.
### هل يدعم GroupDocs.Annotation تنسيقات المستندات الأخرى غير Excel؟
نعم، يدعم GroupDocs.Annotation مجموعة واسعة من تنسيقات المستندات، بما في ذلك PDF وWord وPowerPoint والمزيد.
### هل يتوفر الدعم الفني لمستخدمي GroupDocs.Annotation؟
نعم، يمكنك الوصول إلى الدعم الفني والمنتديات المجتمعية من خلال الخدمات المقدمة [رابط الدعم](https://forum.groupdocs.com/c/annotation/10).
### هل يمكنني تجربة GroupDocs.Annotation قبل شراء الترخيص؟
بالتأكيد! يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Annotation من [موقع إلكتروني](https://releases.groupdocs.com/).