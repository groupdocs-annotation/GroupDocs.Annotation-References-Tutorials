---
categories:
- Java Development
date: '2025-12-21'
description: تعرّف على كيفية إنشاء ملفات PDF نظيفة في Java وتعليق PDF في Java باستخدام
  GroupDocs.Annotation، مع أمثلة شاملة على الشيفرة ونصائح لحل المشكلات.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'إنشاء PDF نظيف بجافا: تعليقات توضيحية بخط تحت باستخدام GroupDocs'
type: docs
url: /ar/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# إنشاء ملفات PDF نظيفة بجافا: تعليقات توضيحية بخط سفلي باستخدام GroupDocs

## المقدمة

هل تواجه صعوبة في إدارة المستندات والتعاون في تطبيقات جافا الخاصة بك؟ لست وحدك. يواجه العديد من المطورين تحديًا في تنفيذ ميزات تعليقات توضيحية قوية للمستندات تعمل بشكل موثوق عبر صيغ ملفات مختلفة.

في هذا الدليل، ستقوم **بإنشاء ملفات PDF نظيفة بجافا** وتتعلم كيفية **إضافة تعليقات توضيحية إلى PDF في جافا** باستخدام GroupDocs.Annotation. بنهاية هذا الشرح، ستعرف بالضبط كيفية إضافة تعليقات توضيحية بخط سفلي مع تعليقات، وإزالة التعليقات التوضيحية الموجودة، وتكامل هذه الميزات بسلاسة في مشاريعك.

**ما ستتقنه في هذا الدليل:**
- إعداد GroupDocs.Annotation في مشروع جافا الخاص بك (بالطريقة الصحيحة)  
- إضافة تعليقات توضيحية بخط سفلي مع تعليقات مخصصة وتنسيق  
- إزالة جميع التعليقات التوضيحية لإنشاء إصدارات نظيفة من المستند  
- حل المشكلات الشائعة التي يواجهها المطورون  
- تحسين الأداء لتطبيقات الإنتاج  

سواء كنت تبني نظام مراجعة مستندات، منصة تعليمية، أو أداة تحرير تعاونية، يغطي هذا الشرح أمثلة عملية ومختبرة.

## إجابات سريعة
- **كيف يمكنني إضافة تعليق توضيحي بخط سفلي؟** استخدم `UnderlineAnnotation` و `annotator.add()` ثم احفظ المستند.  
- **كيف يمكنني إنشاء ملف PDF نظيف بجافا؟** حمّل الملف المعلَّق، اضبط `AnnotationType.NONE` في `SaveOptions`، واحفظ نسخة جديدة.  
- **ما المكتبات المطلوبة؟** GroupDocs.Annotation v25.2 (أو أحدث) ومستودع Maven الخاص بها.  
- **هل أحتاج إلى ترخيص للإنتاج؟** نعم—طبق ترخيص GroupDocs صالح لتجنب العلامات المائية.  
- **هل يمكنني معالجة مستندات متعددة بكفاءة؟** غلف كل `Annotator` بكتلة try‑with‑resources وتخلص منه بعد كل ملف.

## كيفية إنشاء ملفات PDF نظيفة بجافا
إنشاء ملف PDF نظيف بجافا يعني توليد نسخة من المستند **بدون أي تعليقات توضيحية** مع الحفاظ على المحتوى الأصلي. هذا مفيد للتوزيع النهائي، الأرشفة، أو عندما تحتاج إلى مشاركة نسخة “نظيفة” بعد دورة المراجعة.

يجعل GroupDocs.Annotation ذلك بسيطًا: حمّل الملف المعلَّق، اضبط `SaveOptions` لاستبعاد جميع أنواع التعليقات التوضيحية، واحفظ النتيجة. يتم توضيح الخطوات لاحقًا في قسم **إزالة التعليقات التوضيحية**.

## كيفية إضافة تعليقات توضيحية إلى PDF في جافا باستخدام GroupDocs
يوفر GroupDocs.Annotation واجهة برمجة تطبيقات غنية لـ **إضافة تعليقات توضيحية إلى PDF في جافا**. يدعم مجموعة واسعة من أنواع التعليقات، بما في ذلك التظليل، الطوابع، والخطوط السفلية. في هذا الشرح نركز على التعليقات السفلية لأنها تُستخدم عادة لتأكيد النص مع السماح بالتعليقات المتسلسلة.

