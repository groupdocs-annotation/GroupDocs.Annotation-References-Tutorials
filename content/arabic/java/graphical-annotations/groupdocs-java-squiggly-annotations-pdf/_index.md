---
categories:
- Java Development
date: '2026-05-16'
description: تعلم كيفية إنشاء ردود التعليقات في Java باستخدام GroupDocs.Annotation.
  إتقان تعليقات PDF في Java مع أمثلة عملية، ونصائح الأداء، وأفضل الممارسات.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: دليل Java PDF Annotation
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'مكتبة Java PDF Annotation: إنشاء رد على التعليق في Java'
type: docs
url: /ar/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# مكتبة جافا لتعليقات PDF: إنشاء رد على التعليق في جافا

إذا كنت بحاجة إلى **create annotation reply java** لملفات PDF — سواء كنت تبني بوابة مراجعة عقود، أو نظام تعلم إلكتروني، أو خط أنابيب معالجة جماعية — فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك باستخدام GroupDocs.Annotation للغة جافا. سنستعرض الإعداد، إنشاء تعليقات squiggly، خيوط الردود، وتحسين الأداء حتى تتمكن من نشر حل موثوق خلال أيام، وليس أسابيع.

## إجابات سريعة
- **What is the primary purpose of GroupDocs.Annotation?** يتيح إنشاء وتعديل واستخراج تعليقات PDF برمجيًا في جافا.  
- **How do I add a squiggly annotation?** إنشاء كائن `SquigglyAnnotation`، ضبط الهندسة والنمط، ثم استدعاء `annotator.add(...)`.  
- **Can I attach replies to an annotation?** نعم — أنشئ كائنات `Reply`، حدد المؤلف والنص، واربطها بالتعليق الأصلي.  
- **Do I need a license for production?** بالتأكيد؛ بدون ترخيص صالح سيحتوي الناتج على علامات مائية.  
- **Is it suitable for batch processing?** نعم — استخدم try‑with‑resources لفتح كل مستند، إضافة التعليقات، وإغلاقه، مع الحفاظ على استهلاك الذاكرة منخفضًا.

## لماذا يحتاج مطورو جافا إلى مكتبات تعليقات PDF

التعليق اليدوي على ملفات PDF يستغرق وقتًا طويلاً وعرضة للأخطاء، خاصةً عندما تحتاج إلى مراجعة مئات العقود أو أوراق الامتحانات. تقوم مكتبة تعليقات PDF لجافا بأتمتة هذه العملية، مما يتيح لك تضمين التظليل، الخطوط المتموجة، والتعليقات المتسلسلة مباشرةً في الملف. النتيجة هي مستند قابل للبحث ومحمول يحتفظ بجميع التعليقات دون الحاجة إلى عارض منفصل.

**ما ستتقنه في هذا الدليل**
- تثبيت وترخيص GroupDocs.Annotation في مشروع Maven  
- بناء تعليقات squiggly التي تبدو كخطوط تحتية أصلية في Word  
- إضافة ردود متسلسلة إلى أي تعليق للمراجعة التعاونية  
- تحسين استخدام الذاكرة والمعالج عند معالجة ملفات PDF الكبيرة  
- نشر الحل في Spring Boot، أو الخدمات المصغرة، أو تطبيقات سطح المكتب  

سواءً كنت تبني نظام مراجعة مستندات قانونية، أو أداة تقييم تعليمية، أو خط أنابيب مراقبة جودة آلي، فإن التقنيات أدناه ستوفر لك أساسًا جاهزًا للإنتاج.

## ما هو create annotation reply java؟

`create annotation reply java` هو العملية البرمجية لإرفاق سلسلة تعليقات (Reply) بتعليق PDF موجود باستخدام جافا. تتيح الردود لعدة مراجعين مناقشة علامة محددة دون مغادرة المستند، مما يحقق تعاونًا سلسًا داخل المستند. هذه القدرة تحول PDF ثابت إلى منصة مناقشة تفاعلية، مع الحفاظ على السياق وسجلات التدقيق داخل الملف.

