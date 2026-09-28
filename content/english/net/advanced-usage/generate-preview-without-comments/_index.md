---
categories:
- Document Processing
date: '2026-09-20'
description: Learn how to remove PDF comments and generate clean thumbnails in .NET
  using GroupDocs.Annotation. This guide shows how to hide annotations, create comment‑free
  previews, and produce professional PDF thumbnails.
images:
- /net/advanced-usage/generate-preview-without-comments/og-image.png
keywords:
- remove pdf comments
- hide pdf annotations
- file explorer pdf thumbnail
- render pdf pages images
- pdf to png thumbnail
lastmod: '2026-09-20'
linktitle: Generate preview without comments
og_description: Remove PDF comments and create clean thumbnails in .NET with GroupDocs.Annotation.
  Follow step‑by‑step instructions to hide annotations, choose formats, and optimize
  performance.
og_image_alt: Guide showing clean PDF thumbnail generation in .NET using GroupDocs.Annotation
og_title: How to remove PDF comments and generate thumbnails in .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-20'
  description: Learn how to remove PDF comments and generate clean thumbnails in .NET
    using GroupDocs.Annotation. This guide shows how to hide annotations, create comment‑free
    previews, and produce professional PDF thumbnails.
  headline: How to remove PDF comments and generate thumbnails in .NET
  type: TechArticle
- description: Learn how to remove PDF comments and generate clean thumbnails in .NET
    using GroupDocs.Annotation. This guide shows how to hide annotations, create comment‑free
    previews, and produce professional PDF thumbnails.
  name: How to remove PDF comments and generate thumbnails in .NET
  steps:
  - name: Initialize the annotator
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and processing documents. The `Annotator` object loads the source file. The
      `using` block guarantees that all unmanaged resources are released once we’re
      done.'
  - name: Configure preview options
    text: '`PreviewOptions` defines how each page is rendered, including format, DPI,
      and output stream. Here we tell the library where to store each page’s image.
      The lambda receives the page number and returns a writable `FileStream`.'
  - name: Choose format and pages
    text: PNG delivers crisp thumbnails, but you can switch to JPEG if file size is
      a bigger concern. Selecting a subset of pages reduces processing time—perfect
      for thumbnail galleries that only need the first few pages.
  - name: Disable rendering of comments
    text: '`RenderComments` is a boolean flag that tells the renderer whether to include
      annotation comment layers in the output. **This line is the key to “how to hide
      annotations.”** Setting `RenderComments` to `false` strips out all comment layers,
      giving you a clean PDF preview.'
  - name: Generate the preview images
    text: The library processes the document and writes the images to the locations
      you defined earlier.
  type: HowTo
