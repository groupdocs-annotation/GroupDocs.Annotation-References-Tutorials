---
title: Generate Preview without Comments
linktitle: Generate Preview without Comments
second_title: GroupDocs.Annotation .NET API
description: Learn how to seamlessly integrate document annotation capabilities into your .NET applications using GroupDocs.Annotation for .NET.
type: docs
weight: 14
url: /net/advanced-usage/generate-preview-without-comments/
---
## Introduction
GroupDocs.Annotation for .NET is a powerful tool that allows developers to incorporate annotation features into their .NET applications seamlessly. Whether you're working on a document management system, collaboration platform, or any other application requiring document annotation capabilities, GroupDocs.Annotation provides a comprehensive set of tools to enhance your application's functionality.
## Prerequisites
Before diving into using GroupDocs.Annotation for .NET, ensure you have the following prerequisites set up:
### 1. Install GroupDocs.Annotation for .NET
To begin, you need to download and install GroupDocs.Annotation for .NET. You can find the download link [here](https://releases.groupdocs.com/annotation/net/). Follow the installation instructions provided in the documentation for a smooth setup process.
### 2. Obtain License
GroupDocs.Annotation for .NET requires a license for commercial use. You can acquire a license from [here](https://purchase.groupdocs.com/buy) or opt for a temporary license [here](https://purchase.groupdocs.com/temporary-license/) for testing purposes.
### 3. Familiarity with .NET Framework
Basic knowledge of .NET Framework and C# programming language is essential to effectively utilize GroupDocs.Annotation for .NET.

## Import Namespaces
Now that you have set up the prerequisites, let's import the necessary namespaces into your .NET application.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Follow these step-by-step instructions to generate a preview without comments using GroupDocs.Annotation for .NET:
## Step 1: Initialize Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Step 2: Configure Preview Options
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Step 3: Specify Preview Format and Page Numbers
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Step 4: Disable Rendering of Comments
```csharp
    previewOptions.RenderComments = false;
```
## Step 5: Generate Preview
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Once you've followed these steps, your .NET application will be able to generate a preview of the specified pages from the document without rendering comments.

## Conclusion
Incorporating annotation features into your .NET applications has never been easier thanks to GroupDocs.Annotation for .NET. By following the steps outlined in this tutorial, you can seamlessly integrate document annotation capabilities into your applications, enhancing collaboration and document management.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation for .NET supports a wide range of document formats, including PDF, DOCX, PPTX, XLSX, and more.
### Can I customize the appearance of annotations generated using GroupDocs.Annotation for .NET?
Yes, GroupDocs.Annotation for .NET provides extensive customization options, allowing you to tailor the appearance of annotations to suit your application's needs.
### Does GroupDocs.Annotation for .NET support multi-user collaboration?
Yes, GroupDocs.Annotation for .NET offers collaborative annotation features, enabling multiple users to annotate documents simultaneously.
### Is technical support available for GroupDocs.Annotation for .NET?
Yes, technical support for GroupDocs.Annotation for .NET is available through the [support forum](https://forum.groupdocs.com/c/annotation/10).
### Can I try GroupDocs.Annotation for .NET for free before purchasing?
Yes, you can explore the features of GroupDocs.Annotation for .NET by downloading the free trial [here](https://releases.groupdocs.com/).