## المتطلبات المسبقة: تجهيز بيئتك

قبل الغوص في الشيفرة، تأكد من أن محطة عمل التطوير الخاصة بك تلبي المواصفات التالية:
- **JDK** 8 أو أعلى (يوصى بـ JDK 11 + لأداء أفضل في جمع القمامة)  
- **Maven** أو **Gradle** لإدارة التبعيات (الأمثلة تستخدم Maven)  
- بيئة تطوير متكاملة (IDE) تدعم Maven (IntelliJ IDEA، Eclipse، أو VS Code)  
- على الأقل **2 GB** من الذاكرة العشوائية المتاحة للـ IDE وتشغيل الاختبارات  
- ملفات PDF تجريبية للتجربة (يمكنك إنشاء ملفات PDF بسيطة بأي محرر PDF)

GroupDocs.Annotation يعمل بالكامل داخل العملية؛ لا يلزم أي عارض PDF خارجي أو مكتبات أصلية.

## إعداد GroupDocs.Annotation للغة جافا

دمج المكتبة هو عملية من عدة خطوات، لكن بعض العقبات الخفية قد تتسبب في أخطاء وقت التشغيل إذا تم تجاهلها.

### تكوين تبعية Maven

أضف المستودع والتبعية إلى ملف `pom.xml`. ضع عنصر `<repositories>` **قبل** `<dependencies>` لضمان قدرة Maven على حل القطعة.

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

> **نصيحة احترافية:** تحقق من صفحة إصدارات GroupDocs للحصول على أحدث نسخة. الإصدارات الجديدة غالبًا ما تشمل دعمًا للمعايير الناشئة لـ PDF وتحسينات في الأداء.

### إعداد الترخيص (لا تتخطى هذه الخطوة!)

GroupDocs.Annotation يتطلب ملف ترخيص للاستخدام في الإنتاج. بدون ذلك، سيحمل كل PDF مُولد علامة مائية.

1. **Free Trial** – مجموعة كاملة من الميزات لمدة 30 يومًا، مثالية للتقييم.  
2. **Temporary License** – مناسبة للتطوير والاختبار الداخلي.  
3. **Full License** – مطلوبة لأي نشر تجاري.

ضع ملف `GroupDocs.Annotation.lic` في مجلد الموارد الخاص بك وحمّله عند بدء التشغيل:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **خطأ شائع:** نسيان خطوة الترخيص يؤدي إلى ملفات PDF ذات علامات مائية واستدعاءات API تفشل بصمت. تأكد دائمًا من التحقق من الترخيص مبكرًا في روتين بدء التشغيل.

## دليل التنفيذ الكامل: إضافة تعليقات Squiggly

فيما يلي دليل خطوة بخطوة يوضح كيفية **create annotation reply java** أثناء بناء تعليق squiggly. كل خطوة تتضمن شرحًا مختصرًا، لتفهم “السبب” وراء كل سطر.

