---
categories:
- Java Tutorials
date: '2026-09-30'
description: تعلم كيفية إنشاء تمييزات PDF java باستخدام GroupDocs. يوضح هذا البرنامج
  التعليمي خطوة بخطوة كيفية تمييز PDF في Java، إضافة تعليقات، وتحسين الأداء.
keywords:
- create pdf highlights java
- highlight text pdf java
- groupdocs annotation java
- pdf annotation java tutorial
lastmod: '2026-09-30'
linktitle: دليل توضيح PDF في Java
og_description: إنشاء تمييزات PDF java باستخدام GroupDocs.Annotation. اتبع هذا البرنامج
  التعليمي خطوة بخطوة لإضافة تمييزات، تعليقات، وتحسين الأداء في Java.
og_image_alt: Developer guide illustrating PDF highlight creation using GroupDocs.Annotation
  for Java
og_title: إنشاء تمييزات PDF java – دليل كامل لمطوري Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-30'
  description: Learn how to create PDF highlights java using GroupDocs. This step‑by‑step
    tutorial shows how to highlight PDF in Java, add comments, and optimise performance.
  headline: 'How to create PDF highlights java: complete guide for highlighting PDFs'
  type: TechArticle
- description: Learn how to create PDF highlights java using GroupDocs. This step‑by‑step
    tutorial shows how to highlight PDF in Java, add comments, and optimise performance.
  name: 'How to create PDF highlights java: complete guide for highlighting PDFs'
  steps:
  - name: Initialize your annotator object
    text: '`Annotator` is the core class in GroupDocs.Annotation that loads a PDF
      and provides methods to add, edit, and save annotations. **What''s happening
      here?** - The `Annotator` constructor loads your PDF into memory. - We set an
      output path where the annotated PDF will be saved. - The input PDF remains '
  - name: Create interactive replies and comments
    text: '`Reply` and `Comment` objects enable threaded conversations on a highlight,
      turning a static annotation into a collaborative discussion. Reply represents
      a single comment in a thread, while Comment groups replies under a specific
      annotation. **Why this matters**: In real applications you often need '
  - name: Define precise highlight coordinates
    text: '`HighlightAnnotation` is the class that represents a highlight region on
      a PDF page. HighlightAnnotation defines a rectangular highlight region on a
      PDF page, specified by a set of points. **Understanding PDF coordinates**: -
      Origin (0,0) is at the bottom‑left of the page. - X increases to the right'
  - name: Configure your highlight annotation
    text: '`HighlightAnnotation` lets you customise colour, opacity, font colour,
      and page number. **Customization options explained**: - `setBackgroundColor(65535)`:
      Yellow highlight (RGB integer). - `setOpacity(0.5)`: 50 % transparency keeps
      the underlying text readable. - `setFontColor(0)`: Black text ensur'
  - name: Save your annotated PDF
    text: '`dispose()` releases native resources and finalizes the PDF file. `dispose()`
      releases native resources and finalizes the PDF file. **Resource management**:
      The `dispose()` call is crucial—it frees up memory and guarantees all changes
      are persisted. Always wrap the annotator in a try‑with‑resources '
  type: HowTo
- questions:
  - answer: Absolutely. It integrates with Spring Boot, Servlets, and other Java web
      frameworks. Expose a REST endpoint that accepts a PDF, applies highlights, and
      returns the annotated file.
    question: Can I use GroupDocs.Annotation in web applications?
  - answer: The library supports Unicode, so you can add comments and messages in
      any language. Just ensure your Java application uses UTF‑8 encoding.
    question: How do I handle annotations in different languages?
  - answer: Performance scales with the number of annotations, but PDF size has a
      larger impact. For documents with hundreds of highlights, consider lazy loading
      or pagination to keep memory usage low.
    question: What's the performance impact of adding many annotations?
  - answer: Yes. Load a PDF with existing annotations, update properties such as colour
      or position, and save the updated version. This is ideal for building annotation‑management
      tools.
    question: Can I modify existing annotations programmatically?
  - answer: GroupDocs.Annotation provides enumeration methods to read metadata (author,
      creation date, comment text, etc.). Export this data to CSV, JSON, or feed it
      into analytics pipelines.
    question: How do I extract annotation data for reporting?
  type: FAQPage
