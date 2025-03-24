---
title: Add Polyline Annotation to Document
linktitle: Add Polyline Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add polyline annotations to documents using GroupDocs.Annotation for .NET. Enhance collaboration and document review processes effortlessly.
weight: 18
url: /net/unlocking-annotation-power/add-polyline-annotation/
---
## Introduction
GroupDocs.Annotation for .NET is a powerful tool that allows developers to annotate PDF and Microsoft Office documents programmatically. Among its features is the ability to add polyline annotations to documents, enhancing collaboration and document review processes.
## Prerequisites
Before proceeding with this tutorial, make sure you have the following:
- Visual Studio installed on your system.
- Basic knowledge of C# programming language.
- GroupDocs.Annotation for .NET library installed. You can download it from [here](https://releases.groupdocs.com/annotation/net/).

## Import Namespaces
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Step 1: Define Output Path
First, define the output path where the annotated document will be saved.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Initialize the annotator by providing the input document name.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Step 3: Create Polyline Annotation Object
Create a polyline annotation object and set its properties such as position, message, opacity, pen color, pen style, and pen width.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Step 4: Add Polyline Annotation
Add the polyline annotation to the document using the annotator object.
```csharp
annotator.Add(polyline);
```
## Step 5: Save Document
Save the annotated document to the specified output path.
```csharp
annotator.Save(outputPath);
```
## Step 6: Display Success Message
Display a message confirming the successful saving of the document.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In this tutorial, we have learned how to add a polyline annotation to a document using GroupDocs.Annotation for .NET. This feature enhances collaboration and document review processes, making it easier for users to communicate feedback and suggestions effectively.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation for .NET supports popular document formats such as PDF and Microsoft Office formats including Word, Excel, and PowerPoint.
### Can I customize the appearance of annotations?
Yes, you can customize various properties of annotations such as color, opacity, style, and width to suit your requirements.
### Does GroupDocs.Annotation for .NET offer a free trial?
Yes, you can avail of a free trial of GroupDocs.Annotation for .NET by visiting [this link](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Annotation for .NET?
You can find the documentation for GroupDocs.Annotation for .NET [here](https://tutorials.groupdocs.com/annotation/net/).
### How can I get support for any issues or queries related to GroupDocs.Annotation for .NET?
You can get support by visiting the GroupDocs.Annotation forum [here](https://forum.groupdocs.com/c/annotation/10).
