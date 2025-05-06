---
title: "How to Add Distance Annotations in Java with GroupDocs.Annotation&#58; A Step-by-Step Guide"
description: "Learn how to implement distance annotations in Java documents using GroupDocs.Annotation. This step-by-step guide covers setup, configuration, and practical applications."
date: "2025-05-06"
weight: 1
url: "/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/"
keywords:
- distance annotations Java
- GroupDocs.Annotation setup
- Java document measurements

---


# How to Add Distance Annotations in Java Using GroupDocs.Annotation

Welcome to our comprehensive guide on adding distance annotations to your Java-based document applications with GroupDocs.Annotation. This feature is essential for projects that require precise measurements within digital documents, such as technical drawings or architectural plans.

## What You'll Learn:
- **Understanding the Basics**: Discover what distance annotations are and how they can enhance your documents.
- **Setting Up Your Environment**: Follow our guide to prepare your development environment with GroupDocs.Annotation for Java.
- **Implementing Distance Annotations**: A detailed, step-by-step process for adding distance annotations in a Java application.

Before you begin, ensure you have the necessary prerequisites covered!

## Prerequisites

Ensure the following before starting:
### Required Libraries and Dependencies:
- **GroupDocs.Annotation for Java** version 25.2 or later.
- Maven for dependency management (recommended).

### Environment Setup Requirements:
- A working Java Development Kit (JDK) setup on your system.
- Basic understanding of Java programming concepts.

### Knowledge Prerequisites:
- Familiarity with object-oriented programming in Java.

## Setting Up GroupDocs.Annotation for Java

Integrate the GroupDocs.Annotation library into your project using Maven. Add the following configuration to your `pom.xml`:

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

### License Acquisition Steps:
1. **Free Trial**: Begin with a free trial to explore the features.
2. **Temporary License**: Obtain a temporary license for extended testing capabilities.
3. **Purchase**: Consider purchasing a commercial license for full access.

Initialize GroupDocs.Annotation in your project like this:

```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with the input file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

## Implementation Guide

### Adding Distance Annotations to Your Document

**Overview**: This section guides you through adding a distance annotation, representing measurements between two points.

#### Step 1: Create and Configure Replies for the Annotation

Annotations can be interactive. Here’s how to add replies:

```java
import com.groupdocs.annotation.models.Reply;
import java.util.ArrayList;
import java.util.Calendar;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

#### Step 2: Configure the Distance Annotation

Set up your distance annotation with properties such as position, size, and opacity.

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30)); // Set the annotation's position and size
distance.setCreatedOn(Calendar.getInstance().getTime()); 
distance.setMessage("This is a distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0); 
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.DOT);
distance.setPenWidth((byte) 3);

distance.setReplies(replies); // Attach replies
```

#### Step 3: Add the Annotation to Your Document

Add the configured annotation to your document and save it.

```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```

### Troubleshooting Tips:
- **Check File Paths**: Ensure input and output paths are correct.
- **Verify Library Version**: Confirm you're using a compatible version of GroupDocs.Annotation for Java.

## Practical Applications

Distance annotations can enhance document interactivity in various ways:
1. **Technical Manuals**: Mark measurements on schematics.
2. **Real Estate Plans**: Highlight property boundaries.
3. **Medical Imaging**: Annotate distances between anatomical structures.
4. **Architectural Designs**: Provide precise dimensions on blueprints.

Integrating GroupDocs.Annotation with other systems can further extend its capabilities, such as cloud storage or document management solutions.

## Performance Considerations

Optimize your application's performance by:
- Managing memory effectively when processing large documents.
- Using appropriate Java garbage collection settings to handle annotations efficiently.

Best practices for memory management include closing annotator instances after use and avoiding unnecessary object retention in memory.

## Conclusion

You've now learned how to add distance annotations using GroupDocs.Annotation for Java. This feature opens up numerous possibilities for enhancing document interactivity and precision.

**Next Steps:**
- Explore other annotation types supported by GroupDocs.
- Integrate with your existing document management system.

**Call-to-Action**: Try implementing these steps in your project to see how they enhance your application's functionality!

## FAQ Section

1. **What is a distance annotation?**
   - A visual representation used to denote measurements between two points in a document.
2. **Can I use GroupDocs.Annotation for free?**
   - Yes, start with a free trial and explore its features.
3. **How do I set the opacity of an annotation?**
   - Use `setOpacity()` method on your annotation object to adjust transparency levels.
4. **What are some common issues when adding annotations?**
   - Common problems include incorrect file paths, incompatible library versions, or misconfigured annotation properties.
5. **Where can I find more resources about GroupDocs.Annotation for Java?**
   - Visit the [official documentation](https://docs.groupdocs.com/annotation/java/) and API reference for comprehensive guides and examples.

## Resources
- [Documentation](https://docs.groupdocs.com/annotation/java/)
- [API Reference](https://reference.groupdocs.com/annotation/java/)
- [Download GroupDocs.Annotation](https://releases.groupdocs.com/annotation/java/)
- [Purchase GroupDocs Licensing](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/annotation/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
