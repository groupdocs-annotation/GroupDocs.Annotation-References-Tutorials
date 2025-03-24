---
title: Add Link Annotation to Document
linktitle: Add Link Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add link annotations to documents using Groupdocs.Annotation for .NET. Enhance collaboration and interactivity effortlessly.
weight: 16
url: /net/unlocking-annotation-power/add-link-annotation/
---
## Introduction
Groupdocs.Annotation for .NET is a powerful library that enables developers to integrate comprehensive annotation functionalities into their .NET applications effortlessly. One of the key features it offers is the ability to add link annotations to documents, enhancing collaboration and interactivity.
## Prerequisites
Before diving into the process of adding link annotations, ensure you have the following prerequisites:
- Basic understanding of C# programming language.
- Installed Groupdocs.Annotation for .NET library.
- Access to a document that you want to annotate.

## Import Namespaces
Firstly, you need to import the necessary namespaces to utilize Groupdocs.Annotation for .NET functionalities. This allows your application to access the classes and methods required for annotating documents.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Step 1: Set Output Path
Define the path where you want to save the annotated document.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Create an instance of the `Annotator` class by providing the path of the document you want to annotate.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will go here
}
```
## Step 3: Create Link Annotation
Define a `LinkAnnotation` object and specify its properties such as message, opacity, page number, background color, points, replies, and URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    },
    Url = "https://www.google.com"
};
```
## Step 4: Add Annotation
Add the created link annotation to the document using the `Add` method of the annotator instance.
```csharp
annotator.Add(link);
```
## Step 5: Save Document
Save the annotated document to the specified output path.
```csharp
annotator.Save(outputPath);
```
## Step 6: Display Success Message
Inform the user about the successful saving of the annotated document.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In conclusion, by following the above steps, you can seamlessly add link annotations to documents using Groupdocs.Annotation for .NET. This enhances document collaboration and provides users with interactive features.
## FAQ's
### Is Groupdocs.Annotation for .NET compatible with all types of documents?
Groupdocs.Annotation for .NET supports a wide range of document formats including PDF, Word, Excel, and more.
### Can I customize the appearance of annotations?
Yes, you can customize various properties of annotations such as color, opacity, and size to suit your requirements.
### Does Groupdocs.Annotation for .NET offer real-time collaboration features?
Yes, Groupdocs.Annotation for .NET provides real-time collaboration features allowing multiple users to annotate documents simultaneously.
### Is technical support available for Groupdocs products?
Yes, technical support for Groupdocs products is available through the forum and support [here](https://forum.groupdocs.com/c/annotation/10).
### Can I try Groupdocs.Annotation for .NET before purchasing?
Yes, you can avail of a free trial of Groupdocs.Annotation for .NET to explore its features before making a purchase[here](https://purchase.groupdocs.com/temporary-license/).
