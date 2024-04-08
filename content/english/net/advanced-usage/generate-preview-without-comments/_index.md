---
title: Generate Preview without Comments
linktitle: Generate Preview without Comments
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 14
url: /net/advanced-usage/generate-preview-without-comments/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    /// <summary>
    /// This example demonstrates generating preview of document without rendering comments
    /// </summary>
    class GeneratePreviewWithoutComments
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
                previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
                previewOptions.RenderComments = false;
                annotator.Document.GeneratePreview(previewOptions);
            }
        }
    }
}

```
