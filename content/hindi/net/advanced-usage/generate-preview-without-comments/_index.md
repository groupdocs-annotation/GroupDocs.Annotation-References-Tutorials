---
title: टिप्पणियों के बिना पूर्वावलोकन उत्पन्न करें
linktitle: टिप्पणियों के बिना पूर्वावलोकन उत्पन्न करें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ एनोटेशन क्षमताओं को अपने .NET अनुप्रयोगों में सहजता से एकीकृत करने का तरीका जानें।
type: docs
weight: 14
url: /hi/net/advanced-usage/generate-preview-without-comments/
---
## परिचय
.NET के लिए GroupDocs.Annotation एक शक्तिशाली उपकरण है जो डेवलपर्स को अपने .NET अनुप्रयोगों में एनोटेशन सुविधाओं को निर्बाध रूप से शामिल करने की अनुमति देता है। चाहे आप दस्तावेज़ प्रबंधन प्रणाली, सहयोग प्लेटफ़ॉर्म, या दस्तावेज़ एनोटेशन क्षमताओं की आवश्यकता वाले किसी अन्य एप्लिकेशन पर काम कर रहे हों, GroupDocs.Annotation आपके एप्लिकेशन की कार्यक्षमता को बढ़ाने के लिए उपकरणों का एक व्यापक सेट प्रदान करता है।
## आवश्यक शर्तें
.NET के लिए GroupDocs.Annotation का उपयोग करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ स्थापित हैं:
### 1. .NET के लिए GroupDocs.Annotation स्थापित करें
 आरंभ करने के लिए, आपको .NET के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल करना होगा। आप डाउनलोड लिंक पा सकते हैं[यहाँ](https://releases.groupdocs.com/annotation/net/). सुचारू सेटअप प्रक्रिया के लिए दस्तावेज़ में दिए गए इंस्टॉलेशन निर्देशों का पालन करें।
### 2. लाइसेंस प्राप्त करें
 .NET के लिए GroupDocs.Annotation को व्यावसायिक उपयोग के लिए लाइसेंस की आवश्यकता होती है। आप से लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/buy) या अस्थायी लाइसेंस का विकल्प चुनें[यहाँ](https://purchase.groupdocs.com/temporary-license/) परीक्षण प्रयोजनों के लिए.
### 3. .NET फ्रेमवर्क से परिचित होना
.NET के लिए GroupDocs.Annotation का प्रभावी ढंग से उपयोग करने के लिए .NET फ्रेमवर्क और C# प्रोग्रामिंग भाषा का बुनियादी ज्ञान आवश्यक है।

## नामस्थान आयात करें
अब जब आपने आवश्यक शर्तें सेट कर ली हैं, तो आइए अपने .NET एप्लिकेशन में आवश्यक नेमस्पेस आयात करें।

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

.NET के लिए GroupDocs.Annotation का उपयोग करके टिप्पणियों के बिना पूर्वावलोकन तैयार करने के लिए इन चरण-दर-चरण निर्देशों का पालन करें:
## चरण 1: एनोटेटर प्रारंभ करें
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## चरण 2: पूर्वावलोकन विकल्प कॉन्फ़िगर करें
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## चरण 3: पूर्वावलोकन प्रारूप और पृष्ठ संख्या निर्दिष्ट करें
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## चरण 4: टिप्पणियों का प्रतिपादन अक्षम करें
```csharp
    previewOptions.RenderComments = false;
```
## चरण 5: पूर्वावलोकन उत्पन्न करें
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
एक बार जब आप इन चरणों का पालन कर लेते हैं, तो आपका .NET एप्लिकेशन टिप्पणी प्रस्तुत किए बिना दस्तावेज़ से निर्दिष्ट पृष्ठों का पूर्वावलोकन उत्पन्न करने में सक्षम होगा।

## निष्कर्ष
.NET के लिए GroupDocs.Annotation की बदौलत आपके .NET अनुप्रयोगों में एनोटेशन सुविधाओं को शामिल करना इतना आसान कभी नहीं रहा। इस ट्यूटोरियल में उल्लिखित चरणों का पालन करके, आप सहयोग और दस्तावेज़ प्रबंधन को बढ़ाते हुए दस्तावेज़ एनोटेशन क्षमताओं को अपने अनुप्रयोगों में सहजता से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
.NET के लिए GroupDocs.Annotation PDF, DOCX, PPTX, XLSX और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं .NET के लिए GroupDocs.Annotation का उपयोग करके उत्पन्न एनोटेशन की उपस्थिति को अनुकूलित कर सकता हूँ?
हां, .NET के लिए GroupDocs.Annotation व्यापक अनुकूलन विकल्प प्रदान करता है, जिससे आप अपने एप्लिकेशन की आवश्यकताओं के अनुरूप एनोटेशन की उपस्थिति को अनुकूलित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Annotation बहु-उपयोगकर्ता सहयोग का समर्थन करता है?
हाँ, .NET के लिए GroupDocs.Annotation सहयोगी एनोटेशन सुविधाएँ प्रदान करता है, जो कई उपयोगकर्ताओं को एक साथ दस्तावेज़ों को एनोटेट करने में सक्षम बनाता है।
### क्या .NET के लिए GroupDocs.Annotation के लिए तकनीकी सहायता उपलब्ध है?
 हां, .NET के लिए GroupDocs.Annotation के लिए तकनीकी सहायता उपलब्ध है[सहयता मंच](https://forum.groupdocs.com/c/annotation/10).
### क्या मैं खरीदने से पहले .NET के लिए GroupDocs.Annotation निःशुल्क आज़मा सकता हूँ?
 हाँ, आप निःशुल्क परीक्षण डाउनलोड करके .NET के लिए GroupDocs.Annotation की सुविधाओं का पता लगा सकते हैं[यहाँ](https://releases.groupdocs.com/).