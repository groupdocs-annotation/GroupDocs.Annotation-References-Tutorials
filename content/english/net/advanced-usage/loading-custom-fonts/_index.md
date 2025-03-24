---
title: Loading Custom Fonts
linktitle: Loading Custom Fonts
second_title: GroupDocs.Annotation .NET API
description: Learn how to seamlessly load custom fonts in GroupDocs.Annotation for .NET to enhance document annotation. Follow our step-by-step for easy integration.
weight: 20
url: /net/advanced-usage/loading-custom-fonts/
---
## Introduction
GroupDocs.Annotation for .NET is a powerful library that enables developers to add annotation features to their .NET applications effortlessly. One of the key functionalities it offers is the ability to load custom fonts, allowing for enhanced customization and flexibility in document annotation.
## Prerequisites
Before proceeding with the tutorial, ensure that you have the following prerequisites:
1. GroupDocs.Annotation for .NET Library: Download and install the library from [here](https://releases.groupdocs.com/annotation/net/).
2. .NET Development Environment: Make sure you have a working environment set up for .NET development.
3. Access to Custom Fonts: Prepare the custom fonts that you want to load into your application.

## Import Namespaces
In your .NET project, import the necessary namespaces for utilizing GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Step 1: Instantiate Annotator Object
Create an instance of the `Annotator` class by providing the path to the input PDF document along with the custom font directories:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Your code for further operations will go here
}
```
## Step 2: Configure Preview Options
Define the preview options to specify how the document previews will be generated. You can set options such as preview format, page numbers, etc.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Step 3: Generate Document Previews
Utilize the `GeneratePreview` method of the `Document` property to generate previews with custom fonts:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Step 4: Display Output Path
Finally, display a message indicating the successful generation of document previews along with the output directory path:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Conclusion
In conclusion, loading custom fonts in GroupDocs.Annotation for .NET provides developers with the flexibility to customize document annotations according to their requirements. By following the steps outlined in this tutorial, you can seamlessly integrate custom fonts into your .NET applications and enhance the annotation experience for users.
## FAQ's
### Can I load multiple custom fonts simultaneously?
Yes, you can specify multiple font directories when instantiating the `Annotator` object.
### Are there any limitations on the types of fonts supported?
GroupDocs.Annotation for .NET supports a wide range of font types, including TrueType (.ttf) and OpenType (.otf) fonts.
### Can I dynamically change the loaded fonts during runtime?
Yes, you can dynamically modify the font directories and reload the document annotations as needed.
### Does GroupDocs.Annotation support font embedding in output documents?
Yes, you can embed custom fonts in the output documents to ensure consistent rendering across different platforms.
### Is there a way to handle font licensing within the application?
GroupDocs.Annotation provides options for managing font licensing, including temporary licenses for evaluation purposes.
