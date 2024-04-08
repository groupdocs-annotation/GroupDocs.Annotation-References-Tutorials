---
title: Get All Version Keys on Document
linktitle: Get All Version Keys on Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 16
url: /net/advanced-usage/get-all-version-keys-document/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    /// <summary>
    /// This example demonstrates getting all version keys from document
    /// </summary>
    class GetAllVersionKeysOnDocument
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
            {
                List<object> versionKeys = annotator.GetVersionsList();
            }
        }
    }
}

```
