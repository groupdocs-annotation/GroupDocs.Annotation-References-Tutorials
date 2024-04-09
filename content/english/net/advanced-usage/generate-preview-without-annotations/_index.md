---
title: Generate Preview without Annotations
linktitle: Generate Preview without Annotations
second_title: GroupDocs.Annotation .NET API
description: Enhance document collaboration and annotation within .NET applications using GroupDocs.Annotation for .NET. Easily annotate, mark up, and review documents with this powerful library.
type: docs
weight: 13
url: /net/advanced-usage/generate-preview-without-annotations/
---
## Introduction
In today's digital age, efficient collaboration on documents is key to productivity and success. Whether you're working on a project with team members scattered across the globe or collaborating with clients on important contracts, the ability to annotate and review documents seamlessly is crucial. With GroupDocs.Annotation for .NET, you can take your document collaboration to the next level, allowing for easy annotation, markup, and review directly within your .NET applications.
## Prerequisites
Before diving into the world of document annotation with GroupDocs.Annotation for .NET, there are a few prerequisites you'll need to have in place:
### 1. Install GroupDocs.Annotation for .NET
First and foremost, you'll need to download and install GroupDocs.Annotation for .NET. You can find the download link [here](https://releases.groupdocs.com/annotation/net/). Follow the installation instructions provided to set up the library in your .NET environment.
### 2. Obtain a License (Optional)
While GroupDocs.Annotation for .NET offers a free trial, you may want to consider obtaining a license for full access to its features. You can purchase a license [here](https://purchase.groupdocs.com/buy) or request a temporary license [here](https://purchase.groupdocs.com/temporary-license/) for testing purposes.
### 3. Familiarity with C# and .NET Development
To make the most of GroupDocs.Annotation for .NET, it's helpful to have a basic understanding of C# and .NET development. This will enable you to integrate the library seamlessly into your existing applications and workflows.
### 4. Install a PDF Viewer
Since GroupDocs.Annotation for .NET works with PDF documents, you'll need a PDF viewer installed on your system to preview annotated documents. Adobe Acrobat Reader or any other PDF viewer will suffice.

## Import Namespaces
Before you can start annotating documents, you'll need to import the necessary namespaces into your .NET project. This allows you to access the classes and methods provided by GroupDocs.Annotation for .NET.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

Now that you have everything set up, let's generate a preview of a document without any annotations. Follow these steps to accomplish this:
## Step 1: Initialize Annotator
First, create an instance of the `Annotator` class, passing the path to the document you want to annotate.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## Step 2: Configure Preview Options
Next, configure the preview options according to your requirements. You can specify the page numbers you want to include in the preview, the preview format (e.g., PNG), and whether to render annotations.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## Step 3: Generate Preview
Finally, generate the preview using the `GeneratePreview` method of the `Document` class, passing the configured preview options.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
By following these simple steps, you can generate a preview of a document without annotations using GroupDocs.Annotation for .NET.

## Conclusion
In conclusion, GroupDocs.Annotation for .NET provides a powerful solution for document collaboration and annotation within .NET applications. By following the steps outlined in this tutorial, you can seamlessly integrate document annotation capabilities into your projects, enhancing collaboration and productivity.
## FAQ's
### Q: Can I use GroupDocs.Annotation for .NET with other document formats besides PDF?
Yes, GroupDocs.Annotation for .NET supports a variety of document formats, including DOCX, XLSX, PPTX, and more.
### Q: Is GroupDocs.Annotation for .NET compatible with .NET Core?
Yes, GroupDocs.Annotation for .NET is compatible with both .NET Framework and .NET Core environments.
### Q: Does GroupDocs.Annotation for .NET offer customizable annotation tools?
Yes, GroupDocs.Annotation for .NET provides a range of annotation tools that can be customized to suit your specific requirements.
### Q: Can I integrate GroupDocs.Annotation for .NET into my web applications?
Yes, GroupDocs.Annotation for .NET can be integrated into both desktop and web applications, providing seamless document collaboration capabilities.
### Q: Is there a community forum where I can get support and assistance with GroupDocs.Annotation for .NET?
Yes, you can find support and assistance on the GroupDocs.Annotation forum [here](https://forum.groupdocs.com/c/annotation/10).
