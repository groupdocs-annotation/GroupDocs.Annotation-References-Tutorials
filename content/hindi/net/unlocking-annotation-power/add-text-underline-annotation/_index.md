---
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट अंडरलाइन एनोटेशन जोड़ने का तरीका जानें। सहयोग और संचार को सहजता से बढ़ाएँ।"
"linktitle": "दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, हम GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन जोड़ने की प्रक्रिया के बारे में जानेंगे। टेक्स्ट अंडरलाइन एनोटेशन दस्तावेज़ के विशिष्ट भागों, जैसे महत्वपूर्ण अंश या मुख्य बिंदुओं पर ज़ोर देने के लिए उपयोगी हो सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ स्थापित हैं:
1. .NET के लिए GroupDocs.Annotation: .NET के लिए GroupDocs.Annotation को डाउनलोड करें और इंस्टॉल करें [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके सिस्टम पर .NET फ्रेमवर्क स्थापित है।

## नामस्थान आयात करना
सबसे पहले, आइए अपने प्रोजेक्ट में आवश्यक नेमस्पेस आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

अब, आइए इस उदाहरण को कई चरणों में विभाजित करें:
## चरण 1: आउटपुट पथ परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
इस चरण में, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेट दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर आरंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
यहाँ, हम एक उदाहरण आरंभ करते हैं `Annotator` इनपुट दस्तावेज़ का पथ प्रदान करके क्लास को कॉन्फ़िगर करें।
## चरण 3: रेखांकित एनोटेशन बनाएँ
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // केवल Word और PDF दस्तावेज़ों का समर्थन करता है
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
इस चरण में एक बनाना शामिल है `UnderlineAnnotation` फ़ॉन्ट रंग, संदेश, अपारदर्शिता, पृष्ठ संख्या, पृष्ठभूमि रंग, रेखांकन रंग, बिंदु और उत्तर जैसे विभिन्न गुणों वाली ऑब्जेक्ट।
## चरण 4: दस्तावेज़ में एनोटेशन जोड़ें
```csharp
annotator.Add(underline);
```
यहां, हम दस्तावेज़ में रेखांकित एनोटेशन जोड़ते हैं।
## चरण 5: एनोटेट दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
अंत में, हम एनोटेट दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजते हैं।

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में टेक्स्ट अंडरलाइन एनोटेशन कैसे जोड़ा जाता है। यह शक्तिशाली लाइब्रेरी दस्तावेज़ सहयोग और संचार को बढ़ाने के लिए विभिन्न एनोटेशन विकल्प प्रदान करती है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं रेखांकित एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार रंग, अपारदर्शिता और स्थिति जैसे गुणों को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation विभिन्न दस्तावेज़ प्रारूपों के साथ संगत है?
हां, GroupDocs.Annotation Word और PDF सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
बिल्कुल, GroupDocs.Annotation आपको एक दस्तावेज़ में विभिन्न प्रकार के कई एनोटेशन जोड़ने की अनुमति देता है।
### क्या GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
हां, आप यहां से निःशुल्क परीक्षण संस्करण का उपयोग कर सकते हैं [यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Annotation के लिए समर्थन कहां मिल सकता है?
आप GroupDocs.Annotation समुदाय फ़ोरम से सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).