---
title: Add Text Strikeout Annotation to Document
linktitle: Add Text Strikeout Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add text strikeout annotations to documents using GroupDocs.Annotation for .NET. Enhance collaboration and document review processes efficiently.
type: docs
weight: 26
url: /net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Introduction
In this tutorial, we'll explore how to add a text strikeout annotation to a document using GroupDocs.Annotation for .NET. This library provides powerful tools for annotating various document types, enhancing collaboration and document review processes.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs.Annotation for .NET: Install the library. You can download it from [here](https://releases.groupdocs.com/annotation/net/).
2. Development Environment: Set up a suitable development environment for .NET development.
3. Document: Have a document ready to annotate, such as a PDF file.

## Importing Namespaces
First, import the necessary namespaces to access the functionalities of GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Now, let's break down the process of adding a text strikeout annotation into multiple steps:
## Step 1: Define Output Path
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
```
Here, we define the output path where the annotated document will be saved.
## Step 2: Initialize Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initialize the Annotator object by providing the path to the input document (PDF file in this case).
## Step 3: Create Strikeout Annotation
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
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
    }
};
```
Create a StrikeoutAnnotation object with desired properties such as message, opacity, page number, background color, points (coordinates), and replies.
## Step 4: Add Annotation
```csharp
annotator.Add(strikeout);
```
Add the created strikeout annotation to the document.
## Step 5: Save Document
```csharp
annotator.Save(outputPath);
```
Save the annotated document to the specified output path.

## Conclusion
In this tutorial, we learned how to add a text strikeout annotation to a document using GroupDocs.Annotation for .NET. This powerful library enables efficient document annotation, enhancing collaboration and document review processes.
## FAQ's
### Is GroupDocs.Annotation compatible with various document formats?
Yes, GroupDocs.Annotation supports a wide range of document formats including PDF, Word, Excel, PowerPoint, and more.
### Can I customize the appearance of annotations?
Absolutely, you can customize annotation properties such as color, opacity, font size, and more according to your requirements.
### Does GroupDocs.Annotation provide collaboration features?
Yes, GroupDocs.Annotation facilitates collaboration by allowing users to add comments, replies, and annotations to documents.
### Is there a free trial available?
Yes, you can avail of a free trial from [here](https://releases.groupdocs.com/).
### Where can I get support for GroupDocs.Annotation?
You can get support from the [GroupDocs.Annotation forum](https://forum.groupdocs.com/c/annotation/10).
