---
title: Load Document from URL
linktitle: Load Document from URL
second_title: GroupDocs.Annotation .NET API
description: Learn how to annotate PDF documents programmatically using GroupDocs.Annotation for .NET. Step-by-step tutorial with code examples.
type: docs
weight: 15
url: /net/document-loading-essentials/load-document-from-url/
---
## Introduction
GroupDocs.Annotation for .NET is a feature-rich library that enables developers to add annotation capabilities to their .NET applications effortlessly. With GroupDocs.Annotation, you can annotate PDF documents programmatically, allowing users to highlight text, add comments, draw shapes, and more. This tutorial will walk you through the steps of loading a document from a URL, adding annotations, and saving the annotated document using GroupDocs.Annotation for .NET.
## Prerequisites
Before you begin, ensure that you have the following prerequisites:
1. Visual Studio: Make sure you have Visual Studio installed on your development machine.
2. GroupDocs.Annotation for .NET: Download and install GroupDocs.Annotation for .NET from the [website](https://releases.groupdocs.com/annotation/net/).
3. Basic Knowledge of C#: Familiarize yourself with the C# programming language.
4. Internet Connection: You'll need an internet connection to access external resources and download sample files.

## Import Namespaces
First, let's import the necessary namespaces in your C# project:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Step 1: Load Document from URL
To annotate a PDF document from a URL, follow these steps:
### Step 1.1: Define Output Path
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
```
### Step 1.2: Specify URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Step 1.3: Load Document
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Add annotations here
    annotator.Save(outputPath);
}
```
## Step 2: Add Annotations
Now, let's add annotations to the loaded document. In this example, we'll add an area annotation:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Step 3: Save Annotated Document
Finally, save the annotated document to the specified output path:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In this tutorial, we've learned how to annotate PDF documents using GroupDocs.Annotation for .NET. By following the step-by-step guide, you can seamlessly integrate annotation functionality into your .NET applications, empowering users to collaborate effectively on PDF files.

## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all .NET frameworks?
Yes, GroupDocs.Annotation for .NET is compatible with various .NET frameworks, including .NET Framework, .NET Core, and .NET Standard.
### Can I customize the appearance of annotations?
Absolutely! GroupDocs.Annotation for .NET provides extensive customization options, allowing you to modify the appearance and behavior of annotations according to your requirements.
### Is there a free trial available for GroupDocs.Annotation for .NET?
Yes, you can download a free trial of GroupDocs.Annotation for .NET from the [website](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Annotation for .NET?
If you encounter any technical issues or have questions about GroupDocs.Annotation for .NET, you can seek assistance from the [support forum](https://forum.groupdocs.com/c/annotation/10).
### Where can I purchase a license for GroupDocs.Annotation for .NET?
You can purchase a license for GroupDocs.Annotation for .NET from the [purchase page](https://purchase.groupdocs.com/buy).
