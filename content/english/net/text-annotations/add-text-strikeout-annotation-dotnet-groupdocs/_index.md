---
title: "Strikeout Annotation .NET Tutorial - Complete Developer Guide (2025)"
linktitle: "Strikeout Annotation .NET Guide"
description: "Learn how to add strikeout annotations in .NET with GroupDocs.Annotation. Step-by-step tutorial with code examples, best practices, and troubleshooting tips."
keywords: "strikeout annotation .NET, document annotation tutorial C#, GroupDocs annotation examples, PDF text strikethrough .NET, C# PDF annotation code"
weight: 1
url: "/net/text-annotations/add-text-strikeout-annotation-dotnet-groupdocs/"
date: "2025-01-02"
lastmod: "2025-01-02"
categories: ["Document Processing"]
tags: ["GroupDocs", "Annotations", "C#", "PDF", "Document Markup"]
type: docs
---
# How to Add Strikeout Annotations in .NET: Complete Developer Guide

## Introduction

Ever wished you could digitally cross out text in documents like you would with a red pen? Whether you're building a document review system, creating collaborative editing tools, or just need to mark outdated information, strikeout annotations are incredibly useful.

Here's the thing though – implementing document annotations from scratch is a nightmare. You'd need to handle different file formats, coordinate systems, rendering... the list goes on. That's where **GroupDocs.Annotation for .NET** comes in.

In this tutorial, you'll learn exactly how to add text strikeout annotations to your .NET applications using GroupDocs.Annotation. We'll cover everything from basic setup to advanced customization, plus I'll share some hard-learned lessons about common pitfalls (so you don't have to learn them the hard way).

## Why Use Strikeout Annotations in Your Applications?

Before we dive into the code, let's talk about why strikeout annotations matter. They're not just fancy visual effects – they solve real problems:

**Document Review Workflows**: Legal teams use strikeouts to indicate deleted clauses in contracts. Medical professionals mark outdated treatment protocols. Content teams show what needs to be removed from articles.

**Version Control Visualization**: Instead of completely removing text, strikeouts let you show what changed while keeping the original context visible.

**Collaborative Editing**: Multiple reviewers can mark different sections for removal without actually deleting content until everyone agrees.

**Audit Trails**: In regulated industries, you often need to show what was removed and when – strikeouts provide that visual history.

## What You'll Need Before Starting

Let's make sure you have everything set up correctly. Nothing's more frustrating than getting halfway through a tutorial only to discover you're missing a crucial piece.

