---
title: Add Text Replacement Annotation to Document
linktitle: Add Text Replacement Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add text replacement annotations to your .NET documents effortlessly using GroupDocs.Annotation for .NET. Enhance your document manipulation capabilities.
type: docs
weight: 24
url: /net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Introduction
In this tutorial, we will guide you through the process of adding a Text Replacement Annotation to your documents using GroupDocs.Annotation for .NET. This powerful library allows developers to manipulate and annotate various types of documents programmatically. By the end of this tutorial, you'll be equipped with the knowledge to seamlessly integrate text replacement annotations into your .NET applications.
## Prerequisites
Before we begin, ensure that you have the following prerequisites installed:
### 1. .NET Framework Installed
Make sure you have the .NET Framework installed on your development machine. You can download it from the Microsoft website.
### 2. GroupDocs.Annotation for .NET Library
Download and install the GroupDocs.Annotation for .NET library from the [website](https://releases.groupdocs.com/annotation/net/). This library provides the necessary tools and functionalities to work with annotations in various document formats.
### 3. Development Environment Setup
Set up your preferred development environment, such as Visual Studio, to create and run .NET applications.

## Import Namespaces
Before diving into the coding part, let's import the necessary namespaces required for working with GroupDocs.Annotation for .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Step 1: Define Output Path
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Here, we define the output path where the annotated document will be saved.
## Step 2: Initialize Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will be placed here
}
```
We initialize the Annotator object by specifying the input document ("input.pdf") within a using block to ensure proper disposal of resources.
## Step 3: Create Replacement Annotation
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    TextToReplace = "replaced text"
};
```
Here, we create a ReplacementAnnotation object with various properties such as creation date, font color, message, opacity, page number, background color, points (coordinates), replies (comments), and the text to replace.
## Step 4: Add Annotation
```csharp
annotator.Add(replacement);
```
We add the created replacement annotation to the annotator.
## Step 5: Save Document
```csharp
annotator.Save(outputPath);
```
Finally, we save the annotated document to the specified output path.
## Step 6: Display Success Message
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
A success message is displayed indicating that the document has been saved successfully.

## Conclusion
In this tutorial, we've covered the process of adding text replacement annotations to documents using GroupDocs.Annotation for .NET. By following the step-by-step guide and understanding the prerequisites, you can easily integrate this functionality into your .NET applications.
## FAQ's
### Can I annotate documents of different formats using GroupDocs.Annotation for .NET?
Yes, GroupDocs.Annotation for .NET supports annotating various document formats such as PDF, DOCX, PPTX, XLSX, and more.
### Is GroupDocs.Annotation for .NET suitable for both desktop and web applications?
Yes, GroupDocs.Annotation for .NET can be used in both desktop and web applications, providing flexibility for developers.
### Can I customize the appearance of annotations added using GroupDocs.Annotation for .NET?
Absolutely, you can customize the appearance of annotations by modifying properties such as color, opacity, font, etc.
### Does GroupDocs.Annotation for .NET offer support for collaborative annotation features?
Yes, GroupDocs.Annotation for .NET provides features for collaborative annotation, allowing multiple users to annotate documents simultaneously.
### Is there a free trial available for GroupDocs.Annotation for .NET?
Yes, you can avail of a free trial of GroupDocs.Annotation for .NET from the [website](https://releases.groupdocs.com/).
