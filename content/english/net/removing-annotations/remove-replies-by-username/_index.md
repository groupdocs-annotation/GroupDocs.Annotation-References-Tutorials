---
title: Remove Replies by User Name in .NET
linktitle: Remove Replies by User Name in .NET
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 17
url: /net/removing-annotations/remove-replies-by-username/
---

## Complete Source Code
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using System;
using System.Collections.Generic;
using System.IO;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to remove replies from annotated document by user name
    /// </summary>
    class RemoveRepliesByUserName
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            // NOTE: Input document already contain annotations with replies
            using (Annotator annotator = new Annotator("annotated_with_replies.pdf"))
            {
                // Obtain annotations collection from document
                List<AnnotationBase> annotations = annotator.Get();

                // Remove all replies where author name is "Tom"
                annotations[0].Replies.RemoveAll(x => x.User.Name == "Tom");

                // Save changes
                annotator.Update(annotations);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
