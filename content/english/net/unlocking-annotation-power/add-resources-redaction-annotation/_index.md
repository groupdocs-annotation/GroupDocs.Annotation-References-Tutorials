---
title: Add Resources Redaction Annotation to Document
linktitle: Add Resources Redaction Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 19
url: /net/unlocking-annotation-power/add-resources-redaction-annotation/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage.AddAnnotationToTheDocument
{
    /// <summary>
    /// This example demonstrates adding resources redaction annotation.
    /// </summary>
    class AddResourcesRedactionAnnotation
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("input.pdf"))
            {
                ResourcesRedactionAnnotation resourcesRedaction = new ResourcesRedactionAnnotation
                {
                    Box = new Rectangle(100, 100, 100, 100),
                    CreatedOn = DateTime.Now,
                    Message = "This is resources redaction annotation",
                    PageNumber = 0,
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "First comment",
                            RepliedOn = DateTime.Now
                        },
                        new Reply
                        {
                            Comment = "Second comment",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                annotator.Add(resourcesRedaction);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
