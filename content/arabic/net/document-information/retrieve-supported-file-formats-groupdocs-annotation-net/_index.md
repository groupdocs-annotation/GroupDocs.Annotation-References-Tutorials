---
categories:
- .NET Development
date: '2026-06-26'
description: تعلم كيفية استرجاع الصيغ باستخدام GroupDocs.Annotation لـ .NET، وحل مشكلات
  عدم دعم صيغ الملفات، وتطبيق أفضل ممارسات التحقق.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: استرجاع صيغ الملفات المدعومة .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: كيفية استرجاع الصيغ في .NET باستخدام GroupDocs.Annotation – دليل كامل
type: docs
url: /ar/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# كيفية استرجاع الصيغ في .NET باستخدام GroupDocs.Annotation

## مقدمة

هل تساءلت يومًا عن صيغ الملفات التي يمكن لتطبيق .NET الخاص بك التعامل معها فعليًا لت anotating المستندات؟ **How to retrieve formats** هو سؤال يطرحه العديد من المطورين عندما يحتاجون إلى التحقق من تحميلات المستخدم أو بناء فلاتر واجهة مستخدم ديناميكية. معرفة الصيغ التي يدعمها تنفيذ GroupDocs.Annotation الخاص بك ليست مجرد مساعدة — إنها أساسية لبناء تطبيقات قوية لا تتعطل بسبب نوع ملف غير متوقع.

في هذا الدليل ستتعلم كيفية استرجاع الصيغ المدعومة والتحقق منها برمجيًا باستخدام GroupDocs.Annotation لـ .NET. سنستعرض التنفيذ الأساسي، ونوضح لك كيفية تحويل القائمة الخام إلى قائمة منسدلة نظيفة للمستخدم النهائي، ونغطي نصائح حل المشكلات الواقعية حتى تتمكن من التعامل مع أي سيناريو صيغة مستند بثقة.

**ما ستحصل عليه**

- فهم واضح تمامًا لقدرات صيغ الملفات في GroupDocs.Annotation  
- كود جاهز للتنفيذ يسترجع ويعرض كل صيغة مدعومة  
- استراتيجيات مثبتة للتخزين المؤقت، معالجة الأخطاء، وحالات الترخيص الخاصة  
- توصيات أفضل الممارسات للتحقق من نوع الملف في بيئات الإنتاج  

دعنا نغوص ونحل لغز صيغ الملفات مرة واحدة وإلى الأبد.

## إجابات سريعة
- **ما معنى “how to retrieve formats”؟** إنه الطريقة البرمجية لسؤال GroupDocs.Annotation عن الامتدادات التي يمكنه التعليق عليها.  
- **ما هي الصيغ الأساسية المدعومة مباشرةً؟** أكثر من 50 صيغة، بما في ذلك PDF، DOCX، XLSX، PPTX، JPEG، PNG، وTIFF.  
- **هل أحتاج إلى ترخيص للحصول على القائمة الكاملة؟** نعم — ترخيص تجاري نشط أو تجريبي يفتح الفهرس الكامل.  
- **هل يُنصح بتخزين قائمة الصيغ مؤقتًا؟** بالتأكيد؛ التخزين المؤقت يجنب الاستدعاءات غير الضرورية ويحسن زمن الاستجابة.  
- **كيف يمكنني التحقق من تحميل ملف مقابل القائمة؟** قارن امتداد الملف مع مجموعة الامتدادات المدعومة المخزنة مؤقتًا.

## ما هو “how to retrieve formats”؟
**How to retrieve formats** يشير إلى عملية استدعاء API الخاص بـ GroupDocs.Annotation للحصول على مجموعة جميع أنواع الملفات التي يمكن للمكتبة التعليق عليها. تُعيد هذه العملية قائمة قراءة‑فقط من كائنات `FileType` التي تشمل كل من امتداد الملف ووصفًا صديقًا.

## لماذا تستخدم GroupDocs.Annotation لاكتشاف الصيغ؟
GroupDocs.Annotation يدعم **أكثر من 50 صيغة إدخال وإخراج** — بما في ذلك PDF، Microsoft Office (Word، Excel، PowerPoint)، وأنواع الصور الشائعة — مع معالجة مستندات مئات الصفحات دون تحميل الملف بالكامل في الذاكرة. تجعل هذه القدرة الكمية منه خيارًا موثوقًا لخطوط أنوتيشن على مستوى المؤسسة.

## المتطلبات وإعداد البيئة

### ما ستحتاجه
- **IDE:** Visual Studio 2019 أو أحدث (إصدار Community يعمل جيدًا)  
- **Target framework:** .NET Framework 4.6.1 + أو .NET Core 2.0 +   
- **C# basics:** إذا كنت تستطيع كتابة تطبيق “Hello World”، فأنت جاهز  

### تثبيت GroupDocs.Annotation
أسهل طريقة هي عبر NuGet. اختر الطريقة التي تتناسب مع سير عملك:

**Option 1: Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Option 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Pro tip:** في بيئات الشركات المقيدة، قم بتحميل الحزمة يدويًا من [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) وأشر إلى ملف DLL محليًا.

