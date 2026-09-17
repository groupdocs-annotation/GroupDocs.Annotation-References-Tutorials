---
categories:
- Java Development
date: '2026-09-10'
description: تعلم كيفية إضافة role based annotation في Java باستخدام GroupDocs.Annotation،
  مع تغطية user roles، permission settings، حفظ PDF، ومعالجة collaboration.
keywords:
- role based annotation java
- java annotation user roles
- groupdocs annotation java
- document annotation permissions
- role based document workflow
lastmod: '2026-09-10'
linktitle: دليل Java Annotation User Roles
og_description: تعلم كيفية إضافة role based annotation في Java باستخدام GroupDocs.Annotation،
  مع تغطية user roles، permission settings، حفظ PDF، ومعالجة collaboration.
og_image_alt: 'Developer guide: Add role based annotation in Java with GroupDocs.Annotation'
og_title: كيفية إضافة role based annotation في Java باستخدام GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-09-10'
  description: Learn how to add role based annotation in Java with GroupDocs.Annotation,
    covering user roles, permission settings, PDF saving, and processing for collaboration.
  headline: How to add role based annotation in Java with GroupDocs
  type: TechArticle
- description: Learn how to add role based annotation in Java with GroupDocs.Annotation,
    covering user roles, permission settings, PDF saving, and processing for collaboration.
  name: How to add role based annotation in Java with GroupDocs
  steps:
  - name: creating replies with custom user roles
    text: '**How do you create a reply that respects a specific user role?** Create
      a `User` instance, assign the appropriate `Role` enum value (e.g., `EDITOR`
      or `VIEWER`), then attach the user to a `Reply` object before adding it to the
      annotation. This ensures the reply inherits the permissions defined by t'
  - name: configuring area annotations
    text: '**What is an area annotation and how do you bind role‑aware replies to
      it?** An area annotation highlights a rectangular region on a page. After you
      create the visual annotation, you attach the previously built `Reply` objects
      so that the role logic is enforced whenever a user interacts with the hig'
  - name: applying annotations and saving the PDF
    text: '**How can you persist the role‑based annotations to a new PDF file?** Load
      the target document with `Annotator`, add the prepared annotation, then call
      `annotator.save("output.pdf")`. The save operation writes only the annotation
      changes, keeping the original content intact while embedding the permi'
  type: HowTo
- questions:
  - answer: It offers a built‑in role‑based permission system, supports 50+ input
      and output formats, and provides enterprise‑grade features like audit trails
      and batch processing.
    question: What makes GroupDocs.Annotation stand out from other Java annotation
      libraries?
  - answer: Map your business‑specific roles to the existing `Role` enum (e.g., `Role.EDITOR`)
      and handle additional logic in your application layer, as shown in the `DocumentRole`
      example.
    question: How can I create custom roles beyond EDITOR and VIEWER?
  - answer: Yes. The `User` object accepts any identifier you use (e.g., database
      ID). Simply map your authenticated user to a `User` instance with the appropriate
      `Role`.
    question: Can I integrate this with my existing authentication system?
  - answer: Yes. The `annotator.save()` method writes only the annotation changes,
      making the save operation fast even for large files.
    question: Is it possible to **save annotated PDF** without re‑rendering the whole
      document?
  - answer: Loop through your file list, create a single `Annotator` per file, add
      all needed annotations, call `save()`, and then `dispose()`. Consider using
      a thread pool to parallelize the work.
    question: How do I efficiently **batch process annotations** across many PDFs?
  type: FAQPage
tags:
- role based annotation
- groupdocs
- java annotations
- pdf collaboration
- document security
title: كيفية إضافة role based annotation في Java باستخدام GroupDocs
type: docs
url: /ar/java/licensing-and-configuration/implement-groupdocs-annotation-java-user-roles/
weight: 1
---

# كيفية إضافة تعليقات توضيحية تعتمد على الدور في Java باستخدام GroupDocs

في هذا الدرس ستكتشف كيفية إضافة **تعليقات توضيحية تعتمد على الدور في Java** باستخدام مكتبة GroupDocs.Annotation. في نهاية الدليل ستكون قادرًا على تعريف أدوار مستخدم مخصصة، التحكم في أذونات التحرير والعرض لكل تعليق توضيحي، حفظ ملف PDF المُعَلَّم، وحتى معالجة العديد من الملفات بطريقة صديقة للدفعات.

## المقدمة

هل واجهت صعوبة في إدارة من يمكنه التحرير أو العرض أو التعليق على أجزاء محددة من مستنداتك؟ لست وحدك. **GroupDocs.Annotation for Java** يجعل تنفيذ **أدوار المستخدم المخصصة** سهلًا بشكل مدهش.

