---
title: Remove Multiple Annotations by IDs
linktitle: Remove Multiple Annotations by IDs
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 13
url: /net/removing-annotations/remove-multiple-annotations-by-ids/
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
    class RemoveAnnotationsByIds
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("annotated.pdf"))
            {
                annotator.Remove(new List<int>{0,1});
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
