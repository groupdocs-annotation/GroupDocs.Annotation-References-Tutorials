---
title: "PDF Page Dimensions .NET - Extract Width & Height with C#"
linktitle: "PDF Page Dimensions .NET Guide"
description: "Learn how to get pdf page size in .NET using GroupDocs.Annotation. Extract pdf page width height, retrieve pdf width height, and handle c# pdf page dimensions efficiently."
keywords: "pdf page dimensions .net, groupdocs.annotation tutorial, pdf metadata extraction c#, .net document processing, retrieve pdf dimensions programmatically"
weight: 1
url: "/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/"
date: "2026-06-16"
lastmod: "2026-06-16"
categories: ["Document Processing"]
tags: ["pdf-processing", "dotnet", "groupdocs", "document-metadata"]
type: docs
schemas:
- type: TechArticle
  headline: PDF Page Dimensions .NET - Extract Width & Height with C#
  description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  dateModified: '2026-06-16'
  author: GroupDocs
- type: HowTo
  name: PDF Page Dimensions .NET - Extract Width & Height with C#
  description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  steps:
  - name: Initialize the Annotator with Your PDF
    text: Create an `Annotator` instance pointing to your PDF file. Always wrap it
      in a `using` block so the file handle is released promptly. **Pro Tip:** Proper
      disposal prevents memory leaks, especially when processing dozens of large PDFs
      in a batch job.
  - name: Retrieve Document Information
    text: '`DocumentInfo` is an object that holds overall PDF metadata such as total
      page count and a collection of `PageInfo` objects for each page. GroupDocs.Annotation
      makes metadata extraction a one‑liner: The returned `DocumentInfo` object gives
      you: - Total page count - File format details - A `Pages` li'
  - name: Validate the Retrieved Data
    text: Before you start looping over pages, confirm the document info isn’t null
      and that the page collection contains entries. This defensive check avoids null‑reference
      exceptions and provides early feedback if the PDF is corrupted.
  - name: Extract Width and Height for Each Page
    text: '`PageInfo` represents a single page’s properties, including its width,
      height, and rotation angle. Iterate through the `Pages` collection and read
      `Width` and `Height`. Remember that the values are expressed in **points** (1
      point = 1/72 inch). **Key Points** - Width appears first, then height. - Pa'
- type: FAQPage
  questions:
  - question: Can I extract PDF page dimensions without a license?
    answer: Yes. The free trial version supports basic dimension extraction, though
      it may impose a limit on the number of pages processed per session.
  - question: What units are the width and height measurements in?
    answer: GroupDocs.Annotation returns dimensions in **points** (1 point = 1/72
      inch). Convert to inches by dividing by 72, or to millimeters by multiplying
      by 0.352778.
  - question: How do I handle password‑protected PDFs?
    answer: 'Pass the password via `LoadOptions` when constructing the `Annotator`:
      `new Annotator(path, new LoadOptions { Password = "your‑password" })`.'
  - question: Can this work with PDFs stored in cloud storage like Azure or AWS?
    answer: Yes. Download the file to a local `Stream` first, then use the stream‑based
      `Annotator` constructor to avoid intermediate files.
  - question: What is the performance impact of extracting dimensions from large PDFs?
    answer: GroupDocs.Annotation reads only the PDF’s cross‑reference table and page
      dictionaries, so most PDFs under 100 MB are processed in under 1 second on typical
      server hardware.
---
# PDF Page Dimensions .NET - Extract Width & Height with C#

## Introduction

Ever found yourself wrestling with PDF documents in your .NET application, needing to **get pdf page size** for each page? You're not alone. Whether you're building a document viewer, creating print layouts, or processing forms, accurate page dimensions are the backbone of a polished user experience.

In this comprehensive guide, we'll walk you through extracting PDF page dimensions using **GroupDocs.Annotation for .NET**—one of the most reliable libraries for this task. By the end, you'll have working code that retrieves width, height, and other essential metadata from any PDF document.

### Quick Answers
- **How do I get pdf page size in .NET?** Use `Annotator.GetDocumentInfo()` and read `PageInfo.Width` / `PageInfo.Height`.
- **Which library supports pdf page width height extraction?** GroupDocs.Annotation for .NET (v25.4.0+).
- **Do I need a license for basic dimension extraction?** A free trial works; a commercial license is required for production.
- **What units are returned?** Points (1/72 inch); convert to inches or millimeters as needed.
- **Can I process large PDFs efficiently?** Yes—GroupDocs.Annotation reads metadata without loading the full file into memory.