## المتطلبات والبيئة التحضيرية

### ما ستحتاجه قبل البدء

**متطلبات بيئة التطوير:**
- مجموعة تطوير جافا (JDK) 8 أو أعلى (يفضل JDK 11+)  
- Maven 3.6+ أو Gradle 6.0+ لإدارة التبعيات  
- بيئة تطوير متكاملة مثل IntelliJ IDEA، Eclipse، أو VS Code مع ملحقات جافا  
- على الأقل 2 GB من الذاكرة المتاحة (معالجة المستندات قد تكون كثيفة الذاكرة)

**المتطلبات المعرفية:**
يجب أن تكون مرتاحًا مع مفاهيم جافا الأساسية—تهيئة الكائنات، استدعاءات الطرق، وتبعيات Maven. الخبرة السابقة مع المكتبات الخارجية ستسرّع عملية الاعتماد.

**مستندات الاختبار:**
احرص على وجود بعض ملفات PDF التجريبية. تعمل ملفات PDF النصية بشكل أفضل؛ قد تتطلب الصور الممسوحة ضوئيًا OCR قبل إضافة التعليقات.

### إعداد Maven: إضافة GroupDocs إلى مشروعك

إليك كيفية تكوين مشروع Maven بشكل صحيح (هذا يسبب إرباكًا للعديد من المطورين في محاولتهم الأولى):

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

**مهم:** الإصدار 25.2 هو أحدث إصدار مستقر في وقت كتابة هذا الدليل. تحقق بانتظام من مستودع GroupDocs للحصول على إصدارات أحدث تتضمن إصلاحات الأخطاء وتحسينات الأداء.

### إعداد الترخيص (لا تتخطى هذه الخطوة)

**للتطوير/الاختبار:**  
حمّل النسخة التجريبية المجانية من موقع GroupDocs. تشمل النسخة التجريبية جميع الميزات لكنها تضيف علامة مائية إلى المستندات المعالجة.

**للإنتاج:**  
اشترِ ترخيصًا وطبقه أثناء بدء تشغيل التطبيق. بدون ترخيص صالح، ستقتصر بنُسخ الإنتاج.

## دليل التنفيذ: إضافة تعليقات توضيحية بخط سفلي

### فهم سير عمل التعليقات التوضيحية

قبل الغوص في الكود، دعنا نستعرض سير العمل المكوّن من أربع خطوات يحدث عندما **تضيف تعليقات توضيحية إلى PDF في جافا**:

1. **تحميل المستند** – `Annotator` يقرأ الملف إلى الذاكرة.  
2. **إنشاء التعليق** – تحديد الخصائص مثل الموقع، النمط، والتعليقات.  
3. **تطبيق التعليق** – المكتبة تُدرج التعليق في بنية PDF.  
4. **حفظ المستند** – حفظ الملف المعدل، مع إمكانية الحفاظ على الأصلي.

العملية غير مدمرة؛ يبقى الملف الأصلي دون تغيير ما لم تقم بالكتابة فوقه.

### الخطوة 1: تهيئة Annotator وتحميل المستند

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**نصيحة احترافية:** استخدم مسارات مطلقة أثناء التطوير لتجنب أخطاء “الملف غير موجود”. في الإنتاج، فكر في تحميل الموارد من classpath أو من دلو تخزين سحابي.

### الخطوة 2: إنشاء تعليقات وردود (الجزء التعاوني)

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**استخدام عملي:** يمكن للمراجعين مناقشة بند معين بإضافة ردود متسلسلة، مما يبقي الحوار مرتبطًا بالتعليق المحدد.

### الخطوة 3: تحديد إحداثيات التعليق (ضبط الموقع بدقة)

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**نظام الإحداثيات:**  
- النقاط 1 و 2 تحددان الحافة العلوية للخط السفلي.  
- النقاط 3 و 4 تحددان الحافة السفلية.  
- الفرق في قيمة Y (730 مقابل 650) يتحكم في السماكة.

