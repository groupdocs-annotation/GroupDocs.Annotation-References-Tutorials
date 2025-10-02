---
"description": "GroupDocs.Annotation का उपयोग करके .NET में दस्तावेज़ों में दीर्घवृत्त एनोटेशन जोड़ने का तरीका जानें। सहयोग और संचार को सहजता से बढ़ाएँ।"
"linktitle": "दस्तावेज़ में दीर्घवृत्त एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में दीर्घवृत्त एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# दस्तावेज़ में दीर्घवृत्त एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, आप सीखेंगे कि GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में दीर्घवृत्त एनोटेशन कैसे जोड़ें। यह चरण-दर-चरण मार्गदर्शिका आपको प्रक्रिया के माध्यम से ले जाएगी, यह सुनिश्चित करते हुए कि आप प्रत्येक चरण को स्पष्ट रूप से समझते हैं।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1. .NET के लिए GroupDocs.Annotation: सुनिश्चित करें कि आपने .NET के लिए GroupDocs.Annotation डाउनलोड और इंस्टॉल किया है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. IDE (एकीकृत विकास वातावरण): कोड लिखने और निष्पादित करने के लिए आपको अपने सिस्टम पर Visual Studio जैसे IDE को स्थापित करने की आवश्यकता होगी।

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
आउटपुट पथ को परिभाषित करें जहां एनोटेट दस्तावेज़ सहेजा जाएगा:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## चरण 2: एनोटेटर आरंभ करें
इनपुट दस्तावेज़ पथ प्रदान करके एनोटेटर को आरंभ करें:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## चरण 3: दीर्घवृत्त एनोटेशन बनाएँ
इसका एक उदाहरण बनाएं `EllipseAnnotation` क्लास और उसके गुण सेट करें:
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
एनोटेट किए गए दस्तावेज़ को आउटपुट पथ पर सहेजें:
```csharp
annotator.Save(outputPath);
```

## निष्कर्ष
बधाई हो! आपने .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ में सफलतापूर्वक एक दीर्घवृत्त एनोटेशन जोड़ा है। अब आप दस्तावेज़ सहयोग और संचार को बढ़ाने के लिए इस कार्यक्षमता को अपने .NET अनुप्रयोगों में एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या मैं दीर्घवृत्त एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
हां, आप अपनी आवश्यकताओं के अनुसार विभिन्न गुणों जैसे पृष्ठभूमि रंग, सीमा रंग, अपारदर्शिता आदि को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation for .NET सभी दस्तावेज़ प्रारूपों के साथ संगत है?
.NET के लिए GroupDocs.Annotation पीडीएफ, DOCX, पीपीटीएक्स, एक्सएलएसएक्स, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एक ही दस्तावेज़ में एकाधिक एनोटेशन जोड़ सकता हूँ?
हां, आप एक ही दस्तावेज़ में दीर्घवृत्त, आयत, पाठ आदि सहित कई एनोटेशन जोड़ सकते हैं।
### क्या परीक्षण के उद्देश्य से कोई परीक्षण संस्करण उपलब्ध है?
हां, आप यहां से निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/) इसकी विशेषताओं का मूल्यांकन करने के लिए।
### मैं .NET के लिए GroupDocs.Annotation के लिए तकनीकी सहायता कहां से प्राप्त कर सकता हूं?
आप GroupDocs.Annotation समुदाय फ़ोरम से तकनीकी सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.groupdocs.com/c/annotation/10).