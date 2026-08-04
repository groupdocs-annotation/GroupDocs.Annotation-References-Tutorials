---
additionalTitle: GroupDocs API references
date: 2026-08-04
description: Learn how to use the document annotation API to add PDF, Word, Excel
  & PowerPoint annotations in .NET and Java applications. Step‑by‑step tutorials cover
  text markup, comments, shapes, and collaboration features.
keywords:
- document annotation API
- PDF annotation
- Java annotation library
- collaborative review
- .NET annotation
lastmod: 2026-08-04
linktitle: GroupDocs.Annotation developer guides
og_description: Document annotation API lets you add PDF, Word, Excel, and PowerPoint
  annotations quickly. Learn how to integrate highlights, comments, and shapes in
  .NET and Java applications.
og_image_alt: Guide showing how to annotate PDFs and Office documents using GroupDocs.Annotation
og_title: Document annotation API – add highlights, comments & shapes in .NET & Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Learn how to use the document annotation API to add PDF, Word, Excel
    & PowerPoint annotations in .NET and Java applications. Step‑by‑step tutorials
    cover text markup, comments, shapes, and collaboration features.
  headline: Document annotation API | GroupDocs.Annotation tutorials & SDK examples
  type: TechArticle
- questions:
  - answer: Yes. A valid GroupDocs license is required for production deployments,
      and a free trial is available for evaluation.
    question: Can I use the document annotation API in a commercial product?
  - answer: Absolutely. You can supply the password when opening the document, and
      all annotation operations work transparently.
    question: Does the API support password‑protected PDFs?
  - answer: The SDK supports .NET Framework 4.5+, .NET Core 3.1+, .NET 5, and .NET
      6+.
    question: Which .NET versions are compatible?
  - answer: Yes. You can load and save documents directly from Amazon S3, Azure Blob
      Storage, Google Cloud Storage, and other cloud providers.
    question: Is there built‑in support for cloud storage services?
  type: FAQPage
tags:
- document annotation
- GroupDocs.Annotation
- .NET annotation
- Java annotation
title: Document annotation API | GroupDocs.Annotation tutorials & SDK examples
type: docs
url: /
weight: 11
---

# GroupDocs.Annotation developer guide – document annotation API

In this guide you’ll discover how the **document annotation API** empowers you to embed rich annotation features—such as highlights, comments, and shapes—directly into PDF, Word, Excel, PowerPoint, and many other file types. Whether you’re building a collaborative review portal, an educational app, or a legal‑document workflow, the API gives you a consistent, high‑performance way to work with annotations in both .NET and Java environments.

## Quick answers
- **What does the document annotation API do?** It lets developers add, edit, and manage annotations across 50+ document formats without external dependencies.  
- **Which platforms are supported?** .NET (Framework, Core, .NET 5/6) and Java (any JDK 8+).  
- **Do I need a license for development?** A free trial is available; a license is required for production use.  
- **Can I annotate PDFs and Office files with the same code?** Yes—one unified API handles PDFs, Word, Excel, PowerPoint, images, HTML, and more.  
- **Is cloud deployment possible?** Absolutely—run on Windows, Linux, macOS, Docker, or any cloud service.

## What is the document annotation API?

The document annotation API is a cross‑platform SDK for adding, editing, and removing annotations in documents. It supports over 50 formats—including PDF, Word, Excel, PowerPoint, images, and HTML—so you can work with a single object model and avoid format‑specific code, while preserving layout fidelity and metadata.

## Why choose GroupDocs.Annotation?

GroupDocs.Annotation stands out because it handles annotations for over 50 file types—including PDF, Word, Excel, PowerPoint, and images—without any external dependencies such as Adobe Reader or Microsoft Office. Its high‑performance rendering engine processes multi‑hundred‑page documents in under a second on standard servers, and built‑in collaboration tools let multiple users add threaded comments in real time.

- **Format independence** – One API works with over 50 document types, from PDFs to Excel spreadsheets.  
- **Rich annotation types** – Text markup, graphical shapes, comments, and collaborative reply threads are all built‑in.  
- **No external dependencies** – No need for Adobe Reader, Office, or other third‑party tools.  
- **High‑performance rendering** – Adjustable quality and resolution for fast preview generation.  
- **Cross‑platform support** – Seamlessly run on Windows, Linux, macOS, Docker, or serverless environments.

