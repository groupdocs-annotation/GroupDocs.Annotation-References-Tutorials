---
categories:
- Document Processing
date: '2026-06-01'
description: تعلم كيفية استخراج عدد صفحات PDF في C#، الحصول على نوع الملف، وقراءة
  خصائص الملف باستخدام GroupDocs.Annotation .NET. يتضمن كودًا عمليًا ونصائح.
keywords:
- c# pdf page count
- c# get file type
- read file properties c#
- c# read document size
lastmod: '2026-06-01'
linktitle: استخراج معلومات المستند C#
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  headline: c# pdf page count – Extract Document Info with GroupDocs
  type: TechArticle
- description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  name: c# pdf page count – Extract Document Info with GroupDocs
  steps:
  - name: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
    text: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
  - name: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
    text: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
  - name: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
    text: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
  - name: Clone the sample project and run the provided placeholders with real files.
    text: Clone the sample project and run the provided placeholders with real files.
  - name: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
    text: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
  - name: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
    text: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports over 50 document formats, including PDF,
      DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD files, and many more.
    question: What document formats does GroupDocs.Annotation support for information
      extraction?
  - answer: '`GetDocumentInfo()` provides core metadata like file type, page count,
      and size. For custom properties such as author or creation date, combine GroupDocs.Annotation
      with GroupDocs.Metadata or use the native file format’s property APIs.'
    question: Can I extract custom metadata or properties from documents?
  - answer: Provide the password when creating the `Annotator` instance, e.g., `new
      Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.
    question: How do I handle password‑protected documents?
  - answer: Yes—`GetDocumentInfo()` reads only the file header, so memory consumption
      stays low even for multi‑hundred‑page PDFs.
    question: Is there a way to extract document information without loading the entire
      file into memory?
  - answer: Absolutely. GroupDocs.Annotation is thread‑safe; just create a new `Annotator`
      per request and dispose of it promptly.
    question: Can I use this in a web application or multi‑threaded environment?
  type: FAQPage
tags:
- csharp
- document-extraction
- groupdocs
- dotnet
title: عدد صفحات PDF في C# – استخراج معلومات المستند باستخدام GroupDocs
type: docs
url: /ar/net/annotation-management/mastering-document-extraction-groupdocs-annotation-net/
weight: 1
---

# عدد صفحات PDF في C# – استخراج معلومات المستند باستخدام GroupDocs.Annotation

## المقدمة

هل وجدت نفسك يومًا تحدق في مجموعة من المستندات، متسائلًا ما الذي تحتويه فعليًا دون الحاجة إلى فتح كل واحدة؟ أنت لست وحدك في هذه المعاناة. سواء كنت تبني نظام إدارة مستندات، أو تعالج ملفات قانونية، أو تحاول فقط تنظيم الأصول الرقمية لشركتك، فإن معرفة كيفية **استخراج معلومات المستند في C#**—بما في ذلك **عدد صفحات PDF في C#**—يمكن أن تكون نقطة تحول حقيقية.

التحقق اليدوي من خصائص الملفات يستغرق وقتًا ويعرضك للأخطاء. باستخدام **GroupDocs.Annotation for .NET**، يمكنك أتمتة هذه العملية بالكامل واسترجاع نوع الملف، عدد الصفحات، حجم المستند، وأكثر في بضع أسطر من الشيفرة. يوضح لك هذا الدرس لماذا هذا مهم، وكيفية إعداد المكتبة، وشيفرة خطوة بخطوة تعمل مباشرةً.

## إجابات سريعة
- **ما الذي تستخرجه GroupDocs.Annotation؟** نوع الملف، عدد الصفحات، الحجم، والبيانات الوصفية الأساسية.  
- **كم عدد الصيغ المدعومة؟** أكثر من 50 صيغة إدخال وإخراج، بما في ذلك PDF، DOCX، XLSX، PPTX، وأنواع الصور الشائعة.  
- **هل يمكنني الحصول على عدد صفحات PDF في C# دون تحميل الملف بالكامل؟** نعم—`GetDocumentInfo()` يقرأ فقط معلومات الترويسة اللازمة لعدد الصفحات.  
- **هل أحتاج إلى ترخيص للتطوير؟** النسخة التجريبية المجانية تكفي للاختبار؛ الترخيص الكامل مطلوب للإنتاج.  
- **هل الـ API آمن للخطوط المتعددة في تطبيقات الويب؟** بالتأكيد—فقط تأكد من التخلص من كائنات `Annotator` بشكل صحيح.

## ما هو عدد صفحات PDF في C#؟
**عدد صفحات PDF في C#** هو إجمالي عدد الصفحات التي يُبلغ عنها ملف PDF عند الاستعلام عبر API. باستخدام GroupDocs.Annotation، تحصل على هذه القيمة فورًا عبر طريقة `GetDocumentInfo()` دون الحاجة إلى عرض المستند بالكامل. يُستمد هذا العدد من البنية الداخلية للملف PDF، مما يتيح لك اتخاذ قرارات حول المعالجة أو التخزين أو العرض دون فتح الملف في عارض. وهو مفيد بشكل خاص للتحقق على دفعات، وفحوصات الامتثال، ومعاينات الواجهة حيث تكون حدود الصفحات مهمة.

## لماذا استخراج معلومات المستند باستخدام GroupDocs.Annotation؟
يدعم GroupDocs.Annotation **أكثر من 50 صيغة مستند** ويمكنه معالجة ملفات مئات الصفحات دون تحميل الملف بالكامل إلى الذاكرة، حيث يقدم البيانات الوصفية في أقل من 200 ms على خادم نموذجي. هذه السرعة وتعدد الصيغ تجعلها مثالية للأتمتة على نطاق واسع، وفحوصات الامتثال، وتصنيف المحتوى الذكي.

## المتطلبات المسبقة والإعداد

### ما ستحتاجه
- Visual Studio 2019 أو أحدث (إصدار Community يعمل جيدًا)  
- .NET Framework 4.6.1+ **أو** .NET Core 2.0+  
- معرفة أساسية بـ C# وإلمام بـ NuGet  

### تثبيت GroupDocs.Annotation
إدخال المكتبة إلى مشروعك سهل. اختر الطريقة التي تفضلها:

**Option 1: Package Manager Console (Recommended)**
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Option 2: .NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Option 3: Package Manager UI**  
إذا كنت تفضّل النقر على الكتابة، ابحث عن "GroupDocs.Annotation" في واجهة NuGet Package Manager وقم بتثبيت أحدث نسخة.

### الحصول على الترخيص الخاص بك
1. **ابدأ بالنسخة التجريبية المجانية**: قم بالتحميل من [موقع GroupDocs](https://releases.groupdocs.com/annotation/net/) – بدون أي شروط.  
2. **هل تحتاج إلى مزيد من الوقت؟** احصل على [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) لتقييم ممتد.  
3. **مستعد للإنتاج؟** [اشترِ ترخيصًا كاملاً](https://purchase.groupdocs.com/buy) عندما تكون جاهزًا للنشر.  

> **نصيحة محترف:** النسخة التجريبية تشمل علامات مائية، لكنها مثالية للتعلم واختبار الشيفرة الخاصة بك.

لأحدث التغييرات، راجع [ملاحظات الإصدار](https://releases.groupdocs.com/annotation/net/).

## كيفية الحصول على عدد صفحات PDF في C# باستخدام GroupDocs.Annotation؟

**Annotator** هو الفئة الرئيسية التي تُحمّل المستند وتوفر وظائف التعليق والبيانات الوصفية.  
حمّل ملف PDF الخاص بك باستخدام `new Annotator("file.pdf")` واستدعِ `GetDocumentInfo()` – خاصية `PageCount` تُعيد عدد الصفحات بدقة في سطرين فقط من الشيفرة. **GetDocumentInfo()** تُعيد كائن **DocumentInfo** يحتوي على بيانات وصفية مثل عدد الصفحات، نوع الملف، والحجم. هذه الطريقة تقرأ فقط بيانات الترويسة الضرورية، لذا حتى ملفات PDF الكبيرة تُعالج بكفاءة.

### الإعداد الأساسي وتحميل المستند
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main(string[] args)
    {
        // Initialize the annotator with a document path
        using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
        {
            Console.WriteLine("Document loaded successfully!");
            // We'll add the extraction code here next
        }
    }
}
```  