### الخطوة 1: استيراد جميع الفئات المطلوبة

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` هو نقطة الدخول لجميع عمليات مستوى المستند.  
- `Point` يمثل إحداثيًا على الصفحة (X و Y مقاسان من الزاوية العلوية اليسرى).  
- `SquigglyAnnotation` يحدد الخط المتموج المستخدم لتسليط الضوء على الأخطاء.  
- `Reply` يخزن التعليقات المتسلسلة المرفقة بالتعليق.  
- `SaveOptions` يسمح لك بالتحكم في تنسيق الإخراج والضغط.

### الخطوة 2: إنشاء وتكوين تعليق Squiggly الخاص بك

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

`SquigglyAnnotation` هي فئة تنشئ خطًا متموجًا يستخدم لتسليط الضوء على الأخطاء في PDF.

- **نظام الإحداثيات**: تبدأ النقاط من الزاوية العلوية اليسرى. النقطتان أعلاه ترسمان خطًا متموجًا أفقيًا من (100, 200) إلى (300, 200).  
- **الشفافية** 0.7 يعني أن التعليق شفاف بنسبة 70 %، مما يسمح للنص الأساسي بالبقاء قابلًا للقراءة.

### الخطوة 3: إضافة ردود تفاعلية (اختياري لكن قوي)

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

`Reply` هي فئة تمثل سلسلة تعليقات مرفقة بتعليق.

- الردود تنشئ **نقاشًا متسلسلًا** مباشرة على التعليق، مشابه لتجربة مراجعى PDF الحديثة.  
- كل رد يخزن معلومات المؤلف والطابع الزمني، والذي يمكنك لاحقًا تصفيته أو عرضه في واجهة المستخدم.

### الخطوة 4: تطبيق التعليق وحفظ المستند

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- بنية **try‑with‑resources** تغلق تلقائيًا `Annotator`، وتحرر مقابض الملفات والذاكرة الأصلية.  
- `save` يكتب PDF المعدل إلى `output.pdf`.

> **ملاحظة الذاكرة:** `Annotator` يحمل فقط الصفحات التي تتعامل معها. بالنسبة لملفات PDF ذات مئات الصفحات، يحافظ هذا النهج على استهلاك الذاكرة تحت 150 MB على خادم عادي.

## خيارات التكوين المتقدمة

### تخصيص مظهر التعليق

يمكنك ضبط النمط البصري بدقة ليتطابق مع إرشادات علامتك التجارية:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **عرض الحدود** يتحكم في سمك الخط (بالنقاط).  
- تنسيق **ARGB** يتضمن قناة ألفا للشفافية.

### تحديد موضع التعليقات بدقة

الحصول على الإحداثيات الصحيحة قد يكون صعبًا في ملفات PDF ذات أحجام صفحات مختلفة. اتبع هذا النهج المنهجي:

1. **افتح PDF في عارض** (مثل Adobe Acrobat) وسجل قيم المسطرة للمنطقة المستهدفة.  
2. **حوّل قيم المسطرة** إلى نقاط (1 نقطة = 1/72 بوصة).  
3. **استخدم `annotator.getPageInfo(pageIndex)`** للحصول على عرض وارتفاع الصفحة، ثم احسب المواضع النسبية.

## المشكلات الشائعة والحلول

### المشكلة: التعليقات لا تظهر

**الأسباب الأكثر احتمالًا**
- النقاط تقع خارج حدود الصفحة  
- الترخيص غير محمل (العلامة المائية تخفي التعليق)  
- رقم الصفحة غير صحيح (الصفحات تبدأ من الصفر في الـ API)

**قائمة التحقق للحل**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### المشكلة: أداء ضعيف مع ملفات كبيرة

تحميل PDF مكوّن من 500 صفحة إلى الذاكرة قد يبطئ خدمتك. خفّف ذلك عن طريق:
- **معالجة صفحة واحدة في كل مرة** – افتح المستند، علق صفحة واحدة، احفظ، ثم انتقل إلى التالية.  
- **البث** – استخدم API البث الخاص بـ `Annotator` لتجنب تخزين المستند بالكامل في الذاكرة.  
- **التخزين المؤقت** – احفظ ملفات PDF التي تُستَخدم كثيرًا في ذاكرة مؤقتة سريعة (مثل Redis) وعَلّق النسخة المخزنة.

### المشكلة: قيم اللون لا تعمل

GroupDocs يتوقع **ARGB** (ألفا، أحمر، أخضر، أزرق) بدلاً من RGB العادي. قيمة ARGB `0xFFFF0000` تعني أحمر غير شفاف بالكامل. إذا قدمت `0xFF0000` فإن المكتبة تفسره بشكل غير صحيح، مما ينتج عنه تعليق أسود.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## أفضل ممارسات الأداء

### إدارة الذاكرة

عند التعليق على العشرات من ملفات PDF في مهمة دفعة، احط كل ملف بكتلة try‑with‑resources خاصة به:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- هذا النمط يضمن تحرير المخازن الأصلية بعد كل تكرار، مما يمنع **OutOfMemoryError** في العمليات طويلة الأمد.

### تحسين معالجة الدُفعات

في بيئات ذات إنتاجية عالية، فكر في استخدام التدفقات المتوازية مع مجموعة مؤشرات محدودة:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **المجموعة المحدودة** تتجنب انفجار المؤشرات، بينما تحافظ التدفقات المتوازية على إشغال نوى المعالج.

### اعتبارات حجم الملف

ملفات PDF الكبيرة (> 100 MB) قد تضعف الأداء. طبق هذه الاستراتيجيات:
- **ضغط مسبق** لملف PDF الأصلي باستخدام أداة مثل Ghostscript قبل التعليق.  
- **التعليق على الصفحات المطلوبة فقط** – تخطى الصفحات التي لا تحتاج إلى تعليقات.  
- **تقسيم** المستند إلى أقسام منطقية (مثلًا كل فصل) ومعالجة كل جزء بشكل مستقل.

## تطبيقات واقعية

### أنظمة مراجعة المستندات

غالبًا ما تحتاج الشركات القانونية إلى وضع علامة على البنود الإشكالية. تعليقات Squiggly المدمجة مع الردود المتسلسلة تتيح لعدة محامين مناقشة فقرة واحدة دون مغادرة PDF:
- **المحامي A** يضيف خطًا متموجًا أحمر تحت بند ويكتب “صياغة غامضة”.  
- **المحامي B** يرد “أضف تعريفًا لـ ‘خرق مادي’”.  
- يبقى النقاش بالكامل مدمجًا، قابلًا للبحث، وقابلًا للتدقيق.

### التكامل مع الأنظمة الحالية

GroupDocs.Annotation يعمل بسلاسة مع أطر جافا الشهيرة:
- **Spring Boot** – عرض نقطة REST `/api/annotate` التي تقبل تحميل PDF متعدد الأجزاء، وتضيف التعليقات، وتعيد النتيجة عبر البث.  
- **JSF** – ربط إجراءات التعليق بمكونات الواجهة لتعديل سريع في عرض الويب.  
- **الخدمات المصغرة** – حجم المكتبة الصغير (< 15 MB) يتيح لك حاويتها باستخدام Docker وتوسيعها أفقياً.

### أتمتة سير العمل

اجمع التعليق مع منتجات GroupDocs الأخرى (مثل GroupDocs.Signature) لبناء خطوط معالجة شاملة من البداية إلى النهاية:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## متى تستخدم تعليقات Squiggly مقابل البدائل

| حالة الاستخدام | التعليق الموصى به |
|----------------|-------------------|
| وضع علامة على الأخطاء الإملائية أو النحوية | **Squiggly** – إشارة بصرية مشابهة لمعالجات النصوص |
| تظليل الأقسام المهمة دون الإيحاء بوجود خطأ | **Highlight** – طبقة شفافة |
| تقديم ملاحظات مفصلة | **Text** أو **Comment** – صندوق ملاحظات حر |
| الموافقة على مستند أو رفضه | **Stamp** – شارة “موافق” أو “مرفوض” |

## الخلاصة

أصبح لديك الآن وصفة كاملة وجاهزة للإنتاج لـ **create annotation reply java** باستخدام GroupDocs.Annotation. من خلال إتقان الـ API، ومعالجة الترخيص، وتطبيق نصائح الأداء أعلاه، يمكنك:
- أتمتة وضع العلامات على الأخطاء عبر آلاف ملفات PDF  
- تمكين مناقشات متسلسلة تعاونية داخل الملف نفسه  
- الحفاظ على استهلاك الذاكرة منخفضًا حتى عند معالجة مستندات ضخمة  

**الخطوات التالية**
1. تجربة أنواع تعليقات أخرى (التظليل، الأختام، النص).  
2. بناء خدمة REST تستقبل ملفات PDF، وتضيف التعليقات، وتعيد النتيجة.  
3. استكشاف API الاستخراج (`annotator.get()`) لسحب التعليقات الموجودة للتحليلات.  

تكمن قوة التعليق البرمجي على ملفات PDF في قدرته على استبدال التعليقات اليدوية المرهقة بكود قابل للتكرار والتدقيق. سواءً كنت تبني منتجًا قانونيًا تقنيًا متخصصًا أو محرك سير عمل مستندات عام، فإن التقنيات في هذا الدليل تمنحك أساسًا قويًا للمضي قدمًا.

## الأسئلة المتكررة

**س: ما الذي يجعل GroupDocs.Annotation أفضل من مكتبات PDF الأخرى لجافا؟**  
ج: يركز GroupDocs.Annotation حصريًا على سير عمل التعليقات، ويقدم أكثر من 30 نوعًا من التعليقات، ردودًا متسلسلة، ودعمًا أصليًا لأكثر من 50 تنسيق ملف مع الحفاظ على استهلاك الذاكرة أقل من 200 MB لملفات PDF مكوّنة من 500 صفحة.

**س: هل يمكنني استخدام هذه المكتبة مع تطبيقات Spring Boot؟**  
ج: بالتأكيد. أنشئ `@RestController` يحقن خدمة `Annotator`، يعالج تحميلات multipart، ويبث PDF المعلق مرة أخرى إلى العميل. تذكر تكوين مجموعة مؤشرات للطلبات المتزامنة.

**س: كيف أتعامل مع مستندات ذات أحجام صفحات مختلفة؟**  
ج: استعلم عن أبعاد كل صفحة عبر `annotator.getPageInfo(pageIndex)` واحسب الإحداثيات النسبية (مثل النسب المئوية) بدلاً من ترميز قيم النقاط صلبًا. يضمن ذلك ظهور التعليقات بشكل صحيح على صفحات A4، Letter، والصفحات ذات الأحجام المخصصة.

**س: هل هناك طريقة لاستخراج التعليقات الموجودة من ملفات PDF؟**  
ج: نعم. استدعِ `annotator.get()` لاسترجاع مجموعة من جميع التعليقات، ثم كرّر لقراءة الخصائص مثل المؤلف، التعليق، والهندسة. هذا مفيد لسيناريوهات الترحيل أو التحليل.

**س: ما هو النهج الأفضل لإدارة أذونات التعليقات في أنظمة متعددة المستخدمين؟**  
ج: نفّذ المصادقة على طبقة التطبيق، خزن معرف المستخدم مع كل `Reply`، وطبق قواعد العمل (مثلًا، فقط المؤلف أو المسؤول يمكنه تعديل أو حذف الرد). الـ API نفسه لا يفرض أذونات، مما يمنحك مرونة كاملة.

**س: كيف أحسن استهلاك الذاكرة عند معالجة مئات ملفات PDF؟**  
ج: استخدم try‑with‑resources لكل مستند، عالج الصفحات بشكل فردي، وفكّر في مجموعة مؤشرات محدودة لتقليل استهلاك الذاكرة المتزامن. مراقبة كومة JVM بأدوات مثل VisualVM يساعدك على ضبط إعداد `-Xmx` بدقة.

---

**آخر تحديث:** 2026-05-16  
**تم الاختبار مع:** GroupDocs.Annotation 25.2 for Java  
**المؤلف:** GroupDocs  

**موارد إضافية**
- [توثيق GroupDocs.Annotation للغة جافا](https://docs.groupdocs.com/annotation/java/)
- [مرجع API الكامل](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## دروس ذات صلة

- [دليل مكتبة تعليقات PDF لجافا](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [إزالة ردود التعليقات في جافا - إدارة الردود حسب المعرف باستخدام GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [تحرير تعليقات PDF في جافا - دليل GroupDocs الكامل](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)