في هذا الدليل الشامل، سنرشدك خطوة بخطوة إلى إعداد أدوار المستخدم المخصصة للتعليقات التوضيحية. في النهاية، ستتمكن من إنشاء تدفقات عمل مستندات آمنة وتعاونية تمنح كل مستخدم الأذونات المناسبة بناءً على دوره.

- **ما ستتقنه:**  
  - إعداد أنظمة تعليقات توضيحية تعتمد على دور المستخدم المخصص في Java  
  - تكوين تعليقات توضيحية مساحية بخصائص خاصة بالدور  
  - إدارة الأذونات للتعليقات والردود وحفظ المستند  
  - التعامل مع سيناريوهات واقعية مثل تعليقات المستندات القانونية ومعالجة الدفعات  

هل أنت مستعد لبناء إدارة مستندات أذكى في تطبيقات Java الخاصة بك؟ لنبدأ!

## إجابات سريعة
- **ما الفائدة الأساسية من أدوار المستخدم المخصصة؟** تتيح لك التحكم في من يمكنه التحرير أو العرض أو التعليق على كل تعليق توضيحي، مما يضمن الأمان والامتثال.  
- **أي مكتبة توفر هذه الوظيفة؟** GroupDocs.Annotation for Java.  
- **هل أحتاج إلى ترخيص مدفوع للبدء؟** لا—استخدم النسخة التجريبية المجانية لتطوير واختبار مجموعة الميزات الكاملة.  
- **هل يمكنني حفظ ملف PDF المُعَلَّم بعد تطبيق الأدوار؟** نعم—استدعِ `annotator.save()` لإنشاء **ملف PDF مُعَلَّم** مع تطبيق جميع الأذونات.  
- **هل تدعم المعالجة الدفعية؟** بالتأكيد؛ يمكنك معالجة العديد من المستندات أو التعليقات التوضيحية على دفعات للحصول على أداء أفضل.

## ما هي أدوار المستخدم المخصصة؟

أدوار المستخدم المخصصة هي تعريفات دور (مثل EDITOR، VIEWER، REVIEWER) تُعيّن لكل كائن `User`. يحدد الدور ما يمكن للمستخدم القيام به على التعليق التوضيحي—سواء كان يمكنه تحرير المحتوى، أو مجرد عرضه، أو إضافة ردود.

## لماذا نستخدم أدوار المستخدم المخصصة؟

توفر أدوار المستخدم المخصصة تحكمًا دقيقًا في من يمكنه تعديل أو عرض أو التعليق على كل تعليق توضيحي، وهو أمر أساسي للحفاظ على سلامة المستند وتلبية متطلبات الامتثال. من خلال تعيين أذونات محددة لكل دور، تقلل من خطر التغييرات غير المقصودة وتُنشئ سجلات تدقيق واضحة.

- **تعليق المستندات القانونية** – تأكد من أن المحامين المخولين فقط يمكنهم الموافقة على التغييرات بينما يمكن للمساعدين القانونيين فقط التعليق.  
- **التحكم في التعاون** – منع الكتابة غير المقصودة عن طريق تقييد حقوق التحرير.  
- **قابلية التدقيق** – تتبع من قام بأي تغييرات ومتى، وهو أمر أساسي للامتثال.  

## متى نستخدم التعليقات التوضيحية المعتمدة على الدور؟

تكون التعليقات التوضيحية المعتمدة على الدور ذات قيمة قصوى في البيئات التي يحتاج فيها أصحاب المصلحة المختلفون إلى مستويات وصول متميزة، مثل العقود القانونية، المحتوى التعليمي، سير عمل الشركات، أو سجلات الرعاية الصحية. يضمن تنفيذها أن المستخدمين المخولين فقط يمكنهم تحرير الأقسام الحرجة بينما يمكن للآخرين تقديم ملاحظات أو عرض المستند بأمان.

- **المستندات القانونية والامتثال** – العقود، اتفاقيات عدم الإفشاء، والوثائق السياسية تحتاج إلى أذونات تحرير صارمة.  
- **المنصات التعليمية** – المدربون (محررون) مقابل الطلاب (مشاهدون).  
- **سير عمل الشركات** – مدراء المشاريع (حقوق كاملة) مقابل أعضاء الفريق (تعليقات فقط).  
- **سجلات الرعاية الصحية** – الأطباء، الممرضات، والمرضى كل منهم يحتاج إلى مستويات وصول مختلفة.  

