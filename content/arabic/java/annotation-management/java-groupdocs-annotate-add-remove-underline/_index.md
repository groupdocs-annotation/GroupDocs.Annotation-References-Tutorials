---
"date": "2025-05-06"
"description": "تعرّف على كيفية إضافة التعليقات التوضيحية المسطرة وإزالتها في مستندات جافا باستخدام GroupDocs.Annotation. حسّن إدارة مستنداتك مع هذا الدليل المفصل."
"title": "إضافة وإزالة التعليقات التوضيحية المسطرة في Java باستخدام GroupDocs - دليل شامل"
"url": "/ar/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# كيفية تنفيذ Java: إضافة وإزالة التعليقات التوضيحية المسطرة باستخدام GroupDocs

## مقدمة

هل ترغب في تحسين نظام إدارة المستندات لديك بإضافة أو إزالة التعليقات التوضيحية برمجيًا؟ يرشدك هذا البرنامج التعليمي إلى كيفية استخدام مكتبة GroupDocs.Annotation القوية في جافا لإضافة تعليقات توضيحية مسطرة وإزالتها من مستندات مثل ملفات PDF.

**ما سوف تتعلمه:**
- قم بتهيئة فئة Annotator.
- قم بإضافة تعليق توضيحي مسطر مع التعليقات باستخدام GroupDocs.Annotation لـ Java.
- إزالة كافة التعليقات التوضيحية من المستند.
- قم بتكوين بيئتك لاستخدام GroupDocs.Annotation بكفاءة.

دعونا نستكشف كيفية الاستفادة من هذه الوظائف في مشاريعك. تأكد من تلبية المتطلبات الأساسية اللازمة قبل البدء.

## المتطلبات الأساسية

### المكتبات والتبعيات المطلوبة
لمتابعة هذا البرنامج التعليمي بشكل فعال، تأكد من أن لديك:
- **GroupDocs.Annotation لـ Java**:يوصى باستخدام الإصدار 25.2 أو الإصدار الأحدث.
- **مجموعة تطوير جافا (JDK)**:يجب أن يكون الإصدار 8 أو أعلى.

### متطلبات إعداد البيئة
تأكد من أن بيئة التطوير الخاصة بك تتضمن IDE مثل IntelliJ IDEA أو Eclipse وأداة بناء مثل Maven.

### متطلبات المعرفة
سيكون من المفيد الحصول على فهم أساسي لبرمجة Java، وخاصة العمل مع المكتبات عبر Maven.

## إعداد GroupDocs.Annotation لـ Java

لبدء استخدام GroupDocs.Annotation في مشاريع Java الخاصة بك، اتبع خطوات الإعداد التالية:

**تكوين Maven:**
أضف التكوين التالي إلى ملفك `pom.xml` ملف لتنزيل GroupDocs.Annotation ودمجه.

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

**الحصول على الترخيص:**
ابدأ بتنزيل نسخة تجريبية مجانية أو احصل على ترخيص مؤقت من GroupDocs لاستكشاف كامل إمكانيات مكتبتهم. للاستخدام الإنتاجي، يلزم شراء ترخيص.

## دليل التنفيذ

### الميزة 1: تهيئة المُعلِّق وإضافة تعليق توضيحي مُسطَّر

يرشدك هذا القسم خلال عملية تهيئة `Annotator` الفئة وإضافة تعليق توضيحي مسطر إلى مستندك.

#### ملخص
تُساعد إضافة التعليقات التوضيحية على إبراز أجزاء مُحددة من المستند. هنا، نُركز على تسطير النص بالتعليقات للتوضيح أو التعليق.

#### التنفيذ خطوة بخطوة

**1. تهيئة المُعلِّق**
إنشاء `Annotator` الكائن وتحميل ملف PDF الخاص بك.

