---
title: Add Text Underline Annotation to Document
linktitle: Add Text Underline Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add text underline annotations to documents using GroupDocs.Annotation for .NET. Enhance collaboration and communication effortlessly.
type: docs
weight: 27
url: /net/unlocking-annotation-power/add-text-underline-annotation/
---
## Introduction
In this tutorial, we'll walk through the process of adding a text underline annotation to a document using GroupDocs.Annotation for .NET. Text underline annotations can be useful for emphasizing specific parts of a document, such as important passages or key points.
## Prerequisites
Before we begin, ensure that you have the following prerequisites installed:
1. GroupDocs.Annotation for .NET: Download and install GroupDocs.Annotation for .NET from [here](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Make sure you have .NET Framework installed on your system.

## Importing Namespaces
First, let's import the necessary namespaces into our project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Now, let's break down the example into multiple steps:
## Step 1: Define Output Path
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In this step, we define the output path where the annotated document will be saved.
## Step 2: Initialize Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Here, we initialize an instance of the `Annotator` class by providing the input document's path.
## Step 3: Create Underline Annotation
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // works supported only Word and PDF documents
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
This step involves creating an `UnderlineAnnotation` object with various properties such as font color, message, opacity, page number, background color, underline color, points, and replies.
## Step 4: Add Annotation to Document
```csharp
annotator.Add(underline);
```
Here, we add the underline annotation to the document.
## Step 5: Save Annotated Document
```csharp
annotator.Save(outputPath);
```
Finally, we save the annotated document to the specified output path.

## Conclusion
In this tutorial, we learned how to add a text underline annotation to a document using GroupDocs.Annotation for .NET. This powerful library provides various annotation options to enhance document collaboration and communication.
## FAQ's
### Can I customize the appearance of the underline annotation?
Yes, you can customize properties such as color, opacity, and position according to your requirements.
### Is GroupDocs.Annotation compatible with different document formats?
Yes, GroupDocs.Annotation supports a wide range of document formats including Word and PDF.
### Can I add multiple annotations to a single document?
Absolutely, GroupDocs.Annotation allows you to add multiple annotations of different types to a document.
### Is there a free trial available for GroupDocs.Annotation?
Yes, you can access the free trial version from [here](https://releases.groupdocs.com/).
### Where can I get support for GroupDocs.Annotation?
You can get support from the GroupDocs.Annotation community forum [here](https://forum.groupdocs.com/c/annotation/10).