### استخراج بيانات المستند الوصفية
**DocumentInfo** يضم الخصائص المستخرجة للملف، مما يجعل قراءتها واستخدامها في تطبيقك سهلًا.  
```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    // Extract document info
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    // Always check if info was retrieved successfully
    if (info == null || info.PageCount == 0)
    {
        throw new Exception("Unexpected document information!");
    }

    // Display the extracted information
    Console.WriteLine($"\
File type: {info.FileType}\
Number of pages: {info.PageCount}\
Document size: {info.Size} bytes.");
    
    // Convert size to more readable format
    string readableSize = FormatFileSize(info.Size);
    Console.WriteLine($"Document size (formatted): {readableSize}");
}

// Helper method to format file size
static string FormatFileSize(long bytes)
{
    string[] suffixes = { "B", "KB", "MB", "GB", "TB" };
    int counter = 0;
    decimal number = bytes;
    
    while (Math.Round(number / 1024) >= 1)
    {
        number /= 1024;
        counter++;
    }
    
    return string.Format("{0:n1}{1}", number, suffixes[counter]);
}
```  

### عرض معلومات محسّن
إذا كنت تحتاج إلى مزيد من السياق—مثل ما إذا كان المستند يتجاوز حدًا معينًا للحجم—يمكنك توسيع المثال الأساسي بإضافة فحوصات منطقية إضافية.  

