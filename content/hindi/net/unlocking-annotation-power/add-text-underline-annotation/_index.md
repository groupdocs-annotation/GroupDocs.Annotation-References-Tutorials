---
title: दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ें
linktitle: दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट अंडरलाइन एनोटेशन कैसे जोड़ें। सहजता से सहयोग और संचार बढ़ाएँ।
weight: 27
url: /hi/net/unlocking-annotation-power/add-text-underline-annotation/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ने की प्रक्रिया से गुजरेंगे। टेक्स्ट अंडरलाइन एनोटेशन किसी दस्तावेज़ के विशिष्ट भागों, जैसे महत्वपूर्ण अंश या मुख्य बिंदुओं पर जोर देने के लिए उपयोगी हो सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ स्थापित हैं:
1.  .NET के लिए GroupDocs.Annotation: .NET के लिए GroupDocs.Annotation को डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके सिस्टम पर .NET फ्रेमवर्क स्थापित है।

## नामस्थान आयात करना
सबसे पहले, आइए अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

अब, आइए उदाहरण को कई चरणों में विभाजित करें:
## चरण 1: आउटपुट पथ को परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
इस चरण में, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर प्रारंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 यहां, हम इसका एक उदाहरण प्रारंभ करते हैं`Annotator` इनपुट दस्तावेज़ का पथ प्रदान करके क्लास।
## चरण 3: अंडरलाइन एनोटेशन बनाएं
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // केवल वर्ड और पीडीएफ दस्तावेज़ों का समर्थन करता है
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
 इस चरण में एक बनाना शामिल है`UnderlineAnnotation`फ़ॉन्ट रंग, संदेश, अस्पष्टता, पृष्ठ संख्या, पृष्ठभूमि रंग, रेखांकित रंग, बिंदु और उत्तर जैसे विभिन्न गुणों वाली वस्तु।
## चरण 4: दस्तावेज़ में एनोटेशन जोड़ें
```csharp
annotator.Add(underline);
```
यहां, हम दस्तावेज़ में अंडरलाइन एनोटेशन जोड़ते हैं।
## चरण 5: एनोटेटेड दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
अंत में, हम एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजते हैं।

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन कैसे जोड़ा जाए। यह शक्तिशाली लाइब्रेरी दस्तावेज़ सहयोग और संचार को बढ़ाने के लिए विभिन्न एनोटेशन विकल्प प्रदान करती है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं अंडरलाइन एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार रंग, अस्पष्टता और स्थिति जैसे गुणों को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation विभिन्न दस्तावेज़ प्रारूपों के साथ संगत है?
हाँ, GroupDocs.Annotation Word और PDF सहित दस्तावेज़ स्वरूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
बिल्कुल, GroupDocs.Annotation आपको एक दस्तावेज़ में विभिन्न प्रकार के कई एनोटेशन जोड़ने की अनुमति देता है।
### क्या GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हां, आप नि:शुल्क परीक्षण संस्करण तक पहुंच सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Annotation के लिए समर्थन कहाँ से मिल सकता है?
 आप GroupDocs.Annotation समुदाय मंच से समर्थन प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).