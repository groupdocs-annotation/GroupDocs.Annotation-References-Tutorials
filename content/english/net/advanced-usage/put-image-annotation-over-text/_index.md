---
title: Put Image Annotation over Text
linktitle: Put Image Annotation over Text
second_title: GroupDocs.Annotation .NET API
description: Learn how to add image annotations over text in .NET using GroupDocs.Annotation for efficient document management and collaboration.
type: docs
weight: 21
url: /net/advanced-usage/put-image-annotation-over-text/
---
## Introduction
In the world of .NET development, GroupDocs.Annotation offers a powerful solution for adding annotations to documents, making collaboration and document management more efficient. One common requirement is putting image annotations over text, which can be accomplished seamlessly using GroupDocs.Annotation for .NET.
## Prerequisites
Before diving into the process of putting image annotations over text using GroupDocs.Annotation for .NET, ensure you have the following:
1. GroupDocs.Annotation for .NET Library: Download and install the library from [here](https://releases.groupdocs.com/annotation/net/).
2. Development Environment: Set up a suitable development environment, such as Visual Studio or any other .NET IDE.
3. Document and Image Files: Prepare the document file (PDF, DOCX, etc.) and the image file you want to use for annotations.
4. Basic Understanding of C#: Familiarity with C# programming language is necessary to implement the code snippets provided in this tutorial.

## Import Namespaces
Before proceeding with the annotation process, ensure you import the necessary namespaces in your C# project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Step 1: Define Output Path
First, define the output path where the annotated document will be saved:
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "annotated_document.pdf");
```
## Step 2: Initialize Annotator
Initialize the `Annotator` object by providing the input document path:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will go here
}
```
## Step 3: Create Image Annotation
Create an `ImageAnnotation` object with the desired properties such as box dimensions, opacity, page number, image path, and z-index:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Step 4: Add Annotation
Add the image annotation to the document using the `Add` method of the `Annotator` object:
```csharp
annotator.Add(image);
```
## Step 5: Save Annotated Document
Save the annotated document to the specified output path:
```csharp
annotator.Save(outputPath);
```
## Step 6: Display Success Message
Display a success message with the path to the annotated document:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In conclusion, adding image annotations over text in .NET applications using GroupDocs.Annotation is a straightforward process. By following the step-by-step guide provided in this tutorial, you can efficiently annotate documents and enhance collaboration and document management capabilities in your .NET projects.
## FAQ's
### Can I annotate documents other than PDFs?
Yes, GroupDocs.Annotation supports various document formats such as DOCX, XLSX, PPTX, and more.
### Is there a free trial available for GroupDocs.Annotation?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get support for GroupDocs.Annotation?
You can get support from the GroupDocs.Annotation community forum [here](https://forum.groupdocs.com/c/annotation/10).
### Do I need a temporary license for testing purposes?
Yes, you can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/) for testing purposes.
### Can I customize the appearance of annotations?
Yes, GroupDocs.Annotation provides various options to customize the appearance of annotations such as color, opacity, font size, etc.
