---
title: Get All Version Keys on Document
linktitle: Get All Version Keys on Document
second_title: GroupDocs.Annotation .NET API
description: Learn how to retrieve all version keys on a document using GroupDocs.Annotation for .NET. Enhance your document management capabilities with this comprehensive.
weight: 16
url: /net/advanced-usage/get-all-version-keys-document/
---

# Get All Version Keys on Document

## Introduction
In today's fast-paced digital world, effective document management is crucial for businesses and individuals alike. Whether you're collaborating on projects, reviewing contracts, or simply organizing your files, having the right tools can make all the difference. GroupDocs.Annotation for .NET offers a comprehensive solution for annotating and manipulating documents within .NET applications. In this tutorial, we'll explore how to leverage GroupDocs.Annotation for .NET to retrieve all version keys on a document.
## Prerequisites
Before we dive into the tutorial, ensure you have the following prerequisites:
### 1. Install GroupDocs.Annotation for .NET
To get started, you need to download and install GroupDocs.Annotation for .NET. You can obtain the latest version from the [download link](https://releases.groupdocs.com/annotation/net/).
### 2. Obtain API Credentials
Ensure you have the necessary API credentials to access GroupDocs.Annotation for .NET functionalities.

## Import Necessary Namespaces
Before proceeding, make sure to import the required namespaces into your project:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

Let's break down the process of getting all version keys on a document into simple steps:
## Step 1: Initialize the Annotator Object
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Code goes here
}
```
Initialize the `Annotator` object with the path to the document you want to work with.
## Step 2: Retrieve Version Keys
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
Invoke the `GetVersionsList()` method on the `Annotator` object to retrieve all version keys associated with the document. This method returns a list of version keys.

## Conclusion
GroupDocs.Annotation for .NET simplifies document annotation and manipulation tasks within .NET applications. By following this tutorial, you've learned how to retrieve all version keys on a document using GroupDocs.Annotation for .NET. Incorporate this functionality into your projects to enhance document management capabilities.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation for .NET supports a wide range of document formats, including PDF, DOCX, XLSX, PPTX, and more.
### Can I try GroupDocs.Annotation for .NET before purchasing?
Yes, you can explore the features of GroupDocs.Annotation for .NET by accessing the free trial available [here](https://releases.groupdocs.com/).
### How can I obtain support for GroupDocs.Annotation for .NET?
You can seek assistance and engage with the community through the support forum [here](https://forum.groupdocs.com/c/annotation/10).
### Are there temporary licenses available for GroupDocs.Annotation for .NET?
Yes, temporary licenses are available for evaluation purposes. You can obtain one from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I purchase GroupDocs.Annotation for .NET?
You can purchase GroupDocs.Annotation for .NET from the website [here](https://purchase.groupdocs.com/buy).
