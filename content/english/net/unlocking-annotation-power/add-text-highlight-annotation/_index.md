---
title: Add Text Highlight Annotation to Document
linktitle: Add Text Highlight Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add text highlight annotations to documents using GroupDocs.Annotation for .NET. Enhance collaboration and productivity with this comprehensive.
type: docs
weight: 22
url: /net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Introduction
In the realm of document management and collaboration, GroupDocs.Annotation for .NET emerges as a robust solution, empowering developers to seamlessly integrate text highlight annotations into their applications. This tutorial serves as a comprehensive guide to adding text highlight annotations to documents using GroupDocs.Annotation for .NET. Through step-by-step instructions and detailed explanations, you will gain proficiency in harnessing the capabilities of this powerful library.
## Prerequisites
Before delving into the implementation of text highlight annotations, ensure that you have the following prerequisites in place:
1. Environment Setup: Have a suitable development environment configured for .NET development.
2. Installation of GroupDocs.Annotation for .NET: Download and install GroupDocs.Annotation for .NET from the provided [download link](https://releases.groupdocs.com/annotation/net/).
3. Familiarity with C#: Basic understanding of C# programming language.
4. Document to Annotate: Prepare a document (e.g., PDF) that you intend to annotate.

## Import Namespaces
To begin, import the necessary namespaces in your C# code to utilize the functionalities of GroupDocs.Annotation for .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Now, let's break down the process of adding text highlight annotations into multiple steps:
## Step 1: Define Output Path
Specify the output path where the annotated document will be saved:
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Create an instance of the `Annotator` class, passing the document filename as a parameter:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Step 3: Create Highlight Annotation
Instantiate a `HighlightAnnotation` object and configure its properties:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## Step 4: Add Annotation
Add the created highlight annotation to the document:
```csharp
annotator.Add(highlight);
```
## Step 5: Save Annotated Document
Save the annotated document to the specified output path:
```csharp
annotator.Save(outputPath);
```

## Conclusion
In conclusion, GroupDocs.Annotation for .NET offers a streamlined approach to incorporate text highlight annotations into documents. By following the steps outlined in this tutorial, developers can seamlessly enhance document collaboration and productivity within their applications.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation for .NET supports various document formats, including PDF, Word, Excel, and more. Refer to the documentation for the complete list.
### Can annotations be customized according to specific requirements?
Yes, developers have full control over the properties and appearance of annotations, allowing for customization to meet diverse needs.
### Is there a free trial available for GroupDocs.Annotation for .NET?
Yes, you can explore the features of GroupDocs.Annotation for .NET by accessing the free trial from the provided [link](https://releases.groupdocs.com/).
### How can I get support for any issues or queries related to GroupDocs.Annotation for .NET?
For support and assistance, you can visit the GroupDocs.Annotation forum [here](https://forum.groupdocs.com/c/annotation/10).
### What licensing options are available for GroupDocs.Annotation for .NET?
GroupDocs.Annotation for .NET offers various licensing options, including temporary licenses for testing purposes and commercial licenses for production environments. Visit the purchase page [here](https://purchase.groupdocs.com/buy) for more details.
