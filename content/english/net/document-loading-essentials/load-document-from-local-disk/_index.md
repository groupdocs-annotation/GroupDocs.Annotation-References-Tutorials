---
title: Load Document from Local Disk
linktitle: Load Document from Local Disk
second_title: GroupDocs.Annotation .NET API
description: Unlock the power of document annotation with GroupDocs.Annotation for .NET. Seamlessly integrate annotation features into your .NET applications.
type: docs
weight: 13
url: /net/document-loading-essentials/load-document-from-local-disk/
---
## Introduction
Unlocking the potential of document annotation has never been easier with GroupDocs.Annotation for .NET. This powerful tool empowers developers to integrate robust annotation features seamlessly into their .NET applications. In this comprehensive guide, we will walk you through the process of leveraging GroupDocs.Annotation for .NET to annotate documents step by step. Whether you're a seasoned developer or just starting, this tutorial will equip you with the knowledge to enhance document collaboration and streamline your workflow.
## Prerequisites
Before diving into document annotation with GroupDocs.Annotation for .NET, ensure you have the following prerequisites:
1. Basic Knowledge of C#: Familiarity with C# programming language fundamentals is essential.
2. Installation of GroupDocs.Annotation for .NET: Download and install GroupDocs.Annotation for .NET from [here](https://releases.groupdocs.com/annotation/net/).
3. Development Environment: Set up a development environment with Visual Studio or any compatible IDE.

## Import Namespaces
To begin annotating documents with GroupDocs.Annotation for .NET, import the necessary namespaces into your project:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Step 1: Load Document from Local Disk
First, you need to load the document from your local disk. Use the following code snippet:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Step 2: Define Annotation Area
Next, define the annotation area. In this example, we'll create an AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Step 3: Save Document with Annotations
After annotating the document, save it with the annotations:
```csharp
    annotator.Save(outputPath);
}
```
## Step 4: Display Success Message
Finally, display a success message with the output path:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion
In conclusion, GroupDocs.Annotation for .NET provides a robust solution for integrating document annotation capabilities into your .NET applications. By following this step-by-step guide, you can effortlessly annotate documents and enhance collaboration in your projects.
## FAQ's
### Can I try GroupDocs.Annotation for .NET before purchasing?
Yes, you can download a free trial from [here](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Annotation for .NET?
You can access the documentation [here](https://reference.groupdocs.com/annotation/net/).
### How can I obtain a temporary license for GroupDocs.Annotation for .NET?
You can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Is support available for GroupDocs.Annotation for .NET?
Yes, you can find support on the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10).
### Where can I purchase GroupDocs.Annotation for .NET?
You can purchase GroupDocs.Annotation for .NET [here](https://purchase.groupdocs.com/buy).