### Essential Requirements
- **GroupDocs.Annotation for .NET**: Version 25.4.0 or later (earlier versions had some quirky behavior with text positioning)
- **Development Environment**: Visual Studio 2019+ or Visual Studio Code with C# extension
- **Framework**: .NET Framework 4.6.1+ or .NET Core 2.0+ (I recommend .NET 6+ if you're starting fresh)
- **Basic C# Knowledge**: You should be comfortable with classes, methods, and using statements

### Nice-to-Have Skills
- Understanding of coordinate systems (helpful for positioning annotations)
- Experience with document processing (not required, but makes things easier)

## Setting Up GroupDocs.Annotation for .NET

Alright, let's get GroupDocs.Annotation installed and running. I'll show you multiple ways to do this because different developers prefer different approaches.

### Installation Options

**Option 1: NuGet Package Manager Console** (my personal favorite)
```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**Option 2: .NET CLI** (great for command-line enthusiasts)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**Option 3: Visual Studio Package Manager UI** (if you prefer clicking)
1. Right-click your project → Manage NuGet Packages
2. Search for "GroupDocs.Annotation"
3. Install version 25.4.0 or later

### Licensing: What You Need to Know

Here's something that trips up a lot of developers: GroupDocs.Annotation isn't free for commercial use. But don't worry, you have options:

- **Free Trial**: Perfect for testing and proof-of-concepts. You'll get a watermark on output documents.
- **Temporary License**: Full features for evaluation (usually 30 days). Great for serious testing.
- **Commercial License**: Required for production applications.

**Pro Tip**: Start with the free trial to make sure it meets your needs, then get a temporary license for thorough testing before purchasing.

## Step-by-Step Implementation Guide

Now for the fun part – let's write some code! I'll walk you through creating your first strikeout annotation, explaining each step and why it matters.

### Step 1: Set Up Your Document Paths

First, let's define where your documents live. This might seem trivial, but trust me – getting paths wrong is responsible for 90% of the "it doesn't work" support tickets I see.

```csharp
string documentPath = Path.Combine(@"YOUR_DOCUMENT_DIRECTORY\input.pdf");
string outputPath = Path.Combine(@"YOUR_DOCUMENT_DIRECTORY\output.pdf");
```

**Important Notes:**
- Replace `YOUR_DOCUMENT_DIRECTORY` with your actual path
- Use `Path.Combine()` instead of string concatenation (it handles path separators correctly across different operating systems)
- Make sure the input file exists and the output directory is writable

### Step 2: Initialize the Annotator

This is where we create our main workhorse – the Annotator object that'll handle all our annotation needs.

```csharp
using (Annotator annotator = new Annotator(documentPath))
{
    // All our annotation magic happens inside this using block
}
```

**Why the `using` statement?** The Annotator class implements `IDisposable`, which means it holds onto system resources (like file handles). The `using` statement ensures these resources get cleaned up properly, even if something goes wrong.

### Step 3: Create Your Strikeout Annotation

Now we're getting to the meat of it. Let's create a strikeout annotation with all the bells and whistles.

```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    Box = new Rectangle(100, 100, 200, 50), // Position and size
    PageNumber = 0, // First page (zero-indexed)
    PenColor = 65535, // Yellow color in RGB
    PenStyle = PenStyle.Dash,
    PenWidth = 2
};
```

**Let's break down each property:**

- **Box**: Defines where the annotation appears. Format is `(X, Y, Width, Height)` where X,Y is the top-left corner
- **PageNumber**: Which page to add the annotation to (starts at 0, not 1!)
- **PenColor**: Color of the strikeout line. This example uses yellow (65535 in RGB)
- **PenStyle**: How the line looks. Options include Solid, Dash, Dot, DashDot, etc.
- **PenWidth**: Thickness of the strikeout line in points

**Coordinate System Gotcha**: The coordinate system starts at the top-left corner of the page, not bottom-left like some graphics systems. If your annotations appear in weird places, this is probably why.

### Step 4: Add the Annotation and Save

Finally, let's add our annotation to the document and save the result.

```csharp
annotator.Add(strikeout);
annotator.Save(outputPath);
```

That's it! Your document now has a strikeout annotation. Pretty straightforward, right?

## Complete Working Example

Here's everything put together in one complete, copy-pasteable example:

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System.IO;

class Program
{
    static void Main(string[] args)
    {
        // Define your file paths
        string documentPath = Path.Combine(@"C:\Documents\input.pdf");
        string outputPath = Path.Combine(@"C:\Documents\output.pdf");
        
        try
        {
            using (Annotator annotator = new Annotator(documentPath))
            {
                // Create the strikeout annotation
                StrikeoutAnnotation strikeout = new StrikeoutAnnotation
                {
                    Box = new Rectangle(100, 100, 200, 50),
                    PageNumber = 0,
                    PenColor = 65535, // Yellow
                    PenStyle = PenStyle.Dash,
                    PenWidth = 2
                };
                
                // Add and save
                annotator.Add(strikeout);
                annotator.Save(outputPath);
                
                Console.WriteLine($"Annotation added successfully! Check: {outputPath}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

## Common Pitfalls and How to Avoid Them

After helping hundreds of developers implement GroupDocs.Annotation, I've seen the same mistakes over and over. Here are the big ones:

### Pitfall #1: Wrong Coordinate Calculations

**The Problem**: Annotations appear in unexpected places because coordinates are calculated incorrectly.

**The Solution**: Remember that coordinates are in points (1/72 of an inch), not pixels. If you're working with pixel coordinates from a UI, you'll need to convert them.

```csharp
// Convert pixels to points (assuming 96 DPI)
double pointsX = pixelsX * 72 / 96;
double pointsY = pixelsY * 72 / 96;
```

### Pitfall #2: Forgetting Zero-Based Page Numbers

**The Problem**: Trying to add an annotation to "page 1" by setting `PageNumber = 1`, but the annotation doesn't appear.

**The Solution**: Page numbers start at 0, not 1. If you want to annotate the first page, use `PageNumber = 0`.

### Pitfall #3: File Path Issues

**The Problem**: "File not found" errors even when the file exists.

**The Solution**: 
- Use absolute paths during development
- Check file permissions (the application needs read access to input files, write access to output location)
- Avoid spaces and special characters in file paths if possible

### Pitfall #4: Memory Leaks with Large Documents

**The Problem**: Your application's memory usage keeps growing when processing multiple documents.

**The Solution**: Always wrap your Annotator in a `using` statement or manually call `Dispose()`.

## Advanced Customization Options

Once you've got basic strikeouts working, you might want to customize them further. Here are some options I find particularly useful:

### Custom Colors and Styles

```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    Box = new Rectangle(100, 100, 200, 50),
    PageNumber = 0,
    PenColor = 16711680, // Red color (RGB: FF0000)
    PenStyle = PenStyle.Solid, // or Dash, Dot, DashDot, etc.
    PenWidth = 3,
    Opacity = 0.8 // Semi-transparent
};
```

### Adding Metadata to Annotations

```csharp
strikeout.Message = "This section needs to be removed";
strikeout.CreatedOn = DateTime.Now;
strikeout.Replies = new List<Reply>
{
    new Reply
    {
        Comment = "Approved for removal",
        RepliedOn = DateTime.Now
    }
};
```

## Real-World Use Cases and Best Practices

Let me share some scenarios where I've seen strikeout annotations used effectively:

### Document Review Systems

**Scenario**: A legal firm needs to review contracts and mark sections for removal.

**Implementation**: Create a review interface where users can select text, and automatically generate strikeout annotations with reviewer information and timestamps.

**Best Practice**: Include reviewer metadata in the annotation so you can track who marked what for removal.

### Content Management Workflows

**Scenario**: A content team wants to mark outdated information in knowledge base articles.

**Implementation**: Build a content review tool that highlights outdated sections with strikeout annotations, allowing multiple reviewers to collaborate.

**Best Practice**: Use different colors for different types of issues (red for factual errors, yellow for outdated info, blue for style changes).

### Collaborative Editing Tools

**Scenario**: Multiple editors need to suggest deletions in a shared document.

**Implementation**: Each editor gets a unique annotation color, and their suggested deletions are shown as strikeouts.

**Best Practice**: Implement a voting or approval system where multiple strikeouts on the same text automatically flag it for review.

## Performance Optimization Tips

When you're dealing with large documents or high-volume processing, performance matters. Here's what I've learned:

### Memory Management

```csharp
// Good: Process documents one at a time
foreach (string docPath in documentPaths)
{
    using (Annotator annotator = new Annotator(docPath))
    {
        // Process document
        ProcessDocument(annotator);
    } // Annotator is disposed here, freeing memory
}

