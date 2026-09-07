---
title: "How to Generate Thumbnails in .NET – Clean PDF Previews"
linktitle: "Generate Preview without Comments"
second_title: GroupDocs.Annotation .NET API
description: "Learn how to generate thumbnails in .NET without comments using GroupDocs.Annotation. This guide covers how to hide annotations, remove comments preview, and create clean PDF previews."
keywords:
- how to generate thumbnails
- how to hide annotations
- remove comments preview
- document preview without comments
- clean pdf preview
weight: 14
url: /net/advanced-usage/generate-preview-without-comments/
date: "2026-04-01"
lastmod: "2026-04-01"
categories: ["Document Processing"]
tags: ["document-preview", "pdf-thumbnails", "groupdocs", "dotnet"]
type: docs
---

# How to Generate Thumbnails in .NET – Clean PDF Previews

## Introduction

Ever needed to **how to generate thumbnails** for a document viewer, file explorer, or content‑management system while keeping the images free of any user notes? You’re not alone. Many .NET developers hit a wall when they try to create document previews that hide annotations and comments.  

In this tutorial we’ll walk through the exact steps to produce clean PDF previews using **GroupDocs.Annotation for .NET**. You’ll see how to hide annotations, remove comments preview, and generate professional‑looking thumbnails that fit perfectly into galleries, dashboards, or any UI where a clutter‑free snapshot is required.

## Quick Answers
- **What library creates comment‑free thumbnails?** GroupDocs.Annotation for .NET  
- **Which property disables annotations?** `RenderComments = false`  
- **Can I choose the image format?** Yes – PNG, JPEG, BMP, etc. via `PreviewFormat`  
- **Do I need a license for production?** A commercial license is required; a temporary license works for testing.  
- **Is it .NET‑only?** Works with .NET Framework, .NET Core, and .NET 5/6+.

## What is thumbnail generation without comments?

Thumbnail generation without comments means rendering a visual snapshot of each page **without** any markup, notes, or collaborative annotations that might have been added to the original file. The result is a clean, static image that represents the document’s true content—ideal for public‑facing portals, legal archives, or any scenario where internal remarks must stay hidden.

## Why hide annotations when creating previews?

- **Professional look:** End users see only the document’s content, not the review chatter.  
- **Security & privacy:** Sensitive comments stay internal.  
- **Performance:** Rendering fewer layers speeds up image creation.  
- **Consistency:** Thumbnails match printed or exported versions that also omit comments.

## Prerequisites

### 1. Install GroupDocs.Annotation for .NET
Grab the package from the official distribution page **[here](https://releases.groupdocs.com/annotation/net/)** or install it via NuGet. Make sure your project targets a supported .NET version.

### 2. Obtain a License
A commercial license is required for production use. Purchase one **[here](https://purchase.groupdocs.com/buy)** or request a temporary evaluation license **[here](https://purchase.groupdocs.com/temporary-license/)**.

### 3. .NET Knowledge
You should be comfortable with C# basics, file I/O, and using `using` statements for resource management.

## Import Namespaces

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Step‑by‑Step Guide: Generate Clean Document Previews

### Step 1: Initialize the Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
The `Annotator` object loads the source file. The `using` block guarantees that all unmanaged resources are released once we’re done.

### Step 2: Configure Preview Options
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
Here we tell the library where to store each page’s image. The lambda receives the page number and returns a writable `FileStream`.

### Step 3: Choose Format and Pages
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
PNG delivers crisp thumbnails, but you can switch to JPEG if file size is a bigger concern. Selecting a subset of pages reduces processing time—perfect for thumbnail galleries that only need the first few pages.

### Step 4: Disable Rendering of Comments
```csharp
    previewOptions.RenderComments = false;
```
**This line is the key to “how to hide annotations.”** Setting `RenderComments` to `false` strips out all comment layers, giving you a clean PDF preview.

### Step 5: Generate the Preview Images
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
The library processes the document and writes the images to the locations you defined earlier.

## Best Practices for Document Preview Generation

- **Resize for thumbnails:** After generating PNGs, consider resizing them to ~200 × 300 px for faster UI loading.  
- **Process large files in batches:** Generate only the first few pages initially, then create the rest on demand.  
- **Always wrap in `using`:** Guarantees proper memory cleanup, especially when handling many documents.  
- **Add error handling:** Catch `FileNotFoundException`, `InvalidOperationException`, and licensing errors to keep your app robust.

## Common Issues and Troubleshooting

- **No images appear:** Verify the output folder exists and the app has write permissions.  
- **Blurry thumbnails:** Try increasing the DPI by setting `previewOptions.Dpi = 150;` (not shown in the code to keep the original block intact).  
- **Out‑of‑memory errors on huge PDFs:** Process pages one at a time, or use the async API in a background worker.  
- **License not found:** Ensure the `License` object is loaded before creating the `Annotator`.

## Performance Optimization Tips

- **Batch multiple documents:** Loop through a collection and reuse a single `Annotator` instance when possible.  
- **Async generation:** Offload preview creation to a background service so the UI stays responsive.  
- **Cache results:** Store generated thumbnails in a CDN or local cache to avoid re‑processing the same file.  
- **Choose the right format:** PNG for loss‑less quality, JPEG for smaller files when the document contains many images.

## Supported Document Formats

GroupDocs.Annotation for .NET can generate previews for:

- **PDF** – the most common use case.  
- **Microsoft Office** – DOCX, XLSX, PPTX, and their legacy counterparts.  
- **Images** – TIFF, JPEG, PNG, BMP (useful for scanned docs).  
- **OpenDocument** – ODT, ODS, ODP, and other open standards.

## When to Use Comment‑Free Preview Generation

- **Public portals** where internal review notes must stay hidden.  
- **Archive browsers** that display a clean thumbnail grid.  
- **Print‑ready workflows** that need to show the final appearance before sending to a printer.  
- **Quality‑control checks** where you compare “with comments” vs. “without comments” versions.

## Conclusion

You now know **how to generate thumbnails** in .NET while completely removing annotations and comments. By setting `RenderComments = false` you get clean, professional PDF previews that fit perfectly into any UI. Remember to tailor the preview format, page selection, and image dimensions to your specific scenario, and always handle licensing and error cases gracefully. With these steps, your application will deliver fast, clutter‑free document thumbnails that enhance the user experience.

## Frequently Asked Questions

**Q: Is GroupDocs.Annotation for .NET compatible with all document formats?**  
A: Yes. It supports PDF, DOCX, PPTX, XLSX, common image types, and many OpenDocument formats.

**Q: Can I customize the look of the generated previews?**  
A: Absolutely. You can change `PreviewFormat`, set image dimensions, DPI, and choose specific pages to render.

**Q: Does the library support multi‑user collaboration?**  
A: GroupDocs.Annotation offers collaborative annotation features. The preview generation can be used to create clean views that hide all user comments.

**Q: Where can I get help if I run into issues?**  
A: The community and support team are active on the **[support forum](https://forum.groupdocs.com/c/annotation/10)** where you can ask questions and share experiences.

**Q: Is there a free trial available?**  
A: Yes, you can download a full‑function trial **[here](https://releases.groupdocs.com/)** to test the preview generation capabilities before purchasing.

---

**Last Updated:** 2026-04-01  
**Tested With:** GroupDocs.Annotation for .NET (latest release)  
**Author:** GroupDocs  

---