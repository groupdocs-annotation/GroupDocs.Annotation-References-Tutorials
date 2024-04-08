---
title: Generate Document Pages Preview
linktitle: Generate Document Pages Preview
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 12
url: /net/advanced-usage/generate-document-pages-preview/
---

## Complete Source Code
```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    /// <summary>
    /// This example demonstrates annotating generating previews from document
    /// </summary>
    internal class GenerateDocumentPagesPreview
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("input.pdf"))
            {
                PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
                {
                    var pagePath = Path.Combine(Constants.GetOutputDirectoryPath(), $"result_{pageNumber}.png");
                    return File.Create(pagePath);
                });
                previewOptions.PreviewFormat = PreviewFormats.PNG;

                previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
                annotator.Document.GeneratePreview(previewOptions);
            }
            Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {Constants.GetOutputDirectoryPath()}.");
        }
    }
}
```
