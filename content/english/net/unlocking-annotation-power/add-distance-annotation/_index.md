---
title: Add Distance Annotation to Document
linktitle: Add Distance Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add distance annotations to documents using GroupDocs.Annotation for .NET. Enhance collaboration and communication effortlessly.
type: docs
weight: 12
url: /net/unlocking-annotation-power/add-distance-annotation/
---
## Introduction
In this tutorial, you will learn how to add a distance annotation to a document using GroupDocs.Annotation for .NET. Follow these steps to accomplish the task:
## Prerequisites

Ensure that you have the following prerequisites in place before proceeding:

- GroupDocs.Annotation for .NET Library: Download and install the GroupDocs.Annotation for .NET library from [this link](https://releases.groupdocs.com/annotation/net/).
- Document to Annotate: Prepare the document (e.g., PDF) to which you want to add the distance annotation.
- Development Environment: Set up your development environment with Visual Studio or any other IDE of your choice.

## Import Namespaces

Before you begin, make sure to include the necessary namespaces in your code. These namespaces are essential for accessing the required classes and methods.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Step 1: Initialize Annotator

Begin by initializing the `Annotator` object with the path to the document you want to annotate.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will go here
}
```

## Step 2: Create Distance Annotation

Now, create a `DistanceAnnotation` object and configure its properties such as box dimensions, message, opacity, pen color, etc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## Step 3: Add Annotation

Add the created distance annotation to the document using the `Add` method of the annotator object.

```csharp
annotator.Add(distance);
```

## Step 4: Save Document

Save the annotated document to the desired location on your system.

```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Step 5: Display Confirmation

Finally, display a message confirming the successful saving of the annotated document.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

Adding distance annotations to documents using GroupDocs.Annotation for .NET is a straightforward process. By following the steps outlined in this tutorial, you can enhance your documents with valuable annotations, facilitating better collaboration and communication.

## FAQ's

### Q: Can I customize the appearance of the distance annotation?

A: Yes, you can customize various properties such as color, opacity, line style, etc., to suit your requirements.

### Q: Does GroupDocs.Annotation support annotations on different types of documents?

A: Yes, GroupDocs.Annotation supports annotations on a wide range of document formats including PDF, Word, Excel, PowerPoint, and more.

### Q: Is there a free trial available for GroupDocs.Annotation?

A: Yes, you can access a free trial of GroupDocs.Annotation from [this link](https://releases.groupdocs.com/).

### Q: Where can I find the documentation for GroupDocs.Annotation for .NET?

A: You can refer to the detailed documentation available [here](https://reference.groupdocs.com/annotation/net/).

### Q: How can I get support or assistance with GroupDocs.Annotation?

A: You can seek support and assistance from the GroupDocs.Annotation community forum [here](https://forum.groupdocs.com/c/annotation/10).
