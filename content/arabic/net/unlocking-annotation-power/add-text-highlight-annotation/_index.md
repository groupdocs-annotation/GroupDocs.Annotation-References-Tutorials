---
"description": "تعرّف على كيفية إضافة تعليقات توضيحية لتمييز النصوص إلى المستندات باستخدام GroupDocs.Annotation لـ .NET. عزّز التعاون والإنتاجية مع هذا الدليل الشامل."
"linktitle": "إضافة تعليق توضيحي لتمييز النص إلى المستند"
"second_title": "GroupDocs.Annotation .NET API"
"title": "إضافة تعليق توضيحي لتمييز النص إلى المستند"
"url": "/ar/net/unlocking-annotation-power/add-text-highlight-annotation/"
type: docs
"weight": 22
---

# إضافة تعليق توضيحي لتمييز النص إلى المستند

## مقدمة
في مجال إدارة المستندات والتعاون، تبرز GroupDocs.Annotation for .NET كحلٍّ فعّال، يُمكّن المطورين من دمج تعليقات تمييز النصوص بسلاسة في تطبيقاتهم. يُعدّ هذا البرنامج التعليمي دليلاً شاملاً لإضافة تعليقات تمييز النصوص إلى المستندات باستخدام GroupDocs.Annotation for .NET. من خلال التعليمات التفصيلية والشروحات المُفصّلة، ستُتقن استخدام إمكانيات هذه المكتبة الفعّالة.
## المتطلبات الأساسية
قبل الخوض في تنفيذ تعليقات تمييز النص، تأكد من توفر المتطلبات الأساسية التالية:
1. إعداد البيئة: قم بإعداد بيئة تطوير مناسبة لتطوير .NET.
2. تثبيت GroupDocs.Annotation لـ .NET: قم بتنزيل GroupDocs.Annotation لـ .NET وتثبيته من المجلد المقدم [رابط التحميل](https://releases.groupdocs.com/annotation/net/).
3. المعرفة بلغة C#: فهم أساسي للغة البرمجة C#.
4. المستند الذي تريد التعليق عليه: قم بإعداد مستند (على سبيل المثال، PDF) الذي تنوي التعليق عليه.

## استيراد مساحات الأسماء
للبدء، قم باستيراد المساحات الأساسية اللازمة في كود C# الخاص بك للاستفادة من وظائف GroupDocs.Annotation لـ .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#الآن، دعنا نقسم عملية إضافة تعليقات تمييز النص إلى خطوات متعددة:
## الخطوة 1: تحديد مسار الإخراج
حدد مسار الإخراج حيث سيتم حفظ المستند الموضح:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## الخطوة 2: تهيئة المُعلّق
إنشاء مثيل لـ `Annotator` الفئة، تمرير اسم ملف المستند كمعلمة:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## الخطوة 3: إنشاء تعليق توضيحي مميز
إنشاء مثيل `HighlightAnnotation` الكائن وتكوين خصائصه:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## الخطوة 4: إضافة التعليقات التوضيحية
أضف التعليق التوضيحي المميز الذي تم إنشاؤه إلى المستند:
```csharp
annotator.Add(highlight);
```
## الخطوة 5: حفظ المستند الموضح
احفظ المستند الموضح في مسار الإخراج المحدد:
```csharp
annotator.Save(outputPath);
```

## خاتمة
في الختام، يُقدم GroupDocs.Annotation لـ .NET نهجًا مُبسطًا لدمج تعليقات تمييز النصوص في المستندات. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يُمكن للمطورين تحسين التعاون والإنتاجية في المستندات بسلاسة داخل تطبيقاتهم.
## الأسئلة الشائعة
### هل GroupDocs.Annotation لـ .NET متوافق مع كافة تنسيقات المستندات؟
يدعم GroupDocs.Annotation لـ .NET تنسيقات مستندات متنوعة، بما في ذلك PDF وWord وExcel وغيرها. راجع الوثائق للاطلاع على القائمة الكاملة.
### هل يمكن تخصيص التعليقات التوضيحية وفقًا لمتطلبات محددة؟
نعم، يتمتع المطورون بالتحكم الكامل في خصائص ومظهر التعليقات التوضيحية، مما يسمح بالتخصيص لتلبية الاحتياجات المتنوعة.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Annotation لـ .NET؟
نعم، يمكنك استكشاف ميزات GroupDocs.Annotation لـ .NET من خلال الوصول إلى الإصدار التجريبي المجاني من الموقع المقدم [وصلة](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم لأي مشاكل أو استفسارات متعلقة بـ GroupDocs.Annotation لـ .NET؟
للحصول على الدعم والمساعدة، يمكنك زيارة منتدى GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10).
### ما هي خيارات الترخيص المتاحة لـ GroupDocs.Annotation لـ .NET؟
يوفر GroupDocs.Annotation لـ .NET خيارات ترخيص متنوعة، بما في ذلك تراخيص مؤقتة لأغراض الاختبار وتراخيص تجارية لبيئات الإنتاج. تفضل بزيارة صفحة الشراء. [هنا](https://purchase.groupdocs.com/buy) لمزيد من التفاصيل.