### الخطوة 4: إنشاء وتكوين التعليق السُفلي

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**نصائح اللون والشفافية:**  
- `FontColor` يستخدم ARGB؛ القيمة `65535` (0x00FFFF) تعطي أصفر ساطع.  
- للون الأحمر استخدم `16711680` (0xFF0000)؛ للأزرق `255` (0x0000FF).  
- قيم الشفافية بين 0.5 و 0.8 توفر قراءة جيدة دون إخفاء النص.

### الخطوة 5: حفظ المستند المعلَّق

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**إدارة الذاكرة:** استدعاء `dispose()` يحرّر الموارد الأصلية ويمنع تسرب الذاكرة—أمر حاسم عند معالجة العديد من الملفات على دفعة.

## إزالة التعليقات التوضيحية: إنشاء إصدارات نظيفة من المستند

أحيانًا تحتاج إلى نسخة من PDF **بدون أي تعليقات توضيحية**—مثلاً عند تسليم العقد النهائي المعتمد. يجعل GroupDocs ذلك سهلًا.

### فهم خيارات إزالة التعليقات

يمكنك:
- إزالة **جميع** التعليقات (الأكثر شيوعًا)  
- إزالة أنواع محددة (مثل التظليل فقط)  
- إزالة التعليقات حسب المؤلف أو الصفحة  

### خطوة بخطوة لإزالة التعليقات

**الخطوة 1: تحميل المستند المعلَّق مسبقًا**

```java
Annotator annotator = new Annotator(outputPath);
```

**الخطوة 2: ضبط خيارات الحفظ لإخراج نظيف**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**الخطوة 3: حفظ النسخة النظيفة**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

ينتج عن ذلك ملف **PDF نظيف بجافا** لا يحتوي على كائنات تعليقات توضيحية، وهو مثالي للتوزيع النهائي.

## المشكلات الشائعة والحلول

### المشكلة 1: خطأ “المستند غير موجود”

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### المشكلة 2: ظهور التعليقات في مواقع غير صحيحة

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### المشكلة 3: مشاكل الذاكرة مع المستندات الكبيرة

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### المشكلة 4: مشكلات الترخيص في الإنتاج

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## أفضل ممارسات الأداء لتطبيقات الإنتاج

### استراتيجيات إدارة الذاكرة

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### اعتبارات الخيوط (Threading)

GroupDocs.Annotation **ليس آمنًا للخطوط المتعددة** بشكل افتراضي. إذا كان تطبيقك يعالج المستندات بشكل متزامن:

- **لا تشارك** كائن `Annotator` بين الخيوط.  
- **زامن** الوصول إلى الملفات أو استخدم آلية قفل.  
- فكر في **تجميع** كائنات `Annotator` إذا كنت بحاجة إلى معدل معالجة مرتفع.

### استراتيجيات التخزين المؤقت (Caching)

- خزن قوالب التعليقات التوضيحية المستخدمة بشكل متكرر.  
- أعد استخدام مجموعات `Point` لإحداثيات شائعة.  
- احتفظ بـ **قالب PDF** في الذاكرة إذا كنت تعلّق نفس المستند الأساسي مرارًا.

## تطبيقات واقعية وحالات استخدام

### أنظمة مراجعة المستندات

- **مراجعة قانونية:** خط سُفلي على بنود العقد وإضافة تعليقات حول المخاطر.  
- **تدقيق الامتثال:** تظليل الأقسام المشكلة في القوائم المالية.  
- **مراجعة أكاديمية:** يضع الأساتذة خطوطًا سفلية على مقاطع تحتاج إلى توضيح.

### المنصات التعليمية

- **أدوات تعليقات الطلاب:** تمكين المتعلمين من وضع خطوط سفلية على المفاهيم الرئيسية في الكتب الإلكترونية.  
- **تعليقات المعلمين:** تقديم ملاحظات مدمجة مباشرة على الواجبات المقدمة.

### سير عمل ضمان الجودة

