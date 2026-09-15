---
categories:
- Document Management
date: '2026-07-06'
description: تعلم كيفية تكوين بيانات اعتماد AWS وتكامل GroupDocs Annotation مع Amazon
  S3 باستخدام C#. دليل خطوة بخطوة لتحميل المستندات وتعليقها وإدارتها.
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: تحميل المستند من Amazon S3
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: تكوين بيانات اعتماد AWS لتكامل GroupDocs Annotation مع S3
type: docs
url: /ar/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# تكوين بيانات اعتماد AWS لتكامل GroupDocs Annotation مع S3

في هذا الدرس ستتعلم كيفية **تكوين بيانات اعتماد AWS** وتكامل GroupDocs.Annotation بسلاسة مع Amazon S3 باستخدام C#. سنستعرض تحميل مستند من دلو S3، إضافة التعليقات التوضيحية، وحفظ النتيجة مرة أخرى إلى السحابة، مع تغطية نصائح الأمن والأداء وفق أفضل الممارسات.

## إجابات سريعة
- **كيف يمكنني تكوين بيانات اعتماد AWS؟** استخدم مُنشئ `AmazonS3Client` مع `BasicAWSCredentials` أو اعتمد على أدوار IAM لحل البيانات تلقائيًا.  
- **ما هي حزم NuGet المطلوبة؟** `GroupDocs.Annotation` و `AWSSDK.S3`.  
- **هل يمكنني إضافة تعليقات توضيحية إلى ملفات PDF أكبر من 100 ميجابايت؟** نعم – استخدم البث وواجهات برمجة التطبيقات غير المتزامنة لتجنب تحميل الملف بالكامل في الذاكرة.  
- **هل التكامل آمن من حيث تعدد الخيوط؟** أنشئ نسخة منفصلة من `Annotator` لكل طلب؛ الـ SDK نفسه لا يحتفظ بحالة.  
- **هل أحتاج إلى تشفير المستندات في S3؟** فعّل التشفير من جانب الخادم (SSE‑S3 أو SSE‑KMS) للامتثال وحماية البيانات.

## لماذا نستخدم S3 لتعليق المستندات؟

استخدام S3 لتعليق المستندات يمنحك حلاً للتخزين عالي القابلية للتوسع، وفعّال من حيث التكلفة، ومتوفراً عالمياً مع الحفاظ على أمان ملفاتك.  
- **Scalability**: S3 يتعامل مع عدد غير محدود من الكائنات، يدعم حتى 5 TB لكل ملف وملايين الطلبات في الثانية.  
- **Cost‑Effectiveness**: تدفع فقط مقابل التخزين الذي تستخدمه فعليًا، مع تصنيف تلقائي إلى فئات أقل تكلفة.  
- **Global Accessibility**: وصول منخفض الكمون من أي منطقة AWS يضمن أن مستنداتك المُعَلَّقة دائمًا متاحة.  
- **Security**: تشفير مدمج (SSE‑S3، SSE‑KMS) وسياسات IAM دقيقة تحمي البيانات الحساسة.  
- **Integration**: يعمل بشكل أصلي مع خدمات AWS الحالية مثل CloudFront و Lambda و IAM.

## المتطلبات المسبقة

قبل أن نبدأ في البناء، تأكد من توفر الأساسيات التالية:

1. **بيئة تطوير C#** – Visual Studio أو VS Code مع دعم .NET.  
2. **GroupDocs.Annotation لـ .NET** – تحميل من [الموقع الرسمي](https://releases.groupdocs.com/annotation/net/).  
3. **الوصول إلى AWS S3** – بيانات اعتماد AWS صالحة مع أذونات القراءة/الكتابة على الدلو المستهدف.  
4. **معرفة أساسية بـ C#** – فهم الفئات، async/await، وتدفقات البيانات.  
5. **Amazon S3 SDK** – تثبيت عبر NuGet (`AWSSDK.S3`).  

## كيفية تكوين بيانات اعتماد AWS للوصول إلى S3؟

`BasicAWSCredentials` هي فئة تحتفظ بمعرف مفتاح وصول AWS ومفتاح الوصول السري.  
`AmazonS3Client` هو عميل AWS SDK المستخدم للتفاعل مع خدمات S3.

حمّل مفاتيح AWS مرة واحدة ودع الـ SDK يعيد استخدامها في كل طلب. أبسط طريقة هي إنشاء كائن `BasicAWSCredentials` وتمريره إلى مُنشئ `AmazonS3Client`. لأعباء العمل الإنتاجية، يفضَّل استخدام أدوار IAM أو متغيّرات البيئة لتجنب كتابة الأسرار صراحةً.

**نصيحة احترافية:** عند التشغيل على EC2 أو ECS أو Lambda، احذف بيانات الاعتماد الصريحة ودع الـ SDK يسترجع تلقائيًا بيانات الاعتماد المؤقتة من ملف تعريف المثيل.

## استيراد مساحات الأسماء

لنبدأ باستيراد جميع مساحات الأسماء الضرورية لتكامل S3 الخاص بنا:

```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

هذه الاستيرادات تمنحنا الوصول إلى عمليات AWS S3 ووظائف التعليق في GroupDocs. مساحة الأسماء `Amazon.S3` تتعامل مع تفاعلات التخزين السحابي، بينما `GroupDocs.Annotation.Models` توفر إطار العمل للتعليقات.

## تنفيذ خطوة بخطوة

الآن دعنا نستعرض العملية الكاملة لتحميل مستند من S3 وإضافة تعليقات توضيحية. سنقسم ذلك إلى خطوات قابلة للإدارة يمكنك اتباعها.

### الخطوة 1: تعريف مسار الإخراج

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

هذا ينشئ مسارًا محليًا حيث سيتم حفظ المستند المُعَلَّق. طريقة `Path.Combine` تضمن توافقًا عبر الأنظمة، ونحن نحافظ على امتداد الملف الأصلي للحفاظ على سلامة نوع المستند.

**نصيحة احترافية**: فكر في استخدام طابع زمني في اسم ملف الإخراج لتجنب الكتابة فوق التعليقات السابقة: `"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`.

### الخطوة 2: تحديد مفتاح المستند

```csharp
string key = "sample.pdf";
```

هذا هو المعرف الفريد للمستند في دلو S3. في السيناريوهات الواقعية، ستحصل عادةً على هذا من إدخال المستخدم أو سجل قاعدة البيانات أو معلمة API. تأكد من أن المفتاح يطابق تمامًا اسم كائن S3، بما في ذلك أي بادئات مجلد (مثال: `documents/2025/sample.pdf`).

### الخطوة 3: تهيئة Annotator

`Annotator` هو الفئة الأساسية في GroupDocs.Annotation التي تمثل جلسة مستند قابلة للتحرير. توفر طرقًا لإضافة وتعديل وحذف التعليقات.

```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

من خلال تغليف تدفق تحميل S3 داخل كتلة `using`، نضمن التخلص السليم من كل من التدفق وكائن الـ annotator.

### الخطوة 4: إنشاء تعليقات توضيحية من النوع Area

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

هذا ينشئ تعليقًا مستطيليًا على المستند. معلمات `Rectangle(100, 100, 100, 100)` تمثل موضع X، موضع Y، العرض، والارتفاع على التوالي. قيمة `BackgroundColor` `65535` تُنشئ تمييزًا أصفر – يمكنك تخصيص ذلك باستخدام رموز ألوان RGB القياسية.

**حالات الاستخدام الشائعة لتعليقات Area**:
- تمييز الأقسام المهمة في العقود  
- وضع علامات على مناطق المراجعة في المواصفات التقنية  
- إضافة إشارات بصرية إلى شرائح العروض التقديمية  

### الخطوة 5: إضافة التعليق التوضيحي إلى المستند

```csharp
annotator.Add(area);
```

هذه الطريقة تضيف تعليق الـ area إلى المستند. يمكنك استدعاء `Add()` عدة مرات لتضمين أنواع مختلفة من التعليقات مثل تعليقات النص، الأسهم، أو الأختام. تبقى التعليقات في الذاكرة حتى تقوم بحفظ المستند صراحةً.

### الخطوة 6: حفظ المستند المُعَلَّق

```csharp
annotator.Save(outputPath);
```

الآن نقوم بحفظ المستند المُعَلَّق إلى مسار الإخراج المحدد. هذا ينشئ ملفًا جديدًا يحتوي على جميع التعليقات المدمجة. إذا كنت بحاجة لتخزين النتيجة مرة أخرى في S3—وهو سيناريو شائع في الإنتاج—فقط قم بتحميل الملف باستخدام SDK الخاص بـ S3 بعد هذه الخطوة.

### الخطوة 7: عرض رسالة النجاح

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

رسالة تأكيد بسيطة تساعد في تصحيح الأخطاء وتوفر ملاحظات للمستخدم. في تطبيق حقيقي ستستبدلها بسجلات مناسبة أو إشعارات واجهة المستخدم.

## تنفيذ طريقة تحميل S3

ستلاحظ أننا أشرنا إلى طريقة `DownloadFile(key)` التي لم نقم بتنفيذها بعد. إليك كيفية إنشاء هذه المساعدة الأساسية:

```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**ملاحظة أمان**: لا تقم أبدًا بكتابة بيانات اعتماد AWS صراحةً في كود الإنتاج. استخدم أدوار IAM أو متغيّرات البيئة أو ملف بيانات الاعتماد المشترك لإبقاء الأسرار خارج التحكم في المصدر.

## كيفية تحميل مستند من Amazon S3؟

`GetObjectAsync` هي طريقة غير متزامنة تسترجع كائنًا من S3 وتعيد استجابة تحتوي على تدفق.  
`MemoryStream` هو تدفق .NET يخزن البيانات في الذاكرة، مما يسمح بقراءة/كتابة سريعة دون إدخال/إخراج من القرص.  
`Annotator` (كما عُرِّف سابقًا) هو الفئة التي تحمل المستند للتعليق.

حمّل ملف PDF مباشرة من S3 باستخدام طريقة `GetObjectAsync`، غلف تدفق الاستجابة داخل `MemoryStream`، ومرره إلى مُنشئ `Annotator`. هذا النهج يتجنب كتابة الملف الأصلي إلى القرص، يقلل من عبء الإدخال/الإخراج، ويمكنك من العمل مع ملفات كبيرة بكفاءة مع الحفاظ على استهلاك الذاكرة تحت السيطرة.

```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## المشكلات الشائعة في التكامل والحلول

استنادًا إلى خبرة التنفيذ في العالم الحقيقي، إليك أكثر المشكلات شيوعًا التي قد تواجهها وكيفية حلها:

### المشكلة 1: أخطاء "Access Denied"
**Problem**: تطبيقك لا يستطيع الوصول إلى كائنات S3.  
**Solution**: تحقق من أن مستخدم IAM أو الدور الخاص بك يمتلك صلاحية `s3:GetObject` للدلو والكائنات المحددة.

### المشكلة 2: مهلات الملفات الكبيرة
**Problem**: المستندات التي تزيد عن 50 ميجابايت تتسبب في أخطاء مهلة.  
**Solution**: نفّذ عمليات غير متزامنة وزد قيم المهلة:

```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### المشكلة 3: مشكلات الذاكرة مع مستندات متعددة
**Problem**: معالجة العديد من المستندات تتسبب في استثناءات نفاد الذاكرة.  
**Solution**: تخلص من التدفقات بسرعة وعالج المستندات على دفعات.

### المشكلة 4: أخطاء عدم تطابق المنطقة
**Problem**: عميل S3 لا يستطيع تحديد موقع الدلو الخاص بك.  
**Solution**: تأكد من أن `RegionEndpoint` يطابق المنطقة الفعلية للدلو.

## أفضل ممارسات الأداء والأمان

### تحسين الأداء
- **Use Async Methods**: يفضَّل `GetObjectAsync()` على الاستدعاءات المتزامنة.  
- **Implement Caching**: خزن المستندات التي يتم الوصول إليها بشكل متكرر محليًا لفترة قصيرة.  
- **Batch Operations**: عالج ملفات متعددة بشكل متوازي عندما يكون ذلك مناسبًا.  
- **Stream Processing**: تجنّب تحميل المستندات الكبيرة بالكامل في الذاكرة؛ اعمل مع التدفقات.

### اعتبارات الأمان
- **Use IAM Roles**: أزل بيانات الاعتماد المكتوبة صراحةً.  
- **Enable S3 Encryption**: فعّل التشفير من جانب الخادم (SSE‑S3 أو SSE‑KMS).  
- **Implement Access Logging**: تتبع من يصل إلى أي مستندات.  
- **Validate File Types**: تحقق من الامتدادات وأنواع MIME قبل المعالجة.

## حالات الاستخدام في العالم الحقيقي

نمط تكامل S3 هذا يبرز في العديد من الصناعات:

1. **مراجعة المستندات القانونية** – مكاتب المحاماة تُعلّق العقود المخزنة في S3.  
2. **منصات التعليم** – المعلمون يعلّقون ملفات الطلاب المستضافة في السحابة.  
3. **إدارة الإنشاءات** – المعماريون يعلّقون المخططات عبر المناطق.  
4. **السجلات الطبية** – مقدمو الرعاية الصحية يضيفون ملاحظات إلى مستندات المرضى بأمان.  
5. **الخدمات المالية** – المدققون يتعاونون على مستندات الامتثال المخزنة في S3.

## دليل استكشاف الأخطاء وإصلاحها

**Cannot Load Document from S3**  
- تحقق من بيانات اعتماد AWS وأذونات الدلو.  
- أعد فحص اسم الدلو ومفتاح الكائن للتأكد من صحة التهجئة.  
- تأكد من أن المستند غير تالف في S3.

**Annotations Not Appearing**  
- تأكد من أنك استدعيت `annotator.Save()` بعد إضافة التعليقات.  
- تحقق من أن تنسيق المستند يدعم نوع التعليق الذي استخدمته.  
- تأكد من أن إحداثيات التعليق ضمن حدود الصفحة.

**Performance Issues**  
- راقب معدلات طلبات S3 ونفّذ تقنية back‑off المتدرجة.  
- استخدم CDN CloudFront للملفات التي يتم الوصول إليها بشكل متكرر.  
- فكر في تفعيل S3 Transfer Acceleration للتطبيقات العالمية.

## الأسئلة المتكررة

**س: هل GroupDocs.Annotation لـ .NET متوافق مع جميع تنسيقات المستندات؟**  
ج: يدعم GroupDocs.Annotation أكثر من 50 تنسيقًا للإدخال والإخراج – بما في ذلك PDF و DOCX و PPTX و HTML – رغم أن أنواع التعليقات قد تختلف حسب التنسيق.

**س: هل يمكنني تجربة GroupDocs.Annotation لـ .NET قبل الشراء؟**  
ج: نعم، يمكنك استكشاف ميزات GroupDocs.Annotation لـ .NET عبر النسخة التجريبية المجانية المتاحة [هنا](https://releases.groupdocs.com/). يتيح لك ذلك اختبار تكامل S3 وقدرات التعليق دون مخاطر.

**س: أين يمكنني العثور على وثائق GroupDocs.Annotation لـ .NET؟**  
ج: الوثائق الشاملة لـ GroupDocs.Annotation لـ .NET متوفرة [هنا](https://tutorials.groupdocs.com/annotation/net/). تشمل المراجع API، أمثلة متقدمة، وأدلة التكامل.

**س: هل أحتاج إلى ترخيص مؤقت لتقييم GroupDocs.Annotation لـ .NET؟**  
ج: يمكنك الحصول على ترخيص مؤقت لأغراض التقييم من [هنا](https://purchase.groupdocs.com/temporary-license/). يزيل هذا القيود التجريبية ويمنحك وصولًا كاملًا لاختبار سيناريوهات الإنتاج.

**س: أين يمكنني طلب المساعدة أو الدعم لـ GroupDocs.Annotation لـ .NET؟**  
ج: لأي استفسارات أو مشكلات دعم، يمكنك زيارة منتدى GroupDocs.Annotation [هنا](https://forum.groupdocs.com/c/annotation/10). المجتمع وفريق الدعم نشطان ومفيدان في حل مشاكل التكامل.

**س: هل يمكنني حفظ المستندات المُعَلَّقة مرة أخرى إلى S3 بدلاً من التخزين المحلي؟**  
ج: بالتأكيد! بعد استدعاء `annotator.Save(localPath)`, يمكنك رفع الملف المُعَلَّق إلى S3 باستخدام طريقة `PutObjectAsync()`. هذا يخلق تدفقًا كاملاً من السحابة إلى السحابة مثاليًا لتطبيقات الويب.

**س: ما هو الحد الأقصى لحجم الملف المدعوم لتعليق المستندات في S3؟**  
ج: بينما يمكن لـ GroupDocs.Annotation التعامل مع ملفات كبيرة، فإن الحدود العملية تعتمد على ذاكرة الخادم ووقت مهلة نقل S3. للملفات التي تتجاوز 100 ميجابايت، يُنصح بتنفيذ البث أو المعالجة على أجزاء لتجنب استنزاف الذاكرة.

---

**آخر تحديث:** 2026-07-06  
**تم الاختبار مع:** GroupDocs.Annotation 23.12 for .NET  
**المؤلف:** GroupDocs  

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## دروس ذات صلة

- [تحميل مستندات GroupDocs.Annotation .NET](/annotation/net/document-loading-essentials/)
- [كيفية تحميل المستندات من FTP .NET - دليل GroupDocs الكامل](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [دروس معاينة المستندات .NET - دليل GroupDocs.Annotation الكامل](/annotation/net/document-preview/)
