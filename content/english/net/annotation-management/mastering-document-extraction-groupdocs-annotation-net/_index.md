---
title: "c# pdf page count – Extract Document Info with GroupDocs"
linktitle: "Extract Document Info C#"
description: "Learn how to extract c# pdf page count, get file type, and read file properties c# using GroupDocs.Annotation .NET. Includes practical code and tips."
keywords:
- c# pdf page count
- c# get file type
- read file properties c#
- c# read document size
date: "2026-06-01"
lastmod: "2026-06-01"
weight: 1
url: "/net/annotation-management/mastering-document-extraction-groupdocs-annotation-net/"
categories: ["Document Processing"]
tags: ["csharp", "document-extraction", "groupdocs", "dotnet"]
type: docs
schemas:
- type: TechArticle
  headline: c# pdf page count – Extract Document Info with GroupDocs
  description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  dateModified: '2026-06-01'
  author: GroupDocs
- type: HowTo
  name: c# pdf page count – Extract Document Info with GroupDocs
  description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
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
- type: FAQPage
  questions:
  - question: What document formats does GroupDocs.Annotation support for information
      extraction?
    answer: GroupDocs.Annotation supports over 50 document formats, including PDF,
      DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD files, and many more.
  - question: Can I extract custom metadata or properties from documents?
    answer: '`GetDocumentInfo()` provides core metadata like file type, page count,
      and size. For custom properties such as author or creation date, combine GroupDocs.Annotation
      with GroupDocs.Metadata or use the native file format’s property APIs.'
  - question: How do I handle password‑protected documents?
    answer: Provide the password when creating the `Annotator` instance, e.g., `new
      Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.
  - question: Is there a way to extract document information without loading the entire
      file into memory?
    answer: Yes—`GetDocumentInfo()` reads only the file header, so memory consumption
      stays low even for multi‑hundred‑page PDFs.
  - question: Can I use this in a web application or multi‑threaded environment?
    answer: Absolutely. GroupDocs.Annotation is thread‑safe; just create a new `Annotator`
      per request and dispose of it promptly.
---

# c# pdf page count – Extract Document Info with GroupDocs.Annotation

## Introduction

Ever found yourself staring at a pile of documents, wondering what's actually inside them without having to open each one? You're definitely not alone in this struggle. Whether you're building a document management system, processing legal files, or just trying to organize your company's digital assets, knowing how to **extract document information in C#**—including the **c# pdf page count**—can be a real game‑changer.

Manually checking file properties is time‑consuming and error‑prone. With **GroupDocs.Annotation for .NET**, you can automate this entire process and retrieve file type, page count, document size, and more in just a few lines of code. This tutorial shows you why this matters, how to set up the library, and step‑by‑step code that works out of the box.

## Quick Answers
- **What does GroupDocs.Annotation extract?** File type, page count, size, and basic metadata.  
- **How many formats are supported?** Over 50 input and output formats, including PDF, DOCX, XLSX, PPTX, and common image types.  
- **Can I get the c# pdf page count without loading the whole file?** Yes—`GetDocumentInfo()` reads only the header information needed for page count.  
- **Do I need a license for development?** A free trial works for testing; a full license is required for production.  
- **Is the API thread‑safe for web apps?** Absolutely—just dispose of `Annotator` instances properly.

## What is c# pdf page count?
The **c# pdf page count** is the total number of pages reported by a PDF file when queried through an API. Using GroupDocs.Annotation, you obtain this value instantly via the `GetDocumentInfo()` method without rendering the entire document. This count is derived from the PDF’s internal structure, allowing you to make decisions about processing, storage, or display without opening the file in a viewer. It is especially useful for batch validation, compliance checks, and UI previews where page limits matter.

## Why extract document information with GroupDocs.Annotation?
GroupDocs.Annotation supports **50+ document formats** and can process multi‑hundred‑page files without loading the whole file into memory, delivering metadata in under 200 ms on a typical server. This speed and format breadth make it ideal for large‑scale automation, compliance checks, and intelligent content classification.

## Prerequisites and Setup

### What You'll Need
- Visual Studio 2019 or later (Community edition works fine)  
- .NET Framework 4.6.1+ **or** .NET Core 2.0+  
- Basic C# knowledge and familiarity with NuGet  

### Installing GroupDocs.Annotation
Getting the library into your project is straightforward. Choose the method you prefer:

**Option 1: Package Manager Console (Recommended)**
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Option 2: .NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Option 3: Package Manager UI**  
If you prefer clicking over typing, just search for "GroupDocs.Annotation" in the NuGet Package Manager UI and install the latest version.

### Getting Your License
1. **Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/) – no strings attached.  
2. **Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/) for extended evaluation.  
3. **Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy) when you're ready to deploy.  

> **Pro tip:** The free trial includes watermarks, but it's perfect for learning and testing your code.

For the latest changes, see the [release notes](https://releases.groupdocs.com/annotation/net/).

## How to Get c# pdf page count with GroupDocs.Annotation?

**Annotator** is the main class that loads a document and provides annotation and metadata functions.  
Load your PDF with `new Annotator("file.pdf")` and call `GetDocumentInfo()` – the `PageCount` property returns the exact number of pages in just two lines of code. **GetDocumentInfo()** returns a **DocumentInfo** object containing metadata such as page count, file type, and size. This method reads only the necessary header data, so even large PDFs are handled efficiently.

### Basic Setup and Document Loading
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

### Extracting Document Metadata
**DocumentInfo** encapsulates the extracted properties of a file, making them easy to read and use in your application.  
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

### Enhanced Information Display
If you need more context—such as whether the document exceeds a size threshold—you can extend the basic example with additional checks and business logic.

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

## Common Issues and Solutions

### Issue 1: "File Not Found" Errors
**Direct answer:** Verify that the file path is absolute or correctly rooted to the application base directory, and ensure the process has read permissions.  

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

### Issue 2: Unsupported File Format
**Direct answer:** Confirm that the file’s extension matches one of the 50+ supported formats; if not, convert it to a supported type before calling `GetDocumentInfo()`.  

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

### Issue 3: Memory Issues with Large Documents
**Direct answer:** Implement size checks before loading and use `using` statements to guarantee disposal of the `Annotator` instance, preventing memory leaks.  

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

## Real‑World Use Cases

### Document Management System Integration
When a user uploads a file, extract its metadata first to decide storage location, indexing strategy, or required approval workflow.

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

### Batch Document Analysis
Process a folder of files in a background job, logging each document’s page count and type for reporting purposes.

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

### Compliance and Validation
Regulated industries often require documents to be under a certain page count or size. Use the extracted metadata to automatically reject non‑compliant uploads.

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

## Performance Optimization Tips

### 1. Implement Caching
Cache `DocumentInfo` results for frequently accessed files to avoid repeated I/O operations.

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

### 2. Use Async Processing for Multiple Documents
Leverage `Task.Run` or async streams to process many files concurrently without blocking the main thread.

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

### 3. Memory Management Best Practices
- Always wrap `Annotator` in a `using` block.  
- Process documents in batches, not all at once.  
- For files larger than 100 MB, consider streaming the file to disk first and then reading metadata.  

## Troubleshooting Guide

### License‑Related Issues
**License** is the object that registers your product activation file with the GroupDocs library. Ensure the license file is placed in the application’s root folder and that the `License` object is instantiated before any other GroupDocs calls.  

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

### Performance Issues
**Direct answer:** Profile your application, limit file sizes to 100 MB for real‑time processing, and enable caching for repeated reads.  

### Platform‑Specific Issues
**Direct answer:** Use `Path.Combine` for cross‑platform path construction; Windows uses backslashes while Linux uses forward slashes.  

```csharp
// Use Path.Combine for cross-platform compatibility
string documentPath = Path.Combine(baseDirectory, "documents", fileName);
```  

### Handling Password‑Protected Documents
**Direct answer:** Pass the password to the `Annotator` constructor or set it via the `LoadOptions` before calling `GetDocumentInfo()`.  

```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-document.pdf", loadOptions))
{
    // Extract information normally
}
```  

### Updating GroupDocs.Annotation
**Direct answer:** Run `dotnet add package GroupDocs.Annotation --version <latest>` or use the NuGet Package Manager UI to pull the newest version.  

```shell
Update-Package GroupDocs.Annotation
```  

## Frequently Asked Questions

**Q: What document formats does GroupDocs.Annotation support for information extraction?**  
A: GroupDocs.Annotation supports over 50 document formats, including PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD files, and many more.

**Q: Can I extract custom metadata or properties from documents?**  
A: `GetDocumentInfo()` provides core metadata like file type, page count, and size. For custom properties such as author or creation date, combine GroupDocs.Annotation with GroupDocs.Metadata or use the native file format’s property APIs.

**Q: How do I handle password‑protected documents?**  
A: Provide the password when creating the `Annotator` instance, e.g., `new Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.

