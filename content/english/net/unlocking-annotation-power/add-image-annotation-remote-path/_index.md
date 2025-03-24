---
title: Add Image Annotation to Document (Remote Path)
linktitle: Add Image Annotation to Document (Remote Path)
second_title: GroupDocs.Annotation .NET API
description: Learn how to add image annotations to documents using GroupDocs.Annotation for .NET. Enhance document management with powerful annotation capabilities.
weight: 15
url: /net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## Introduction
In this tutorial, we'll walk through the process of adding image annotations to a document using GroupDocs.Annotation for .NET. This library provides powerful tools for annotating various types of documents programmatically.
## Prerequisites
Before we begin, make sure you have the following:
1. GroupDocs.Annotation for .NET: Download and install the library from [here](https://releases.groupdocs.com/annotation/net/).
2. Development Environment: Ensure you have a working development environment set up for .NET development.
3. Document: Prepare the document you want to annotate. For this tutorial, we'll assume you have a PDF document named `input.pdf`.
4. Image for Annotation: Choose the image you want to use for annotation. Ensure you have the image URL or local path ready.

## Import Namespaces
Before we start coding, let's import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Step 1: Set Output Path
First, define the output path where the annotated document will be saved.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Create an instance of the `Annotator` class and specify the input document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotation code will go here
}
```
## Step 3: Add Image Annotation
Now, let's add the image annotation to the document. We'll specify the properties of the image annotation such as position, opacity, page number, and image path.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Specify the position of the annotation
    CreatedOn = DateTime.Now, // Set the creation date
    Opacity = 0.7, // Set opacity (0 to 1)
    PageNumber = 0, // Specify the page number
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Provide the URL of the image
};
annotator.Add(image); // Add the image annotation
```
## Step 4: Save Document
Save the annotated document to the specified output path.
```csharp
annotator.Save(outputPath);
```
## Step 5: Display Output Path
Inform the user about the successful document save operation and display the output path.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In this tutorial, we've learned how to add image annotations to a document using GroupDocs.Annotation for .NET. By following these steps, you can enhance your document management applications with powerful annotation capabilities.
## FAQ's
### Can GroupDocs.Annotation be used with other document formats besides PDF?
Yes, GroupDocs.Annotation supports various document formats including Word, Excel, PowerPoint, and more.
### Is GroupDocs.Annotation compatible with .NET Core?
Yes, GroupDocs.Annotation is compatible with both .NET Framework and .NET Core.
### Can I customize the appearance of annotations?
Yes, you can customize the appearance of annotations such as color, opacity, and size.
### Does GroupDocs.Annotation support collaborative annotation features?
Yes, GroupDocs.Annotation offers collaborative annotation features for real-time collaboration on documents.
### Is there a trial version available for testing?
Yes, you can get a free trial of GroupDocs.Annotation from [here](https://releases.groupdocs.com/).
