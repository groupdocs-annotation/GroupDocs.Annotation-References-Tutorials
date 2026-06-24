---
categories:
- Java PDF Processing
date: '2026-05-21'
description: تعلم كيفية إضافة تعليقات الخط عبر إلى ملفات PDF في Java باستخدام GroupDocs.
  يغطي هذا البرنامج التعليمي خطوة بخطوة الإعداد، الكود، استكشاف الأخطاء وإصلاحها،
  ونصائح الأداء.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: دليل الخط عبر لنص PDF في Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: كيفية إضافة تعليقات الخط عبر إلى ملفات PDF في Java – دليل GroupDocs الكامل
type: docs
url: /ar/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# كيفية إضافة تعليقات الخط المشطوب إلى ملفات PDF في Java

هل احتجت يوماً إلى شطب النص في ملف PDF برمجياً؟ سواء كنت تبني نظام مراجعة مستندات، أو تنشئ سير عمل تحرير، أو فقط تحتاج إلى وضع علامة على النص للحذف، فإن **كيفية إضافة شطب** في Java هي مهارة عملية توفر الوقت وتقلل الجهد اليدوي. في هذا الدليل الشامل ستكتشف كل ما تحتاج معرفته لتطبيق تعليقات الشطب باستخدام GroupDocs.Annotation للـ Java، من إعداد المشروع إلى تحسين الأداء.

## إجابات سريعة
- **ما هي الخطوة الأولى؟** أضف تبعية GroupDocs.Annotation Maven إلى ملف `pom.xml` الخاص بك.  
- **كيف أنشئ شطبًا؟** أنشئ كائن `Annotator`، عرّف `StrikeoutAnnotation` بالنقاط، حدد اللون/الشفافية، ثم استدعِ `addAnnotation`.  
- **هل يمكنني إضافة تعليقات؟** نعم، أرفق كائن `Comment` بالتعليق لتسهيل التعاون.  
- **ماذا لو كان التعليق في موقع غير صحيح؟** عدّل نقاط الإحداثيات؛ يستخدم PDF نظام أصل من الزاوية السفلية اليسرى.  
- **هل هناك حد لحجم المستند؟** تقوم GroupDocs بمعالجة ملفات PDF مئات الصفحات دون تحميل الملف بالكامل في الذاكرة.

## ما هو “كيفية إضافة شطب” في تعليقات PDF؟
تشير العبارة “كيفية إضافة شطب” إلى عملية رسم خط عبر النص المحدد داخل مستند PDF برمجياً باستخدام واجهة برمجة تطبيقات التعليقات. في Java، توفر GroupDocs.Annotation فئة `StrikeoutAnnotation` مخصصة التي تدير عرض الخط، وتنسيقه، وحفظ علامات الشطب.

## لماذا تستخدم GroupDocs للخط المشطوب في PDF باستخدام Java؟
يدعم GroupDocs.Annotation **أكثر من 50 تنسيقًا للإدخال والإخراج** — بما في ذلك PDF و DOCX و XLSX و PPTX و HTML وأنواع الصور الشائعة — لذا لست مقيدًا بنوع ملف واحد. يوفر API عالي المستوى يُجرد بنية PDF منخفضة المستوى، ويتعامل تلقائيًا مع تضمين الخطوط، وعرض الصفحات، وحفظ التعليقات، مما يسمح للمطورين بالتركيز على منطق الأعمال بدلاً من تفاصيل PDF الداخلية.

## المتطلبات المسبقة ومتطلبات الإعداد

### المتطلبات الأساسية
- **Java Development Kit (JDK):** الإصدار 8 أو أحدث (يوصى بـ JDK 11+ لأداء جمع القمامة المثالي).  
- **GroupDocs.Annotation للـ Java:** مدمج عبر Maven (انظر المقتطف Maven أدناه).  
- **IDE:** IntelliJ IDEA أو Eclipse أو أي محرر متوافق مع Java.

### إعداد تبعيات Maven
أضف كتلة التبعيات التالية إلى ملف `pom.xml` الخاص بك:

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

**نصيحة احترافية:** تحقق دائمًا من أحدث نسخة على صفحة إصدارات GroupDocs؛ الإصدارات الأحدث تضيف ميزات وتصلح أخطاء قد تؤثر على عرض التعليقات.

