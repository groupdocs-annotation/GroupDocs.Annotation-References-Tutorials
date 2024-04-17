---
title: Add Watermark Annotation to Document
linktitle: Add Watermark Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to add watermark annotations to your documents effortlessly using GroupDocs.Annotation for .NET. Enhance document clarity and security.
type: docs
weight: 28
url: /net/unlocking-annotation-power/add-watermark-annotation/
---
## Introduction
In this tutorial, we'll walk through the process of adding a watermark annotation to a document using GroupDocs.Annotation for .NET. Watermark annotations are useful for indicating the status of a document, marking it as confidential, or adding any other relevant information.

## Prerequisites

Before we begin, make sure you have the following:

1. GroupDocs.Annotation for .NET: You can download it from [here](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Ensure you have Visual Studio installed on your system.
3. Basic Knowledge of C#: Familiarity with C# programming language is necessary to understand and implement the code examples.

## Import Namespaces

Before we start coding, let's import the necessary namespaces:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Now, let's break down the process of adding a watermark annotation into multiple steps:

## Step 1: Define Output Path

First, we need to define the output path where the annotated document will be saved. We'll use the `Path` class from `System.IO` namespace to combine the output directory path with the filename.

```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
```

## Step 2: Initialize Annotator

Next, we'll initialize the annotator by providing the input document's path. This will allow us to add annotations to the document.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will go here
}
```

## Step 3: Create Watermark Annotation

Now, let's create a watermark annotation object with the desired properties such as angle, position, text, font color, opacity, etc.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Step 4: Add Watermark Annotation

Now, we'll add the watermark annotation to the document using the `Add` method of the annotator object.

```csharp
annotator.Add(watermark);
```

## Step 5: Save Document

Finally, we'll save the annotated document to the specified output path.

```csharp
annotator.Save(outputPath);
```

## Conclusion

In this tutorial, we learned how to add a watermark annotation to a document using GroupDocs.Annotation for .NET. Watermark annotations are a valuable tool for marking documents with relevant information or indicating their status.

## FAQ's

### Q: Can I customize the appearance of the watermark annotation?

A: Yes, you can customize various properties such as text, font size, color, opacity, position, etc., to tailor the watermark according to your requirements.

### Q: Is GroupDocs.Annotation for .NET compatible with different document formats?

A: Yes, GroupDocs.Annotation supports a wide range of document formats including PDF, Microsoft Word, Excel, PowerPoint, and image formats.

### Q: Can I add multiple annotations to a single document?

A: Absolutely, GroupDocs.Annotation allows you to add multiple annotations of different types to a single document, enabling comprehensive document markup.

### Q: Does GroupDocs.Annotation provide support for collaborative annotation?

A: Yes, GroupDocs.Annotation facilitates collaborative annotation by allowing users to add comments, replies, and annotations, fostering effective collaboration among team members.

### Q: Is there a trial version available for GroupDocs.Annotation for .NET?

A: Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