## المتطلبات المسبقة والإعداد

تأكد من توفر ما يلي قبل البدء:

- **GroupDocs.Annotation for Java** (الإصدار 25.2 أو أحدث)  
- JDK 8 + وMaven مثبتان  
- ملف PDF تجريبي للتعليق عليه  

## إعداد GroupDocs.Annotation for Java

### تكوين Maven

أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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

### الحصول على الترخيص

يمكنك البدء بنسخة **تجريبية مجانية** توفر جميع الوظائف. عندما تكون جاهزًا للإنتاج، احصل على **ترخيص تطوير مؤقت** أو اشترِ ترخيصًا كاملًا.

**نصيحة احترافية:** اختبر سير عمل التعليقات التوضيحية بالكامل باستخدام النسخة التجريبية قبل الالتزام بالشراء.

## التنفيذ الأساسي: إضافة أدوار مستخدم مخصصة إلى التعليقات التوضيحية

### الخطوة 1: إنشاء ردود مع أدوار مستخدم مخصصة

**كيف تنشئ ردًا يحترم دور مستخدم محدد؟**  
أنشئ كائن `User`، عيّن قيمة تعداد `Role` المناسبة (مثل `EDITOR` أو `VIEWER`)، ثم اربط المستخدم بكائن `Reply` قبل إضافته إلى التعليق التوضيحي. يضمن ذلك أن الرد يرث الأذونات المحددة بالدور.

يمثل صف `User` الفرد الذي يتفاعل مع التعليق التوضيحي، بينما يحدد تعداد `Role` مجموعة الأذونات لذلك المستخدم.

```java
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.User;
import com.groupdocs.annotation.models.Role;

import java.util.ArrayList;
import java.util.Calendar;

// Create the first reply with an EDITOR role
Reply reply1 = new Reply();
reply1.setComment("This comment will be applied");
reply1.setRepliedOn(Calendar.getInstance().getTime());
User user1 = new User(1, "Reviewer", Role.EDITOR);
reply1.setUser(user1);

// Create the second reply with a VIEWER role
Reply reply2 = new Reply();
reply2.setComment("This comment will NOT be applied");
reply2.setRepliedOn(Calendar.getInstance().getTime());
User user2 = new User(1, "Member", Role.VIEWER);
reply2.setUser(user2);

java.util.List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

> **لماذا هذا مهم:** يتحكم تعداد `Role` في ما يمكن لكل مستخدم القيام به. يمكن للمحرر (EDITOR) تعديل التعليق، بينما يمكن للمشاهد (VIEWER) فقط عرضه.

### الخطوة 2: تكوين تعليقات توضيحية مساحية

**ما هي التعليقات التوضيحية المساحية وكيف تربط الردود المدعومة بالدور بها؟**  
التعليق التوضيحي المساحي يبرز منطقة مستطيلة على صفحة. بعد إنشاء التعليق البصري، تُرفق كائنات `Reply` التي تم إنشاؤها مسبقًا بحيث تُطبق منطق الدور كلما تفاعل المستخدم مع المنطقة المظللة.

يحدد صف `AreaAnnotation` الشكل واللون ونمط المنطقة المظللة.

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.AreaAnnotation;

// Initialize the AreaAnnotation object
AreaAnnotation area = new AreaAnnotation();
area.setBackgroundColor(65535); // Use RGB for color coding
area.setBox(new Rectangle(100, 100, 100, 100)); // Position and size
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("This is an area annotation");
area.setOpacity(0.7);
area.setPageNumber(0);
area.setPenColor(65535); // Outline color
area.setPenStyle(PenStyle.DOT);
area.setPenWidth((byte) 3);
area.setReplies(replies); // Attach the replies to this annotation
```

**ملاحظات التكوين الأساسية**

- **ترميز اللون**: `65535` (سماوي) يجعل التعليق بارزًا دون إخفاء النص.  
- **الموقع**: `Rectangle(100, 100, 100, 100)` يضع صندوقًا بحجم 100 × 100 بكسل عند (100, 100).  
- **النمط**: نمط قلم منقط مع شفافية 0.7 يوفر إشارة بصرية دقيقة.  
- **إرفاق الرد**: يربط ردودنا المخصصة بالدور إلى التعليق البصري.

### الخطوة 3: تطبيق التعليقات وحفظ ملف PDF