- questions:
  - answer: Yes. It supports PDF, DOCX, PPTX, XLSX, common image types, and many OpenDocument
      formats.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Absolutely. You can change `PreviewFormat`, set image dimensions, DPI,
      and choose specific pages to render.
    question: Can I customize the look of the generated previews?
  - answer: GroupDocs.Annotation offers collaborative annotation features. The preview
      generation can be used to create clean views that hide all user comments.
    question: Does the library support multi‑user collaboration?
  - answer: The community and support team are active on the **[support forum](https://forum.groupdocs.com/c/annotation/10)**
      where you can ask questions and share experiences.
    question: Where can I get help if I run into issues?
  - answer: Yes, you can download a full‑function trial **[full‑function trial download](https://releases.groupdocs.com/)**
      to test the preview generation capabilities before purchasing.
    question: Is there a free trial available?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- remove pdf comments
- pdf thumbnail
- groupdocs annotation
- dotnet preview
title: How to remove PDF comments and generate thumbnails in .NET
type: docs
url: /net/advanced-usage/generate-preview-without-comments/
weight: 14
---

# How to remove PDF comments and generate thumbnails in .NET

## Introduction

If you need to **remove PDF comments** while generating thumbnails for a document viewer, file explorer, or content‑management system, you’ve come to the right place. Many .NET developers struggle to produce clean previews that hide user notes and annotations. In this tutorial we’ll walk through the exact steps to create comment‑free PDF thumbnails using **GroupDocs.Annotation for .NET**. You’ll learn how to hide annotations, configure output formats, and produce professional‑looking images that fit perfectly into galleries, dashboards, or any UI where a clutter‑free snapshot is required.

## Quick answers
- **What library creates comment‑free thumbnails?** GroupDocs.Annotation for .NET  
- **Which property disables annotations?** `RenderComments = false`  
- **Can I choose the image format?** Yes – PNG, JPEG, BMP, etc. via `PreviewFormat`  
- **Do I need a license for production?** A commercial license is required; a temporary license works for testing.  
- **Is it .NET‑only?** Works with .NET Framework, .NET Core, and .NET 5/6+.

## What is thumbnail generation without comments?

Thumbnail generation without comments means rendering a visual snapshot of each page **without** any markup, notes, or collaborative annotations that might have been added to the original file. The result is a clean, static image that represents the document’s true content—ideal for public‑facing portals, legal archives, or any scenario where internal remarks must stay hidden.

## Why hide annotations when creating previews?

You should hide annotations to keep the preview professional, secure, and fast. Rendering fewer layers reduces processing time, protects sensitive remarks, and ensures the thumbnail matches the final printed or exported version that also omits comments.

- **Professional look:** End users see only the document’s content, not the review chatter.  
- **Security & privacy:** Sensitive comments stay internal.  
- **Performance:** Rendering fewer layers speeds up image creation.  
- **Consistency:** Thumbnails match printed or exported versions that also omit comments.

## Prerequisites

### 1. Install GroupDocs.Annotation for .NET
Grab the package from the official distribution page **[official distribution page](https://releases.groupdocs.com/annotation/net/)** or install it via NuGet. Make sure your project targets a supported .NET version.

### 2. Obtain a license
A commercial license is required for production use. Purchase one **[purchase page](https://purchase.groupdocs.com/buy)** or request a temporary evaluation license **[temporary evaluation license page](https://purchase.groupdocs.com/temporary-license/)**.

### 3. .NET knowledge
You should be comfortable with C# basics, file I/O, and using `using` statements for resource management.

## Import namespaces

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Step‑by‑step guide: generate clean document previews

### Step 1: Initialize the annotator

`Annotator` is the main entry point in GroupDocs.Annotation for loading and processing documents.  
The `Annotator` object loads the source file. The `using` block guarantees that all unmanaged resources are released once we’re done.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```

### Step 2: Configure preview options

`PreviewOptions` defines how each page is rendered, including format, DPI, and output stream.  
Here we tell the library where to store each page’s image. The lambda receives the page number and returns a writable `FileStream`.

```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```

### Step 3: Choose format and pages

PNG delivers crisp thumbnails, but you can switch to JPEG if file size is a bigger concern. Selecting a subset of pages reduces processing time—perfect for thumbnail galleries that only need the first few pages.

```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```

### Step 4: Disable rendering of comments

`RenderComments` is a boolean flag that tells the renderer whether to include annotation comment layers in the output.  
**This line is the key to “how to hide annotations.”** Setting `RenderComments` to `false` strips out all comment layers, giving you a clean PDF preview.

```csharp
    previewOptions.RenderComments = false;
```

### Step 5: Generate the preview images

The library processes the document and writes the images to the locations you defined earlier.

```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```

## Best practices for document preview generation

- **Resize for thumbnails:** After generating PNGs, consider resizing them to ~200 × 300 px for faster UI loading.  
- **Process large files in batches:** Generate only the first few pages initially, then create the rest on demand.  
- **Always wrap in `using`:** Guarantees proper memory cleanup, especially when handling many documents.  
- **Add error handling:** Catch `FileNotFoundException`, `InvalidOperationException`, and licensing errors to keep your app robust.

## Common issues and troubleshooting

- **No images appear:** Verify the output folder exists and the app has write permissions.  
- **Blurry thumbnails:** Try increasing the DPI by setting `previewOptions.Dpi = 150;` (not shown in the code to keep the original block intact).  
- **Out‑of‑memory errors on huge PDFs:** Process pages one at a time, or use the async API in a background worker.  
- **License not found:** Ensure the `License` object is loaded before creating the `Annotator`.

## Performance optimisation tips

- **Batch multiple documents:** Loop through a collection and reuse a single `Annotator` instance when possible.  
- **Async generation:** Offload preview creation to a background service so the UI stays responsive.  
- **Cache results:** Store generated thumbnails in a CDN or local cache to avoid re‑processing the same file.  
- **Choose the right format:** PNG for loss‑less quality, JPEG for smaller files when the document contains many images.

## Supported document formats

GroupDocs.Annotation for .NET supports **30+** input and output formats, enabling preview generation for PDFs, Office files, images, and OpenDocument standards.

- **PDF** – the most common use case.  
- **Microsoft Office** – DOCX, XLSX, PPTX, and their legacy counterparts.  
- **Images** – TIFF, JPEG, PNG, BMP (useful for scanned docs).  
- **OpenDocument** – ODT, ODS, ODP, and other open standards.

## When to use comment‑free preview generation

Comment‑free preview generation is ideal for public portals where internal review notes must stay hidden, for archive browsers that display a clean thumbnail grid, for print‑ready workflows that need to show the final appearance before printing, and for quality‑control checks where you compare versions with and without comments.

## Conclusion

You now know **how to remove PDF comments and generate thumbnails** in .NET while completely stripping annotations. By setting `RenderComments = false` you get clean, professional PDF previews that fit perfectly into any UI. Remember to tailor the preview format, page selection, and image dimensions to your specific scenario, and always handle licensing and error cases gracefully. With these steps, your application will deliver fast, clutter‑free document thumbnails that enhance the user experience.

## Frequently asked questions

**Q: Is GroupDocs.Annotation for .NET compatible with all document formats?**  
A: Yes. It supports PDF, DOCX, PPTX, XLSX, common image types, and many OpenDocument formats.

**Q: Can I customize the look of the generated previews?**  
A: Absolutely. You can change `PreviewFormat`, set image dimensions, DPI, and choose specific pages to render.

**Q: Does the library support multi‑user collaboration?**  
A: GroupDocs.Annotation offers collaborative annotation features. The preview generation can be used to create clean views that hide all user comments.

**Q: Where can I get help if I run into issues?**  
A: The community and support team are active on the **[support forum](https://forum.groupdocs.com/c/annotation/10)** where you can ask questions and share experiences.

**Q: Is there a free trial available?**  
A: Yes, you can download a full‑function trial **[full‑function trial download](https://releases.groupdocs.com/)** to test the preview generation capabilities before purchasing.

---

**Last Updated:** 2026-09-20  
**Tested With:** GroupDocs.Annotation for .NET (latest release)  
**Author:** GroupDocs

## Related Tutorials

- [Generate Document Previews Without Comments in .NET](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [Create PDF Thumbnail with GroupDocs.Annotation for .NET](/annotation/net/advanced-usage/generate-document-pages-preview/)
- [How to Remove PDF Annotations C# – GroupDocs.Annotation Guide](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)