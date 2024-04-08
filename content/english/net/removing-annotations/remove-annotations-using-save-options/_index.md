---
title: Remove Annotations Using Save Options in .NET
linktitle: Remove Annotations Using Save Options in .NET
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 14
url: /net/removing-annotations/remove-annotations-using-save-options/
---

## Complete Source Code
```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to remove annotations from document using SaveOptions Property
    /// </summary>
    class RemoveAnnotationUsingSaveOptions
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("annotated.pdf"))
            {
                annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
