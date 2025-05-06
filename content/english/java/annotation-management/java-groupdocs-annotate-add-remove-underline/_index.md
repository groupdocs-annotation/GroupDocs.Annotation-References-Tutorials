---
title: "Add and Remove Underline Annotations in Java using GroupDocs&#58; A Comprehensive Guide"
description: "Learn how to add and remove underline annotations in Java documents using GroupDocs.Annotation. Enhance your document management with this detailed guide."
date: "2025-05-06"
weight: 1
url: "/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
keywords:
- GroupDocs.Annotation for Java
- underline annotation in Java
- remove annotations from documents

---


# How to Implement Java: Add and Remove Underline Annotations with GroupDocs

## Introduction

Enhancing your document management system by adding or removing annotations programmatically? This tutorial guides you through using the powerful GroupDocs.Annotation library in Java to add underline annotations and remove them from documents like PDFs.

**What You'll Learn:**
- Initialize the Annotator class.
- Add an underline annotation with comments using GroupDocs.Annotation for Java.
- Remove all annotations from a document.
- Configure your environment to use GroupDocs.Annotation efficiently.

Let's explore how these functionalities can be leveraged in your projects. Ensure you have the necessary prerequisites covered before starting.

## Prerequisites

### Required Libraries and Dependencies
To follow this tutorial effectively, ensure you have:
- **GroupDocs.Annotation for Java**: Version 25.2 or later is recommended.
- **Java Development Kit (JDK)**: Version 8 or higher is required.

### Environment Setup Requirements
Ensure your development environment includes an IDE like IntelliJ IDEA or Eclipse and a build tool such as Maven.

### Knowledge Prerequisites
A basic understanding of Java programming, especially working with libraries via Maven, will be beneficial.

## Setting Up GroupDocs.Annotation for Java

To start using GroupDocs.Annotation in your Java projects, follow these setup steps:

**Maven Configuration:**
Add the following configuration to your `pom.xml` file to download and integrate GroupDocs.Annotation.

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**License Acquisition:**
Start by downloading a free trial or obtaining a temporary license from GroupDocs to explore the full capabilities of their library. For production use, purchasing a license is necessary.

## Implementation Guide

### Feature 1: Initialize Annotator and Add Underline Annotation

This section guides you through initializing the `Annotator` class and adding an underline annotation to your document.

#### Overview
Adding annotations helps highlight specific parts of a document. Here, we focus on underlining text with comments for clarification or feedback.

#### Step-by-Step Implementation

**1. Initialize Annotator**
Create an `Annotator` object and load your PDF file.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Create Comments with Replies**
Define comments associated with the underline annotation.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. Define Points for Underline Annotation**
Set coordinates to determine where the underline should appear.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. Create and Configure Underline Annotation**
Create the underline annotation and set its properties like color, opacity, and comments.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Save the Annotated Document**
Save your changes to a new file.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Troubleshooting Tips
- Ensure all coordinates for points are within the document bounds.
- Verify that the `outputPath` directory exists and is writable.

### Feature 2: Save Document with No Annotations

This section covers how to remove all annotations from a previously annotated document.

#### Overview
You may need to save a clean version of your document without any annotations for sharing or archiving purposes.

#### Step-by-Step Implementation

**1. Initialize Annotator with the Annotated Document**
Load the document that has existing annotations.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Configure Save Options to Remove Annotations**
Specify that no annotations should be saved in the output file.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Save the Document Without Annotations**
Define the path for the cleaned document and save it.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Practical Applications

Here are some real-world scenarios where these features can be beneficial:
1. **Document Review**: Highlighting and commenting on sections of a contract or report for review.
2. **Educational Tools**: Annotating textbooks with notes or corrections for students.
3. **Collaborative Editing**: Sharing annotated drafts among team members for feedback.
4. **Legal Documentation**: Underlining key clauses in legal documents during discussions.
5. **Marketing Materials**: Highlighting important information in brochures before distribution.

## Performance Considerations
When working with GroupDocs.Annotation, consider these tips to optimize performance:
- **Memory Management**: Properly dispose of `Annotator` objects to free up resources.
- **Batch Processing**: If annotating multiple documents, process them in batches to manage system load effectively.
- **Resource Allocation**: Ensure your environment has sufficient memory and processing power for handling large files.

## Conclusion
You've learned how to add and remove underline annotations using GroupDocs.Annotation for Java. This tutorial covered initializing the Annotator class, configuring annotations with comments, and saving documents without any annotations. 

For further exploration, consider integrating these features into your existing document management systems or experimenting with other annotation types provided by GroupDocs.

## FAQ Section
1. **How do I configure multiple underline annotations in a single run?**
   - Create multiple `UnderlineAnnotation` objects and add them sequentially using the `annotator.add()` method.
2. **Can I annotate images within PDFs using this library?**
   - Yes, GroupDocs.Annotation supports annotating images within documents like PDFs.
3. **What file formats does GroupDocs.Annotation support?**
   - It supports various document formats including PDF, Word, Excel, and more.
