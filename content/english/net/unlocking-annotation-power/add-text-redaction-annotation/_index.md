---
title: Add Text Redaction Annotation to Document
linktitle: Add Text Redaction Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add text redaction annotations to PDF documents using GroupDocs.Annotation for .NET. Safeguard sensitive information effortlessly.
type: docs
weight: 23
url: /net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Introduction
Adding a text redaction annotation to a document can be a crucial step in securely managing sensitive information. GroupDocs.Annotation for .NET provides a robust solution to achieve this seamlessly. In this tutorial, we'll guide you through the process of adding a text redaction annotation to your document step by step.
## Prerequisites
Before we begin, make sure you have the following prerequisites in place:
1. GroupDocs.Annotation for .NET: Ensure you have installed the GroupDocs.Annotation for .NET library. You can download it from the [website](https://releases.groupdocs.com/annotation/net/).
2. Development Environment: Set up a development environment with a .NET compatible IDE such as Visual Studio.

## Importing Namespaces
Firstly, let's import the necessary namespaces to our project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Step 1: Define Output Path
Define the output path where you want to save the annotated document. Ensure it's accessible and writable.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Initialize the annotator with the input document path. Replace `"input.pdf"` with the path to your document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will go here
}
```
## Step 3: Create Text Redaction Annotation
Create a `TextRedactionAnnotation` object with the required properties such as `PageNumber`, `FontColor`, and `Points`. Customize the annotation as per your requirements.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
```
## Step 4: Add Annotation and Save
Add the created annotation to the document using the annotator and save the annotated document to the specified output path.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Step 5: Check Output
Finally, confirm that the document has been saved successfully to the specified output path.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In this tutorial, we've walked through the process of adding a text redaction annotation to a document using GroupDocs.Annotation for .NET. With these steps, you can now securely manage sensitive information within your documents.
## FAQ's
### Can I customize the appearance of the text redaction annotation?
Yes, you can customize various properties such as font color, fill color, and opacity to suit your requirements.
### Is there a trial version available before purchasing?
Yes, you can access a free trial version from the [website](https://releases.groupdocs.com/).
### How can I get support if I encounter any issues?
You can get support from the GroupDocs.Annotation community forum [here](https://forum.groupdocs.com/c/annotation/10).
### Do I need a temporary license for testing purposes?
Yes, you can obtain a temporary license from the [purchase page](https://purchase.groupdocs.com/temporary-license/) for testing.
### Can I add multiple annotations to a single document?
Absolutely, GroupDocs.Annotation allows you to add various types of annotations and multiple instances to a single document.
