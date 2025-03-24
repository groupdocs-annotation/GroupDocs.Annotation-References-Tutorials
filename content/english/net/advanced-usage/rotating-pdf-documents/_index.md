---
title: Rotating PDF Documents
linktitle: Rotating PDF Documents
second_title: GroupDocs.Annotation .NET API
description: Learn how to rotate PDF documents effortlessly using Groupdocs.Annotation for .NET. Improve document management efficiency.
weight: 22
url: /net/advanced-usage/rotating-pdf-documents/
---

# Rotating PDF Documents

## Introduction
Rotating PDF documents can be a crucial task when dealing with files that need to be viewed or processed differently. In this tutorial, we'll explore how to rotate PDF documents step by step using Groupdocs.Annotation for .NET.
## Prerequisites
Before diving into the tutorial, make sure you have the following prerequisites:
1. Groupdocs.Annotation for .NET Library: Ensure that you have downloaded and installed the Groupdocs.Annotation for .NET library. You can download it from [here](https://releases.groupdocs.com/annotation/net/).
2. Basic Knowledge of C# Programming: This tutorial assumes you have a basic understanding of C# programming language and how to work with .NET libraries.

## Import Namespaces
First, you need to import the necessary namespaces into your C# project to access the functionality provided by the Groupdocs.Annotation library.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Step 1: Load the PDF Document
Begin by loading the PDF document that you want to rotate using the `Annotator` class.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Step 2: Set Rotation and Process Pages
Specify the rotation angle and the pages you want to rotate. In this example, we'll rotate the first page by 90 degrees clockwise.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Step 3: Save the Rotated Document
Save the rotated PDF document with the specified changes.
```csharp
annotator.Save("result.pdf");
```
## Step 4: Display Confirmation
Inform the user that the document has been successfully rotated.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusion
Rotating PDF documents is a fundamental operation, and with Groupdocs.Annotation for .NET, it becomes simple and efficient. By following the steps outlined in this tutorial, you can easily rotate PDF files according to your requirements.
## FAQ's
### Can I rotate multiple pages in a PDF document using Groupdocs.Annotation for .NET?
Yes, you can specify multiple pages to rotate by adjusting the `ProcessPages` property accordingly.
### Is Groupdocs.Annotation for .NET compatible with all versions of .NET framework?
Groupdocs.Annotation for .NET supports a wide range of .NET framework versions, ensuring compatibility for most development environments.
### Does Groupdocs.Annotation for .NET provide options for rotating PDF documents in different directions?
Yes, you can rotate PDF documents clockwise, counterclockwise, or at custom angles based on your requirements.
### Can I integrate Groupdocs.Annotation for .NET into my existing document management system?
Absolutely, Groupdocs.Annotation for .NET offers seamless integration options, allowing you to enhance document management capabilities effortlessly.
### Is there a trial version available for Groupdocs.Annotation for .NET?
Yes, you can get a free trial version from [here](https://releases.groupdocs.com/).
