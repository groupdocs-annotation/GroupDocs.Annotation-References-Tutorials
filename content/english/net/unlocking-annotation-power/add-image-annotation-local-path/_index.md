---
title: Add Image Annotation to Document (Local Path)
linktitle: Add Image Annotation to Document (Local Path)
second_title: GroupDocs.Annotation .NET API
description: Learn how to add image annotations to documents using GroupDocs.Annotation for .NET. Enhance document processing capabilities with ease.
weight: 14
url: /net/unlocking-annotation-power/add-image-annotation-local-path/
---

# Add Image Annotation to Document (Local Path)

## Introduction
GroupDocs.Annotation for .NET is a powerful library that allows developers to add various types of annotations to documents programmatically. In this tutorial, we will learn how to add image annotations to a document using a local path.
## Prerequisites
Before we begin, make sure you have the following prerequisites:
1. Basic knowledge of C# programming language.
2. Visual Studio installed on your system.
3. GroupDocs.Annotation for .NET library installed or tutorialsd in your project.
4. An input document (e.g., PDF) and an image file for annotation.
## Import Namespaces
First, you need to import the necessary namespaces to your C# file. These namespaces provide access to the classes and methods required for working with GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Step 1: Define Output Path
Define the output path where the annotated document will be saved.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Initialize the annotator by providing the path to the input document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code goes here
}
```
## Step 3: Create Image Annotation
Create an instance of the `ImageAnnotation` class and specify its properties such as position, opacity, page number, and image path.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Step 4: Add Annotation
Add the created image annotation to the document using the `Add` method of the annotator.
```csharp
annotator.Add(image);
```
## Step 5: Save Document
Save the annotated document to the output path.
```csharp
annotator.Save(outputPath);
```
## Step 6: Display Output Path
Display a message indicating the successful saving of the document and the location of the output file.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In this tutorial, we have learned how to add image annotations to a document using GroupDocs.Annotation for .NET. By following these simple steps, you can enhance your document processing capabilities with powerful annotation features.
## FAQ's
### Can I annotate documents other than PDF?
Yes, GroupDocs.Annotation supports various document formats including Word, Excel, PowerPoint, and more.
### Is GroupDocs.Annotation compatible with .NET Core?
Yes, GroupDocs.Annotation is compatible with both .NET Framework and .NET Core.
### Can I customize the appearance of annotations?
Absolutely, you can customize the appearance, size, color, and other properties of annotations according to your requirements.
### Does GroupDocs.Annotation provide support for collaborative annotation?
Yes, GroupDocs.Annotation offers collaborative annotation features that enable multiple users to annotate documents simultaneously.
### Where can I find additional help or support?
You can visit the GroupDocs.Annotation forum for assistance and support from the community.
