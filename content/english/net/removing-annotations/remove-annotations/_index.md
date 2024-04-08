---
title: Remove Annotations in .NET
linktitle: Remove Annotations in .NET
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 10
url: /net/removing-annotations/remove-annotations/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage
{
    class RemoveAnnotationByAnnotation
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("annotated.pdf"))
            {
                annotator.Remove(annotator.Get()[0]);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