// Bad: Creating multiple annotators without disposal
var annotators = new List<Annotator>();
foreach (string docPath in documentPaths)
{
    annotators.Add(new Annotator(docPath)); // Memory leak!
}
```

### Batch Processing

For multiple annotations on the same document, add them all before saving:

```csharp
using (Annotator annotator = new Annotator(documentPath))
{
    // Add multiple annotations
    annotator.Add(strikeout1);
    annotator.Add(strikeout2);
    annotator.Add(strikeout3);
    
    // Save once at the end
    annotator.Save(outputPath);
}
```

### Async Processing for Web Applications

If you're building a web application, consider processing annotations asynchronously:

```csharp
public async Task<string> AddStrikeoutAnnotationAsync(string inputPath, AnnotationRequest request)
{
    return await Task.Run(() =>
    {
        using (Annotator annotator = new Annotator(inputPath))
        {
            var strikeout = CreateStrikeoutFromRequest(request);
            annotator.Add(strikeout);
            
            string outputPath = GenerateOutputPath();
            annotator.Save(outputPath);
            return outputPath;
        }
    });
}
```

## Troubleshooting Common Issues

### Issue: Annotations Don't Appear

**Possible Causes:**
1. Wrong page number (remember: zero-based)
2. Coordinates outside the page boundaries
3. Pen width set to 0
4. Color set to transparent

**Debug Steps:**
1. Print out your annotation properties before adding
2. Try with simple, known-good coordinates (like `new Rectangle(100, 100, 200, 50)`)
3. Use a bright, obvious color for testing (like red: `16711680`)

### Issue: "File Access" Errors

**Solutions:**
1. Make sure the input file isn't open in another application
2. Check that your application has write permissions to the output directory
3. Use different filenames for input and output to avoid conflicts

### Issue: Poor Performance with Large Documents

**Solutions:**
1. Process documents in smaller batches
2. Use async processing for web applications
3. Consider caching processed documents if they'll be accessed multiple times

## FAQ Section

**Q: Can I add strikeout annotations to formats other than PDF?**
A: Absolutely! GroupDocs.Annotation supports Word documents, Excel spreadsheets, PowerPoint presentations, and many other formats. The code is virtually identical.

**Q: How do I remove annotations after adding them?**
A: You can remove annotations by their ID or remove all annotations of a specific type. Here's a quick example:
```csharp
annotator.Remove(annotationId);
// or remove all strikeouts
annotator.Remove(typeof(StrikeoutAnnotation));
```

**Q: Can users interact with the annotations in the final document?**
A: That depends on the viewer application. In most PDF viewers, users can see the annotations and any associated comments, but they can't modify them unless they have the right software.

**Q: What's the difference between strikeout and redaction annotations?**
A: Great question! Strikeout annotations cross out text but leave it visible (like crossing out with a pen). Redaction annotations completely black out text, making it unreadable. Use strikeout for "suggested deletions" and redaction for "confidential information."

**Q: How do I handle documents with different page sizes?**
A: GroupDocs.Annotation automatically handles different page sizes. However, if you're calculating coordinates programmatically, you might need to get the page dimensions first:
```csharp
var pageInfo = annotator.Document.GetDocumentInfo().PagesInfo[pageNumber];
double pageWidth = pageInfo.Width;
double pageHeight = pageInfo.Height;
```

**Q: Can I style strikeouts to look like handwritten annotations?**
A: While you can't make them look exactly handwritten, you can use different pen styles (`PenStyle.Dash`, `PenStyle.Dot`) and vary the opacity to create more organic-looking annotations.

**Q: What happens to annotations when I convert the document to a different format?**
A: This depends on the target format and conversion method. Some formats preserve annotations (like PDF to PDF/A), while others might flatten them into the document or lose them entirely. Test your specific conversion workflow.

**Q: How do I add multiple strikeouts that overlap?**
A: Just add them normally – GroupDocs.Annotation handles overlapping annotations fine. The visual result will show both strikeouts, which can be useful for showing multiple reviewers' suggestions.

## Next Steps and Further Learning

Congratulations! You now know how to add strikeout annotations to documents in .NET. But this is just the beginning of what's possible with GroupDocs.Annotation.

### Explore Other Annotation Types
- **Highlight Annotations**: Perfect for marking important sections
- **Text Annotations**: Add comments and notes
- **Arrow Annotations**: Point to specific areas
- **Area Annotations**: Highlight rectangular regions

### Advanced Features to Investigate
- **Custom Annotation Properties**: Add your own metadata
- **Annotation Events**: Respond to annotation creation/modification
- **Batch Processing**: Handle large document sets efficiently
- **Integration Patterns**: Connect with existing document management systems

### Resources for Continued Learning
- **Documentation**: [GroupDocs.Annotation for .NET Documentation](https://docs.groupdocs.com/annotation/net/)
- **API Reference**: [Complete API Reference](https://reference.groupdocs.com/annotation/net/)
- **Code Examples**: [GitHub Repository with Samples](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
- **Community Support**: [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

### Getting Help
If you run into issues or have questions beyond what's covered here, the GroupDocs community is pretty helpful. Their support forum is active, and the team is responsive to bug reports and feature requests.

## Conclusion

Adding strikeout annotations to documents doesn't have to be complicated. With GroupDocs.Annotation for .NET, you can implement professional document markup features in just a few lines of code.

The key takeaways from this tutorial:
- **Start simple**: Get basic functionality working before adding bells and whistles
- **Mind the coordinates**: The coordinate system can trip you up if you're not careful
- **Handle resources properly**: Always use `using` statements with the Annotator class
- **Plan for scale**: Consider performance implications if you'll be processing many documents

Whether you're building a document review system, collaborative editing tool, or just need to mark up documents programmatically, strikeout annotations are a powerful feature that your users will appreciate.

Now go build something awesome! And remember – the best way to learn is by doing, so fire up your IDE and start experimenting with different annotation styles and configurations.