- **مراجعة الوثائق التقنية:** يضع المهندسون خطوطًا سفلية على الأقسام التي تحتاج إلى تحديث.  
- **إجراءات التشغيل القياسية:** يبرز مسؤولو السلامة الخطوات الحرجة.

### أنظمة إدارة المحتوى

- **سير تحرير المحتوى:** يضع المحررون خطوطًا سفلية على النص الذي يتطلب تدقيقًا للحقائق.  
- **التحكم في الإصدارات:** تتبع تاريخ التعليقات عبر إصدارات المستند.

## نصائح متقدمة للتنفيذ الاحترافي

### أنماط تعليقات مخصصة

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### بيانات تعريف التعليقات لتتبعها

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### التكامل مع أنظمة إدارة المستخدمين

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## استكشاف مشكلات الإنتاج

### مراقبة الأداء

راقب المقاييس التالية في الإنتاج:
- **استخدام الذاكرة** – تأكد من استدعاء `dispose()`.  
- **وقت المعالجة لكل مستند** – سجّل الطوابع الزمنية قبل/بعد `annotator.save()`.  
- **معدل الأخطاء** – التقط الاستثناءات وصنّفها.

### مشكلات شائعة في الإنتاج

- **قفل الملفات** – تأكد من إغلاق الملفات المرفوعة قبل التعليق.  
- **التعديلات المتزامنة** – نفّذ قفلًا متفائلًا أو فحصًا للإصدارات.  
- **ملفات كبيرة (> 50 ميغابايت)** – زد مهلة JVM وفكّر في استخدام واجهات برمجة التطبيقات المتدفقة.

### أفضل ممارسات معالجة الأخطاء

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## الخلاصة

أصبحت الآن تمتلك كل ما يلزم لـ **إنشاء ملفات PDF نظيفة بجافا** و**إضافة تعليقات توضيحية إلى PDF في جافا** باستخدام GroupDocs.Annotation. تذكّر أن:

- تدير الموارد باستخدام try‑with‑resources أو استدعاء `dispose()` صريح.  
- تتحقق من الإحداثيات مبكرًا لتجنب الخطوط السفلية غير الموضعة.  
- تطبق معالجة أخطاء قوية لضمان استقرار الإنتاج.  
- تستفيد من تنسيق الأنماط بناءً على الأدوار والبيانات الوصفية لتتناسب مع سير عملك.

ما الخطوة التالية؟ جرّب إضافة أنواع تعليقات أخرى—تظليل، طوابع، أو استبدال نصوص—لبناء حل مراجعة مستندات متكامل.

## الأسئلة المتكررة

**س: كيف يمكنني إضافة تعليقات توضيحية على عدة مناطق نصية في عملية واحدة؟**  
ج: أنشئ عدة كائنات `UnderlineAnnotation` بإحداثيات مختلفة وأضفها بالتتابع باستخدام `annotator.add()`.

**س: هل يمكنني التعليق على الصور داخل ملفات PDF؟**  
ج: نعم. استخدم نفس نظام الإحداثيات، مع التأكد من أن النقاط تقع داخل حدود الصورة.

**س: ما صيغ الملفات التي يدعمها GroupDocs.Annotation بخلاف PDF؟**  
ج: Word (DOC/DOCX)، Excel (XLS/XLSX)، PowerPoint (PPT/PPTX)، وصيغ الصور مثل JPEG، PNG، TIFF.

**س: كيف أتعامل مع مستندات ضخمة جدًا دون نفاد الذاكرة؟**  
ج: عالج المستندات واحدةً تلو الأخرى، زد حجم الذاكرة المخصصة للـ JVM (`-Xmx`)، وتأكد دائمًا من التخلص من كائنات `Annotator` فور الانتهاء.

**س: هل يمكن استخراج التعليقات التوضيحية الموجودة من مستند؟**  
ج: نعم. استخدم `annotator.get()` لاسترجاع جميع التعليقات، ثم صَفِّها حسب النوع أو المؤلف أو الصفحة حسب الحاجة.

---

**آخر تحديث:** 2025-12-21  
**تم الاختبار مع:** GroupDocs.Annotation 25.2  
**المؤلف:** GroupDocs