---
title: "Text Strikeout Annotation .NET"
linktitle: "Add Text Strikeout Annotation"
second_title: GroupDocs.Annotation .NET API
description: "Learn how to add text strikeout annotations in .NET with GroupDocs.Annotation. Step-by-step tutorial with code examples and best practices for document markup."
keywords: "text strikeout annotation .NET, GroupDocs annotation tutorial, document annotation C#, strikeout markup .NET, PDF annotation library"
weight: 26
url: /net/unlocking-annotation-power/add-text-strikeout-annotation/
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["Document Annotation"]
tags: ["strikeout-annotation", "groupdocs", "dotnet", "pdf-markup"]

---
# Text Strikeout Annotation .NET - Complete Implementation Guide

## Introduction

Need to mark text as deleted or incorrect in your documents? You're in the right place. Text strikeout annotations are essential for document review processes, legal markups, and collaborative editing workflows. In this comprehensive guide, we'll walk through implementing text strikeout annotations using GroupDocs.Annotation for .NET.

Whether you're building a document management system, creating review workflows, or adding markup capabilities to your application, strikeout annotations help users visually indicate content that should be removed or revised. Let's dive into the complete implementation process.

## When to Use Text Strikeout Annotations

Before jumping into the code, it's helpful to understand the practical applications of strikeout annotations:

- **Document Review Processes**: Mark text for deletion during editing phases
- **Legal Document Markups**: Indicate clauses or terms to be removed
- **Version Control**: Show what content has been superseded
- **Collaborative Editing**: Allow multiple reviewers to suggest deletions
- **Compliance Documentation**: Track what information needs to be redacted

## Prerequisites and Setup

Before we begin implementing text strikeout annotations, ensure you have the following prerequisites:

1. **GroupDocs.Annotation for .NET**: Install the library from [here](https://releases.groupdocs.com/annotation/net/). This is your core dependency for all annotation functionality.

2. **Development Environment**: Set up a suitable .NET development environment (Visual Studio, VS Code, or your preferred IDE).

3. **Document for Testing**: Have a document ready to annotate, such as a PDF file. PDF files work particularly well for annotation testing.

4. **Basic C# Knowledge**: Familiarity with C# syntax and object-oriented programming concepts will help you understand the implementation better.

## Essential Namespace Imports

First, let's import the necessary namespaces to access GroupDocs.Annotation functionalities. These imports give you access to all the annotation models and options you'll need:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

These namespaces provide everything from basic system functionality to specialized annotation models. The `GroupDocs.Annotation.Models.AnnotationModels` namespace is particularly important as it contains the `StrikeoutAnnotation` class we'll be working with.

## Step-by-Step Implementation Guide

Now, let's break down the process of adding a text strikeout annotation into clear, manageable steps. Each step builds upon the previous one, creating a complete workflow.

### Step 1: Define Output Path

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

This step sets up where your annotated document will be saved. The `Path.Combine` method ensures cross-platform compatibility, while `Path.GetExtension` preserves the original file format. Make sure to replace "Your Document Directory" with the actual path where you want to save the output file.

**Pro Tip**: Consider using timestamp-based naming for output files in production environments to avoid overwriting existing files.

### Step 2: Initialize Annotator

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```

Here we initialize the Annotator object with our input document. The `using` statement ensures proper disposal of resources after we're done processing. This is crucial for memory management, especially when processing large documents or multiple files in batch operations.

The Annotator class is your main interface for adding, modifying, and managing annotations. It handles document loading, annotation processing, and final output generation.

### Step 3: Create Strikeout Annotation

```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```

This is where the magic happens. We create a comprehensive StrikeoutAnnotation object with several important properties:

- **CreatedOn**: Timestamp for tracking when the annotation was added
- **FontColor**: Color of the strikeout line (65535 represents a bright blue)
- **Message**: Descriptive text explaining why the content is marked for deletion
- **Opacity**: Controls transparency (0.7 means 70% opacity, allowing underlying text to show through)
- **PageNumber**: Specifies which page contains the annotation (0-indexed)
- **BackgroundColor**: Background highlight color for better visibility
- **Points**: Defines the rectangular area where the strikeout appears (coordinates in points)
- **Replies**: Enables collaborative discussion about the strikeout annotation

**Understanding Coordinates**: The Points array defines a rectangle using four coordinates. The format is [top-left, top-right, bottom-left, bottom-right]. Adjust these values based on your document's layout and the text you want to mark.

### Step 4: Add Annotation to Document

```csharp
annotator.Add(strikeout);
```

This simple but crucial step adds your configured strikeout annotation to the document. The Annotator handles all the complex processing of integrating the annotation with the document structure.

### Step 5: Save Annotated Document

```csharp
annotator.Save(outputPath);
```

Finally, we save the annotated document to our specified output path. The Save method handles format preservation and ensures all annotation data is properly embedded in the output file.

## Best Practices for Strikeout Annotations

### Styling and Appearance Considerations

When implementing strikeout annotations in production applications, consider these styling best practices:

- **Color Contrast**: Choose colors that provide sufficient contrast against your document background
- **Opacity Levels**: Use opacity between 0.5-0.8 to maintain readability of underlying text
- **Consistent Sizing**: Maintain consistent annotation dimensions for professional appearance
- **Message Clarity**: Write clear, concise messages explaining why text is being struck out

### Performance Optimization Tips

For applications that process many documents or large files:

- **Batch Processing**: Process multiple annotations in a single operation when possible
- **Memory Management**: Always use `using` statements to ensure proper resource disposal
- **File Size Considerations**: Be mindful that annotations increase output file size
- **Coordinate Precision**: Use precise coordinates to avoid overlapping annotations

## Common Implementation Issues and Solutions

### Issue: Annotation Not Appearing

If your strikeout annotation isn't visible in the output document:

1. **Check Coordinates**: Verify that your Points array coordinates correspond to actual document content
2. **Page Number**: Ensure the PageNumber property matches the target page (remember it's 0-indexed)
3. **Opacity Settings**: Make sure opacity isn't set to 0 (completely transparent)
4. **Color Values**: Verify that font and background colors aren't identical

### Issue: Incorrect Positioning

When annotations appear in the wrong location:

1. **Coordinate System**: Remember that coordinates are in points (1/72 of an inch)
2. **Document Layout**: Different document formats may have different coordinate systems
3. **Page Margins**: Account for document margins when calculating positions
4. **Testing**: Always test with sample documents before production deployment

### Issue: Performance Problems

If annotation processing is slow:

1. **Document Size**: Large documents naturally take longer to process
2. **Resource Management**: Ensure you're properly disposing of Annotator objects
3. **Batch Operations**: Consider processing multiple annotations simultaneously
4. **Memory Usage**: Monitor memory consumption during bulk operations

## Advanced Customization Options

The StrikeoutAnnotation class offers additional properties for fine-tuning appearance and behavior:

- **Author**: Set the annotation author for tracking purposes
- **Box**: Define precise bounding box dimensions
- **PenStyle**: Customize the strikeout line style
- **PenWidth**: Adjust the thickness of the strikeout line

## Integration with Document Workflows

Strikeout annotations work particularly well in these scenarios:

- **Review and Approval Processes**: Mark content for removal during document reviews
- **Content Migration**: Indicate deprecated information when updating documentation
- **Legal Redaction Workflows**: Mark sensitive information for removal (though consider proper redaction tools for sensitive data)
- **Educational Materials**: Show corrections and improvements in teaching documents

## Conclusion

Adding text strikeout annotations with GroupDocs.Annotation for .NET is straightforward once you understand the core concepts. The combination of precise coordinate positioning, customizable styling options, and collaborative features makes it an excellent choice for document annotation needs.

Remember to test your implementation thoroughly with various document types and sizes. Pay attention to coordinate accuracy, performance optimization, and user experience when deploying to production environments.

With this foundation, you can now implement sophisticated document review workflows that enable users to mark text for deletion while maintaining full visibility and collaborative discussion capabilities.

## Frequently Asked Questions

### Is GroupDocs.Annotation compatible with various document formats?

Yes, GroupDocs.Annotation supports a wide range of document formats including PDF, Word, Excel, PowerPoint, and more. This makes it versatile for different document processing needs in enterprise applications.

### Can I customize the appearance of annotations?

Absolutely, you can customize annotation properties such as color, opacity, font size, pen style, and more according to your requirements. The library provides extensive styling options for professional-looking annotations.

### Does GroupDocs.Annotation provide collaboration features?

Yes, GroupDocs.Annotation facilitates collaboration by allowing users to add comments, replies, and annotations to documents. The reply system enables threaded discussions about specific annotations.

### How do I handle coordinate positioning for different document sizes?

Coordinate positioning requires understanding that coordinates are measured in points (1/72 inch). For dynamic positioning, you might need to calculate coordinates based on document dimensions or implement user-interactive selection tools.

### Can I process multiple annotations in batch operations?

Yes, you can add multiple annotations to a single document before saving. This is more efficient than processing documents multiple times and helps maintain better performance in production applications.

### Is there a free trial available?

Yes, you can avail of a free trial from [here](https://releases.groupdocs.com/).

### Where can I get support for GroupDocs.Annotation?

You can get support from the [GroupDocs.Annotation forum](https://forum.groupdocs.com/c/annotation/10).