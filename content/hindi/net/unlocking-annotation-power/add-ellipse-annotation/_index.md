---
title: दस्तावेज़ में एलिप्स एनोटेशन जोड़ें
linktitle: दस्तावेज़ में एलिप्स एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि GroupDocs.Annotation का उपयोग करके .NET में दस्तावेज़ों में दीर्घवृत्त एनोटेशन कैसे जोड़ें। सहजता से सहयोग और संचार बढ़ाएँ।
weight: 13
url: /hi/net/unlocking-annotation-power/add-ellipse-annotation/
---
## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में दीर्घवृत्त एनोटेशन कैसे जोड़ा जाए। यह चरण-दर-चरण मार्गदर्शिका आपको प्रक्रिया से गुजराएगी, यह सुनिश्चित करते हुए कि आप प्रत्येक चरण को स्पष्ट रूप से समझें।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  .NET के लिए GroupDocs.Annotation: सुनिश्चित करें कि आपने .NET के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल कर लिया है। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. आईडीई (एकीकृत विकास पर्यावरण): कोड लिखने और निष्पादित करने के लिए आपको अपने सिस्टम पर विजुअल स्टूडियो जैसे एक आईडीई स्थापित करने की आवश्यकता होगी।

## नामस्थान आयात करें
सबसे पहले, अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ सेट करें
आउटपुट पथ को परिभाषित करें जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर प्रारंभ करें
इनपुट दस्तावेज़ पथ प्रदान करके एनोटेटर को प्रारंभ करें:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## चरण 3: एलिप्स एनोटेशन बनाएं
 का एक उदाहरण बनाएं`EllipseAnnotation` क्लास बनाएं और उसके गुण सेट करें:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
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
## चरण 4: एनोटेशन जोड़ें
दस्तावेज़ में दीर्घवृत्त एनोटेशन जोड़ें:
```csharp
annotator.Add(ellipse);
```
## चरण 5: दस्तावेज़ सहेजें
एनोटेटेड दस्तावेज़ को आउटपुट पथ पर सहेजें:
```csharp
annotator.Save(outputPath);
```

## निष्कर्ष
बधाई हो! आपने .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में सफलतापूर्वक एक दीर्घवृत्त एनोटेशन जोड़ दिया है। दस्तावेज़ सहयोग और संचार को बढ़ाने के लिए अब आप इस कार्यक्षमता को अपने .NET अनुप्रयोगों में एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं दीर्घवृत्त एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार विभिन्न गुणों जैसे पृष्ठभूमि रंग, बॉर्डर रंग, अस्पष्टता आदि को अनुकूलित कर सकते हैं।
### क्या .NET के लिए GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
.NET के लिए GroupDocs.Annotation PDF, DOCX, PPTX, XLSX और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
हां, आप एक ही दस्तावेज़ में दीर्घवृत्त, आयत, पाठ आदि सहित कई एनोटेशन जोड़ सकते हैं।
### क्या परीक्षण प्रयोजनों के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हां, आप यहां से नि:शुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/) इसकी विशेषताओं का मूल्यांकन करने के लिए।
### मुझे .NET के लिए GroupDocs.Annotation के लिए तकनीकी सहायता कहां मिल सकती है?
 आप GroupDocs.Annotation समुदाय मंच से तकनीकी सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).