### What is **get pdf page size**?
**Get pdf page size** refers to the programmatic retrieval of a PDF page’s width and height. This operation is essential for layout calculations, print preparation, and form field positioning in .NET applications.

## Why PDF Page Dimensions Matter in .NET Development

Before we jump into the code, let’s explore why knowing the **pdf page width height** matters. These numbers aren’t just trivia—they drive real‑world functionality:

- **Layout Management** – Responsive viewers can auto‑scale based on exact page size, eliminating awkward scrollbars.
- **Print Optimization** – Precise dimensions prevent paper waste and mis‑aligned prints in commercial workflows.
- **Form Processing** – Extraction coordinates rely on accurate page size; a 2 mm error can break data capture.
- **Resource Planning** – Large, mixed‑size PDFs require different memory strategies; early size knowledge enables smarter batching.

## Prerequisites

### Required Libraries and Versions
- **GroupDocs.Annotation for .NET** (Version 25.4.0 or later). This version supports **50+ input and output formats** and can handle multi‑hundred‑page PDFs without loading the entire file into memory.
- .NET Framework 4.6.1+ **or** .NET Core 2.0+

### Environment Setup Requirements
- Visual Studio 2019 or later (Community edition works perfectly)
- A test PDF file (we’ll show you how to handle different types)
- Basic familiarity with `using` statements and object disposal in C#

### Knowledge Prerequisites
You only need:
- C# fundamentals
- NuGet package management basics
- Simple file I/O in .NET

Got everything ready? Great—let’s set up the library.

## Setting Up GroupDocs.Annotation for .NET

Installing GroupDocs.Annotation is straightforward, but there are a few ways to do it depending on your workflow.

### Method 1: Using NuGet Package Manager Console
Open the Package Manager Console in Visual Studio and run:

```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Method 2: Using .NET CLI
If you prefer command‑line tools:

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Method 3: Visual Package Manager
1. Right‑click your project in Solution Explorer  
2. Select **Manage NuGet Packages**  
3. Search for **GroupDocs.Annotation**  
4. Click **Install**

#### Licensing Options (Choose What Works for You)

- **Free Trial** – Core features, including dimension extraction, are available with minor usage caps—perfect for proof‑of‑concept work.  
- **Temporary License** – Request a 30‑day temporary key for full functionality during evaluation.  
- **Commercial License** – Required for production deployments; pricing scales with developer count and deployment model.

### Quick Setup Verification

Here's a simple test to confirm everything is wired correctly:

```csharp
using GroupDocs.Annotation;

// This should compile without errors if installation succeeded
using (Annotator annotator = new Annotator(@"path\to\your\test.pdf"))
{
    Console.WriteLine("GroupDocs.Annotation is ready to use!");
}
```

If this compiles and runs without throwing exceptions, you’re ready to extract page sizes.

## What is the **Annotator** class?

The `Annotator` class is GroupDocs.Annotation’s core object that represents a PDF document in memory and provides methods to read metadata, add annotations, and extract page information. It encapsulates file handling, supports loading from streams, and ensures that all subsequent operations flow through an `Annotator` instance, simplifying workflow management.

## How to **get pdf page size** using GroupDocs.Annotation?

`GetDocumentInfo()` returns a `DocumentInfo` object containing overall PDF metadata, including page count and a collection of page details. Load your PDF with `new Annotator("file.pdf")` and call this method; each `PageInfo` in the `Pages` collection holds `Width` and `Height`. This two‑step approach provides dimensions in points instantly, without parsing the entire file.

## Step‑by‑Step Implementation Guide

### Step 1: Initialize the Annotator with Your PDF

Create an `Annotator` instance pointing to your PDF file. Always wrap it in a `using` block so the file handle is released promptly.

```csharp
using (Annotator annotator = new Annotator(@"YOUR_DOCUMENT_DIRECTORY\INPUT_PDF"))
{
    // All our dimension extraction magic happens here
}
```

**Pro Tip:** Proper disposal prevents memory leaks, especially when processing dozens of large PDFs in a batch job.

### Step 2: Retrieve Document Information

`DocumentInfo` is an object that holds overall PDF metadata such as total page count and a collection of `PageInfo` objects for each page.  

GroupDocs.Annotation makes metadata extraction a one‑liner:

```csharp
IDocumentInfo info = annotator.Document.GetDocumentInfo();
```

The returned `DocumentInfo` object gives you:
- Total page count  
- File format details  
- A `Pages` list where each entry contains width, height, rotation, and more

### Step 3: Validate the Retrieved Data

Before you start looping over pages, confirm the document info isn’t null and that the page collection contains entries.

```csharp
if (info.PagesInfo != null && info.PagesInfo.Count > 0)
{
    Console.WriteLine($"\t Document info: Type {info.FileType}, size = {info.Size}, pages = {info.PageCount}");
}
else
{
    Console.WriteLine("No page information available - check your PDF file");
    return;
}
```

This defensive check avoids null‑reference exceptions and provides early feedback if the PDF is corrupted.

### Step 4: Extract Width and Height for Each Page

`PageInfo` represents a single page’s properties, including its width, height, and rotation angle.  

Iterate through the `Pages` collection and read `Width` and `Height`. Remember that the values are expressed in **points** (1 point = 1/72 inch).

```csharp
foreach (var page in info.PagesInfo)
{
    Console.WriteLine($"\t\t page #{page.PageNumber}: {page.Width}x{page.Height}");
}
```

**Key Points**  
- Width appears first, then height.  
- Page numbers are 1‑based, matching what users see in viewers.  
- Rotation information is also available if you need to adjust coordinates.

### Complete Working Example (Method)

You can wrap the above steps into a reusable method:

```csharp
using GroupDocs.Annotation;
using System;