```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    if (info == null)
    {
        Console.WriteLine("Could not retrieve document information.");
        return;
    }

    // Comprehensive info display
    Console.WriteLine("=== Document Information ===");
    Console.WriteLine($"File Type: {info.FileType}");
    Console.WriteLine($"Page Count: {info.PageCount}");
    Console.WriteLine($"Size: {FormatFileSize(info.Size)}");
    
    // Additional checks you might want to perform
    if (info.PageCount > 100)
    {
        Console.WriteLine("⚠️  Large document detected - consider batch processing");
    }
    
    if (info.Size > 10 * 1024 * 1024) // 10MB
    {
        Console.WriteLine("⚠️  Large file size - may impact processing time");
    }
    
    Console.WriteLine("=== Analysis Complete ===");
}
```  

## المشكلات الشائعة والحلول

### المشكلة 1: أخطاء "الملف غير موجود"
**الإجابة المباشرة:** تأكد من أن مسار الملف مطلق أو مُحدد بشكل صحيح بالنسبة إلى دليل قاعدة التطبيق، وتأكد من أن العملية لديها صلاحيات القراءة.  

```csharp
string documentPath = @"C:\Documents\test.pdf";

// Always check if file exists first
if (!File.Exists(documentPath))
{
    Console.WriteLine($"File not found: {documentPath}");
    return;
}

try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        // Your code here
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```  

### المشكلة 2: صيغة ملف غير مدعومة
**الإجابة المباشرة:** تأكد من أن امتداد الملف يطابق إحدى الصيغ الـ 50+ المدعومة؛ إذا لم يكن كذلك، حوّله إلى نوع مدعوم قبل استدعاء `GetDocumentInfo()`.  

```csharp
try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        if (info == null)
        {
            Console.WriteLine("Unsupported file format or corrupted document");
            return;
        }
        
        // Process the info
    }
}
catch (UnsupportedFileTypeException ex)
{
    Console.WriteLine($"File type not supported: {ex.Message}");
}
```  

### المشكلة 3: مشاكل الذاكرة مع المستندات الكبيرة
**الإجابة المباشرة:** نفّذ فحوصات الحجم قبل التحميل واستخدم عبارات `using` لضمان التخلص من كائن `Annotator`، مما يمنع تسرب الذاكرة.  

```csharp
const long MAX_FILE_SIZE = 50 * 1024 * 1024; // 50MB limit

FileInfo fileInfo = new FileInfo(documentPath);
if (fileInfo.Length > MAX_FILE_SIZE)
{
    Console.WriteLine("File too large for processing");
    return;
}

// Use proper disposal patterns
using (Annotator annotator = new Annotator(documentPath))
{
    // Process quickly and dispose
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    // Handle info immediately
}
// Annotator is automatically disposed here
```  

## حالات الاستخدام الواقعية

### دمج نظام إدارة المستندات
عند رفع المستخدم لملف، استخرج بياناته الوصفية أولًا لتحديد موقع التخزين، استراتيجية الفهرسة، أو سير عمل الموافقة المطلوب.  

```csharp
public class DocumentProcessor
{
    public DocumentMetadata ProcessUpload(string filePath)
    {
        using (Annotator annotator = new Annotator(filePath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            return new DocumentMetadata
            {
                FileName = Path.GetFileName(filePath),
                FileType = info.FileType.ToString(),
                PageCount = info.PageCount,
                FileSizeBytes = info.Size,
                ProcessedDate = DateTime.UtcNow,
                Category = DetermineCategory(info)
            };
        }
    }
    
    private string DetermineCategory(IDocumentInfo info)
    {
        // Business logic for automatic categorization
        if (info.FileType.ToString().Contains("Pdf"))
        {
            return info.PageCount > 20 ? "Legal Document" : "Standard Document";
        }
        
        return "Other";
    }
}
```  

### تحليل المستندات على دفعات
عالج مجلد من الملفات في مهمة خلفية، وسجّل عدد الصفحات ونوع كل مستند لأغراض التقارير.  

