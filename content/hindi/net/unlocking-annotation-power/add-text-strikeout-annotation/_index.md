---
"description": ".NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ने का तरीका जानें। सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को कुशलतापूर्वक बढ़ाएँ।"
"linktitle": "दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ें"
"second_title": "GroupDocs.Annotation .NET एपीआई"
"title": "दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ें"
"url": "/hi/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, हम GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ने का तरीका जानेंगे। यह लाइब्रेरी विभिन्न दस्तावेज़ प्रकारों को एनोटेट करने, सहयोग बढ़ाने और दस्तावेज़ समीक्षा प्रक्रियाओं के लिए शक्तिशाली उपकरण प्रदान करती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. .NET के लिए GroupDocs.Annotation: लाइब्रेरी स्थापित करें। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास वातावरण: .NET विकास के लिए उपयुक्त विकास वातावरण स्थापित करें।
3. दस्तावेज़: टिप्पणी करने के लिए एक दस्तावेज़ तैयार रखें, जैसे कि PDF फ़ाइल.

## नामस्थान आयात करना
सबसे पहले, GroupDocs.Annotation की कार्यक्षमताओं तक पहुँचने के लिए आवश्यक नामस्थानों को आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

अब, आइए टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ने की प्रक्रिया को कई चरणों में विभाजित करें:
## चरण 1: आउटपुट पथ परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
यहां, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेट दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर आरंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
इनपुट दस्तावेज़ (इस मामले में PDF फ़ाइल) का पथ प्रदान करके एनोटेटर ऑब्जेक्ट को आरंभ करें।
## चरण 3: स्ट्राइकआउट एनोटेशन बनाएँ
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
संदेश, अपारदर्शिता, पृष्ठ संख्या, पृष्ठभूमि रंग, बिंदु (निर्देशांक) और उत्तर जैसे वांछित गुणों के साथ एक स्ट्राइकआउटएनोटेशन ऑब्जेक्ट बनाएं।
## चरण 4: एनोटेशन जोड़ें
```csharp
annotator.Add(strikeout);
```
बनाए गए स्ट्राइकआउट एनोटेशन को दस्तावेज़ में जोड़ें.
## चरण 5: दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
एनोटेट किए गए दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें.

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि GroupDocs.Annotation for .NET का उपयोग करके दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन कैसे जोड़ा जाता है। यह शक्तिशाली लाइब्रेरी कुशल दस्तावेज़ एनोटेशन को सक्षम बनाती है, सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को बढ़ाती है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Annotation विभिन्न दस्तावेज़ प्रारूपों के साथ संगत है?
हां, GroupDocs.Annotation पीडीएफ, वर्ड, एक्सेल, पावरपॉइंट और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, आप अपनी आवश्यकताओं के अनुसार एनोटेशन गुण जैसे रंग, अपारदर्शिता, फ़ॉन्ट आकार आदि को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation सहयोग सुविधाएं प्रदान करता है?
हां, GroupDocs.Annotation उपयोगकर्ताओं को दस्तावेज़ों में टिप्पणियां, उत्तर और एनोटेशन जोड़ने की अनुमति देकर सहयोग की सुविधा प्रदान करता है।
### क्या कोई निःशुल्क परीक्षण उपलब्ध है?
हां, आप यहां से निःशुल्क परीक्षण का लाभ उठा सकते हैं [यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Annotation के लिए समर्थन कहां मिल सकता है?
आप यहाँ से सहायता प्राप्त कर सकते हैं [ग्रुपडॉक्स.एनोटेशन फ़ोरम](https://forum.groupdocs.com/c/annotation/10).