**Q: Is there a way to extract document information without loading the entire file into memory?**  
A: Yes—`GetDocumentInfo()` reads only the file header, so memory consumption stays low even for multi‑hundred‑page PDFs.

**Q: Can I use this in a web application or multi‑threaded environment?**  
A: Absolutely. GroupDocs.Annotation is thread‑safe; just create a new `Annotator` per request and dispose of it promptly.

## Conclusion and Next Steps

You now have a complete, production‑ready approach to extract the **c# pdf page count**, file type, and size using GroupDocs.Annotation. You’ve learned how to set up the library, retrieve metadata, handle common pitfalls, and optimize performance for large‑scale scenarios.

**Next actions:**  
1. Clone the sample project and run the provided placeholders with real files.  
2. Explore additional GroupDocs.Annotation features like annotation rendering and document comparison.  
3. Integrate the metadata extraction into your existing upload pipeline to automate classification and validation.

Remember, robust document processing starts with reliable metadata. With GroupDocs.Annotation, you can build smarter, faster, and more scalable solutions.

---

**Last Updated:** 2026-06-01  
**Tested With:** GroupDocs.Annotation 25.4.0 (latest)  
**Author:** GroupDocs  

**Essential Links:**  
- **[Documentation](https://docs.groupdocs.com/annotation/net/)**  
- **[API Reference](https://reference.groupdocs.com/annotation/net/)**  
- **[Download Latest Version](https://releases.groupdocs.com/annotation/net/)**  
- **[Purchase Licenses](https://purchase.groupdocs.com/buy)**  
- **[Free Trial Download](https://releases.groupdocs.com/annotation/net/)**  
- **[Temporary License Request](https://purchase.groupdocs.com/temporary-license/)**  
- **[Community Support Forum](https://forum.groupdocs.com/c/annotation/)**

## Related Tutorials

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [PDF Page Dimensions .NET - Extract Width & Height with C#](/annotation/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/)
- [GroupDocs.Annotation .NET Tutorial: Extract & Save Specific PDF Pages](/annotation/net/annotation-management/groupdocs-annotation-dotnet-page-range-management/)
