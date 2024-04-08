---
title: Add Search Text Fragment Annotation to Document
linktitle: Add Search Text Fragment Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 20
url: /net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage.AddAnnotationToTheDocument
{
    /// <summary>
    /// This example demonstrates adding search text fragment annotation.
    /// </summary>
    class AddSearchTextFragmentAnnotation
    {
        public static void Run()
        {
            
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("input.pdf"))
            {
                SearchTextFragment searchText = new SearchTextFragment()
                {
                    Text = "Welcome to GroupDocs", //here should be the text that is contained in your document, otherwise nothing will be highlighted
                    FontSize = 10,
                    FontFamily = "Calibri",
                    FontColor = 65535,
                    BackgroundColor = 16761035,
                };
                annotator.Add(searchText);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
