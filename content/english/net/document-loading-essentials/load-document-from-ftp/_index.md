---
title: Load Document from FTP
linktitle: Load Document from FTP
second_title: GroupDocs.Annotation .NET API
description: Enhance your .NET applications with GroupDocs.Annotation for seamless document annotation. Step-by-step tutorial included.
weight: 12
url: /net/document-loading-essentials/load-document-from-ftp/
---
## Introduction
GroupDocs.Annotation for .NET is a versatile library designed to facilitate document annotation capabilities within .NET applications effortlessly. Whether you're dealing with PDFs, Microsoft Office documents, images, or other formats, this library provides a unified solution for adding annotations, such as comments, highlights, and shapes, to enhance collaboration and document management.
## Prerequisites
Before diving into the tutorial, ensure that you have the following prerequisites in place:
1. Knowledge of C#: Proficiency in C# programming language is essential to understand and implement the code examples provided in this tutorial.
2. GroupDocs.Annotation for .NET: Make sure to download and install GroupDocs.Annotation for .NET from the [download link](https://releases.groupdocs.com/annotation/net/). Follow the installation instructions to integrate the library into your .NET project successfully.
## Import Namespaces
In order to utilize GroupDocs.Annotation for .NET functionalities, you need to import the required namespaces into your C# project. Follow these steps:

Within your C# project, include the necessary namespaces at the beginning of your code file:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Now, let's delve into the process of loading a document from FTP and adding annotations to it using GroupDocs.Annotation for .NET.
## Step 1: Define Output Path
Specify the output path where the annotated document will be saved.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Step 2: Load Document from FTP
Retrieve the document from the FTP server using the provided file path.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Annotation code will be added here
}
```
## Step 3: Add Annotation
Define and add the desired annotation, such as an area annotation, to the document.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Step 4: Save Annotated Document
Save the annotated document to the specified output path.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Step 5: Retrieve File from FTP
Implement the method to fetch the file from the FTP server.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Step 6: Create FTP Request
Generate an FTP request to download the file.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Step 7: Get File Stream
Retrieve the file stream from the FTP response.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Conclusion
In conclusion, GroupDocs.Annotation for .NET empowers developers to seamlessly integrate document annotation functionalities into their .NET applications. By following the step-by-step guide outlined in this tutorial, you can efficiently load documents from FTP and add annotations with ease, enhancing collaboration and document management within your applications.
## FAQ's
### Is GroupDocs.Annotation for .NET compatible with all document formats?
Yes, GroupDocs.Annotation for .NET supports a wide range of document formats, including PDF, Microsoft Office documents, images, and more.
### Can I customize the appearance of annotations added using GroupDocs.Annotation for .NET?
Absolutely, GroupDocs.Annotation for .NET offers extensive customization options for annotation appearance, including colors, styles, and shapes.
### Does GroupDocs.Annotation for .NET provide support for cloud storage services?
Yes, GroupDocs.Annotation for .NET seamlessly integrates with popular cloud storage services, allowing you to load and save documents from services like Dropbox, Google Drive, and OneDrive.
### Is there a trial version available for GroupDocs.Annotation for .NET?
Yes, you can explore the features of GroupDocs.Annotation for .NET by downloading the free trial version from the [release page](https://releases.groupdocs.com/).
### How can I get technical assistance or support for GroupDocs.Annotation for .NET?
For technical assistance, troubleshooting, or general inquiries, you can visit the GroupDocs.Annotation for .NET [support forum](https://forum.groupdocs.com/c/annotation/10).
