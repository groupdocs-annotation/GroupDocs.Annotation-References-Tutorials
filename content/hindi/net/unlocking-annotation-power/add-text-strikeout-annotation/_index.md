---
title: दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ें
linktitle: दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: जानें कि .NET के लिए GroupDocs.Annotation का उपयोग करके दस्तावेज़ों में टेक्स्ट स्ट्राइकआउट एनोटेशन कैसे जोड़ें। सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को कुशलतापूर्वक बढ़ाएँ।
weight: 26
url: /hi/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन जोड़ें

## परिचय
इस ट्यूटोरियल में, हम जानेंगे कि .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन कैसे जोड़ा जाए। यह लाइब्रेरी विभिन्न दस्तावेज़ प्रकारों की व्याख्या करने, सहयोग बढ़ाने और दस्तावेज़ समीक्षा प्रक्रियाओं के लिए शक्तिशाली उपकरण प्रदान करती है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए GroupDocs.Annotation: लाइब्रेरी स्थापित करें। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/annotation/net/).
2. विकास वातावरण: .NET विकास के लिए एक उपयुक्त विकास वातावरण स्थापित करें।
3. दस्तावेज़: टिप्पणी करने के लिए एक दस्तावेज़ तैयार रखें, जैसे कि एक पीडीएफ फ़ाइल।

## नामस्थान आयात करना
सबसे पहले, GroupDocs.Annotation की कार्यक्षमताओं तक पहुँचने के लिए आवश्यक नामस्थान आयात करें:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

अब, आइए टेक्स्ट स्ट्राइकआउट एनोटेशन को कई चरणों में जोड़ने की प्रक्रिया को तोड़ें:
## चरण 1: आउटपुट पथ को परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
यहां, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर प्रारंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
इनपुट दस्तावेज़ (इस मामले में पीडीएफ फ़ाइल) के लिए पथ प्रदान करके एनोटेटर ऑब्जेक्ट को प्रारंभ करें।
## चरण 3: स्ट्राइकआउट एनोटेशन बनाएं
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
संदेश, अपारदर्शिता, पृष्ठ संख्या, पृष्ठभूमि रंग, बिंदु (निर्देशांक), और उत्तर जैसे वांछित गुणों के साथ एक स्ट्राइकआउटएनोटेशन ऑब्जेक्ट बनाएं।
## चरण 4: एनोटेशन जोड़ें
```csharp
annotator.Add(strikeout);
```
दस्तावेज़ में निर्मित स्ट्राइकआउट एनोटेशन जोड़ें।
## चरण 5: दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजें।

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में टेक्स्ट स्ट्राइकआउट एनोटेशन कैसे जोड़ा जाए। यह शक्तिशाली लाइब्रेरी कुशल दस्तावेज़ एनोटेशन, सहयोग और दस्तावेज़ समीक्षा प्रक्रियाओं को बढ़ाने में सक्षम बनाती है।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Annotation विभिन्न दस्तावेज़ प्रारूपों के साथ संगत है?
हां, GroupDocs.Annotation पीडीएफ, वर्ड, एक्सेल, पावरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल, आप अपनी आवश्यकताओं के अनुसार एनोटेशन गुणों जैसे रंग, अस्पष्टता, फ़ॉन्ट आकार और बहुत कुछ को अनुकूलित कर सकते हैं।
### क्या GroupDocs.Annotation सहयोग सुविधाएँ प्रदान करता है?
हाँ, GroupDocs.Annotation उपयोगकर्ताओं को दस्तावेज़ों में टिप्पणियाँ, उत्तर और एनोटेशन जोड़ने की अनुमति देकर सहयोग की सुविधा प्रदान करता है।
### क्या कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप निःशुल्क परीक्षण का लाभ उठा सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मुझे GroupDocs.Annotation के लिए समर्थन कहाँ से मिल सकता है?
 से आपको सहयोग मिल सकता है[GroupDocs.एनोटेशन फ़ोरम](https://forum.groupdocs.com/c/annotation/10).