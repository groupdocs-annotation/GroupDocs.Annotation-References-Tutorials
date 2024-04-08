---
title: Add Watermark Annotation to Document
linktitle: Add Watermark Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 28
url: /net/unlocking-annotation-power/add-watermark-annotation/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage.AddAnnotationToTheDocument
{
    /// <summary>
    /// This example demonstrates adding watermark annotation.
    /// </summary>
    class AddWatermarkAnnotation
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("input.pdf"))
            {
                WatermarkAnnotation watermark = new WatermarkAnnotation
                {
                    Angle = 75,
                    Box = new Rectangle(200, 200, 100, 50),
                    CreatedOn = DateTime.Now,
                    Text = "Watermark",
                    FontColor = 65535,
                    FontSize = 12,
                    Message = "This is watermark annotation",
                    Opacity = 0.7,
                    PageNumber = 0,
                    AutoScale = true,
                    HorizontalAlignment = HorizontalAlignment.Center,
                    VerticalAlignment = VerticalAlignment.Center,
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
                annotator.Add(watermark);
                annotator.Save(outputPath);
            }
            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}

```
