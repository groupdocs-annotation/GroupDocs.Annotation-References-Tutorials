---
"date": "2025-05-06"
"description": "تعرّف على كيفية تحسين مستندات PDF الخاصة بك بإضافة عناصر قائمة منسدلة تفاعلية باستخدام GroupDocs.Annotation لـ .NET. اتبع هذا الدليل خطوة بخطوة لتبسيط إدخال المستخدم وتحسين وظائف المستند."
"title": "إضافة قائمة منسدلة إلى ملفات PDF باستخدام GroupDocs.Annotation لـ .NET - دليل شامل"
"url": "/ar/net/form-field-annotations/add-dropdown-pdf-groupdocs-annotation-net/"
"weight": 1
---

# كيفية إضافة مكون القائمة المنسدلة إلى مستند PDF باستخدام GroupDocs.Annotation لـ .NET

## مقدمة

حسّن مستندات PDF الخاصة بك بدمج عناصر تفاعلية مثل القوائم المنسدلة، مما يسمح للمستخدمين باختيار الخيارات مباشرةً داخل المستند. يرشدك هذا البرنامج التعليمي إلى كيفية استخدام GroupDocs.Annotation لـ .NET لإضافة مكونات القوائم المنسدلة بكفاءة.

**ما سوف تتعلمه:**
- إعداد GroupDocs.Annotation واستخدامه لـ .NET
- تنفيذ مكونات القائمة المنسدلة في مستندات PDF
- تكوين خصائص مثل الخيارات والموضع والتعليقات التوضيحية

لنبدأ بالتأكد من أن بيئتك جاهزة!

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك الإعداد التالي:

### المكتبات والإصدارات المطلوبة:
- **GroupDocs.Annotation لـ .NET**:ضروري لإضافة التعليقات التوضيحية إلى مستندات PDF.

### متطلبات إعداد البيئة:
- تم تثبيت Visual Studio على جهاز التطوير الخاص بك.
- المعرفة الأساسية بلغة البرمجة C# والتعرف على تطبيقات .NET.

## إعداد GroupDocs.Annotation لـ .NET

للبدء، ثبّت مكتبة GroupDocs.Annotation. إليك تعليمات التثبيت:

**وحدة تحكم مدير الحزم NuGet**
```bash
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### خطوات الحصول على الترخيص

يمكنك الحصول على ترخيص لـ GroupDocs.Annotation بعدة طرق:
- **نسخة تجريبية مجانية**:قم بتنزيل النسخة التجريبية لاستكشاف ميزات المكتبة.
- **رخصة مؤقتة**:الحصول على ترخيص مؤقت للاختبار الموسع.
- **شراء**:شراء ترخيص كامل للاستخدام الإنتاجي.

### التهيئة الأساسية والإعداد باستخدام C#

إليك كيفية تهيئة GroupDocs.Annotation:

```csharp
using GroupDocs.Annotation;

// قم بتهيئة كائن المعلق باستخدام المسار إلى مستند PDF الخاص بك.
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

## دليل التنفيذ

### إضافة مكون القائمة المنسدلة إلى ملف PDF الخاص بك

#### ملخص
في هذا القسم، سنضيف مكونًا منسدلة بخيارات محددة مسبقًا. تتيح هذه الميزة للمستخدمين التفاعل باختيار خيار من القائمة المنسدلة.

#### التنفيذ خطوة بخطوة

**الخطوة 1: تهيئة المُعلّق**

أولاً، قم بإنشاء مثيل لـ `Annotator` الفئة باستخدام مسار مستند PDF المدخل الخاص بك:

```csharp
using GroupDocs.Annotation;
using System;

string inputPdfPath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY/result.pdf");
```

**الخطوة 2: إنشاء مكون القائمة المنسدلة**

الآن، دعنا نقوم بإنشاء مكون القائمة المنسدلة مع خيارات مخصصة:

```csharp
// إنشاء مكون القائمة المنسدلة الجديد
DropdownComponent dropdown = new DropdownComponent
{
    // قم بتحديد الخيارات التي ستظهر في القائمة المنسدلة
    Options = new List<string> { "Item1", "Item2", "Item3" },
    
    // اترك الخيار المحدد فارغًا في البداية
    SelectedOption = null,
    
    // إضافة نص نائب
    Placeholder = "Choose option",
    
    // تعيين موضع وحجم القائمة المنسدلة (X، Y، العرض، الارتفاع)
    Box = new Rectangle(100, 100, 100, 100),
    
    // تعيين طابع زمني للإنشاء
    CreatedOn = DateTime.Now,
    
    // أضف رسالة/تلميحًا للقائمة المنسدلة
    Message = "This is dropdown component",
    
    // تعيين رقم الصفحة (فهرس يعتمد على 0)
    PageNumber = 0,
    
    // ضبط لون القلم (65535 يمثل اللون الأزرق في RGB)
    PenColor = 65535,
    
    // ضبط نمط القلم
    PenStyle = PenStyle.Dot,
    
    // ضبط عرض القلم
    PenWidth = 3
};
```

**الخطوة 3: إضافة التعليقات إلى القائمة المنسدلة (اختياري)**

يمكنك إضافة ردود أو تعليقات إلى مكون القائمة المنسدلة:

```csharp
// إضافة الردود/التعليقات إلى القائمة المنسدلة
dropdown.Replies = new List<Reply>
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
};
```

**الخطوة 4: إضافة القائمة المنسدلة إلى المستند وحفظها**

وأخيرًا، أضف القائمة المنسدلة إلى المستند واحفظه:

```csharp
// أضف مكون القائمة المنسدلة إلى المستند
annotator.Add(dropdown);

// احفظ المستند باستخدام القائمة المنسدلة المضافة
annotator.Save(outputPath);
```

### مثال التنفيذ الكامل

فيما يلي الكود الكامل لإضافة مكون القائمة المنسدلة إلى مستند PDF:

```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;

namespace GroupDocs.Annotation.Examples
{
    class AddDropdownComponentExample
    {
        public static void Run()
        {
            Console.WriteLine("Adding dropdown component to a PDF document...");
            
            // تحديد مسارات الإدخال والإخراج
            string inputPath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
            string outputPath = "YOUR_OUTPUT_DIRECTORY/output-with-dropdown.pdf";
            
            // قم بتهيئة المُعلق باستخدام مستند الإدخال
            using (Annotator annotator = new Annotator(inputPath))
            {
                // إنشاء مكون القائمة المنسدلة
                DropdownComponent dropdown = new DropdownComponent
                {
                    // تحديد خيارات القائمة المنسدلة
                    Options = new List<string> { "Option 1", "Option 2", "Option 3", "Option 4" },
                    SelectedOption = null,
                    Placeholder = "Select an option...",
                    
                    // الموقع والحجم
                    Box = new Rectangle(100, 100, 150, 30),
                    
                    // البيانات الوصفية
                    CreatedOn = DateTime.Now,
                    Message = "Please select one option from the dropdown",
                    PageNumber = 0,
                    
                    // التصميم
                    PenColor = 65535,  // اللون الأزرق
                    PenStyle = PenStyle.Solid,
                    PenWidth = 2,
                    
                    // تعليقات اختيارية
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "This dropdown is for demonstration purposes",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                
                // أضف القائمة المنسدلة إلى المستند
                annotator.Add(dropdown);
                
                // حفظ المستند الموضح
                annotator.Save(outputPath);
                
                Console.WriteLine($"Dropdown component added successfully.\nCheck the output file at: {outputPath}");
            }
        }
    }
}
```

## تخصيص مكون القائمة المنسدلة

### تحديد المواقع والحجم

يمكنك تعديل موضع وحجم القائمة المنسدلة عن طريق تعديل `Box` ملكية:

```csharp
// الموضع عند الإحداثيات (200، 150) بعرض 200 وارتفاع 40
dropdown.Box = new Rectangle(200, 150, 200, 40);
```

### خيارات التصميم

قم بتخصيص مظهر القائمة المنسدلة الخاصة بك باستخدام الخصائص التالية:

```csharp
// تغيير لون القلم إلى اللون الأحمر (قيمة RGB)
dropdown.PenColor = 16711680; // الأحمر في RGB

// تغيير نمط القلم
dropdown.PenStyle = PenStyle.Solid; // الخيارات: صلب، شرطة، نقطة، DashDot، وما إلى ذلك.

// ضبط عرض القلم
dropdown.PenWidth = 2;
```

### خيارات القائمة المنسدلة الديناميكية

يمكنك ملء خيارات القائمة المنسدلة بشكل ديناميكي من مصدر البيانات:

```csharp
// مثال: خيارات التحميل من قاعدة بيانات أو واجهة برمجة التطبيقات
List<string> dynamicOptions = GetOptionsFromDataSource();
dropdown.Options = dynamicOptions;

// مثال على طريقة المساعدة (سيختلف التنفيذ)
private static List<string> GetOptionsFromDataSource()
{
    // في تطبيق حقيقي، قد يأتي هذا من قاعدة بيانات
    return new List<string> { "Value 1", "Value 2", "Value 3" };
}
```

## التطبيقات العملية

### أتمتة النماذج

استخدم مكونات القائمة المنسدلة لإنشاء نماذج PDF تفاعلية تجمع بيانات منظمة من المستخدمين، وهي مثالية للتطبيقات والاستطلاعات والاستبيانات.

### التحقق من صحة البيانات

تنفيذ القوائم المنسدلة لتقييد إدخال المستخدم إلى خيارات محددة مسبقًا، مما يضمن اتساق البيانات وتقليل الأخطاء في عمليات إرسال النماذج.

### الوثائق التفاعلية

قم بتعزيز الوثائق الفنية من خلال إضافة عناصر تفاعلية تسمح للمستخدمين باختيار التكوينات أو الخيارات مباشرة داخل المستند.

### إدارة سير العمل

إنشاء سير عمل الموافقة على المستندات حيث يمكن للمراجعين تحديد خيارات الحالة (على سبيل المثال، "موافق"، "يحتاج إلى مراجعة"، "مرفوض") مباشرة في ملف PDF.

### المواد التعليمية

قم بتطوير مواد تعليمية تفاعلية حيث يمكن للطلاب الإجابة على أسئلة الاختيار من متعدد المضمنة في المستند.

## اعتبارات الأداء

### إدارة الذاكرة

عند العمل مع مستندات PDF كبيرة أو إضافة مكونات قائمة منسدلة متعددة:

```csharp
// ضمان التخلص السليم من الموارد
using (Annotator annotator = new Annotator(inputPath))
{
    // إضافة قوائم منسدلة متعددة
    for (int i = 0; i < numberOfDropdowns; i++)
    {
        // إنشاء وإضافة قائمة منسدلة
        DropdownComponent dropdown = CreateDropdown(i);
        annotator.Add(dropdown);
    }
    
    annotator.Save(outputPath);
} // يتم التخلص من الموارد بشكل صحيح هنا
```

### معالجة المستندات الكبيرة

للحصول على أداء أفضل مع المستندات الكبيرة:

```csharp
// استخدم خيارات التحميل لتحسين استخدام الذاكرة
LoadOptions loadOptions = new LoadOptions
{
    // تعيين خيارات محددة للمستندات الكبيرة
};

using (Annotator annotator = new Annotator(inputPath, loadOptions))
{
    // أضف مكونات القائمة المنسدلة الخاصة بك
    // ...
}
```

## خاتمة

إضافة عناصر القوائم المنسدلة إلى مستندات PDF باستخدام GroupDocs.Annotation لـ .NET يُحسّن التفاعل والوظائف بشكل ملحوظ. يوضح لك هذا البرنامج التعليمي كيفية إنشاء حقول القوائم المنسدلة وتخصيصها وتنفيذها في ملفات PDF، مما يفتح آفاقًا جديدة لأتمتة النماذج وجمع البيانات وتجارب المستندات التفاعلية.

