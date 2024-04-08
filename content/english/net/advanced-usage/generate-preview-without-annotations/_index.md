---
title: Generate Preview without Annotations
linktitle: Generate Preview without Annotations
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 13
url: /net/advanced-usage/generate-preview-without-annotations/
---

## Complete Source Code
```csharp
using System.IO;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates generating preview of document without rendering comments
    /// </summary>
    class GeneratePreviewWithoutAnnotations
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
            {
                PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
                {
                    var pagePath = $"result{pageNumber}.png";
                    return File.Create(pagePath);
                });

                previewOptions.PreviewFormat = PreviewFormats.PNG;
                previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
                previewOptions.RenderAnnotations = false;
                annotator.Document.GeneratePreview(previewOptions);
            }
        }
    }
}

```
