---
categories:
- Java Development
date: '2026-03-30'
description: تعلم كيفية إضافة تعليمة شطب في جافا باستخدام GroupDocs.Annotation. دليل
  خطوة بخطوة مع أمثلة على الشيفرة، ونصائح لحل المشكلات، وأفضل الممارسات لتعليم المستند.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: إضافة تعليمة شطب في جافا مع GroupDocs
type: docs
url: /ar/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# إضافة تعليقات الخط عبر Java - دليل GroupDocs الكامل

هل وجدت نفسك يومًا تحدق في مستند وتفكر، “أحتاج إلى شطب هذا النص، لكن لا يمكنني فقط أخذ قلم أحمر”؟ لست وحدك. سواء كنت تبني نظام مراجعة مستندات، أو تنشئ سير عمل تحرير، أو فقط تحتاج إلى وضع علامة على النص للحذف في تطبيق Java الخاص بك، فإن **add strikeout annotation java** هي مهارة أساسية. في هذا الدرس سنستعرض كل ما تحتاج معرفته لتنفيذ وظيفة شطب النص التي تعمل فعليًا في بيئة الإنتاج.

## إجابات سريعة
- **ما المكتبة التي تدعم تعليقات الخط عبر في Java؟** GroupDocs.Annotation for Java  
- **ما هي الكلمة المفتاحية الأساسية التي يجب استهدافها لتحسين محركات البحث؟** add strikeout annotation java  
- **هل أحتاج إلى ترخيص لتشغيل الكود التجريبي؟** تجربة مجانية أو ترخيص مؤقت يعمل للتطوير؛ ترخيص كامل مطلوب للإنتاج.  
- **هل يمكنني استخدام هذا مع ملفات PDF و DOCX و PPTX؟** نعم – يدعم GroupDocs.Annotation جميع صيغ المستندات الرئيسية.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى (يوصى بـ JDK 11+).

## ما هو add strikeout annotation java؟
تعليق الخط عبر يرسم خطًا عبر النص المحدد، مما يشير بصريًا إلى أن المحتوى يجب إزالته أو تجاهله. إنها طريقة غير مدمرة لاقتراح الحذف مع الحفاظ على النص الأصلي سليمًا لتتبع المراجعات أو للمراجعات التعاونية.

## لماذا نستخدم تعليقات الخط عبر في تطبيقات Java؟
- **سير عمل مراجعة المستندات** – يمكن للمراجعين وضع علامة على النص غير المرغوب فيه دون تعديل المصدر.  
- **تحرير تعاوني** – يرى أعضاء الفريق الحذف المقترح فورًا.  
- **القانونية والامتثال** – الحفاظ على سجل تدقيق واضح للتغييرات.  
- **ترحيل المحتوى** – وضع علامة على الأقسام القديمة قبل نقل المحتوى بين الأنظمة.  

## المتطلبات المسبقة وإعداد البيئة
ستحتاج إلى ما يلي قبل الغوص في الكود:

- **Java Development Kit (JDK)** 8+ (JDK 11+ موصى به)  
- **Maven أو Gradle** لإدارة التبعيات  
- **IDE** – IntelliJ IDEA أو Eclipse أو VS Code مع ملحقات Java  
- **GroupDocs.Annotation library** – سنستخدم الإصدار 25.2 في الأمثلة  

*مفيد أن تكون لديك:* معرفة أساسية بتعليقات Java ومعالجة PDF.

## إعداد GroupDocs.Annotation لـ Java

### تكوين Maven الذي يعمل فعليًا
أضف المستودع والتبعيات إلى ملف `pom.xml` الخاص بك تمامًا كما هو موضح:

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

### الحصول على الترخيص الخاص بك
تقدم GroupDocs عدة خيارات للترخيص:

- **تجربة مجانية** – مثالية للاختبار (لا تحتاج إلى بطاقة ائتمان)  
- **ترخيص مؤقت** – مثالي للتطوير والاختبار  
- **ترخيص كامل** – مطلوب للاستخدام في الإنتاج؛ راجع [صفحة الشراء](https://purchase.groupdocs.com/buy)

> **نصيحة احترافية:** ابدأ بالتجربة المجانية لاستكشاف API، ثم انتقل إلى ترخيص مؤقت عندما تكون جاهزًا لبناء ميزة حقيقية.

### إعداد فحص الصحة السريع
شغّل هذا البرنامج البسيط للتحقق من تحميل المكتبة بشكل صحيح:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

إذا طبع الطرفية رسالة النجاح دون أخطاء، فأنت جاهز لإضافة تعليقات الخط عبر.

## كيفية إضافة تعليقات الخط عبر java

فيما يلي تنفيذ كامل وجاهز للإنتاج مقسم إلى خطوات واضحة.

### الخطوة 1 – تهيئة Annotator
أنشئ كائن `Annotator` يشير إلى المستند المصدر:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **لماذا هذا مهم:** استخدام مسار مطلق أو مسار نسبي مُحلّ بشكل صحيح يمنع استثناءات “الملف غير موجود”.

### الخطوة 2 – (اختياري) إعداد ردود التعليقات
إضافة الردود تجعل التعليق تعاونيًا:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

تظهر هذه التعليقات عندما يمر المستخدم فوق الخط عبر.

### الخطوة 3 – تعريف منطقة الخط عبر
حدد المستطيل الذي يحيط بالنص الذي تريد شطبه:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **نصيحة إحداثيات:** الأصل (0,0) هو الزاوية العلوية اليسرى للصفحة؛ X يزداد إلى اليمين، Y يزداد إلى الأسفل. استخدم عارض PDF يُظهر الإحداثيات لضبط هذه القيم بدقة.

### الخطوة 4 – تكوين تعليقات الخط عبر
حدد المظهر، رقم الصفحة، وأرفق التعليقات:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*ملاحظة اللون:* `65535` يطابق الأصفر في صيغة RGB عددية. غيّر القيمة لاستخدام ألوان أخرى.

### الخطوة 5 – تطبيق التعليق وحفظه
أضف التعليق إلى المستند واكتب ملف الإخراج:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### الخطوة 6 – تنظيف الموارد (حاسم!)
دائمًا قم بتحرير Annotator لتفريغ الموارد الأصلية:

```java
if (annotator != null) {
    annotator.dispose();
}
```

في الإنتاج، غلف الاستخدام داخل كتلة try‑with‑resources أو بنية `try/finally`.

## المشكلات الشائعة وكيفية حلها

| المشكلة | العرض | الحل |
|---------|---------|-----|
| **File Not Found** | `Annotator` يرمي استثناء | استخدم مسارات مطلقة، تحقق من أذونات القراءة، تأكد من عدم حجز ملف من عملية أخرى |
| **Wrong Coordinates** | الخط عبر يظهر بعيدًا عن النص المقصود | تحقق مرة أخرى من نظام إحداثيات عارض PDF؛ اضبط النقاط وفقًا لذلك |
| **Annotation Invisible** | لا يظهر خط عبر بعد الحفظ | زيادة `opacity` (مثلاً `0.9`)، تحقق من `pageNumber` (قائمة صفرية)، تأكد من أن النقاط تشكل مستطيلًا صحيحًا |
| **OutOfMemoryError** | يتعطل التطبيق عند ملفات PDF الكبيرة | زيادة مساحة الذاكرة JVM (`-Xmx2048m`)، معالجة المستندات على دفعات، دائمًا استدعاء `dispose()` |

## أفضل ممارسات الأداء للإنتاج

### إدارة الذاكرة
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### استراتيجية المعالجة الدفعية
عندما تحتاج إلى تعليقات على عشرات أو مئات الملفات:

- معالجة 10‑20 مستندًا لكل دفعة.  
- سجّل النجاح/الفشل لكل ملف.  
- أعد تهيئة `Annotator` لكل مستند لتجنب تسرب الذاكرة.  

### نصائح التخزين المؤقت
- خزن قوالب المستندات المستخدمة بشكل متكرر.  
- احفظ خرائط الإحداثيات المحسوبة مسبقًا للتصاميم القياسية.  

## حالات الاستخدام الواقعية

- **أنظمة مراجعة المستندات** – يقترح المحررون حذفًا دون تعديل العقد الأصلي.  
- **التعديلات القانونية** – يتتبع المحامون إزالة البنود مع الحفاظ على الصياغة الأصلية للتدقيق.  
- **مراجعة الأقران الأكاديمية** – يحدد المراجعون الأقسام التي يجب إزالتها ويضيفون تعليقات داخلية.  
- **ترحيل المحتوى** – أثناء ترحيل أنظمة إدارة المحتوى، يبرز الخط عبر النصوص القديمة التي تحتاج إلى استبدال.  

## تخصيص متقدم

### تنسيق مخصص
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### إضافة بيانات تعريفية
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## قائمة التحقق من استكشاف الأخطاء وإصلاحها
- ✅ هل يمكنك فتح ملف المصدر يدويًا؟  
- ✅ هل جميع تبعيات GroupDocs موجودة في classpath؟  
- ✅ هل النقاط تشكل مستطيلًا صالحًا؟  
- ✅ هل رقم الصفحة صحيح (قائمة صفرية)؟  
- ✅ هل هناك ما يكفي من ذاكرة الـ heap؟  
- ✅ هل لديك إذن كتابة لمجلد الإخراج؟  
- ✅ هل صيغة المستند مدعومة (PDF، DOCX، PPTX، إلخ)؟  

## الأسئلة المتكررة

**س: هل يمكنني استخدام GroupDocs.Annotation داخل خدمة Spring Boot؟**  
ج: نعم. أضف تبعية Maven، حقن فئة خدمة تنشئ `Annotator`، وأدر دورة حياتها باستخدام نطاقات bean في Spring.

**س: أي صيغ المستندات تدعم تعليقات الخط عبر؟**  
ج: PDF، DOCX، PPTX، والعديد من الصيغ الأخرى المدعومة بواسطة GroupDocs.Annotation. يوفر PDF أكثر دقة في التعامل مع الإحداثيات.

**س: كيف أتعامل مع المستندات ذات أحجام صفحات مختلفة؟**  
ج: استرجع أبعاد الصفحة عبر `annotator.getPageInfo(pageNumber)` وقم بتعديل إحداثياتك وفقًا لذلك.

**س: هل يمكن تعديل أو حذف تعليق خط عبر موجود؟**  
ج: بالتأكيد. استخدم `annotator.getAnnotations(pageNumber)` لجلبه، ثم `annotator.update(updatedAnnotation)` أو `annotator.delete(annotationId)`.

**س: ما هو تأثير الأداء عند إضافة العديد من التعليقات؟**  
ج: إضافة مئات التعليقات عادةً لا مشكلة، لكن راقب استهلاك الذاكرة. بالنسبة لمجموعات تعليقات كبيرة جدًا، فكر في تقسيم العرض إلى صفحات أو تحميل التعليقات عند الطلب بشكل كسول.

## الخلاصة
أصبح لديك الآن دليل كامل وجاهز للإنتاج لإضافة **add strikeout annotation java** باستخدام GroupDocs.Annotation. ابدأ بالمثال البسيط لفحص الصحة، ثم قم بالتوسع إلى المعالجة الدفعية، التنسيق المخصص، وإثراء البيانات التعريفية. تذكر اختبار الإحداثيات بعناية، إدارة الموارد بمسؤولية، واختيار نموذج الترخيص المناسب لبيئتك.

هل أنت مستعد لاستكشاف المزيد؟ تفقد أنواع التعليقات الأخرى—التظليل، الملاحظة، الصورة، السهم، والعلامة المائية—لبناء مجموعة كاملة من ميزات التعاون على المستندات.

---

**آخر تحديث:** 2026-03-30  
**تم الاختبار مع:** GroupDocs.Annotation 25.2 for Java  
**المؤلف:** GroupDocs  

**موارد إضافية**
- [توثيق GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [دليل مرجع API](https://reference.groupdocs.com/annotation/java/)
- [تحميل أحدث نسخة](https://releases.groupdocs.com/annotation/java/)
- [شراء ترخيص كامل](https://purchase.groupdocs.com/buy)
- [ابدأ تجربة مجانية](https://releases.groupdocs.com/annotation/java/)
- [احصل على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- [منتدى دعم المجتمع](https://forum.groupdocs.com/c/annotation/)