بالاستفادة من الميزات الفعّالة لـ GroupDocs.Annotation، يمكنك تحويل ملفات PDF الثابتة إلى مستندات ديناميكية وتفاعلية تجمع بيانات مُنظّمة من المستخدمين. مع استمرارك في استكشاف المكتبة، ستكتشف المزيد من الطرق لتحسين سير عمل مستنداتك وتجربة المستخدم.

سواء كنت تقوم بإنشاء نماذج أو استطلاعات رأي أو وثائق تفاعلية، يوفر مكون القائمة المنسدلة طريقة سهلة الاستخدام لجمع المدخلات المنظمة مباشرة داخل مستندات PDF.

## قسم الأسئلة الشائعة

### هل يمكنني تعيين خيار محدد افتراضيًا للقائمة المنسدلة؟

نعم، يمكنك تعيين خيار افتراضي عن طريق تعيين قيمة إلى `SelectedOption` ملكية:

```csharp
dropdown.Options = new List<string> { "Option 1", "Option 2", "Option 3" };
dropdown.SelectedOption = "Option 2"; // تعيين الاختيار الافتراضي
```

### كيف يمكنني استرداد القيمة المحددة من القائمة المنسدلة في النموذج المرسل؟

لاسترداد القيمة المحددة، يمكنك استخدام وظيفة محلل GroupDocs.Annotation:

```csharp
using (Annotator annotator = new Annotator("submitted-form.pdf"))
{
    // احصل على جميع التعليقات التوضيحية بما في ذلك القوائم المنسدلة
    List<AnnotationBase> annotations = annotator.Get();
    
    // البحث عن مكونات القائمة المنسدلة
    foreach (var annotation in annotations)
    {
        if (annotation is DropdownComponent dropdown)
        {
            Console.WriteLine($"Selected value: {dropdown.SelectedOption}");
        }
    }
}
```

### هل يمكنني إضافة مكونات القائمة المنسدلة إلى مستندات أخرى غير ملفات PDF؟

يدعم GroupDocs.Annotation بشكل أساسي إضافة عناصر حقول النماذج، مثل القوائم المنسدلة، إلى مستندات PDF. قد يختلف دعم التنسيقات الأخرى، لذا يُرجى مراجعة الوثائق للاطلاع على إمكانيات التنسيقات المحددة.

### كيف أجعل القائمة المنسدلة مطلوبة في النموذج؟

لا يحتوي مُكوِّن القائمة المنسدلة على خاصية "مطلوبة" مُدمجة. ستحتاج إلى تطبيق منطق التحقق في تطبيقك الذي يُعالج إرسال النموذج.

### هل يمكنني تغيير مظهر القائمة المنسدلة بعد إضافتها إلى مستند؟

نعم، يمكنك تحديث القائمة المنسدلة الموجودة عن طريق استرجاعها وتعديل خصائصها وتحديثها:

```csharp
using (Annotator annotator = new Annotator("document-with-dropdown.pdf"))
{
    // احصل على جميع التعليقات التوضيحية
    List<AnnotationBase> annotations = annotator.Get();
    
    // البحث عن القوائم المنسدلة وتحديثها
    foreach (var annotation in annotations)
    {
        if (annotation is DropdownComponent dropdown)
        {
            // تحديث الخصائص
            dropdown.PenColor = 255; // التغيير إلى اللون الأحمر
            dropdown.Options = new List<string> { "New Option 1", "New Option 2" };
            
            // تحديث الشرح التوضيحي
            annotator.Update(dropdown);
        }
    }
    
    // حفظ المستند المحدث
    annotator.Save("updated-document.pdf");
}
```

## موارد

- [توثيق GroupDocs.Annotation](https://docs.groupdocs.com/annotation/net/)
- [مرجع واجهة برمجة التطبيقات](https://reference.groupdocs.com/annotation/net/)
- [تنزيل GroupDocs.Annotation لـ .NET](https://releases.groupdocs.com/annotation/net/)
- [شراء ترخيص](https://purchase.groupdocs.com/buy)
- [نسخة تجريبية مجانية](https://releases.groupdocs.com/annotation/net/)
- [رخصة مؤقتة](https://purchase.groupdocs.com/temporary-license/)
- [منتدى دعم GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation)