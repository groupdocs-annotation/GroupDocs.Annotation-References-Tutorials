---
title: Get List of Annotations using Version Key
linktitle: Get List of Annotations using Version Key
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 18
url: /net/advanced-usage/get-list-annotations-version-key/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Annotation.Models.AnnotationModels;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    /// <summary>
    /// This example demonstrates getting list of annotations from document using version key
    /// </summary>
    class GetListOfAnnotationsUsingVersionKey
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
            {
                List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
            }
        }
    }
}

```