```csharp
public void AnalyzeDocumentFolder(string folderPath)
{
    string[] supportedExtensions = { ".pdf", ".docx", ".xlsx", ".pptx" };
    
    foreach (string file in Directory.GetFiles(folderPath))
    {
        if (!supportedExtensions.Contains(Path.GetExtension(file).ToLower()))
            continue;
            
        try
        {
            using (Annotator annotator = new Annotator(file))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                Console.WriteLine($"{Path.GetFileName(file)}: {info.FileType}, {info.PageCount} pages");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to process {file}: {ex.Message}");
        }
    }
}
```  

### الامتثال والتحقق
تتطلب الصناعات المنظمة غالبًا أن تكون المستندات تحت عدد صفحات أو حجم معين. استخدم البيانات الوصفية المستخرجة لرفض التحميلات غير المتوافقة تلقائيًا.  

```csharp
public bool ValidateDocument(string filePath, DocumentRequirements requirements)
{
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        // Check file type
        if (requirements.AllowedTypes != null && 
            !requirements.AllowedTypes.Contains(info.FileType.ToString()))
        {
            return false;
        }
        
        // Check page count limits
        if (info.PageCount < requirements.MinPages || 
            info.PageCount > requirements.MaxPages)
        {
            return false;
        }
        
        // Check file size
        if (info.Size > requirements.MaxSizeBytes)
        {
            return false;
        }
        
        return true;
    }
}
```  

## نصائح تحسين الأداء

### 1. تنفيذ التخزين المؤقت
خزن نتائج `DocumentInfo` للملفات التي تُستدعى بشكل متكرر لتجنب عمليات I/O المتكررة.  

```csharp
private static readonly Dictionary<string, IDocumentInfo> _infoCache = 
    new Dictionary<string, IDocumentInfo>();

public IDocumentInfo GetDocumentInfoCached(string filePath)
{
    string fileHash = GetFileHash(filePath);
    
    if (_infoCache.ContainsKey(fileHash))
    {
        return _infoCache[fileHash];
    }
    
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        _infoCache[fileHash] = info;
        return info;
    }
}
```  

### 2. استخدم المعالجة غير المتزامنة للعديد من المستندات
استفد من `Task.Run` أو تدفقات async لمعالجة العديد من الملفات بشكل متوازي دون حجب الخيط الرئيسي.  

```csharp
public async Task<List<DocumentMetadata>> ProcessDocumentsAsync(string[] filePaths)
{
    var tasks = filePaths.Select(async path =>
    {
        return await Task.Run(() =>
        {
            using (Annotator annotator = new Annotator(path))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                return new DocumentMetadata(path, info);
            }
        });
    });
    
    return (await Task.WhenAll(tasks)).ToList();
}
```  

### 3. أفضل ممارسات إدارة الذاكرة
- احرص دائمًا على وضع `Annotator` داخل كتلة `using`.  
- عالج المستندات على دفعات، لا جميعها مرة واحدة.  
- بالنسبة للملفات التي يزيد حجمها عن 100 ميغابايت، فكر في تدفق الملف إلى القرص أولاً ثم قراءة البيانات الوصفية.  

## دليل استكشاف الأخطاء وإصلاحها

### مشكلات الترخيص
**License** هو الكائن الذي يسجل ملف تفعيل المنتج مع مكتبة GroupDocs. تأكد من وضع ملف الترخيص في مجلد جذر التطبيق وأن كائن `License` يتم إنشاؤه قبل أي استدعاءات أخرى لـ GroupDocs.  

```csharp
// Set license before using any GroupDocs functionality
License license = new License();
license.SetLicense("path/to/your/license.lic");

// Or use stream for embedded licenses
using (Stream stream = Assembly.GetExecutingAssembly().GetManifestResourceStream("YourApp.license.lic"))
{
    license.SetLicense(stream);
}
```  

### مشكلات الأداء
**الإجابة المباشرة:** قم بملف التطبيق، حدّ من حجم الملفات إلى 100 ميغابايت للمعالجة الفورية، وفعل التخزين المؤقت للقراءات المتكررة.  

### مشكلات خاصة بالمنصة
**الإجابة المباشرة:** استخدم `Path.Combine` لإنشاء مسارات متوافقة عبر الأنظمة؛ فالويندوز يستخدم الشرط المائل العكسي بينما لينكس يستخدم الشرط المائل العادي.  

```csharp
// Use Path.Combine for cross-platform compatibility
string documentPath = Path.Combine(baseDirectory, "documents", fileName);
```  

