---
title: Set Metered License - GroupDocs.Annotation .NET
linktitle: Set Metered License - GroupDocs.Annotation .NET
second_title: GroupDocs.Annotation .NET API
description: Learn how to set up a metered license for GroupDocs.Annotation .NET to resource usage and document annotation capabilities in your .NET applications.
type: docs
weight: 12
url: /net/applying-licenses/set-metered-license-groupdocs-annotation-dotnet/
---
## Introduction
GroupDocs.Annotation for .NET is a powerful library that empowers developers to add document annotation capabilities to their .NET applications effortlessly. Whether you're building a document management system, collaboration platform, or any application that involves document review and markup, GroupDocs.Annotation for .NET provides a comprehensive set of tools to streamline the process.
In this tutorial, we'll delve into the process of setting up a metered license for GroupDocs.Annotation .NET. A metered license allows you to pay only for the resources you consume, making it a cost-effective solution for projects of any scale. By following the steps outlined below, you'll be able to seamlessly integrate GroupDocs.Annotation into your .NET application while optimizing resource usage and maintaining budgetary control.
## Prerequisites
Before diving into the tutorial, ensure that you have the following prerequisites:
1. GroupDocs.Annotation for .NET Library: Download the library from the [website](https://releases.groupdocs.com/annotation/net/).
2. Access to GroupDocs Account: You'll need a GroupDocs account to obtain the public and private keys required for setting up the metered license. If you don't have an account yet, you can sign up for a free trial [here](https://releases.groupdocs.com/).
3. Basic Understanding of C# and .NET Framework: Familiarity with C# programming language and .NET framework will be beneficial for implementing the steps outlined in this tutorial.

## Import Namespaces
To begin, make sure to import the necessary namespaces into your C# project. These namespaces are essential for interacting with GroupDocs.Annotation functionality.
```csharp
using System;
```
## Step 1: Obtain Public and Private Keys
Before setting up the metered license, you need to obtain your public and private keys from your GroupDocs account dashboard.
1. Log in to your GroupDocs account.
2. Navigate to the license management section.
3. Copy your public and private keys provided by GroupDocs.
## Step 2: Set Metered License
Once you have obtained your public and private keys, you can set up the metered license in your .NET application.
```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusion
In conclusion, setting up a metered license for GroupDocs.Annotation .NET is a straightforward process that ensures efficient resource utilization and cost-effectiveness for your document annotation projects. By following the steps outlined in this tutorial, you can seamlessly integrate GroupDocs.Annotation into your .NET application and enhance document collaboration and review capabilities.
## FAQ's
### Can I use GroupDocs.Annotation for .NET in commercial projects?
Yes, GroupDocs.Annotation for .NET can be used in both commercial and non-commercial projects. However, you need to acquire an appropriate license based on your project requirements.
### Is there a trial version available for GroupDocs.Annotation for .NET?
Yes, you can avail of a free trial of GroupDocs.Annotation for .NET by visiting [this link](https://releases.groupdocs.com/).
### How can I obtain technical support for GroupDocs.Annotation for .NET?
You can seek technical support by visiting the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10).
### Are there any temporary license options available?
Yes, you can obtain a temporary license from GroupDocs for short-term usage or evaluation purposes. Visit [this link](https://purchase.groupdocs.com/temporary-license/) for more information.
### Can I customize the annotation features according to my project requirements?
Yes, GroupDocs.Annotation for .NET offers extensive customization options, allowing you to tailor the annotation features to suit your specific project needs.
