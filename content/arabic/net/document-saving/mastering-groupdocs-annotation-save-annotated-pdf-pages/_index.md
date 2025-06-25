---
"date": "2025-05-06"
"description": "تعرّف على كيفية حفظ الصفحات المُعلّقة فقط من ملف PDF بكفاءة باستخدام GroupDocs.Annotation لـ .NET. حسّن إدارة المستندات والتعاون مع الآخرين من خلال هذا الدليل المُفصّل."
"title": "كيفية حفظ الصفحات المُعلّقة في ملف PDF باستخدام GroupDocs.Annotation لـ .NET"
"url": "/ar/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# كيفية حفظ الصفحات المُعلّقة في ملف PDF باستخدام GroupDocs.Annotation لـ .NET

## مقدمة

هل تواجه صعوبة في حفظ صفحات مُعلّقة مُحددة من مستندات PDF؟ يُوضّح هذا الدليل الشامل كيفية تحقيق ذلك بكفاءة باستخدام GroupDocs.Annotation لـ .NET. من خلال الاستفادة من إمكانيات الشرح، يُمكنك تبسيط إدارة المستندات وتعزيز التعاون بالتركيز على المحتوى ذي الصلة.

في هذا البرنامج التعليمي، سوف تتعلم:
- إعداد بيئة التطوير الخاصة بك باستخدام GroupDocs.Annotation
- إضافة أنواع مختلفة من التعليقات التوضيحية
- حفظ الصفحات الموضحة فقط بشكل فعال

هل أنت مستعد للبدء؟ تأكد من أن كل شيء جاهز.

### المتطلبات الأساسية

قبل البدء، تأكد من أن لديك ما يلي:
- **إطار عمل .NET** (الإصدار 4.6 أو أحدث) أو **.NET Core/5+**
- محرر أكواد مثل Visual Studio
- المعرفة الأساسية بإعداد مشروع C# و.NET

## إعداد GroupDocs.Annotation لـ .NET

لبدء استخدام GroupDocs.Annotation، قم بتثبيته عبر NuGet.

**وحدة تحكم مدير الحزم NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### الحصول على الترخيص

تقدم GroupDocs نسخة تجريبية مجانية لاستكشاف برنامجها بالكامل. للاستخدام الممتد، اشترِ ترخيصًا أو اطلب ترخيصًا مؤقتًا:
- **نسخة تجريبية مجانية**:استكشف الميزات دون قيود لفترة أولية.
- **رخصة مؤقتة**:استخدم GroupDocs.Annotation في الإنتاج مؤقتًا.
- **شراء**:تأمين احتياجاتك طويلة الأمد من خلال ترخيص تجاري.

بمجرد التثبيت، قم بتشغيل المكتبة على النحو التالي:

```csharp
using GroupDocs.Annotation;

// الإعداد الأساسي لتحميل المستندات والتعليق عليها
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## دليل التنفيذ

### إضافة التعليقات التوضيحية

#### ملخص

تساعد التعليقات التوضيحية في إبراز الجوانب المهمة في مستندك. لنستكشف إضافة `AreaAnnotation` و `EllipseAnnotation`.

**الخطوة 1: إنشاء شرح المنطقة**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// تعريف شرح المنطقة
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // الموقع والحجم
    BackgroundColor = 65535,                // قيمة لون ARGB للتمييز
    PageNumber = 1                          // رقم الصفحة المحدد
};
```

ال `AreaAnnotation` يُبرز منطقة مستطيلة في المستند. خصّص موضعها (`Box`) ولون الخلفية.

**الخطوة 2: إنشاء شرح القطع الناقص**

```csharp
// تعريف شرح القطع الناقص
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // الموقع والحجم
    BackgroundColor = 123456,                // قيمة لون ARGB للتمييز
    PageNumber = 1                           // رقم الصفحة المحدد
};
```

ال `EllipseAnnotation` يسمح برسم شكل بيضاوي على المستند. اضبط الموضع والأبعاد باستخدام `Box` ملكية.

**الخطوة 3: إضافة التعليقات التوضيحية**

```csharp
// إضافة التعليقات التوضيحية إلى مثيل Annotator
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

باستخدام `Add` تتضمن هذه الطريقة أنواعًا متعددة من التعليقات التوضيحية. تضيف هذه الخطوة كلا من `AreaAnnotation` و `EllipseAnnotation`.

### حفظ الصفحات الموضحة فقط

#### ملخص

لحفظ الصفحات التي تحتوي على تعليقات توضيحية فقط، قم بتكوين خيارات الحفظ وفقًا لذلك.

**الخطوة 4: حفظ الصفحات الموضحة**

```csharp
using GroupDocs.Annotation.Options;

// إعداد خيارات الحفظ لتشمل الصفحات الموضحة فقط
annotator.Save("path/to/output/document.pdf\