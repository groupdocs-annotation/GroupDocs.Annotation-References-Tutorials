---
title: Get List of Annotations using Version Key
linktitle: Get List of Annotations using Version Key
second_title: GroupDocs.Annotation .NET API
description: Enhance your .NET applications with GroupDocs.Annotation for seamless document annotation. Follow our step-by-step guide for effective integration.
weight: 18
url: /net/advanced-usage/get-list-annotations-version-key/
---
## Introduction
In the world of .NET development, managing and manipulating documents efficiently is paramount. Whether it's annotating PDFs, collaborating on Word documents, or marking up Excel sheets, having the right tools can streamline workflows and boost productivity. GroupDocs.Annotation for .NET is one such tool that empowers developers to annotate and manipulate documents seamlessly within their .NET applications.
## Prerequisites
Before diving into the intricacies of using GroupDocs.Annotation for .NET, ensure you have the following prerequisites in place:
### 1. .NET Development Environment Setup
Ensure you have a working .NET development environment set up on your machine. This includes having the .NET SDK installed, along with an Integrated Development Environment (IDE) such as Visual Studio.
### Setting up .NET SDK
1. Visit the .NET website and download the latest version of the .NET SDK.
2. Follow the installation instructions provided for your operating system.
3. Verify the installation by opening a command prompt and typing `dotnet --version`.
### 2. GroupDocs.Annotation Installation
To use GroupDocs.Annotation for .NET, you need to install the necessary packages into your project. You can download the required package from the GroupDocs website or utilize package managers like NuGet.
### Installing via NuGet Package Manager
1. Open your project in Visual Studio.
2. Right-click on your project in the Solution Explorer and select "Manage NuGet Packages".
3. Search for "GroupDocs.Annotation" and install the latest version available.

## Import Namespaces
Before utilizing GroupDocs.Annotation in your .NET project, make sure to import the required namespaces to access its classes and methods seamlessly.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Step 1: Initialize Annotator
First, initialize the Annotator object by providing the path to the document you want to annotate.
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Annotation operations will be performed here
}
```
## Step 2: Get List of Annotations using Version Key
Once the annotator is initialized, you can retrieve a list of annotations using a specific version key.
```csharp
List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
```

## Conclusion
In conclusion, GroupDocs.Annotation for .NET offers a powerful set of tools for annotating documents within .NET applications. By following the steps outlined in this guide, you can seamlessly integrate document annotation functionality into your projects, enhancing collaboration and productivity.
## FAQ's
### Can I annotate documents other than PDFs using GroupDocs.Annotation for .NET?
Yes, GroupDocs.Annotation supports a variety of document formats including Word, Excel, and PowerPoint in addition to PDFs.
### Is there a free trial available for GroupDocs.Annotation for .NET?
Yes, you can access a free trial of GroupDocs.Annotation for .NET by visiting the [website](https://releases.groupdocs.com/annotation/net/).
### How can I get support for any issues or queries related to GroupDocs.Annotation?
You can seek support by visiting the GroupDocs.Annotation forum or contacting their support team directly.
### Can I purchase a temporary license for GroupDocs.Annotation for testing purposes?
Yes, temporary licenses are available for purchase to facilitate testing and evaluation of the product.
### Where can I find comprehensive documentation for GroupDocs.Annotation for .NET?
You can refer to the documentation available on the GroupDocs website for detailed guidance on using the product [here]( https://tutorials.groupdocs.com/annotation/net/).