tags:
- pdf annotation
- groupdocs
- java library
- document processing
- create pdf highlights java
title: 'كيفية إنشاء تمييزات PDF java: دليل كامل لتظليل ملفات PDF'
type: docs
url: /ar/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء تمييزات PDF في Java: دليل كامل لتظليل ملفات PDF

## مقدمة

هل واجهت صعوبة في إدارة التعليقات عبر إصدارات متعددة من المستند؟ لست وحدك. سواء كنت تبني نظام إدارة مستندات، أو تنشئ منصة تعليمية، أو تطور أدوات تعاونية، فإن **create pdf highlights java** قد يكون من الصعب تنفيذه من الصفر.

هنا يأتي دور **GroupDocs.Annotation for Java** لإنقاذ الموقف. هذه المكتبة القوية تحول مهام التعليقات على PDF المعقدة إلى عمليات بسيطة، مما يتيح لك إضافة تمييزات، تعليقات، وردود دون الحاجة إلى التعامل مع معالجة PDF منخفضة المستوى.

في هذا الدرس الشامل، ستكتشف كيفية **highlight pdf in java** باستخدام أمثلة من الواقع. سنستعرض كل شيء من الإعداد الأساسي إلى تقنيات التمييز المتقدمة، بالإضافة إلى مشاركة نصائح عملية تعلمتها من تنفيذ ذلك في بيئات الإنتاج.

إليك ما ستتقنه بالضبط:

- إعداد GroupDocs.Annotation في مشروع Java الخاص بك (بالطريقة الصحيحة)  
- إنشاء تمييزات PDF تفاعلية مع تنسيق مخصص  
- إضافة ردود وتعليقات متسلسلة للتعاون  
- معالجة المشكلات الشائعة وتحسين الأداء  
- استراتيجيات تنفيذ من الواقع  

هل أنت مستعد لتحويل ملفات PDF الخاصة بك إلى مستندات تفاعلية وتعاونية؟ هيا نبدأ!

## إجابات سريعة

- **ما المكتبة التي تبسط تمييزات PDF في Java؟** GroupDocs.Annotation for Java.  
- **ما الاعتماد Maven الذي يضيف المكتبة؟** `com.groupdocs:groupdocs-annotation:25.2`.  
- **هل أحتاج إلى ترخيص للتطوير؟** ترخيص مؤقت مجاني يعمل للاختبار؛ يتطلب الترخيص المدفوع للإنتاج.  
- **هل يمكنني إضافة تعليقات إلى التمييزات؟** نعم، يمكنك إرفاق ردود وتعليقات متسلسلة.  
- **كيف أدير الذاكرة لملفات PDF الكبيرة؟** استخدم try‑with‑resources واستدعِ `dispose()` بعد الحفظ.

## كيف أنشئ تمييزات PDF في Java؟

حمّل ملف PDF المستهدف باستخدام `new Annotator(inputPath)` واستدعِ `addAnnotation(highlight)` ثم `save(outputPath)`. Annotator هو الفئة الأساسية التي تقوم بتحميل مستند PDF وتوفر طرقًا لإضافة وتعديل وحفظ التعليقات. هذه العملية ذات الخطوتين تنشئ ملف PDF مميز خلال ثوانٍ، وتتعامل مع تحويل الإحداثيات تلقائيًا، وتحرّر الموارد عند استدعاء `dispose()`. لا يتطلب أي تحليل يدوي لملف PDF.

## ما هو create pdf highlights java؟

`create pdf highlights java` يشير إلى إضافة تعليقات تمييز إلى ملفات PDF برمجيًا باستخدام كود Java، عادةً عبر مكتبة مخصصة مثل GroupDocs.Annotation. تتيح هذه العملية مراجعة آلية، وتعاون، وتأكيد بصري دون تحرير يدوي.