```java
import com.groupdocs.annotation.Annotator;

// قم بتحميل المستند الذي تريد التعليق عليه
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. إنشاء تعليقات مع الردود**
قم بتحديد التعليقات المرتبطة بالتعليق التوضيحي المسطر.

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

**3. تحديد نقاط للتعليق التوضيحي المسطر**
قم بتعيين الإحداثيات لتحديد المكان الذي يجب أن يظهر فيه الخط السفلي.

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

**4. إنشاء وتكوين تعليق التسطير**
قم بإنشاء تعليق توضيحي مسطر وتعيين خصائصه مثل اللون والتعتيم والتعليقات.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // الأصفر بتنسيق ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. احفظ المستند الموضح**
احفظ التغييرات في ملف جديد.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### نصائح استكشاف الأخطاء وإصلاحها
- تأكد من أن جميع إحداثيات النقاط تقع ضمن حدود المستند.
- تأكد من أن `outputPath` الدليل موجود ويمكن الكتابة فيه.

### الميزة 2: حفظ المستند بدون أي تعليقات توضيحية

يتناول هذا القسم كيفية إزالة جميع التعليقات التوضيحية من مستند تمت إضافته إليه تعليقات توضيحية مسبقًا.

#### ملخص
قد تحتاج إلى حفظ نسخة نظيفة من مستندك بدون أي تعليقات لأغراض المشاركة أو الأرشفة.

#### التنفيذ خطوة بخطوة

**1. قم بتهيئة المُعلق باستخدام المستند المُعلق**
قم بتحميل المستند الذي يحتوي على التعليقات التوضيحية الموجودة.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. قم بتكوين خيارات الحفظ لإزالة التعليقات التوضيحية**
حدد أنه لا ينبغي حفظ أي تعليقات في ملف الإخراج.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. احفظ المستند بدون تعليقات توضيحية**
قم بتحديد المسار للمستند المنظف وحفظه.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## التطبيقات العملية

فيما يلي بعض السيناريوهات الواقعية حيث يمكن أن تكون هذه الميزات مفيدة:
1. **مراجعة المستندات**:تسليط الضوء على أقسام العقد أو التقرير والتعليق عليها للمراجعة.
2. **الأدوات التعليمية**:شرح الكتب المدرسية مع الملاحظات أو التصحيحات للطلاب.
3. **التحرير التعاوني**:مشاركة المسودات الموضحة بين أعضاء الفريق للحصول على ردود الفعل.
4. **الوثائق القانونية**:تسليط الضوء على البنود الرئيسية في الوثائق القانونية أثناء المناقشات.
5. **مواد التسويق**:تسليط الضوء على المعلومات المهمة في الكتيبات قبل توزيعها.

## اعتبارات الأداء
عند العمل مع GroupDocs.Annotation، ضع في اعتبارك النصائح التالية لتحسين الأداء:
- **إدارة الذاكرة**:التخلص منها بشكل صحيح `Annotator` الأشياء لتحرير الموارد.
- **معالجة الدفعات**:إذا كنت تقوم بتعليق توضيحي على مستندات متعددة، فقم بمعالجتها على دفعات لإدارة تحميل النظام بشكل فعال.
- **تخصيص الموارد**:تأكد من أن بيئتك تحتوي على ذاكرة وقوة معالجة كافية للتعامل مع الملفات الكبيرة.

## خاتمة
لقد تعلمت كيفية إضافة وإزالة التعليقات التوضيحية المسطرة باستخدام GroupDocs.Annotation لجافا. غطّى هذا البرنامج التعليمي تهيئة فئة Annotator، وتكوين التعليقات التوضيحية، وحفظ المستندات بدونها. 

لمزيد من الاستكشاف، فكر في دمج هذه الميزات في أنظمة إدارة المستندات الحالية لديك أو تجربة أنواع التعليقات التوضيحية الأخرى التي توفرها GroupDocs.

## قسم الأسئلة الشائعة
1. **كيف أقوم بإعداد تعليقات توضيحية متعددة في تشغيل واحد؟**
   - إنشاء متعددة `UnderlineAnnotation` الكائنات وإضافتها بشكل تسلسلي باستخدام `annotator.add()` طريقة.
2. **هل يمكنني التعليق على الصور داخل ملفات PDF باستخدام هذه المكتبة؟**
   - نعم، يدعم GroupDocs.Annotation التعليق على الصور داخل المستندات مثل ملفات PDF.
3. **ما هي تنسيقات الملفات التي يدعمها GroupDocs.Annotation؟**
   - إنه يدعم تنسيقات المستندات المختلفة بما في ذلك PDF وWord وExcel والمزيد.