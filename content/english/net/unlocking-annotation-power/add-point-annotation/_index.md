---
title: Add Point Annotation to Document
linktitle: Add Point Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add Point Annotation to PDFs using GroupDocs.Annotation for .NET. Step-by-step guide for seamless integration.
weight: 17
url: /net/unlocking-annotation-power/add-point-annotation/
---
## Introduction
GroupDocs.Annotation for .NET is a powerful tool that allows developers to add various types of annotations to documents programmatically. In this tutorial, we will focus on adding a Point Annotation to a document using C#.
## Prerequisites
Before we begin, make sure you have the following:
1. Basic understanding of C# programming language.
2. Visual Studio installed on your system.
3. GroupDocs.Annotation for .NET library installed. You can download it from [here](https://releases.groupdocs.com/annotation/net/).

## Importing Necessary Namespaces
To get started, you need to import the required namespaces into your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Step 1: Define Output Path
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In this step, we define the output path where the annotated document will be saved.
## Step 2: Initialize Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Here, we initialize the `Annotator` object with the input document ("input.pdf").
## Step 3: Create Point Annotation
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
In this step, we create a `PointAnnotation` object and specify its properties such as position, message, page number, and replies.
## Step 4: Add Annotation
```csharp
annotator.Add(point);
```
Here, we add the created point annotation to the document.
## Step 5: Save Document
```csharp
annotator.Save(outputPath);
```
Finally, we save the annotated document to the specified output path.

## Conclusion
In this tutorial, we've learned how to add a Point Annotation to a document using GroupDocs.Annotation for .NET. With this powerful library, you can enhance your document management applications by incorporating annotation functionalities.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
Yes, GroupDocs.Annotation for .NET supports a wide range of document formats including PDF, Microsoft Word, Excel, PowerPoint, and more.
### Can I customize the appearance of annotations?
Absolutely! GroupDocs.Annotation for .NET provides extensive options for customizing the appearance of annotations to suit your application's needs.
### Is there a free trial available for GroupDocs.Annotation for .NET?
Yes, you can avail of a free trial from [here](https://releases.groupdocs.com/).
### How can I get support for any issues or queries related to GroupDocs.Annotation for .NET?
You can get support from the GroupDocs.Annotation forum [here](https://forum.groupdocs.com/c/annotation/10).
### Can I obtain a temporary license for testing purposes?
Yes, you can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
