---
title: Loading Annotated Document Version
linktitle: Loading Annotated Document Version
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 16
url: /net/document-loading-essentials/loading-annotated-document-version/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage.Loading
{
    /// <summary>
    /// This example demonstrates loading annotated document versions that were added using save method.
    /// </summary>
    class LoadingAnnotatedDocumentVersion
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(),
                "result" + Path.GetExtension("input.pdf"));

            LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
            using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
            {
                var annotations = annotator.Get(); // As you can see, the number of annotations are not the same as you can see at the document. It's because we loaded not from last version
                annotator.Save(outputPath); // Now we save this version as separate document, were this version will be added as new, but version from loaded document will be penultimate
            }

            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
