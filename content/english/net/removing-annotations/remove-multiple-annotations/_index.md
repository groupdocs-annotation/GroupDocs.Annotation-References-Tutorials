---
title: Remove Multiple Annotations in .NET
linktitle: Remove Multiple Annotations in .NET
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 12
url: /net/removing-annotations/remove-multiple-annotations/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage
{
    class RemoveAnnotationsByAnnotations
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("annotated.pdf"))
            {
                annotator.Remove(annotator.Get());
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