## Primary use cases
- **Document review workflows** – Enable reviewers to add comments and approve changes in real time.  
- **Educational applications** – Teachers can highlight study material and provide feedback directly in the document.  
- **Legal document processing** – Mark clauses, add notes, and track revisions on contracts.  
- **Healthcare documentation** – Highlight critical patient information while maintaining HIPAA compliance.  
- **Construction & engineering** – Annotate blueprints, schematics, and technical drawings with precise measurements.

## Getting started with .NET
Powerful document annotation for .NET applications

Integrate comprehensive annotation capabilities into your C# and .NET projects with our feature‑rich API.

[Explore .NET Tutorials](./net/)

### Essential .NET tutorials
- [**Document Loading**](./net/document-loading) - Load documents from files, streams, URLs, and cloud storage
- [**Annotation Types**](./net/text-annotations) - Implement text, graphical, form and image annotations
- [**Document Saving**](./net/document-saving) - Save annotated documents with various output options
- [**Annotation Management**](./net/annotation-management) - Add, update, delete and filter annotations programmatically
- [**Collaboration Features**](./net/reply-management) - Implement comment threads and collaborative review
- [**Document Preview**](./net/document-preview) - Generate document previews with custom resolution
- [**Form Fields**](./net/form-field-annotations) - Create interactive form components
- [**Document Analysis**](./net/document-information) - Extract metadata and page information
- [**Licensing Options**](./net/licensing-and-configuration) - Implement and configure licensing

### Advanced .NET features
- [**Document Preview**](./net/document-preview) - Generate document previews with custom resolution
- [**Form Fields**](./net/form-field-annotations) - Create interactive form components
- [**Document Analysis**](./net/document-information) - Extract metadata and page information
- [**Licensing Options**](./net/licensing-and-configuration) - Implement and configure licensing

## Getting started with Java
Java document annotation SDK

Add comprehensive annotation capabilities to Java applications with our platform‑independent API.

[Explore Java Tutorials](./java/)

### Essential Java tutorials
- [**Document Loading**](./java/document-loading) - Multiple methods to load documents including cloud storage integration
- [**Text Annotations**](./java/text-annotations) - Highlighting, underline, strikeout and text replacement
- [**Graphical Annotations**](./java/graphical-annotations) - Add arrows, shapes and measurements
- [**Image Annotations**](./java/image-annotations) - Insert and customize images in documents  
- [**Annotation Management**](./java/annotation-management) - Complete annotation lifecycle management

### Advanced Java features
- [**Document Preview**](./java/document-preview) - Generate high‑quality thumbnails and previews
- [**Collaboration Tools**](./java/reply-management) - Implement threaded comments and replies
- [**Document Information**](./java/document-information) - Access document metadata and structure
- [**Advanced Features**](./java/advanced-features) - Specialized annotation capabilities and optimizations
- [**Configuration Options**](./java/licensing-and-configuration) - Customize annotation behavior and performance

## How to try it today

AnnotationConfig is the configuration class used to set the license key and global settings for the SDK. To try the document annotation API right now, download the free trial from the GroupDocs website, add the NuGet package (for .NET) or Maven dependency (for Java) to your project, and initialize the AnnotationConfig with your license key. The sample projects included demonstrate loading a file, adding a highlight, and saving the annotated document in just a few lines of code.

### Free trial
Get started with a free trial to explore all features before purchasing.  
[Download Trial](https://releases.groupdocs.com/annotation/)

### API documentation
Detailed API references for all supported platforms.  
[Browse API Reference](https://reference.groupdocs.com/annotation/)

## Frequently asked questions

**Q: Can I use the document annotation API in a commercial product?**  
A: Yes. A valid GroupDocs license is required for production deployments, and a free trial is available for evaluation.

**Q: Does the API support password‑protected PDFs?**  
A: Absolutely. You can supply the password when opening the document, and all annotation operations work transparently.

**Q: Which .NET versions are compatible?**  
A: The SDK supports .NET Framework 4.5+, .NET Core 3.1+, .NET 5, and .NET 6+.

**Q: How does the API handle large files?**  
`Document.OptimizeResources()` is a method that frees cached data and reduces memory usage during annotation operations.  
It streams content and offers memory‑optimizing methods such as `Document.OptimizeResources()` to keep memory usage low.

**Q: Is there built‑in support for cloud storage services?**  
A: Yes. You can load and save documents directly from Amazon S3, Azure Blob Storage, Google Cloud Storage, and other cloud providers.

---

**Last updated:** 2026-08-04  
**Tested with:** GroupDocs.Annotation 23.11 for .NET & Java  
**Author:** GroupDocs