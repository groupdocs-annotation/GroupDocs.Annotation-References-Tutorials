---
title: Add Search Text Fragment Annotation to Document
linktitle: Add Search Text Fragment Annotation to Document
second_title: GroupDocs.Annotation .NET API
description: Explore the power of GroupDocs.Annotation for .NET and effortlessly add document annotation capabilities to your applications.
weight: 20
url: /net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## Introduction
In the realm of .NET development, GroupDocs.Annotation stands out as a powerful tool for annotating documents seamlessly. Whether you're a seasoned developer or just stepping into the world of .NET, this comprehensive tutorial will walk you through the essentials of using GroupDocs.Annotation for .NET, from importing namespaces to mastering the intricacies of adding search text fragment annotations to your documents.
## Introduction
GroupDocs.Annotation for .NET empowers developers to incorporate document annotation capabilities into their applications effortlessly. With its intuitive API and robust features, developers can annotate various document formats, including PDFs, Microsoft Office documents, images, and more.
## Prerequisites
Before diving into GroupDocs.Annotation for .NET, ensure you have the following prerequisites in place:

## Import Namespaces
Firstly, import the necessary namespaces to access GroupDocs.Annotation classes and methods in your .NET project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Step 1: Define Output Path
Begin by defining the output path where the annotated document will be saved:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Initialize Annotator
Next, initialize an instance of the `Annotator` class by providing the path to the document you want to annotate:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Step 3: Create Search Text Fragment Annotation
Create a `SearchTextFragment` object with the desired properties, such as text to search for, font size, font family, font color, and background color:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Step 4: Add Annotation
Add the created search text fragment annotation to the document using the `Add` method of the annotator:
```csharp
annotator.Add(searchText);
```
## Step 5: Save Annotated Document
Save the annotated document to the specified output path:
```csharp
annotator.Save(outputPath);
```
## Step 6: Display Success Message
Inform the user that the document has been successfully saved:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In conclusion, GroupDocs.Annotation for .NET simplifies the process of adding annotations to documents, enhancing collaboration and document review processes. By following the steps outlined in this guide, you can seamlessly integrate document annotation capabilities into your .NET applications.
## FAQ's
### Is GroupDocs.Annotation compatible with all document formats?
Yes, GroupDocs.Annotation supports a wide range of document formats, including PDFs, Microsoft Office documents, images, and more.
### Can I customize the appearance of annotations?
Absolutely! GroupDocs.Annotation provides extensive customization options for annotations, allowing you to adjust properties such as font size, color, and style.
### Is there a free trial available for GroupDocs.Annotation?
Yes, you can access a free trial of GroupDocs.Annotation to explore its features and capabilities before making a purchase [here](https://releases.groupdocs.com/)..
### Where can I find support for GroupDocs.Annotation?
For support and assistance with GroupDocs.Annotation, you can visit the GroupDocs [forum](https://forum.groupdocs.com/c/annotation/10) dedicated to annotation-related queries and discussions.
### How do I obtain a temporary license for GroupDocs.Annotation?
You can acquire a temporary license for GroupDocs.Annotation through the GroupDocs [website](https://purchase.groupdocs.com/temporary-license/), enabling you to evaluate the product fully.
