---
title: Add Text Squiggly Annotation to Document
linktitle: Add Text Squiggly Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to effortlessly add text squiggly annotations to documents using Groupdocs.Annotation for .NET. Enhance collaboration and document review processes.
type: docs
weight: 25
url: /net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Introduction

Groupdocs.Annotation for .NET is a versatile library that enables developers to integrate robust annotation capabilities into their .NET applications effortlessly. Whether you're working with PDFs, Word documents, or other popular file formats, Groupdocs.Annotation provides a seamless solution for annotating and enhancing document collaboration.

## Prerequisites

Before diving into the tutorial, ensure that you have the following prerequisites in place:

## Import Namespaces

Make sure to import the necessary namespaces to access the functionalities provided by Groupdocs.Annotation for .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Now that we have the prerequisites covered, let's break down the process of adding text squiggly annotations into multiple steps.

## Step 1: Define Output Path

Define the path where the annotated document will be saved.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Step 2: Initialize Annotator

Initialize the Annotator object by providing the input document path.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code goes here
}
```

## Step 3: Create Squiggly Annotation

Create a SquigglyAnnotation object and specify its properties.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Add the created squiggly annotation to the document.

```csharp
annotator.Add(squiggly);
```

## Step 5: Save Document

Save the annotated document to the specified output path.

```csharp
annotator.Save(outputPath);
```

## Step 6: Display Confirmation

Display a message confirming the successful saving of the annotated document.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

In conclusion, Groupdocs.Annotation for .NET provides developers with a robust set of tools for integrating document annotation functionalities into their .NET applications seamlessly. By following this step-by-step guide, you can effortlessly add text squiggly annotations to your documents, enhancing collaboration and document review processes.

## FAQ's

### Q: Can Groupdocs.Annotation support annotation on various file formats?##

A: Yes, Groupdocs.Annotation supports annotation on a wide range of file formats, including PDFs, Word documents, Excel sheets, and more.

### Q: Is Groupdocs.Annotation compatible with both desktop and web applications?##

A: Absolutely! Groupdocs.Annotation can be seamlessly integrated into both desktop and web applications, offering flexibility and versatility.

### Q: Are there any licensing options available for Groupdocs.Annotation?##

A: Yes, Groupdocs.Annotation offers flexible licensing options tailored to suit individual or enterprise needs, including temporary licenses for trial purposes.

### Q: Can annotations created using Groupdocs.Annotation be customized?##

A: Certainly! Groupdocs.Annotation provides extensive customization options for annotations, allowing developers to tailor annotations to their specific requirements.

### Q: Does Groupdocs.Annotation offer support and documentation for developers?##

A: Indeed! Groupdocs.Annotation provides comprehensive documentation and dedicated support forums to assist developers in utilizing its features effectively.
