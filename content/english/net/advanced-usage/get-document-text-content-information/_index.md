---
title: Get Document Text Content Information
linktitle: Get Document Text Content Information
second_title: GroupDocs.Annotation .NET API
description: 
type: docs
weight: 17
url: /net/advanced-usage/get-document-text-content-information/
---

## Complete Source Code
```csharp
using System;
using GroupDocs.Annotation.Models;

namespace GroupDocs.Annotation.Examples.CSharp.AdvancedUsage
{
    /// <summary>
    /// This example demonstrates how to get an information about document's text content
    /// </summary>
    class GetDocumentTextContentInformation
    {
        public static void Run()
        {
            using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
            {
                IDocumentInfo documentInfo = annotator.Document.GetDocumentInfo();

                foreach (PageInfo page in documentInfo.PagesInfo)
                {
                    //Here you can get information about page through the 'page' object.
                    Console.WriteLine("Page number {0}, width: {1} and height: {2}", page.PageNumber, page.Width, page.Height);

                    foreach (TextLineInfo textLine in page.TextLines)
                    {
                        //Here you can get information about every text line on page, through the 'textLine' object.
                        Console.WriteLine("\tText line. '{0}'", textLine.Text);
                        Console.WriteLine("\t\tText width {0} and height {1}. Top indent: {2}, left indent: {3}",
                            textLine.Width, textLine.Height, textLine.TopIndent, textLine.LeftIndent);
                    }
                }
            }
        }
    }
}

```