## لماذا تختار GroupDocs.Annotation لمعالجة PDF في Java؟

يدعم GroupDocs.Annotation **أكثر من 30 نوعًا من التعليقات** ويمكنه معالجة ملفات PDF حتى **500 ميغابايت** دون تحميل المستند بالكامل في الذاكرة. يقوم تلقائيًا بحل إحداثيات مستوى الصفحة، ويحافظ على المحتوى الموجود، ويقدم API غنيًا لتنسيق، وتعليق، وتصدير بيانات التعليقات.

## المتطلبات المسبقة وإعداد البيئة

### ما ستحتاجه

- **بيئة التطوير**: Java 8+ (يوصى بـ Java 11+)، Maven أو Gradle، وIDE مثل IntelliJ IDEA أو Eclipse أو VS Code.  
- **متطلبات المعرفة**: Java أساسية (المجموعات، الكائنات، إدخال/إخراج الملفات)، إدارة تبعيات Maven، وفهم عام لأنظمة إحداثيات PDF.  

### تثبيت GroupDocs.Annotation لـ Java

أسهل طريقة للبدء هي عبر Maven. أضف هذه الإعدادات إلى ملف `pom.xml` الخاص بك:

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

**نصيحة احترافية**: استخدم دائمًا أحدث نسخة مستقرة. تقوم GroupDocs بإصدار تحديثات بانتظام مع تحسينات في الأداء وإصلاحات للأخطاء.

### إعداد الترخيص (لا تتخطاه!)

ستحتاج إلى ترخيص لاستخدام GroupDocs.Annotation في الإنتاج. إليك كيفية التعامل مع الترخيص:

- **للتطوير**: احصل على نسخة تجريبية مجانية أو [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- **للإنتاج**: اشترِ ترخيصًا من [موقع GroupDocs](https://purchase.groupdocs.com/buy)

الترخيص المؤقت مثالي للاختبار والتطوير — يمنحك جميع الوظائف دون علامات مائية.

## دليل التنفيذ خطوة بخطوة

الآن للجزء المثير — لننشئ نظام تعليقات PDF كامل! سنستعرض كل مكون، موضحين ليس فقط ما يفعله الكود، بل لماذا نفعل ذلك بهذه الطريقة.

### الخطوة 1: تهيئة كائن Annotator الخاص بك

`Annotator` هو الفئة الأساسية في GroupDocs.Annotation التي تقوم بتحميل ملف PDF وتوفر طرقًا لإضافة وتعديل وحفظ التعليقات.

```java
import com.groupdocs.annotation.Annotator;
import org.apache.commons.io.FilenameUtils;

String outputPath = "YOUR_OUTPUT_DIRECTORY/AnnotationOutput.pdf";
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/InputDocument.pdf");
```

**ما الذي يحدث هنا؟**  
- يقوم مُنشئ `Annotator` بتحميل ملف PDF الخاص بك إلى الذاكرة.  
- نحدد مسار الإخراج حيث سيتم حفظ ملف PDF المعلق.  
- يبقى ملف PDF المدخل دون تغيير — نحن ننشئ نسخة جديدة مع التعليقات.

**خطأ شائع**: تأكد من صحة مسارات الملفات ووجود الأدلة. يضيع العديد من المطورين وقتًا في تصحيح مشكلات المسارات البسيطة.

### الخطوة 2: إنشاء ردود وتعليقات تفاعلية

تمكنك كائنات `Reply` و `Comment` من إنشاء محادثات متسلسلة على تمييز، مما يحول التعليق الثابت إلى نقاش تعاوني. يمثل Reply تعليقًا واحدًا في السلسلة، بينما يجمع Comment الردود تحت تعليق محدد.

```java
import java.util.ArrayList;
import java.util.Calendar;
import java.util.List;

List<Reply> replies = new ArrayList<>();

// First reply
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());
replies.add(reply1);

// Second reply  
Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
replies.add(reply2);
```

**لماذا هذا مهم**: في التطبيقات الحقيقية غالبًا ما تحتاج إلى تتبع من قال ماذا ومتى. يتيح لك نظام الردود بناء ميزات مثل:
- سلاسل تعليقات على النص المميز
- سير عمل المراجعة مع سلاسل الموافقة
- سجلات تدقيق لتغييرات المستند
- بيئات تحرير تعاونية

**نصيحة من الواقع**: احفظ معلومات المستخدم والطوابع الزمنية في قاعدة بيانات بدلاً من الاعتماد على القيم الافتراضية.

### الخطوة 3: تحديد إحداثيات تمييز دقيقة

`HighlightAnnotation` هو الفئة التي تمثل منطقة تمييز على صفحة PDF. يحدد HighlightAnnotation منطقة تمييز مستطيلة على صفحة PDF، محددة بمجموعة من النقاط.

```java
import com.groupdocs.annotation.models.Point;
import java.util.ArrayList;
import java.util.List;

List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));   // Top-left corner
points.add(new Point(240, 730));  // Top-right corner  
points.add(new Point(80, 650));   // Bottom-left corner
points.add(new Point(240, 650));  // Bottom-right corner
```

**فهم إحداثيات PDF**:  
- الأصل (0,0) يقع في أسفل يسار الصفحة.  
- X يزداد إلى اليمين، Y يزداد إلى الأعلى.  
- أربعة نقاط تُنشئ صندوقًا محيطًا حول النص المستهدف.

**نصيحة احترافية للعثور على الإحداثيات**: استخدم عارض PDF يعرض إحداثيات المؤشر، أو ابدأ بقيم تقريبية ثم اضبطها بدقة بناءً على النتائج البصرية.

### الخطوة 4: تكوين تمييزك

`HighlightAnnotation` يتيح لك تخصيص اللون، الشفافية، لون الخط، ورقم الصفحة.

```java
import com.groupdocs.annotation.models.annotationmodels.HighlightAnnotation;

HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setBackgroundColor(65535);  // Yellow highlight
highlight.setCreatedOn(Calendar.getInstance().getTime());
highlight.setFontColor(0);            // Black text  
highlight.setMessage("This is a highlight annotation");
highlight.setOpacity(0.5);            // Semi‑transparent
highlight.setPageNumber(0);           // First page (zero‑indexed)
highlight.setPoints(points);
highlight.setReplies(replies);

// Add the highlight to the annotator
annotator.add(highlight);
```

**شرح خيارات التخصيص**:  
- `setBackgroundColor(65535)`: تمييز أصفر (قيمة RGB عددية).  
- `setOpacity(0.5)`: شفافية 50 % تحافظ على قابلية قراءة النص الأساسي.  
- `setFontColor(0)`: نص أسود يضمن تباينًا جيدًا.  
- `setPageNumber(0)`: فهرس الصفحة (0 = الصفحة الأولى).

**نصائح اختيار اللون**:  
- الأصفر (65535) هو اللون الكلاسيكي وغير المزعج.  
- للتمييزات المهمة جرب البرتقالي (16753920) أو الأحمر (16711680).  
- حافظ على الشفافية بين 0.3‑0.7 لأفضل قابلية قراءة.

### الخطوة 5: حفظ ملف PDF المعلق

`dispose()` يحرّر الموارد الأصلية وينهي ملف PDF. `dispose()` يحرّر الموارد الأصلية وينهي ملف PDF.

```java
annotator.save(outputPath);
annotator.dispose();
```

**إدارة الموارد**: استدعاء `dispose()` أمر حاسم — يحرّر الذاكرة ويضمن حفظ جميع التغييرات. احرص دائمًا على وضع الـ annotator داخل كتلة try‑with‑resources أو استدعِ `dispose()` في جملة finally.

## استكشاف الأخطاء الشائعة

### مشكلات مسار الملف  

**العرض**: `FileNotFoundException` أو “Cannot access file”.  
**الحل**: تأكد من أن المسارات مطلقة أو نسبية إلى جذر المشروع، افحص أذونات الملفات، وتأكد من وجود أدلة الإخراج قبل الحفظ.

### الإحداثيات لا تتطابق مع الموقع المتوقع  

**العرض**: تظهر التمييزات في أماكن خاطئة.  
**الحل**: تذكر أن نظام إحداثيات PDF يبدأ من أسفل اليسار. قد يكون هناك اختلافات بسيطة بين مولدات PDF؛ اختبر باستخدام ملفات PDF عينة واضبط وفقًا لذلك.

### مشكلات الذاكرة مع ملفات PDF الكبيرة  

**العرض**: `OutOfMemoryError` أو أداء بطيء.  
**الحل**: زيادة حجم ذاكرة JVM (مثال: `-Xmx2G`)، معالجة ملفات PDF على دفعات أصغر، ودائمًا استدعِ `dispose()` لتحرير الموارد.

### اللون لا يظهر بشكل صحيح  

**العرض**: ألوان تمييز خاطئة أو تعليقات غير مرئية.  
**الحل**: استخدم قيم RGB عددية، وليس سلاسل hex. اختبر قيم الشفافية بين 0.1 و0.9. تأكد من أن ألوان الخلفية والخط لديها تباين جيد.

## أفضل ممارسات تحسين الأداء

### إدارة الذاكرة

```java
// Good practice - use try-with-resources when available
try (Annotator annotator = new Annotator(inputPath)) {
    // Your annotation code here
    annotator.save(outputPath);
} // Automatically disposes resources
```

قم بتخصيص الـ annotator داخل كتلة try‑with‑resources وحرره فورًا. يمنع هذا النمط تسرب الذاكرة عند معالجة العديد من المستندات.

### استراتيجية المعالجة الدفعية

```java
for (String pdfPath : pdfPaths) {
    try (Annotator annotator = new Annotator(pdfPath)) {
        // Process single PDF
        addAnnotations(annotator);
        annotator.save(getOutputPath(pdfPath));
    }
    // Memory freed before next iteration
}
```

بالنسبة لعدة ملفات PDF، عالجها بشكل متسلسل بدلاً من تحميل جميعها في الذاكرة. هذا النهج يتوسع خطيًا ويحافظ على بصمة JVM منخفضة.

### اعتبارات حجم الملف

- ملفات PDF الكبيرة (>10 ميغابايت) تستهلك المزيد من الذاكرة ووقت المعالجة.  
- فكر في تقسيم المستندات الكبيرة جدًا إلى أقسام.  
- حسّن ملفات PDF المدخلة (ضغط الصور، إزالة الكائنات غير المستخدمة) قبل التعليق.

## تطبيقات واقعية وحالات الاستخدام

### أنظمة مراجعة المستندات  

مثالي للعقود القانونية، المواصفات التقنية، ومستندات الامتثال. استخدم ألوان تمييز مختلفة لكل مراجع، طبق قواعد الأذونات، واحفظ بيانات التعليقات الوصفية في قاعدة بيانات للتقارير.

### المنصات التعليمية  

مثالي لتظليل الكتب الدراسية، ملاحظات الواجبات، والدراسة التعاونية. السماح للطلاب بحفظ تعليقاتهم الشخصية، تمكين المعلمين من إضافة تعليقات رسمية، وإدارة إصدارات المستندات مع تطور المناهج.

### سير عمل ضمان الجودة  

مناسب لمراجعات التصميم، وثائق العمليات، وفحص الامتثال. دمج مع أدوات QA الحالية، استخدم حالة التعليق (مفتوح/محلول) للتتبع، وإنشاء تقارير تدقيق من بيانات التعليقات.

### أدوات البحث التعاوني  

ملائم للأوراق الأكاديمية، وثائق البحث، والمراجعة الزميلية. تنفيذ التعاون في الوقت الحقيقي، دعم المراجعات المجهولة، وتصدير التعليقات للتحليل.

## نصائح متقدمة وأفضل الممارسات

### طرق مساعدة لحساب الإحداثيات

```java
public class AnnotationUtils {
    public static List<Point> createRectangle(double x, double y, double width, double height) {
        List<Point> points = new ArrayList<>();
        points.add(new Point(x, y + height));      // Top‑left
        points.add(new Point(x + width, y + height)); // Top‑right  
        points.add(new Point(x, y));               // Bottom‑left
        points.add(new Point(x + width, y));       // Bottom‑right
        return points;
    }
}
```

### قوالب التعليقات

```java
public class AnnotationTemplates {
    public static HighlightAnnotation createStandardHighlight(List<Point> points, String message) {
        HighlightAnnotation highlight = new HighlightAnnotation();
        highlight.setBackgroundColor(65535);  // Yellow
        highlight.setOpacity(0.5);
        highlight.setFontColor(0);
        highlight.setMessage(message);
        highlight.setCreatedOn(Calendar.getInstance().getTime());
        highlight.setPoints(points);
        return highlight;
    }
}
```

## الأسئلة المتكررة

**س: هل يمكنني استخدام GroupDocs.Annotation في تطبيقات الويب؟**  
ج: بالتأكيد. يتكامل مع Spring Boot، Servlets، وأطر عمل الويب Java الأخرى. قم بإنشاء نقطة نهاية REST تستقبل ملف PDF، تطبق التمييزات، وتعيد الملف المعلق.

**س: كيف أتعامل مع التعليقات بلغات مختلفة؟**  
ج: تدعم المكتبة Unicode، لذا يمكنك إضافة تعليقات ورسائل بأي لغة. فقط تأكد من أن تطبيق Java الخاص بك يستخدم ترميز UTF‑8.

**س: ما هو تأثير الأداء عند إضافة العديد من التعليقات؟**  
ج: يتناسب الأداء مع عدد التعليقات، لكن حجم PDF له تأثير أكبر. بالنسبة للمستندات التي تحتوي على مئات التمييزات، فكر في التحميل الكسول أو التقسيم لتقليل استهلاك الذاكرة.

**س: هل يمكنني تعديل التعليقات الموجودة برمجيًا؟**  
ج: نعم. حمّل ملف PDF يحتوي على تعليقات موجودة، حدّث الخصائص مثل اللون أو الموقع، واحفظ النسخة المحدثة. هذا مثالي لبناء أدوات إدارة التعليقات.

**س: كيف يمكنني استخراج بيانات التعليقات للتقارير؟**  
ج: توفر GroupDocs.Annotation طرق تعداد لقراءة البيانات الوصفية (المؤلف، تاريخ الإنشاء، نص التعليق، إلخ). صدّر هذه البيانات إلى CSV أو JSON أو أدخلها في خطوط تحليل البيانات.

## الموارد الأساسية والوثائق

- [توثيق GroupDocs.Annotation Java](https://docs.groupdocs.com/annotation/java/) – أدلة شاملة ومراجع API  
- [مرجع API](https://reference.groupdocs.com/annotation/java/) – توثيق مفصل للطرق  
- [تحميل أحدث نسخة](https://releases.groupdocs.com/annotation/java/) – استخدم دائمًا أحدث إصدار مستقر  
- [شراء ترخيص](https://purchase.groupdocs.com/buy) – خيارات الترخيص للإنتاج  
- [الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) – مثالي للتطوير والاختبار  
- [منتدى دعم المجتمع](https://forum.groupdocs.com/c/annotation/) – احصل على مساعدة من الخبراء والمطورين الآخرين  

---

**آخر تحديث:** 2026-09-30  
**تم الاختبار مع:** GroupDocs.Annotation 25.2  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [تحرير تعليقات PDF Java - دليل GroupDocs الكامل](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [تحميل تعليقات PDF Java - دليل إدارة تعليقات GroupDocs الكامل](/annotation/java/annotation-management/groupdocs-annotation-java-manage-documents/)
- [إضافة سهم PDF في Java – دليل GroupDocs الكامل](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}