### التعامل مع المستندات المحمية بكلمة مرور
**الإجابة المباشرة:** مرّر كلمة المرور إلى مُنشئ `Annotator` أو عيّنها عبر `LoadOptions` قبل استدعاء `GetDocumentInfo()`.  

```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-document.pdf", loadOptions))
{
    // Extract information normally
}
```  

### تحديث GroupDocs.Annotation
**الإجابة المباشرة:** نفّذ `dotnet add package GroupDocs.Annotation --version <latest>` أو استخدم واجهة NuGet Package Manager لسحب أحدث نسخة.  

```shell
Update-Package GroupDocs.Annotation
```  

## الأسئلة المتكررة

**س: ما صيغ المستندات التي تدعمها GroupDocs.Annotation لاستخراج المعلومات؟**  
ج: تدعم GroupDocs.Annotation أكثر من 50 صيغة مستند، بما في ذلك PDF، DOCX، XLSX، PPTX، JPEG، PNG، TIFF، ملفات CAD، والعديد غيرها.

**س: هل يمكنني استخراج بيانات وصفية مخصصة أو خصائص من المستندات؟**  
ج: `GetDocumentInfo()` يوفر البيانات الوصفية الأساسية مثل نوع الملف، عدد الصفحات، والحجم. للحصول على خصائص مخصصة مثل المؤلف أو تاريخ الإنشاء، يمكنك دمج GroupDocs.Annotation مع GroupDocs.Metadata أو استخدام واجهات برمجة التطبيقات الخاصة بصيغة الملف الأصلية.

**س: كيف أتعامل مع المستندات المحمية بكلمة مرور؟**  
ج: قدّم كلمة المرور عند إنشاء كائن `Annotator`، مثال: `new Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.

**س: هل هناك طريقة لاستخراج معلومات المستند دون تحميل الملف بالكامل في الذاكرة؟**  
ج: نعم—`GetDocumentInfo()` يقرأ فقط ترويسة الملف، لذا يظل استهلاك الذاكرة منخفضًا حتى مع ملفات PDF مئات الصفحات.

**س: هل يمكنني استخدام هذا في تطبيق ويب أو بيئة متعددة الخيوط؟**  
ج: بالتأكيد. GroupDocs.Annotation آمن للخطوط المتعددة؛ فقط أنشئ كائن `Annotator` جديد لكل طلب وتأكد من التخلص منه فورًا.

## الخلاصة والخطوات التالية

أصبحت الآن تمتلك نهجًا كاملًا وجاهزًا للإنتاج لاستخراج **عدد صفحات PDF في C#**، نوع الملف، والحجم باستخدام GroupDocs.Annotation. تعلمت كيفية إعداد المكتبة، استرجاع البيانات الوصفية، التعامل مع المشكلات الشائعة، وتحسين الأداء لسيناريوهات على نطاق واسع.

**الخطوات التالية:**  
1. استنساخ مشروع العينة وتشغيل القوالب المقدمة مع ملفات حقيقية.  
2. استكشف ميزات GroupDocs.Annotation الإضافية مثل عرض التعليقات ومقارنة المستندات.  
3. دمج استخراج البيانات الوصفية في خط أنابيب التحميل الحالي لأتمتة التصنيف والتحقق.

تذكر، معالجة المستندات القوية تبدأ ببيانات وصفية موثوقة. مع GroupDocs.Annotation، يمكنك بناء حلول أذكى، أسرع، وأكثر قابلية للتوسع.

---

**Last Updated:** 2026-06-01  
**Tested With:** GroupDocs.Annotation 25.4.0 (latest)  
**Author:** GroupDocs  

**Essential Links:**  
- **[الوثائق](https://docs.groupdocs.com/annotation/net/)**  
- **[مرجع API](https://reference.groupdocs.com/annotation/net/)**  
- **[تحميل أحدث نسخة](https://releases.groupdocs.com/annotation/net/)**  
- **[شراء تراخيص](https://purchase.groupdocs.com/buy)**  
- **[تحميل النسخة التجريبية المجانية](https://releases.groupdocs.com/annotation/net/)**  
- **[طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)**  
- **[منتدى الدعم المجتمعي](https://forum.groupdocs.com/c/annotation/)**

## دروس ذات صلة

- [استخراج بيانات المستند الوصفية .NET - دليل كامل لـ GroupDocs.Annotation](/annotation/net/document-information/)
- [أبعاد صفحة PDF .NET - استخراج العرض والارتفاع باستخدام C#](/annotation/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/)
- [دروس GroupDocs.Annotation .NET: استخراج وحفظ صفحات PDF محددة](/annotation/net/annotation-management/groupdocs-annotation-dotnet-page-range-management/)