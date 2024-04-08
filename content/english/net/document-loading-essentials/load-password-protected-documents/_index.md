---
title: Load Password Protected Documents
linktitle: Load Password Protected Documents
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 17
url: /net/document-loading-essentials/load-password-protected-documents/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage.Loading
{
    /// <summary>
    /// This example demonstrates annotating documents that are protected with a password.
    /// </summary>
    class LoadPasswordProtectedDocuments
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            LoadOptions loadOptions = new LoadOptions() { Password = "1234" };
            using (Annotator annotator = new Annotator("input.pdf"_PROTECTED, loadOptions))
            {
                AreaAnnotation area = new AreaAnnotation()
                {
                    Box = new Rectangle(100, 100, 100, 100),
                    BackgroundColor = 65535,
                };
                annotator.Add(area);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
