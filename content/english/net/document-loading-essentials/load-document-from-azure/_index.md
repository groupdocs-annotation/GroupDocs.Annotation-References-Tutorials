---
title: Load Document from Azure
linktitle: Load Document from Azure
second_title: GroupDocs.Annotation .NET API
description: Learn how to annotate documents in .NET using GroupDocs.Annotation. Step-by-step tutorial for seamless integration with Azure Blob Storage.
type: docs
weight: 11
url: /net/document-loading-essentials/load-document-from-azure/
---
## Introduction
In the realm of document management and collaboration, GroupDocs.Annotation for .NET emerges as a robust solution, facilitating seamless annotation and markup functionalities within .NET applications. This tutorial delves into the intricacies of leveraging GroupDocs.Annotation for .NET to annotate documents, offering step-by-step guidance from prerequisites to advanced usage.
## Prerequisites
Before diving into GroupDocs.Annotation for .NET, ensure you have the following prerequisites in place:
1. Installation of .NET Framework: GroupDocs.Annotation for .NET requires a compatible .NET runtime environment. Ensure that you have the .NET Framework installed on your system.
2. Access to GroupDocs.Annotation Library: Obtain access to the GroupDocs.Annotation for .NET library either by downloading it from the website or through package managers like NuGet.
3. Document to Annotate: Prepare the document (e.g., PDF) that you intend to annotate. Ensure that the document is accessible either locally or via a cloud storage service like Azure Blob Storage.

## Import Namespaces
To begin annotating documents using GroupDocs.Annotation for .NET, import the necessary namespaces into your project. This step ensures that you have access to the required classes and functionalities.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Load Document from Azure
To annotate a document stored in Azure Blob Storage, follow these steps:
### Step 1: Set Output Path
Define the output path where the annotated document will be saved.
```csharp
string outputPath = Path.Combine(Constants.GetOutputDirectoryPath(), "result" + Path.GetExtension("input.pdf"));
```
### Step 2: Download Document
Retrieve the document from Azure Blob Storage by invoking the `DownloadFile` method.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Annotation Logic
    annotator.Save(outputPath);
}
```
## Download File from Azure Blob Storage
To download the document from Azure Blob Storage, implement the `DownloadFile` method.
### Step 1: Retrieve Blob
Access the Azure Blob Storage container and retrieve the desired blob.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Step 2: Download Blob Content
Download the blob content into a memory stream.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Get Azure Blob Storage Container
To interact with Azure Blob Storage, implement the `GetContainer` method.
### Step 1: Initialize Storage Credentials
Provide the necessary account credentials and endpoint information.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Step 2: Create Blob Client
Create a client to interact with Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Step 3: Retrieve Container Reference
Obtain a reference to the specified container.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Step 4: Create Container if Not Exists
Ensure that the container exists, and create it if not.
```csharp
container.CreateIfNotExists();
```

## Conclusion
GroupDocs.Annotation for .NET empowers developers with robust document annotation capabilities, seamlessly integrating into .NET applications. By following the steps outlined in this tutorial, you can effectively leverage the functionalities of GroupDocs.Annotation to annotate documents stored in Azure Blob Storage.
#### FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
GroupDocs.Annotation supports a wide range of document formats, including PDF, DOCX, PPTX, and more.
### Can annotations be customized according to specific requirements?
Yes, GroupDocs.Annotation offers extensive customization options for annotations, allowing users to modify appearance, behavior, and metadata.
### Is GroupDocs.Annotation suitable for collaborative document annotation?
Absolutely! GroupDocs.Annotation facilitates collaborative document annotation by enabling multiple users to add, edit, and review annotations simultaneously.
### Does GroupDocs.Annotation offer cross-platform compatibility?
Yes, GroupDocs.Annotation is designed to work seamlessly across various platforms, including Windows, Linux, and macOS.
### Is technical support available for GroupDocs.Annotation users?
Yes, GroupDocs provides comprehensive technical support through its forums and dedicated support channels.
