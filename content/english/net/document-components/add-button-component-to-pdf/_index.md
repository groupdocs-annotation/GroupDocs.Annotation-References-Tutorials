---
title: Add Button Component to PDF Document
linktitle: Add Button Component to PDF Document
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 10
url: /net/document-components/add-button-component-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;

namespace GroupDocs.Annotation.Examples.CSharp.BasicUsage.AddAnnotationToTheDocument
{
    /// <summary>
    /// This example demonstrates adding button component.
    /// </summary>
    class AddButtonComponent
    {
        public static void Run()
        {
            string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));

            using (Annotator annotator = new Annotator("input.pdf"))
            {
                ButtonComponent button = new ButtonComponent
                {
                    Box = new Rectangle(100, 100, 100, 100),
                    PenColor = 65535,
                    Style = BorderStyle.Dashed,
                    BorderWidth = 0,
                    BorderColor = 0,
                    AlternateName = "Name",
                    PartialName = "Patial Name",
                    NormalCaption = "Caption",
                    ButtonColor = 16761035,
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
                annotator.Add(button);
                annotator.Save("result.pdf");
            }

            Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
        }
    }
}
```
