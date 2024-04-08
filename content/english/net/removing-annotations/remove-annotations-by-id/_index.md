---
title: Remove Annotations by ID
linktitle: Remove Annotations by ID
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 11
url: /net/removing-annotations/remove-annotations-by-id/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to remove annotations from annotated document by Id
    /// </summary>
    class RemoveAnnotationById
    {
        public static void Run()
            {
                string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

                using (Annotator annotator = new Annotator("annotated.pdf"))
                {
                    annotator.Remove(0);
                    annotator.Save(outputPath);
                }
                Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
            }
        
    }
}

```
