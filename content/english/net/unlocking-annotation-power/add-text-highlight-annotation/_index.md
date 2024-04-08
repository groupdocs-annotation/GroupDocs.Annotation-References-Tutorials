---
title: Add Text Highlight Annotation to Document
linktitle: Add Text Highlight Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 22
url: /net/unlocking-annotation-power/add-text-highlight-annotation/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage.AddAnnotationToTheDocument
{
    /// <summary>
    /// This example demonstrates adding text highlight annotation.
    /// </summary>
    class AddTextHighlightAnnotation
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("input.pdf"))
            {
                HighlightAnnotation highlight = new HighlightAnnotation
                {
                    BackgroundColor = 65535,
                    CreatedOn = DateTime.Now,
                    FontColor = 0,
                    Message = "This is highlight annotation",
                    Opacity = 0.5,
                    PageNumber = 0,
                    Points = new List<Point>
                    {
                        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
                    },
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
                annotator.Add(highlight);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