**كيف يمكنك حفظ التعليقات التوضيحية المعتمدة على الدور في ملف PDF جديد؟**  
حمّل المستند الهدف باستخدام `Annotator`، أضف التعليق المُعد مسبقًا، ثم استدعِ `annotator.save("output.pdf")`. عملية الحفظ تكتب فقط تغييرات التعليقات، مع الحفاظ على المحتوى الأصلي وإدراج بيانات الأذونات.

صف `Annotator` هو نقطة الدخول لتحميل وتعديل وحفظ المستندات المُعَلَّمة.

```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with your input PDF file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
annotator.add(area); // Add the area annotation
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf"); // Save the annotated document
annotator.dispose(); // Release resources after saving
```

> **نصيحة الذاكرة:** استدعِ دائمًا `dispose()` بعد الانتهاء من المعالجة لتجنب تسرب الذاكرة، خاصةً عند **معالجة التعليقات التوضيحية على دفعات** عبر ملفات متعددة.

## نصائح متقدمة وأفضل الممارسات

### إدارة أدوار المستخدم المتعددة بكفاءة

**كيف تُطابق الأدوار الخاصة بالأعمال بأدوار GroupDocs دون إغراق الكود؟**  
أنشئ تعدادًا مساعدًا يترجم أدوار نطاقك (مثل `PROJECT_MANAGER`، `DEVELOPER`) إلى قيم `Role` المقابلة المقدمة من GroupDocs. يركز هذا الترجمة في مكان واحد ويسهل تعديلها مستقبلاً.

```java
// Example of how you might organize roles in a real application
public enum DocumentRole {
    OWNER(Role.EDITOR, true, true, true),    // Can edit, delete, and manage permissions
    COLLABORATOR(Role.EDITOR, true, false, false), // Can edit but not delete or manage
    REVIEWER(Role.VIEWER, false, false, false);    // Can only view and comment
    
    private final Role baseRole;
    private final boolean canEdit;
    private final boolean canDelete;
    private final boolean canManagePermissions;
    
    // Constructor and methods...
}
```

### تحسين الأداء للمستندات الكبيرة

**ما الاستراتيجيات التي تحافظ على سرعة التعليقات التوضيحية الدفعية وتقلل استهلاك الذاكرة؟**  
1. عالج التعليقات في مجموعات بدلاً من واحدة تلو الأخرى.  
2. استخدم عرضًا منخفض الدقة للسيناريوهات التي تقتصر على المعاينة.  
3. خزن ملفات PDF المتكررة الوصول على القرص أو في الذاكرة.  
4. انقل أعمال التعليق الثقيلة إلى خيوط خلفية أو طابور وظائف.  

### استراتيجيات ترميز اللون لرؤية الأدوار

- **المحررين** – `65535` (سماوي) – واضح وقابل للتنفيذ.  
- **المراجعين** – `16711680` (أحمر) – يشير إلى عناصر تحتاج انتباهًا.  
- **المشاهدين** – `8421504` (رمادي) – خفيف، للقراءة فقط.

## مشاكل التنفيذ الشائعة (وكيفية حلها)

### التعليقات لا تُعرض بشكل صحيح

- **السبب:** نظام إحداثيات PDF يبدأ من الزاوية السفلية اليسرى.  
- **الحل:** عدّل إحداثيات Y أو استخدم `annotator.getPageHeight()` لحساب المواقع.

### أدوار المستخدم لا تُطبق

- **السبب:** إعادة استخدام نفس كائن `User` لأدوار مختلفة أو نسيان تعيين تعداد `Role`.  
- **الحل:** أنشئ كائن `User` جديد لكل دور وعينه قبل إضافة الردود.

### مشاكل الذاكرة مع ملفات PDF الكبيرة

- **السبب:** عدم استدعاء `dispose()` لكائنات `Annotator` أو معالجة عدد كبير من المستندات في آنٍ واحد.  
- **الحل:** استدعِ `dispose()` بعد كل مستند وحدّ عدد العمليات المتزامنة.

## أمثلة تكامل واقعية

### تكامل منصة التعلم الإلكتروني

```java
// Example: Setting up annotations for an educational document
User instructor = new User(1, "Dr. Smith", Role.EDITOR);
User student = new User(2, "John Doe", Role.VIEWER);

// Instructor can add official feedback
Reply instructorFeedback = new Reply();
instructorFeedback.setComment("Excellent analysis! Consider adding more examples.");
instructorFeedback.setUser(instructor);

// Student can ask questions but can't modify instructor comments
Reply studentQuestion = new Reply();
studentQuestion.setComment("Could you clarify the third point?");
studentQuestion.setUser(student);
```

### حالة استخدام تعليقات المستندات القانونية

في مكتب محاماة، قد تعرف:

- **الشركاء الكبار** – `OWNER` (تحكم كامل في التحرير والأذونات)  
- **المساعدون** – `COLLABORATOR` (تحرير وتعليق)  
- **المساعدون القانونيون** – `REVIEWER` (تعليق فقط)  
- **العملاء** – `VIEWER` (قراءة فقط مع إمكانية التعليق)

تضمن هذه التسلسل الهرمي أن الأشخاص المناسبين فقط يمكنهم الموافقة على التغييرات بينما يمكن للجميع المساهمة بأمان.

## الخاتمة

أصبحت الآن تمتلك أساسًا قويًا لتطبيق **أدوار المستخدم المخصصة** في سير عمل التعليقات التوضيحية في Java باستخدام GroupDocs.Annotation. من خلال دمج منطق الأذونات المعتمد على الدور مع إدارة الذاكرة السليمة وحيل الأداء، يمكنك بناء حلول مستندات آمنة وتعاونية تتوسع من ملف PDF واحد إلى خطوط معالجة دفعية ضخمة.

**الخطوات التالية:**  
- جرّب الشيفرة في مشروع نموذجي صغير.  
- وسّع تعداد `DocumentRole` ليتوافق مع هيكلية مؤسستك.  
- استكشف واجهات تصدير GroupDocs لإنشاء تقارير لجميع التعليقات التوضيحية والأدوار المرتبطة بها.

---

## الأسئلة المتكررة

**س: ما الذي يميز GroupDocs.Annotation عن مكتبات التعليقات التوضيحية الأخرى في Java؟**  
ج: يقدم نظام أذونات مبني على الدور، يدعم أكثر من 50 تنسيق إدخال وإخراج، ويوفر ميزات على مستوى المؤسسة مثل سجلات التدقيق ومعالجة الدفعات.

**س: كيف يمكنني إنشاء أدوار مخصصة تتجاوز EDITOR وVIEWER؟**  
ج: قم بترجمة أدوارك الخاصة إلى تعداد `Role` الموجود (مثل `Role.EDITOR`) وتعالج المنطق الإضافي في طبقة التطبيق، كما هو موضح في مثال `DocumentRole`.

**س: هل يمكن دمجه مع نظام المصادقة الحالي؟**  
ج: نعم. يقبل كائن `User` أي معرف تستخدمه (مثل معرف قاعدة البيانات). ما عليك سوى ربط المستخدم المصادق إليه بكائن `User` مع الدور المناسب.

**س: هل يمكن **حفظ ملف PDF مُعَلَّم** دون إعادة تصيير المستند بالكامل؟**  
ج: نعم. طريقة `annotator.save()` تكتب فقط تغييرات التعليقات، مما يجعل عملية الحفظ سريعة حتى للملفات الكبيرة.

**س: كيف يمكنني **معالجة التعليقات التوضيحية على دفعات** بفعالية عبر العديد من ملفات PDF؟**  
ج: حلق عبر قائمة الملفات، أنشئ كائن `Annotator` واحد لكل ملف، أضف جميع التعليقات المطلوبة، استدعِ `save()`، ثم `dispose()`. فكر في استخدام مجموعة خيوط لتوازي العمل.

**س: هل يمكنني تصدير بيانات التعليقات فقط (مثل JSON) دون الـ PDF الكامل؟**  
ج: نعم. توفر GroupDocs طرق تصدير تُخرج بيانات التعليقات في JSON أو XML، مفيدة للتقارير أو المزامنة مع أنظمة أخرى.

---

**آخر تحديث:** 2026-09-10  
**تم الاختبار مع:** GroupDocs.Annotation 25.2  
**المؤلف:** GroupDocs  

**موارد إضافية**  
- الوثائق: [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/java/)  
- مرجع API: [Complete API Reference Guide](https://reference.groupdocs.com/annotation/java/)  
- تحميل المكتبة: [Get the Latest Version](https://releases.groupdocs.com/annotation/java/)  
- دعم المجتمع: [GroupDocs Support Forum](https://forum.groupdocs.com/c/annotation/)  
- خيارات الشراء: [Licensing Information](https://purchase.groupdocs.com/license)

## دروس ذات صلة

- [Custom User Roles in Java Annotation: Complete Implementation Guide](/annotation/java/licensing-and-configuration/implement-groupdocs-annotation-java-user-roles/)  
- [Load PDF Java with GroupDocs Annotation: Document Loading Guide](/annotation/java/document-loading/)  
- [Create PDF Highlights Java: Complete Guide with GroupDocs Annotation](/annotation/java/annotation-management/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}