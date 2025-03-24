---
title: पीडीएफ दस्तावेज़ में ड्रॉपडाउन घटक जोड़ें
linktitle: पीडीएफ दस्तावेज़ में ड्रॉपडाउन घटक जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए GroupDocs.Annotation का उपयोग करके PDF में ड्रॉपडाउन घटकों को जोड़ने का तरीका जानें। निर्बाध एकीकरण के लिए हमारी चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 12
url: /hi/net/document-components/add-dropdown-component-to-pdf/
---

# पीडीएफ दस्तावेज़ में ड्रॉपडाउन घटक जोड़ें

## परिचय
.NET के लिए GroupDocs.Annotation पीडीएफ दस्तावेज़ों को प्रोग्रामेटिक रूप से एनोटेट करने के लिए टूल का एक शक्तिशाली सेट प्रदान करता है। एक उपयोगी सुविधा पीडीएफ दस्तावेजों में ड्रॉपडाउन घटकों को जोड़ने, उनकी अन्तरक्रियाशीलता और प्रयोज्य को बढ़ाने की क्षमता है।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Annotation: यहां से लाइब्रेरी डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास परिवेश: एक .NET विकास परिवेश स्थापित करें।
3. पीडीएफ दस्तावेज़: पीडीएफ दस्तावेज़ तैयार करें जिसमें आप ड्रॉपडाउन घटक जोड़ना चाहते हैं।

## नामस्थान आयात करना
सुनिश्चित करें कि आप अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ सेट करें
आउटपुट पथ को परिभाषित करें जहां संशोधित दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
 का एक उदाहरण बनाएं`Annotator` इनपुट पीडीएफ दस्तावेज़ का पथ पारित करके कक्षा:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## चरण 3: ड्रॉपडाउन घटक बनाएं
ड्रॉपडाउन घटक के गुणों को परिभाषित करें:
```csharp
DropdownComponent dropdown = new DropdownComponent
{
    Options = new List<string> { "Item1", "Item2", "Item3" },
    SelectedOption = null,
    Placeholder = "Choose option",
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is dropdown component",
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## चरण 4: ड्रॉपडाउन घटक जोड़ें
पीडीएफ दस्तावेज़ में ड्रॉपडाउन घटक जोड़ें:
```csharp
annotator.Add(dropdown);
```
## चरण 5: दस्तावेज़ सहेजें
संशोधित दस्तावेज़ सहेजें:
```csharp
annotator.Save("result.pdf");
```
## चरण 6: आउटपुट पथ प्रदर्शित करें
आउटपुट पथ के साथ दस्तावेज़ की सफल बचत का संकेत देने वाला एक संदेश प्रदर्शित करें:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने पता लगाया है कि .NET के लिए GroupDocs.Annotation का उपयोग करके ड्रॉपडाउन घटकों को जोड़कर पीडीएफ दस्तावेज़ों को कैसे बढ़ाया जाए। चरण-दर-चरण मार्गदर्शिका का पालन करके, आप इस कार्यक्षमता को अपने .NET अनुप्रयोगों में आसानी से एकीकृत कर सकते हैं, जिससे उपयोगकर्ताओं को इंटरैक्टिव और गतिशील दस्तावेज़ देखने का अनुभव प्रदान किया जा सकता है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं ड्रॉपडाउन घटक के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार विभिन्न गुणों जैसे विकल्प, प्लेसहोल्डर टेक्स्ट, बॉक्स आयाम, पेन रंग और शैली को अनुकूलित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Annotation .NET के सभी संस्करणों के साथ संगत है?
हां, .NET के लिए GroupDocs.Annotation .NET फ्रेमवर्क के सभी प्रमुख संस्करणों के साथ संगत है।
### क्या मैं एक ही पीडीएफ दस्तावेज़ में एकाधिक ड्रॉपडाउन घटक जोड़ सकता हूँ?
बिल्कुल, आप एक पीडीएफ दस्तावेज़ में आवश्यकतानुसार उतने ड्रॉपडाउन घटक जोड़ सकते हैं।
### क्या .NET के लिए GroupDocs.Annotation अन्य एनोटेशन प्रकारों का समर्थन करता है?
हाँ, .NET के लिए GroupDocs.Annotation टेक्स्ट, क्षेत्र, बिंदु और स्ट्राइकआउट एनोटेशन सहित विभिन्न एनोटेशन प्रकारों का समर्थन करता है।
### क्या परीक्षण प्रयोजनों के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप परीक्षण संस्करण तक पहुँच सकते हैं[यहाँ](https://releases.groupdocs.com/).