### ترتيب الترخيص الخاص بك
يتطلب GroupDocs.Annotation ترخيصًا صالحًا للاستخدام في الإنتاج. لديك ثلاث خيارات:

- **تجربة مجانية:** تحميل من [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **ترخيص مؤقت:** طلب مفتاح تطوير عبر [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **ترخيص كامل:** شراء للاستخدام الإنتاجي عبر [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)  

تضيف التجربة علامة مائية خفيفة، لذا خطط لاختبارك وفقًا لذلك.

## دليل التنفيذ خطوة بخطوة

### فهم المكونات الأساسية
التعريفات التالية تعطيك نموذجًا ذهنيًا سريعًا:

- **Annotator:** كائن API الأساسي الذي يحمل ملف PDF ويكشف عن طرق التعليقات.  
- **StrikeoutAnnotation:** يمثل خط الشطب البصري وخيارات تنسيقه.  
- **Point:** زوج إحداثيات (X, Y) يحدد للمكتبة مكان بدء وانتهاء الخط.  
- **Comment:** نص اختياري مرفق بالتعليق لتسهيل التعاون.

### الخطوة 1: إعداد مسارات الملفات
حدد مواقع ملف PDF المصدر والملف الوجهة. المسارات غير الصحيحة هي مصدر شائع لأخطاء “الملف غير موجود”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**تنبيه خطأ شائع:** تأكد من وجود دليل الإخراج وأنه قابل للكتابة؛ لن يقوم GroupDocs بإنشاء المجلدات المفقودة تلقائيًا.

### الخطوة 2: تهيئة Annotator
أنشئ مثيل `Annotator` الذي يحمل ملف PDF في الذاكرة.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**ماذا يحدث هنا؟** تقوم المكتبة بتحليل بنية PDF، وبناء تمثيل داخلي، وتحضير لوحة تعليقات لكل صفحة. قد تستغرق هذه الخطوة بضع ثوانٍ للملفات التي تحتوي على مئات الصفحات.

### الخطوة 3: إضافة تعليقات (اختياري لكن موصى به)
`Comment` هي فئة تمثل ملاحظة نصية مرفقة بالتعليق، تسمح للمتعاونين بشرح سبب الشطب.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**نصيحة من الواقع:** استخدم التعليقات لشرح سبب إزالة النص — هذا مفيد بشكل خاص في عمليات مراجعة قانونية أو تحريرية.

### الخطوة 4: تحديد إحداثيات التعليق
كائنات `Point` تخزن أزواج إحداثيات X‑Y التي تحدد الموقع الدقيق للتعليق على صفحة PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**شرح نظام الإحداثيات:** إحداثيات PDF تبدأ من الزاوية السفلية اليسرى (0,0). المثال ينشئ خطًا أفقيًا من (80,730) إلى (240,730) على الصفحة المستهدفة.

**العثور على الإحداثيات الصحيحة:** ينشئ العديد من المطورين أداة مساعدة تحول النسب المئوية لعرض/ارتفاع الصفحة إلى نقاط مطلقة، مما يجعل الكود مرنًا لأحجام الصفحات المختلفة.

### الخطوة 5: إنشاء تعليق الشطب
`StrikeoutAnnotation` يضم الخط البصري، وخصائص النمط مثل اللون والشفافية، وأي بيانات وصفية مرتبطة بعلامة الشطب.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**قيم اللون:** يستخدم `fontColor` قيم RGB عشرية (مثال، 65535 للون الأصفر الفاتح). استخدم محولًا عبر الإنترنت إذا كنت تحتاج إلى درجات ألوان مخصصة للعلامة التجارية.

**توصية الشفافية:** شفافية `0.7` (70 ٪) توفر إشارة بصرية واضحة مع الحفاظ على قابلية قراءة النص الأساسي.

### الخطوة 6: تطبيق التعليق
`addAnnotation` هي طريقة في `Annotator` تسجل التعليق المُعد مع المستند ليتم عرضه وحفظه.

```java
annotator.add(strikeout);
```

### الخطوة 7: حفظ وتنظيف
`dispose()` يحرر الموارد الأصلية التي يحتفظ بها مثيل `Annotator`، مما يمنع تسرب الذاكرة بعد اكتمال المعالجة.

```java
annotator.save(outputPath);
annotator.dispose();
```

**ملاحظة إدارة الذاكرة:** استدعاء `dispose()` يحرر الموارد الأصلية ويمنع تسرب الذاكرة عند معالجة دفعات من ملفات PDF.

## المشكلات الشائعة وكيفية حلها

### المشكلة 1: أخطاء “الملف غير موجود”
**الأعراض:** استثناء يُرمى أثناء إنشاء `Annotator`.  
**الحل:** تحقق من مسارات الإدخال والإخراج، وتأكد من أن التطبيق لديه أذونات القراءة/الكتابة.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### المشكلة 2: ظهور الشطب في الموقع الخطأ
**الأعراض:** الخط لا يتطابق مع النص المقصود.  
**الحل:** تذكر أن إحداثيات Y في PDF تزداد صعودًا. استخدم أداة تصحيح بصرية أو اطبع أبعاد الصفحة لضبط النقاط بدقة.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### المشكلة 3: التعليق غير مرئي
**الأعراض:** لا يظهر أي شطب بعد الحفظ.  
**الأسباب المحتملة والحلول:**  
- **الشفافية منخفضة جدًا:** اضبط الشفافية مؤقتًا إلى `1.0` للتحقق من الرؤية.  
- **خلط الألوان:** استخدم لونًا عالي التباين مثل الأحمر (`255`).  
- **فهرس الصفحة غير صحيح:** أرقام الصفحات تبدأ من الصفر؛ تأكد من استهداف الصفحة الصحيحة.

### المشكلة 4: مشاكل الذاكرة مع الملفات الكبيرة
**الأعراض:** `OutOfMemoryError` أو أداء بطيء.  
**الحلول:**  
- عالج المستندات على دفعات أصغر.  
- استخدم API البث إذا كان متاحًا.  
- استدعِ دائمًا `dispose()` بعد كل مستند.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## تطبيقات واقعية وحالات استخدام

### مراجعة المستندات القانونية
تقوم مكاتب المحاماة بتعليق العقود بشطب لتحديد البنود المحذوفة مع الحفاظ على سجل تدقيق.

### تحرير الأوراق الأكاديمية
يستخدم الأساتذة الشطب لاقتراح الإزالة أثناء مراجعة الأقران، مع إبقاء النص الأصلي مرئيًا للسياق.

### أنظمة إدارة المحتوى
تقوم منصات النشر تلقائيًا بوضع علامة على الأقسام المخالفة للسياسة بشطب قبل المراجعة اليدوية.

### التحكم في إصدارات المستندات
تتعامل المؤسسات مع تعليقات الشطب كـ “علامات حذف” في سير عمل التحكم في إصدارات المستندات، مشابه لاختلافات الكود.

## نصائح تحسين الأداء

### استراتيجية المعالجة الدفعية
عند معالجة العديد من ملفات PDF، أعد استخدام مثيل `Annotator` واحد حيثما أمكن وعالج الملفات في خيوط متوازية.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### أفضل ممارسات إدارة الذاكرة
- استدعِ `dispose()` على كل `Annotator`.  
- قصر عدد تحميلات المستندات المتزامنة لتجنب ضغط الذاكرة.  
- راقب استخدام ذاكرة JVM باستخدام أدوات مثل VisualVM.

### تخزين الإحداثيات مؤقتًا
إذا طبقت نفس تخطيط التعليق عبر ملفات متعددة، خزن كائنات `Point` مؤقتًا لتجنب إعادة الحساب.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## خيارات التخصيص المتقدمة

### اختيار اللون الديناميكي
اختر الألوان في وقت التشغيل بناءً على قواعد العمل (مثال، الأحمر للحذف الحاسم، الأصفر للعمليات المؤقتة).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### شطب متعدد الأسطر
أنشئ سلسلة من أزواج `Point` لرسم خط متعرج يقطع عدة أسطر من النص.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## قائمة التحقق من استكشاف الأخطاء وإصلاحها
1. **أذونات الملف:** تحقق من صلاحية القراءة/الكتابة.  
2. **إصدار المكتبة:** تأكد من أنك تستخدم نسخة مدعومة من GroupDocs.Annotation.  
3. **حالة الترخيص:** تأكد من أن ملف الترخيص مشار إليه بشكل صحيح.  
4. **توافق PDF:** تحقق من أن ملف PDF غير معطوب وأنه ضمن حدود الحجم المدعومة.  
5. **تحقق من الإحداثيات:** تأكد من أن جميع النقاط داخل حدود الصفحة.  
6. **مساحة الكومة:** زد حجم JVM `-Xmx` إذا كنت تعالج ملفات كبيرة جدًا.

## الأسئلة المتكررة

**س: هل يمكنني شطب نص عبر عدة أسطر؟**  
ج: نعم. أنشئ عدة كائنات `Point` تتبع المسار المطلوب؛ سيتبع التعليق الخط المتعدد النقاط المقدم.

**س: ماذا يحدث إذا حددت إحداثيات خارج حدود الصفحة؟**  
ج: سيتم قطع التعليق وقد يصبح غير مرئي. دائمًا تحقق من صحة الإحداثيات مقابل عرض وارتفاع الصفحة.

**س: هل يمكنني إزالة تعليقات الشطب بعد إضافتها؟**  
ج: بالتأكيد. استخدم طريقة `removeAnnotation` مع معرف التعليق أو قم بالفلترة حسب النوع لحذفها برمجيًا.

**س: هل هناك حد لعدد التعليقات التي يمكنني إضافتها إلى ملف PDF واحد؟**  
ج: لا تفرض GroupDocs حدًا ثابتًا، لكن الأداء قد يتدهور بعد آلاف التعليقات. فكر في التقسيم إلى صفحات أو تلخيص التعليقات للمجموعات الكبيرة جدًا.

**س: كيف أتعامل مع ملفات PDF محمية بكلمة مرور؟**  
ج: مرّر كلمة المرور إلى مُنشئ `Annotator`. ستقوم المكتبة بفك تشفير المستند في الذاكرة قبل تطبيق أي تعليقات.

**س: كيف يمكنني التعامل مع ملفات PDF ذات أحجام واتجاهات صفحات مختلفة؟**  
ج: احصل على أبعاد كل صفحة عبر `annotator.getPageInfo(pageNumber)` واحسب الإحداثيات نسبةً لتلك الأبعاد لضمان وضعية ثابتة.

## الخلاصة
أصبح لديك الآن حل كامل وجاهز للإنتاج لإضافة تعليقات **كيفية إضافة شطب** إلى ملفات PDF في Java باستخدام GroupDocs.Annotation. من خلال إتقان التعامل مع مسارات الملفات، وحساب الإحداثيات، وإدارة الموارد، يمكنك دمج هذه القدرة في أدوات مراجعة المستندات، وسلاسل المحتوى، أو أي تطبيق مبني على Java يحتاج إلى ملاحظات بصرية دقيقة.

## الخطوات التالية
1. استنسخ مشروع المثال وشغّله على ملف PDF تجريبي.  
2. جرّب ألوانًا مختلفة، وشفافية مختلفة، ونصوص تعليقات مختلفة.  
3. دمج سير عمل التعليقات في خدمة معالجة المستندات الحالية لديك.  
4. استكشف أنواع التعليقات المرتبطة—التظليل، الملاحظات اللاصقة، وتعليقات الأشكال—لتوسيع مجموعة أدوات معالجة PDF الخاصة بك.

هل تريد المزيد؟ استكشف الوثائق الرسمية للحصول على رؤى أعمق حول API.

## موارد إضافية
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - وثائق عامة لمكتبات GroupDocs  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - مرجع API كامل  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - تفاصيل كل طريقة على حدة  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - حافظ على تحديث مكتبتك  
- [Purchase License](https://purchase.groupdocs.com/buy) - ترخيص جاهز للإنتاج  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - تقييم قبل الشراء  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - اختبار تطوير  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - مساعدة المجتمع والدعم الرسمي  

**آخر تحديث:** 2026-05-21  
**تم الاختبار مع:** GroupDocs.Annotation 23.12 للـ Java  
**المؤلف:** GroupDocs

## دروس ذات صلة
- [إضافة تعليقات PDF Java – دليل GroupDocs الكامل](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [دورة تعليقات PDF Java - دليل كامل لتسليط الضوء على ملفات PDF](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [كيفية إضافة سهم إلى PDF في Java – دورة GroupDocs كاملة](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)