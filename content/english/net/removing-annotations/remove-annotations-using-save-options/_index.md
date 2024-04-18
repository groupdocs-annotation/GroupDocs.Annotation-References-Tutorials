---
title: Remove Annotations Using Save Options in .NET
linktitle: Remove Annotations Using Save Options in .NET
second_title: GroupDocs.Annotation .NET API
description: Learn how to remove annotations from PDF and other documents in .NET using GroupDocs.Annotation. Step-by-step guide with code examples.
type: docs
weight: 14
url: /net/removing-annotations/remove-annotations-using-save-options/
---
## Introduction

GroupDocs.Annotation for .NET is a powerful tool that allows developers to add annotation functionality to their .NET applications with ease. Whether you're working on a document management system, collaboration platform, or any other application that involves document processing, GroupDocs.Annotation provides a comprehensive set of features to annotate PDF and other document formats seamlessly.

## Prerequisites

Before diving into the world of annotating documents using GroupDocs.Annotation for .NET, make sure you have the following prerequisites in place:

### 1. Install GroupDocs.Annotation for .NET

Begin by downloading and installing GroupDocs.Annotation for .NET. You can download the latest version from the [download page](https://releases.groupdocs.com/annotation/net/).

## Importing Namespaces

To start using GroupDocs.Annotation in your .NET project, you need to import the necessary namespaces. Here are the namespaces you'll commonly use:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Now, let's walk through the process of removing annotations from a document using the Save Options feature in .NET:

## Step 1: Define Output Path

First, define the output path where the document with removed annotations will be saved. You can use the `Path.Combine` method to combine the directory path with the output file name.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Step 2: Initialize Annotator

Next, initialize an instance of the `Annotator` class by providing the path to the document containing annotations.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Annotation removal code will go here
}
```

## Step 3: Save Document with Annotation Removal

Now, use the `Save` method of the `Annotator` class along with the `SaveOptions` to save the document with removed annotations. In the `SaveOptions`, set the `AnnotationTypes` property to `AnnotationType.None` to remove all annotations.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Step 4: Display Success Message

Finally, display a success message indicating that the document has been saved successfully with annotations removed.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusion

In conclusion, GroupDocs.Annotation for .NET simplifies the process of removing annotations from documents. By following the step-by-step guide outlined above, developers can seamlessly integrate annotation removal functionality into their .NET applications.

## FAQ's

### Q: Can GroupDocs.Annotation remove annotations from other document formats besides PDF?

A: GroupDocs.Annotation supports various document formats, including PDF, Word, Excel, and PowerPoint, allowing you to remove annotations from a wide range of documents.

### Q: Is GroupDocs.Annotation easy to integrate into existing .NET projects?

A: Yes, GroupDocs.Annotation provides a simple API and comprehensive documentation, making it easy for developers to integrate annotation features into their .NET applications.

### Q: Does GroupDocs.Annotation support selective removal of annotations?

A: Yes, GroupDocs.Annotation allows developers to specify which types of annotations to remove, giving them flexibility in managing annotations within their documents.

### Q: Can I try GroupDocs.Annotation for free before purchasing?

A: Yes, you can download a free trial version of GroupDocs.Annotation from the [releases page](https://releases.groupdocs.com/) to explore its features before making a purchase decision.

### Q: Where can I get support for GroupDocs.Annotation?

A: For technical assistance and community support, you can visit the [GroupDocs.Annotation forum](https://forum.groupdocs.com/c/annotation/10).
