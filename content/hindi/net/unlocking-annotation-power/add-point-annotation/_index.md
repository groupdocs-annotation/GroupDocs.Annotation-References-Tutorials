---
title: दस्तावेज़ में प्वाइंट एनोटेशन जोड़ें
linktitle: दस्तावेज़ में प्वाइंट एनोटेशन जोड़ें
second_title: GroupDocs.Annotation .NET API
description: .NET के लिए GroupDocs.Annotation का उपयोग करके PDF में पॉइंट एनोटेशन जोड़ने का तरीका जानें। निर्बाध एकीकरण के लिए चरण-दर-चरण मार्गदर्शिका।
type: docs
weight: 17
url: /hi/net/unlocking-annotation-power/add-point-annotation/
---
## परिचय
.NET के लिए GroupDocs.Annotation एक शक्तिशाली उपकरण है जो डेवलपर्स को प्रोग्रामेटिक रूप से दस्तावेज़ों में विभिन्न प्रकार के एनोटेशन जोड़ने की अनुमति देता है। इस ट्यूटोरियल में, हम C# का उपयोग करके दस्तावेज़ में पॉइंट एनोटेशन जोड़ने पर ध्यान केंद्रित करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1. C# प्रोग्रामिंग भाषा की बुनियादी समझ।
2. आपके सिस्टम पर विज़ुअल स्टूडियो स्थापित है।
3.  .NET लाइब्रेरी के लिए GroupDocs.Annotation स्थापित किया गया। आप इसे यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/annotation/net/).

## आवश्यक नामस्थान आयात करना
आरंभ करने के लिए, आपको अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करना होगा:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## चरण 1: आउटपुट पथ को परिभाषित करें
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
इस चरण में, हम आउटपुट पथ को परिभाषित करते हैं जहां एनोटेटेड दस्तावेज़ सहेजा जाएगा।
## चरण 2: एनोटेटर प्रारंभ करें
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 यहां, हम आरंभ करते हैं`Annotator` इनपुट दस्तावेज़ ("input.pdf") के साथ ऑब्जेक्ट।
## चरण 3: प्वाइंट एनोटेशन बनाएं
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 इस चरण में, हम एक बनाते हैं`PointAnnotation` ऑब्जेक्ट बनाएं और उसके गुण जैसे स्थिति, संदेश, पृष्ठ संख्या और उत्तर निर्दिष्ट करें।
## चरण 4: एनोटेशन जोड़ें
```csharp
annotator.Add(point);
```
यहां, हम दस्तावेज़ में निर्मित बिंदु एनोटेशन जोड़ते हैं।
## चरण 5: दस्तावेज़ सहेजें
```csharp
annotator.Save(outputPath);
```
अंत में, हम एनोटेटेड दस्तावेज़ को निर्दिष्ट आउटपुट पथ पर सहेजते हैं।

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs.Annotation का उपयोग करके किसी दस्तावेज़ में पॉइंट एनोटेशन कैसे जोड़ा जाए। इस शक्तिशाली लाइब्रेरी के साथ, आप एनोटेशन कार्यात्मकताओं को शामिल करके अपने दस्तावेज़ प्रबंधन अनुप्रयोगों को बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs.Annotation सभी दस्तावेज़ प्रारूपों के साथ संगत है?
हां, .NET के लिए GroupDocs.Annotation पीडीएफ, माइक्रोसॉफ्ट वर्ड, एक्सेल, पावरपॉइंट और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं एनोटेशन के स्वरूप को अनुकूलित कर सकता हूँ?
बिल्कुल! .NET के लिए GroupDocs.Annotation आपके एप्लिकेशन की आवश्यकताओं के अनुरूप एनोटेशन की उपस्थिति को अनुकूलित करने के लिए व्यापक विकल्प प्रदान करता है।
### क्या .NET के लिए GroupDocs.Annotation के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप निःशुल्क परीक्षण का लाभ उठा सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं .NET के लिए GroupDocs.Annotation से संबंधित किसी भी समस्या या प्रश्न के लिए समर्थन कैसे प्राप्त कर सकता हूं?
 आप GroupDocs.Annotation फोरम से समर्थन प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/annotation/10).
### क्या मैं परीक्षण प्रयोजनों के लिए अस्थायी लाइसेंस प्राप्त कर सकता हूँ?
 हां, आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).