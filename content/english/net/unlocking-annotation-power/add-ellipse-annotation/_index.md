---
title: Add Ellipse Annotation to Document
linktitle: Add Ellipse Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add ellipse annotations to documents in .NET using GroupDocs.Annotation. Enhance collaboration and communication effortlessly.
type: docs
weight: 13
url: /net/unlocking-annotation-power/add-ellipse-annotation/
---
## Introduction
In this tutorial, you'll learn how to add an ellipse annotation to a document using GroupDocs.Annotation for .NET. This step-by-step guide will walk you through the process, ensuring that you understand each step clearly.
## Prerequisites
Before you begin, make sure you have the following:
1. GroupDocs.Annotation for .NET: Make sure you have downloaded and installed GroupDocs.Annotation for .NET. You can download it from [here](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): You'll need an IDE installed on your system, such as Visual Studio, to write and execute the code.

## Import Namespaces
First, import the necessary namespaces to your project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Step 1: Set Output Path
Define the output path where the annotated document will be saved:
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Initialize the annotator by providing the input document path:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Step 3: Create Ellipse Annotation
Create an instance of the `EllipseAnnotation` class and set its properties:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## Step 4: Add Annotation
Add the ellipse annotation to the document:
```csharp
annotator.Add(ellipse);
```
## Step 5: Save Document
Save the annotated document to the output path:
```csharp
annotator.Save(outputPath);
```

## Conclusion
Congratulations! You've successfully added an ellipse annotation to a document using GroupDocs.Annotation for .NET. You can now integrate this functionality into your .NET applications to enhance document collaboration and communication.
## FAQ's
### Can I customize the appearance of the ellipse annotation?
Yes, you can customize various properties such as background color, border color, opacity, etc., according to your requirements.
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation for .NET supports a wide range of document formats including PDF, DOCX, PPTX, XLSX, and more.
### Can I add multiple annotations to a single document?
Yes, you can add multiple annotations including ellipses, rectangles, text, etc., to a single document.
### Is there a trial version available for testing purposes?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/) to evaluate its features.
### Where can I get technical support for GroupDocs.Annotation for .NET?
You can get technical support from the GroupDocs.Annotation community forum [here](https://forum.groupdocs.com/c/annotation/10).
