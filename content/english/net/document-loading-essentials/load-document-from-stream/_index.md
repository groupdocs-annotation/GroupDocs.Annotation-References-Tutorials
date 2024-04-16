---
title: Load Document from Stream
linktitle: Load Document from Stream
second_title: GroupDocs.Annotation .NET API
description: Learn how to annotate documents in .NET effortlessly with GroupDocs.Annotation. Enhance collaboration and productivity.
type: docs
weight: 14
url: /net/document-loading-essentials/load-document-from-stream/
---
## Introduction
GroupDocs.Annotation for .NET is a powerful library that empowers developers to integrate document annotation capabilities into their .NET applications effortlessly. Whether you're building a document management system, a collaboration platform, or an e-learning application, GroupDocs.Annotation provides a versatile set of tools to annotate PDFs, Word documents, Excel sheets, and more.
## Prerequisites
Before we dive into the annotation process, ensure you have the following prerequisites:
1. Installation of GroupDocs.Annotation for .NET: Download and install GroupDocs.Annotation for .NET from [here](https://releases.groupdocs.com/annotation/net/).
2. Basic Understanding of C# Programming: Familiarity with C# programming language and .NET framework is essential.
3. Development Environment Setup: Set up your preferred development environment with .NET framework support.

## Importing Namespaces
To begin annotating documents using GroupDocs.Annotation for .NET, import the necessary namespaces into your C# project:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Now, let's break down the annotation process into multiple steps:
## Step 1: Load Document from Stream
Firstly, you need to load the document from a stream. Here's how you can achieve it:
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator(File.OpenRead("input.pdf")))
{
```
## Step 2: Add Annotations
Next, you can add annotations to the document. Let's create an area annotation as an example:
```csharp
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
```
## Step 3: Save Document with Annotations
After adding annotations, save the annotated document:
```csharp
	annotator.Save(File.Create(outputPath));
}
```
## Step 4: Display Confirmation Message
Finally, display a message confirming the successful saving of the annotated document:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In conclusion, GroupDocs.Annotation for .NET provides a comprehensive solution for document annotation within .NET applications. By following the steps outlined in this tutorial, you can seamlessly integrate document annotation functionality into your projects, enhancing collaboration and productivity.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation supports a wide range of document formats, including PDF, Word, Excel, PowerPoint, and more.
### Can annotations be customized according to specific requirements?
Yes, GroupDocs.Annotation offers extensive customization options for annotations, including colors, shapes, and properties.
### Does GroupDocs.Annotation support collaborative annotation features?
Yes, GroupDocs.Annotation facilitates collaborative annotation, allowing multiple users to annotate documents simultaneously.
### Is technical support available for GroupDocs.Annotation users?
Yes, GroupDocs provides dedicated technical support through its forum. Visit [here](https://forum.groupdocs.com/c/annotation/10) for support.
### Can I try GroupDocs.Annotation before purchasing?
Yes, you can explore GroupDocs.Annotation through a free trial available [here](https://releases.groupdocs.com/).