### الترخيص ببساطة
- **Development & testing:** ابدأ بالتجربة المجانية للحصول على جميع الوظائف.  
- **Extended evaluation:** احصل على [temporary license](https://purchase.groupdocs.com/temporary-license/) (يتم إصدارها خلال ~5 دقائق).  
- **Production:** اشترِ ترخيصًا تجاريًا من [GroupDocs Purchase](https://purchase.groupdocs.com/buy)؛ ترخيص واحد يغطي جميع سيناريوهات النشر.

## كيفية استرجاع صيغ الملفات المدعومة برمجياً؟

حمِّل الصيغ المدعومة باستدعاء واحد لـ `FileType.GetSupportedFileTypes()` ثم حوِّل النتيجة إلى قائمة صديقة للمستخدم يمكن عرضها في عناصر واجهة المستخدم أو استخدامها للتحقق. تُعيد الطريقة مجموعة قراءة‑فقط من كائنات `FileType`، كل منها يحتوي على امتداد ووصف، مما يجعل التعامل معها سهلًا.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

الكود أعلاه يستعلم عن البيانات الوصفية الداخلية لـ GroupDocs.Annotation، يرتب الامتدادات أبجديًا، ويعيد مجموعة خفيفة الوزن يمكنك ربطها بعناصر واجهة المستخدم أو استخدامها للتحقق.

### تعريف مرساة: فئة FileType
فئة `FileType` هي تمثيل GroupDocs.Annotation لصيغة مستند واحدة، وتكشف عن خصائص مثل `Extension` و `Description`.  

### دليل خطوة بخطوة
1. **Add the namespace** – `using GroupDocs.Annotation;` في أعلى ملفك.  
2. **Call the static method** – `FileType.GetSupportedFileTypes()` تُعيد `IEnumerable<FileType>`.  
3. **Sort and project** – استخدم `OrderBy` و `Select` من LINQ لتشكيل البيانات للعرض.  
4. **Render** – كرّر عبر القائمة في وحدة تحكم، عرض MVC، أو قائمة منسدلة في WinForms.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## كيفية تخزين قائمة الصيغ في الذاكرة للاستخدام في الإنتاج؟

التخزين المؤقت يلغي عمليات البحث المتكررة في البيانات الوصفية ويضمن أوقات استجابة تحت الملي ثانية لكل طلب، وهو أمر حاسم في التطبيقات ذات الحركة العالية. عن طريق تخزين قائمة الصيغ في حقل ثابت وتحميلها بشكل كسول عند الاستخدام الأول، تضمن أن البيانات تُسترجع مرة واحدة فقط ثم تُعاد استخدامها بفعالية عبر دورة حياة التطبيق بأكملها.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Why cache?** مجموعة الصيغ المدعومة لا تتغير أثناء وقت التشغيل، لذا تحميلها مرة واحدة عند بدء التطبيق يوفر دورات CPU ويتجنب فحوصات الترخيص المحتملة في كل استدعاء.

## المشكلات الشائعة والحلول

### المشكلة 1: خطأ تجميع “GroupDocs.Annotation not found”
**Direct answer:** تحقق من تثبيت حزمة NuGet بشكل صحيح، نظّف وأعد بناء الحل، وتأكد من أن إطار العمل المستهدف يتطابق مع الإصدارات المدعومة للحزمة.  

**Root cause analysis** – مرجع مفقود، إطار عمل غير متوافق، أو قيود مصدر الحزمة في الشركة.

### المشكلة 2: قائمة الصيغ فارغة أو غير مكتملة
**Direct answer:** عادةً ما يؤدي ترخيص منتهي أو غير مُكوَّن بشكل صحيح إلى تقصير القائمة؛ أعد تطبيق ملف ترخيص صالح وأعد تشغيل التطبيق.  

**Possible causes:**  
- ملف الترخيص غير محمَّل (`License.SetLicense("license.json")` مفقود)  
- حزمة NuGet تالفة  
- تبعيات أصلية مفقودة  

**Quick fix:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### المشكلة 3: تدهور الأداء بسبب الاستدعاءات المتكررة
**Direct answer:** خزن النتيجة كما هو موضح في قسم “How to cache”؛ تصبح الاستدعاءات اللاحقة O(1).  

**Implementation tip:** احفظ القائمة في `MemoryCache` أو حقل ثابت، وقم بتحديثها فقط عند ترقية المكتبة.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## تطبيقات واقعية وحالات استخدام

### كيفية التحقق من تحميلات الملفات باستخدام القائمة المخزنة في الذاكرة؟
عند تقديم المستخدم لمستند، استخرج امتداد الملف وقارنه بالمجموعة المخزنة مؤقتًا:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### كيفية إنشاء مرشح ملفات ديناميكي لـ OpenFileDialog؟
املأ سلسلة الفلتر في الحوار من الامتدادات المخزنة، مما يضمن أن الواجهة دائمًا تعكس قدرات المكتبة:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### كيفية تخطي الملفات غير المدعومة في مسح مجلد دفعي؟
تجول عبر دليل، تحقق من كل ملف باستخدام `IsSupported`، وعالج فقط الصالحين:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## اعتبارات الأداء وأفضل الممارسات

- **Cache once, reuse everywhere** – ابدأ `FormatCache` عند تشغيل التطبيق (مثلاً في `Program.cs` أو `Startup.cs`).  
- **Lazy loading** – الخاصية الثابتة تضمن تحميل القائمة فقط عند الحاجة الأولى، متجنبةً الحمل الزائد عند بدء التشغيل.  
- **Thread safety** – عامل الإسناد المتعدد (`??=`) آمن لمعظم السيناريوهات أحادية الخيط؛ لتطبيقات التزامن العالي، غلف التخزين المؤقت في `Lazy<IReadOnlyList<FileType>>`.  
- **Dispose annotation objects** – بينما لا تحتاج قائمة الصيغ إلى تحرير، يجب تغليف أي كائنات `Annotation` في عبارات `using` لتحرير الموارد الأصلية.  

### نمط معالجة الأخطاء لمشكلات الترخيص
غلف استرجاع الصيغ في كتلة try‑catch تبحث تحديدًا عن `LicenseException` وتسجيل رسالة واضحة:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## دليل استكشاف الأخطاء وإصلاحها

### الخطوة 1: التحقق من التثبيت
شغّل `dotnet list package` أو تحقق من مخرجات وحدة تحكم NuGet لأي تحذيرات.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### الخطوة 2: التحقق من حالة الترخيص
تأكد من أن `License.SetLicense("path/to/license.json")` يُنفَّذ قبل أي استدعاء API.  

### الخطوة 3: تشخيص قيود البيئة
- تأكد من أن إصدار .NET runtime يتطابق مع متطلبات المكتبة.  
- تحقق من أن العملية لديها أذونات قراءة/كتابة للمجلد المؤقت الذي يستخدمه GroupDocs.Annotation.  

## الأسئلة المتكررة

**س: ما هي صيغ الملفات التي يدعمها GroupDocs.Annotation فعليًا؟**  
ج: المكتبة تدعم **أكثر من 50 صيغة**، بما في ذلك PDF، DOCX، XLSX، PPTX، JPEG، PNG، TIFF، والعديد غيرها. شغّل الكود النموذجي للحصول على القائمة الدقيقة وفقًا لترخيصك.

**س: لماذا أحصل على صيغ مدعومة أقل مما توقعت؟**  
ج: عادةً ما يشير ذلك إلى مشكلة ترخيص — إما تجربة منتهية أو ملف ترخيص غير محمَّل بشكل صحيح. أعد تطبيق ترخيص صالح وأعد تشغيل التطبيق.

**س: هل يمكنني فحص صيغة واحدة دون سحب القائمة بالكامل؟**  
ج: لا توجد طريقة “IsSupported” مباشرة؛ النهج الموصى به هو تخزين القائمة الكاملة مؤقتًا ثم الاستعلام محليًا للحصول على عمليات بحث سريعة.

**س: كيف يجب أن أتعامل مع فحص الصيغ في تطبيق ويب عالي الحركة؟**  
ج: ابدأ تخزين قائمة الصيغ في الذاكرة عند تشغيل التطبيق (مثلاً في `ConfigureServices`) واحفظها في خدمة ثابتة أو مفردة. هذا يلغي الحمل الزائد لكل طلب.

**س: ماذا لو ألقى GetSupportedFileTypes() استثناءً؟**  
ج: عادةً ما تنبع الاستثناءات من مشكلات الترخيص أو تثبيتات تالفة. تحقق من سلامة الحزمة، أعد تثبيتها إذا لزم الأمر، وتأكد من إمكانية الوصول إلى ملف الترخيص.

## الخلاصة

الآن لديك استراتيجية كاملة وجاهزة للإنتاج **كيفية استرجاع الصيغ** باستخدام GroupDocs.Annotation في .NET. من استدعاء API سطر واحد إلى التخزين المؤقت القوي، معالجة الأخطاء، وتكامل الواجهة، يمكنك التحقق من التحميلات بثقة، إنشاء فلاتر ملفات ديناميكية، وبناء خطوط أنوتيشن قابلة للتوسع.

**Next steps:**  
- استكشف [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/) للحصول على ميزات أنوتيشن أعمق.  
- انضم إلى المجتمع في [Support Forum](https://forum.groupdocs.com/c/annotation/) إذا واجهت سيناريوهات خاصة.  
- جرّب دمج التحقق من الصيغ مع قواعد عمل مخصصة (مثل حدود الحجم، فحص الأمان) لتعزيز سير عمل المستندات الخاص بك.

## الموارد
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/net/)
- [Free Trial](https://releases.groupdocs.com/annotation/net/)
- [temporary license](https://purchase.groupdocs.com/temporary-license/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy)
- [Purchase Licensing](https://purchase.groupdocs.com/buy)
- [Documentation](https://docs.groupdocs.com/annotation/net/)
- [API Reference](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
- [Community Support](https://forum.groupdocs.com/c/annotation/)

---

**Last Updated:** 2026-06-26  
**Tested With:** GroupDocs.Annotation 25.4.0 for .NET  
**Author:** GroupDocs  

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## دروس ذات صلة

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)