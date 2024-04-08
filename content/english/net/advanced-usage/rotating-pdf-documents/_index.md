---
title: Rotating PDF Documents
linktitle: Rotating PDF Documents
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 22
url: /net/advanced-usage/rotating-pdf-documents/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    class RotationDocument
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("input.pdf"))
            {
                annotator.ProcessPages = 1;
                annotator.Rotation = RotationDocument.on90;
                annotator.Save("result.pdf");
            }

            Console.WriteLine($"\nThe document is rotated 90 degrees");
        }
    }
}

```