public void ExtractPdfPageDimensions(string pdfPath)
{
    try
    {
        using (Annotator annotator = new Annotator(pdfPath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            if (info.PagesInfo != null && info.PagesInfo.Count > 0)
            {
                Console.WriteLine($"Document: {info.FileType}, {info.Size} bytes, {info.PageCount} pages");
                
                foreach (var page in info.PagesInfo)
                {
                    Console.WriteLine($"Page {page.PageNumber}: {page.Width} x {page.Height} points");
                }
            }
            else
            {
                Console.WriteLine("Could not retrieve page information");
            }
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error processing PDF: {ex.Message}");
    }
}
```

## Common Pitfalls and How to Avoid Them

Even with straightforward code, developers encounter predictable issues. Below are the most common traps and proven solutions.

### File Path Problems
**Issue:** “File not found” errors during development.  
**Solution:** Use absolute paths while testing and always verify the file exists before creating the `Annotator`.

```csharp
if (!File.Exists(pdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {pdfPath}");
}
```

### Permission Issues
**Issue:** The application lacks read access to the PDF file, especially on web servers.  
**Solution:** Grant the appropriate read permissions to the application pool identity or use impersonation for restricted folders.

### Corrupted PDF Handling
**Issue:** Some PDFs are partially damaged or use non‑standard features.  
**Solution:** Enclose the extraction logic in a `try‑catch` block and surface a clear error message. GroupDocs.Annotation will throw a `DocumentException` for unsupported structures.

### Memory Leaks with Large Files
**Issue:** Processing many large PDFs without disposing of `Annotator` instances leads to out‑of‑memory crashes.  
**Solution:** Always employ `using` statements and consider processing files in smaller batches or streaming mode.

### Version Compatibility
**Issue:** Mixing different GroupDocs library versions can cause type mismatches.  
**Solution:** Standardize on a single version across the solution and update all related packages together.

## Real‑World Applications

Understanding **retrieve pdf width height** unlocks powerful scenarios:

### Document Viewing Applications
Responsive viewers can automatically set the initial zoom level based on page dimensions, delivering a “fit‑to‑screen” experience without manual tweaking.

```csharp
// Example: Calculate optimal zoom for viewport
double optimalZoom = Math.Min(viewportWidth / pageWidth, viewportHeight / pageHeight);
```

### Automated Report Generation
When merging multiple PDFs into a single report, knowing each page’s size ensures consistent scaling and avoids unexpected page breaks.

### Print Management Systems
Exact dimensions let you calculate optimal paper usage, detect portrait vs. landscape orientation, and pre‑flight documents before sending them to commercial printers.

### Form Processing Solutions
Accurate coordinates derived from page size enable reliable extraction of checkboxes, signatures, and text fields across PDFs of varying layouts.

### Digital Asset Management
Tag PDFs with size metadata to facilitate quick searches (e.g., “show all A4‑sized documents”) and improve cataloging efficiency.

## Performance Optimization Tips

When you move from a prototype to production, performance becomes critical.

### Batch Processing Strategy
Group similar operations to reduce overhead. For example, read metadata for a batch of files, store the results, then process annotations in a second pass.

```csharp
var results = new List<PageDimensionResult>();
foreach (var pdfFile in pdfFiles.Take(10)) // Process in batches of 10
{
    // Extract dimensions and add to results
}
```

### Caching Frequently Accessed Dimensions
If the same PDFs are queried repeatedly, cache their `DocumentInfo` objects in a thread‑safe dictionary. Remember to invalidate the cache when the source file changes.

```csharp
private static readonly Dictionary<string, IDocumentInfo> _dimensionCache = 
    new Dictionary<string, IDocumentInfo>();
```

### Asynchronous Processing for Large Files
Leverage `async/await` patterns to keep UI threads responsive while GroupDocs.Annotation reads metadata in the background.

```csharp
public async Task<List<PageInfo>> ExtractDimensionsAsync(string pdfPath)
{
    return await Task.Run(() => {
        // Your dimension extraction code here
    });
}
```

### Memory Management Best Practices
- Dispose of every `Annotator` instance promptly.  
- Process large collections in chunks of 20–50 files to keep memory footprints low.  
- Monitor memory usage with performance counters or profiling tools.  
- Use weak references for cached objects if you expect high turnover.

## Advanced Use Cases

Once you’re comfortable with basic extraction, explore these sophisticated scenarios.

### Handling Mixed‑Size Documents
Some PDFs contain pages of different sizes (e.g., a cover page in A4 followed by A5 inner pages). Detect size changes by comparing consecutive `PageInfo.Width`/`Height` values and apply conditional logic.

```csharp
var pageSizes = info.PagesInfo.Select(p => new { p.PageNumber, p.Width, p.Height }).ToList();
var uniqueSizes = pageSizes.Select(p => new { p.Width, p.Height }).Distinct().Count();

if (uniqueSizes > 1)
{
    Console.WriteLine("Document contains multiple page sizes");
}
```

### Orientation Detection
Determine portrait vs. landscape by comparing width and height. This is useful for auto‑rotating pages in viewers or for generating orientation‑aware thumbnails.

```csharp
foreach (var page in info.PagesInfo)
{
    string orientation = page.Width > page.Height ? "Landscape" : "Portrait";
    Console.WriteLine($"Page {page.PageNumber}: {orientation}");
}
```

### Integration with Other GroupDocs Features
Combine dimension extraction with annotation APIs to place stamps precisely, or with conversion APIs to generate images that respect the original page size.

## Frequently Asked Questions

**Q: Can I extract PDF page dimensions without a license?**  
A: Yes. The free trial version supports basic dimension extraction, though it may impose a limit on the number of pages processed per session.

**Q: What units are the width and height measurements in?**  
A: GroupDocs.Annotation returns dimensions in **points** (1 point = 1/72 inch). Convert to inches by dividing by 72, or to millimeters by multiplying by 0.352778.

**Q: How do I handle password‑protected PDFs?**  
A: Pass the password via `LoadOptions` when constructing the `Annotator`: `new Annotator(path, new LoadOptions { Password = "your‑password" })`.

**Q: Can this work with PDFs stored in cloud storage like Azure or AWS?**  
A: Yes. Download the file to a local `Stream` first, then use the stream‑based `Annotator` constructor to avoid intermediate files.

**Q: What is the performance impact of extracting dimensions from large PDFs?**  
A: GroupDocs.Annotation reads only the PDF’s cross‑reference table and page dictionaries, so most PDFs under 100 MB are processed in under 1 second on typical server hardware.

**Q: How do I handle PDFs with rotated pages?**  
A: The `PageInfo.Rotation` property indicates the rotation angle. If a page is rotated 90° or 270°, swap the width and height values to obtain the displayed dimensions.

**Q: Can I extract dimensions from specific pages only?**  
A: Yes. After calling `GetDocumentInfo()`, filter the `Pages` collection by `PageNumber` to target individual pages.

**Q: Does this work with PDF/A format documents?**  
A: Absolutely. GroupDocs.Annotation fully supports PDF/A‑1, PDF/A‑2, and PDF/A‑3 standards.

**Q: How do I troubleshoot “Unable to load document” errors?**  
A: Verify file permissions, ensure the file isn’t corrupted by opening it in a PDF reader, and confirm you’re using a supported PDF version (1.4–2.0).

**Q: Can I get dimensions in pixels instead of points?**  
A: Convert manually: `pixels = points * DPI / 72`. For typical screen DPI of 96, multiply points by 1.3333.

## Essential Resources

- **Documentation**: [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/net/)
- **API Reference**: [GroupDocs Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- **Download**: [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- **Purchase**: [Buy GroupDocs](https://purchase.groupdocs.com/buy)
- **Free Trial**: [Try Free Version](https://releases.groupdocs.com/annotation/net/)
- **Temporary License**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Support**: [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

---

**Last Updated:** 2026-06-16  
**Tested With:** GroupDocs.Annotation 25.4.0 for .NET  
**Author:** GroupDocs

## Related Tutorials

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Generate Document Preview .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)
