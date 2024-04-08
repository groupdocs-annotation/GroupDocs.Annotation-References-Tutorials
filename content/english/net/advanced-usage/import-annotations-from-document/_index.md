---
title: Import Annotations from Document
linktitle: Import Annotations from Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 19
url: /net/advanced-usage/import-annotations-from-document/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Annotation;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    class ImportAnnotationsFromDocument
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("input.pdf-file")) // specify the path to the file with the annotated
            {
                annotator.ImportAnnotationsFromDocument("result.XML-file"); // specify the path to the result XML file
            }
        }
    }
}

```
